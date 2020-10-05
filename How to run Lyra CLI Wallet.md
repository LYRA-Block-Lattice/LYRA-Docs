# How to run Lyra CLI Wallet

**Note 1:** You don’t need to run Lyra node in order to use the Lyra network. Simply install CLI wallet by following instructions below and start exploring the network by making transfers or even creating your own tokens! Mobile wallets are coming soon as well.

**Note 2:** These are instructions for Windows, but they can be used with minimal to zero modifications on Mac or Linux. Lyra can run on the following OS platforms: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md

## Install the latest .NET Core 3.1 SDK:
https://dotnet.microsoft.com/download/dotnet-core/3.1

## Install Lyra
* Download newest release of lyra from https://github.com/LYRA-Block-Lattice/Lyra-Core/releases
* Extract the file (using 7-zip for example: https://www.7-zip.org/). 
* You’ll be presented with a folder named Lyra. You can move it to “C:\Users\”UserName”. 

## Launch CLI wallet app
* Open a command prompt (Start -> cmd) and change current directory:
`cd C:\Users\”UserName”\lyra\cli`

* Type this command to launch the wallet on testnet:
`dotnet lyra.dll --networkid testnet -p webapi` 
* Type this command to launch the wallet on mainnet:
`dotnet lyra.dll --networkid mainnet -p webapi` 

Once you specified the account name (or created a new one), the client will automatically find the LYRA node and connect.

## To open a new account (aka “wallet”) with default name 'My Account'
Follow the initial client prompts and press Enter key twice when prompted with the following questions: 

`Press Enter for default account, or enter account name:` 
`Local account data not found. Would you like to create a new account? (Y/n):`

## To request testnet LYR tokens: 
To get test LYR, please write to [Telegram group](https://t.me/joinchat/F25OCR1H3Fdq_IUNJfclSQ) or email to info@lyra.live with the subject *“Testnet LYR token request”* and specify your account ID (wallet address). 

## To get your account ID: 
Enter `id` command

## To open another account
Launch another instance of CLI wallet (see above). When prompted, enter desired account name.

## To make a transaction - transfer LYR from one account to another
* Enter `send` command
* Enter account id of the recipient account (if you don’t know the account id of the recipient, ask the recipient to type `id` command in the terminal window of the recipient account).
* Enter transaction amount

**Note** that the recipient’s CLI wallet does not have to be running at the time of send transaction; you just need to know the account id. Once the recipient wallet is up, it will automatically process the incoming transactions. Type sync if you don’t see an updated balance on the recipient's account.

## To see the balance of the account
Enter `balance` command

## To scan for new incoming transfers 
Enter `sync` command 

## To backup your account
Enter `key` command and save the private key in safe place (for example, password manager app). You can restore your account on different device using this private key.

## To see all CLI wallet commands
Enter `help` command

Note that some commands are not implemented yet





