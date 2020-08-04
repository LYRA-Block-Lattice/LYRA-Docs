# Lyra Testnet Node Windows Setup Guide
This guide was originally created by Lyra community member Roggy Dog - thank you!

## System Environment:
This guide was tested on Windows Server 2019 VM, hosted on AWS, using Administrator user.
Using default user “UserName”. Substitute with your username in place of “UserName” in examples below.

## Set Environment Variable.
* In windows search box type "view advanced" and open `View advanced system settings`.
* Click on `Environment Variables`
* Click on `New…`, under User variables for UserName.
* For Variable name: `LYRA_NETWORK`
* For Variable Value: `testnet`
* Click `OK`

## Install MongoDB database service
* Download MongoDB (4.4 is current) from https://www.mongodb.com/download-center/community
* Install it as a service as per directions from https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/

## Configure MongoDB:
* Start mongo shell (File Explorer, go to `C:\Program Files\MongoDB\Server\4.2\bin\` directory and double-click on `mongo.exe`) to create databases and users.
* `>use lyra`
* `>db.createUser({user:'lexuser',pwd:'alongpassword',roles:[{role:'readWrite',db:'lyra'}]})`
* Exit mongo

## Install the latest .NET Core SDK
from https://dotnet.microsoft.com/download

## Install Lyra 
* Download the newest version of lyra code from https://github.com/LYRA-Block-Lattice/Lyra-Core/releases 
* Extract the file (using 7-zip, for example). You’ll be presented with a folder named Lyra. Move it to `C:\Users\UserName`. 

## Generate a wallet
* Open a command prompt and change to the `lyra\cli` directoy:

`cd C:\Users\UserName\lyra\cli`
* Type this command (poswallet is the newly created wallet name, you can change it if you’d like, but I find it’s easier to leave it):

`dotnet lyra.dll --networkid testnet -p webapi -g poswallet`

* Exit after making a note of newly generated wallet address (account id) and private key.

## Prepare to run a node
* Modify `C:\Users\UserName\.Lyra\config.testnet.json` file - change mongodb account/password, 
change the wallet/name (was poswallet) to the name you created in the previous step. It should look something like this:

`"DBConnect": "mongodb://lexuser:alongpassword@127.0.0.1/lyra",
         			        },
        		"Wallet": {
          			"Name": "poswallet"
       	 	}`
	
* Open a command prompt and change directory: 

`cd C:\Users\UserName\lyra\noded`

* Fix the dotnet certificate by entering the following:

`dotnet dev-certs https --clean`

`dotnet dev-certs https`

* Open ports `4503`, `4504`, `4505` in Windows and your router’s firewall if you have one.

* Give Lyra node a testrun to see if all is well:

`dotnet lyra.noded.dll`

The node's terminal window should show something like this:
`info: ConsensusService[0]`
`      BillBoard updated! `

## Checking a node status

`http://localhost:4505/api/Node/GetSyncState` should return somethign like this: 

`{"networkID":"testnet","signature":null,"syncState":0,"lastConsolidationHash":"FyMAkxXUGKG7Dw9qhhjX1sSdUDfrYHzyqKeRxR72VfLg","status":{"accountId":"LH3zYaMTh61kpufRdese6euGgaoL2UpkCHNFmrsoXgdBnU9ZtwP7t88sCmvqi2damMVJveLNnc1F8wveiNu3d7VDocf6mS","version":"LYRA Block Lattice 1.6.0.0","state":3,"totalBlockCount":483,"lastConsolidationHash":"FyMAkxXUGKG7Dw9qhhjX1sSdUDfrYHzyqKeRxR72VfLg","lastUnSolidationHash":"0BC1315FCBC8B11CF16C68BD20DB35FB3A517839DCD938264EA6D2AA07697BA5","connectedPeers":5},"resultCode":0,"resultMessage":null}`

`http://localhost:4505/api/Node/GetBillboard` displays all connected nodes and primary authorizers.

Your node also should show up here:

`https://blockexplorer.testnet.lyra.live/showbb`

However, it will show API Status as `Failed to connect` if the node does not have public static IP assigned, or firewalls are not open for port 4505, or port forwarding is not set up.

## Making your node a primary authorizer
In order to make your node a primary authorizer, you need:

* Make sure the node account (default name is poswallet in the previous instruction above) has a stake balance - at least 1,000,000 LYR. 
To get test LYR, please write to [Telegram group](https://t.me/joinchat/F25OCR1H3Fdq_IUNJfclSQ) or email to info@lyra.live.
* Make sure someone (another account) voted for your node’s account using votefor command, 
and the vote is greater than the minimum vote for existing primary authorizer (this is not an issue yet in testnet as there are still available slots for primary authorizers).
There is `votefor` command in CLI wallet.
