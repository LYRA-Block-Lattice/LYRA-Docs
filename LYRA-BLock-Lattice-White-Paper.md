# LYRA Block Lattice

#### *White Paper*

##### LYRA Block Lattice Developers

##### Version 2.0

##### June 28, 2020

##### Based on original white paper written on January 7, 2019 by Slava Gomzin

## Primary Objectives of the LYRA Block Lattice

* Create a payment platform that provides  “out of the box” basic features of modern payment processing networks such as privacy, real time authorizations, buyer-friendly fee structure, multi-currency support, special merchant transaction flows, and custom merchant tokens
* Eliminate dependency on Proof of Work
* Provide virtually unlimited scalability to enable TPS (transactions per second) rates competitive with existing “traditional” payment processing networks
* Eliminate a prolonged locking of funds in user wallets (both payer and payee) caused by waiting for multiple “block confirmations”
* Reduce the network latency that affects transaction authorization times to the levels acceptable by the payment industry
* Eliminate dependency on a single, large, continuously growing blockchain database
* Provide built-in open banking features that would provide financial benefits to all stakeholders 
* Decouple the payment platform from any specific cryptocurrency

## Basic Use Cases
Once a user created LYRA account and deposited funds, they can perform the following actions:
### Receive a share of revenue from transaction processing
A user can delegate a vote for the authorizer node of their choice and start receiving their share of authorizer’s revenue paid from the transaction fees processed by the authorizer.   
### Make an instant, zero-fee payment to online or brick-and-mortar merchant
No fee is charged to the buyer when paying a merchant using LYRA account balance. Also, there is no cryptocurrency network fee since cryptocurrency is already deposited to the LYRA account. 
### Instantly send crypto or fiat currency to any person using email address
Special one-time access code will be emailed to that person. Once the recipient’s LYRA account is created, the transfer is finished. The recipient can use the new balance to make a payment to a merchant, or transfer funds within LYRA network, or withdraw crypto or fiat currency to an external wallet or account.
### Instantly send crypto or fiat currency to any person with zero fee or small symbolic fee
The LYRA transfer fee is significantly lower than network fees of major cryptocurrencies. First transactions on LYRA accounts might require zero fee. Since crypto or fiat currency is already deposited to the LYRA account, there is no external blockchain network fee. Unlike a typical blockchain transaction, there is no need to wait minutes to hours for several confirmations because funds are already deposited to the LYRA account, and the transfer is performed inside the LYRA network.
### Host an authorizer node and earn transaction processing fees 
Anyone can become an authorizer by setting up an authorization node. The authorizer starts receiving revenues after it receives enough votes from LYRA account holders to move to the top of the authorizers list. 
### Instantly exchange crypto or fiat currencies to other digital assets
A user can exchange their balance to other digital assets (coins, tokens, stablecoins, fiat) supported by LYRA. For example, a merchant can set up automatic exchange of payments received in Bitcoin or other crypto into fiat currency (stablecoins representing fiat currencies deposited to LYRA account) to always get payouts in fiat and eliminate any effect of crypto volatility on its business.
### Withdraw balance to external wallet 
Balance on the LYRA account can be withdrawn and sent to any external wallet, anytime. Thus, the user can use their deposit to collect revenues, but the same deposit can be used to pay anyone, anytime.
### Receive instant payments from customers
A merchant can use LYRA point of sale to receive instant payments online or in brick-and-mortar stores in various fiat and crypto currencies. The payouts can be converted to another crypto of fiat currency and stored on LYRA merchant account or withdrawn anytime.
### Create a custom token
LYRA custom token can be easily created by any user by adding a new currency type and generating a genesis block - no smart contracts required as various predefined token types already have properties and behaviours tailored for particular functions.

## Principles 
The main goal of LYRA is creating a system capable of quickly transferring money from entity A to entity B without a central authority in the middle, i.e. making unconditional, permissionless, instant payments. To eliminate any false expectations from the beginning: such a transfer is only possible with digitized money like crypto. Whenever “traditional” form of payment is involved (cash, plastic card, bank account), it must be digitized (for A) and de-digitized (for B) using semi-centralized or decentralized entities such as exchanges or brokers. At first glance, this is a serious limitation. But looking from a historic perspective, assuming crypto will supersede traditional forms of money handling, such a system eventually will become fully decentralized. 

### Currencies vs Payment Systems
People often confuse between currency and payment system. Currency is Money. Payment System is a mechanism that allows currency to change the owner (transacting).
US dollar is currency. Euro is currency. US dollar bills and coins (cash, banknotes) are a payment system that enables face to face transactions. Visa and Mastercard are payment systems that enable non-cash, electronic transactions. PayPal is a payment system that allows to safely transact online.
Bitcoin is native online currency (cryptocurrency, or simply crypto), with basic “built-in” payment system that allows to process Bitcoin transactions online. There are many other crypto in existence.
The world doesn’t need another currency, but it needs a permissionless, secure, private, fast, and convenient payment system that would be able to process payments and transfers both online and in brick-and-mortar stores, in various currencies and cryptocurrencies. Only decentralized payment systems can provide absolute privacy, highest security, and undiscriminating access to buyers and merchants. Not to mention the fact that only decentralized payment systems can operate decentralized cryptocurrencies without reducing the value of their fundamental properties.

### Traditional Payment Systems vs Cryptocurrencies
Traditional payment systems operate with existing, established currencies, which allows them to focus solely on the payment processing domain. Crypto payment systems, in addition to payment systems, have a burden of taking care of their own underlying currency - something that is usually being taken care of by national governments, banks, or huge communities such as Bitcoins and financial corporations. As a result - inconvenient, slow, insecure payment system, or illiquid, volatile currency, or both.

### Lyra vs Traditional and Crypto Payment Systems
Unlike other crypto, Lyra is a pure payment system which does not have any “built-in” underlying currency or token. Special Lyra Starter Token is created and used to fund the initial development and kick-off the delegated proof-of-stake voting and authorization mechanisms on the initial stage of the project.
Like traditional payment systems, Lyra operates with existing currencies, so it is completely free of monetary policies, volatility, and other concerns not related to the payment processing domain. As a result, Lyra has characteristics that are difficult or impossible to achieve using mono-cryptocurrency systems: high speed, virtually unlimited scalability, and versatility of payment methods. What differentiates it from traditional payment systems, however, is decentralization, which opens a pandora box of priceless features: undiscriminated permissionless access, security, privacy, low fees, open participating economy, and more. 

### PoW vs DPoS
Continuous emission and rapidly growing supply of “mineable” coins contribute to high volatility of those coins. Continuous emission is required for proof-of-work blockchains in order to keep them going. The miners receive significant incentives in a form of block rewards, even if transaction volume is insignificant. Therefore, a mineable blockchain becomes “profitable” even if it does not carry a significant payment function. In absence of voracious miners, the proof-of-stake systems can be sustainable with constant supply. The authorizers’ rewards should be received from transaction fees instead. 

## Design Concepts
Nano was the first cryptocurrency that implemented block lattice, where transactions are recorded in individual accounts (blockchains) instead of single central blockchain.[1] LYRA introduces a similar concept where transactions are also recorded on individual chains but send and receive blocks are not linked directly to preserve privacy.

### Ledger
Unlike traditional bitcoin-like blockchain, where all transactions are compiled in blocks in a single blockchain, block lattice (introduced by Nano) is a collection of multiple blockchains. That’s why we also call it blocklist as that’s how exactly the Lyra node database looks like - a big list (collection in nosql database terms) of blocks. Each user account adds transactions to their own blockchain. Such design enables extremely high scalability, instant authorization and settlements, super light clients, and many other features.  
### Transactions
Each Lyra user maintains its own blockchain called account. Each block contains a single transaction. The network does not maintain a single chain of blocks, which allows it to process transactions faster.
Lyra transaction consists of send and receive blocks. The sender's wallet app generates a send block and sends it to the authorizer nodes for authorization. Once a send block is authorized by the quorum of authorizers, it is added to the sender account’s blockchain.
When a recipient receives the broadcasted authorized send block, it generates the receive block and sends it to the authorizers for authorization. Once authorized, the receive block is added to the recipient account’s blockchain (which is also a part of chain collection).
Compared to traditional payment processing flow, send block processing is similar to authorization phase, while receive block corresponds to the settlement phase of the payment transaction processing. However, once a send block is accepted by the network, Lyra transaction is considered irreversible, even before the receive block is created by the recipient. 
### Consensus
Lyra secures its ledger using proprietary consensus algorithm based on concepts of block lattice, Delegated Proof of Stake, and Byzantine Fault Tolerance. Each concept contributes to security and performance of the system.
Each Lyra transaction is approved by a group of authorizer nodes elected through a voting process. Transaction is considered approved and final when it collects signatures from supermajority (2⁄3+1) of the primary authorizers. Each transaction is located in its own block, with the blocks chained into the individual account blockchains. Authorizer nodes communicate in the most efficient way because they “know” each other. Combination of these factors create a highly secure and super fast authorization process.

### Delegated Proof-of-Stake
Several successful attempts have been made to eliminate proof-of-work and fully replace it with proof-of-stake. Several “high-ranking” crypto projects (EOS, Tezos, Lisk, BitShares, Nano, Ark) have implemented a delegated proof-of-stake (DPOS), or based their consensus mechanism on DPOS principles (Cardano). In DPOS all participants can vote for a few nodes by delegating their coin balances to the nodes they trust. The more votes (the greater stake balance) the node receives, the higher its position and the possibility of being elected as an authorizing node.
It is preferable that the voting currency has a finite supply and be fairly distributed among the network participants. Lyra tokens will be used as the voting token. Account holders can vote for an authorizer by their account balance. Each voting account is linked to a particular authorizer. The dividends come from transaction fees which the authorizer earns by participation in the authorization process. This way, all users are motivated to vote as they participate in Lyra rewards sharing, i. e. account holders become stakeholders of the Lyra system.
In traditional centralized payment systems such as Visa or PayPal, the earnings are received by the corporation that owns the network, and some part is distributed to shareholders. In LYRA, all the earnings are shared directly between the authorizers and voting account holders, with no corporate bureaucracy in the middle.
#### Authorizer Nodes
A candidate node that receives more votes than any authorizer node becomes an authorizer, while the authorizer with least votes moves back to the candidates group. Both authorizer and candidate nodes receive rewards (Tx fees). We suggest limiting the number of authorizer nodes to 21 primary authorizers. The remaining nodes with minimum voting balance become backup authorizers.

### Locked Balance Solution
Most cryptocurrencies have a period of time called “locked balance”, when partial or all funds in a wallet cannot be used for new transactions. It happens after every transaction no matter whether you receive a new transfer or send funds to someone. This way most blockchains prevent spending of funds located in blocks that are not yet “confirmed” by the network. Proof of work blockchains are especially prone to this problem because recent blocks can be “rewritten” by someone who has more computing power. Such a “fork” makes transactions in several recent blocks invalid minutes or even hours after they were initially “accepted” by the network and even added to a blockchain.
Locked balance problem is very inconvenient and prevents adoption by the mainstream. Imagine a situation when you have $1000 in your payment card and you bought something for just $1 but cannot use the card for another hour as the entire card balance is locked by your bank.
Lyra solves the locked balance problem, thanks to block lattice architecture. Since every transaction is written into its own block, and every transaction block is individually and instantly authorized by the network, there is no need to lock any balance to prevent double spending. Once a transaction block is signed by the authorizer nodes it becomes the part of an immutable account blockchain which cannot be modified. The account balance becomes spendable right after authorization response (for any transaction) is received from the network.

### Pruning
Both send and receive blocks contain the updated account balance (for sender and recipient account respectively), which enables pruning, i.e. all nodes don’t have to store the entire chains but can only store the last blocks. Thus, wallets and other applications don’t need to scan the entire blockchain in order to retrieve the current account balance, which enables real time financial transactions and dramatically reduces system requirements for CPU, memory, and disk space. This feature also solves the problem experienced by most crypto with single blockchain - continuously growing transaction databases, which continuously increases the cost of operation of every network node.   

### Scalability
High scalability is achieved by using a chain collection of individual accounts, where transactions belonging to different accounts can be added simultaneously, without the need to accumulate them in blocks and maintain a single continuous chain of blocks. Thus, LYRA has virtually unlimited scalability, which is only limited by authorization nodes performance, and can achieve TPS (transactions per second) numbers competitive with traditional payment processing networks.

### Privacy
Both send and receive blocks are protected by using the methods defined in CryptoNote white paper and its subsequent enhancements, such as unlinkable payments (aka stealth addresses) and ring confidential transactions.[2, 3] The transaction amounts and the wallet addresses are obfuscated, i.e. an observer cannot establish a link between the sender and the recipient, or determine any transaction and account balances. 

### Transfer and Pay Transactions
Although Transfer and Pay are both spending transactions which use the same mechanism described above (send/receive blocks), they are processed in a slightly different way. Since a Pay transaction is intended for merchants to collect payments from their customers in real time, it is prioritized over regular transfers when processed by the network.

### Custom Tokens
There will be reserved codes for tokens created by developers for major crypto and fiat currencies. Other codes can be used by any user for creating custom tokens such as merchant gift certificates or loyalty reward points. All tokens are processed by authorizers in the same way, but only reserved notes can participate in the voting process. 

LYRA tokens can be created as either indistinguishable (fungible) or unique (non-fungible, personalized). In fact, there are uses for both inside most applications, with transition from fungible to non-fungible at the time of redemption. Example: fungible reward tokens (as accumulated loyalty points) and non-fungible discount/gift tokens (as loyalty reward redemption mechanism).

## Special Payment Applications
### Void, Pre-Auth, and Complete Transactions
The fact that every LYRA transaction consists of two blocks (send and receive) enables very important functionality which is not available on regular blockchain while widely used by the payment card industry for years. Pay transactions can be either accepted by the recipient (by generating a complementary Receive block) or rejected (by generating special Void transaction).

LYRA can also easily implement pre-authorization and completion mechanisms which are absolutely required for hospitality, gas stations, and other segments of the payment processing industry.

Pre-auth/Complete is essentially a hard-coded smart contract. Pre-auth transaction is a send block of Pay transaction with a special flag. Pre-auth must be followed by Complete, which is another transaction issued by the merchant with the change amount that cannot exceed the original pre-auth amount. Complete can be issued with zero amount which means that the entire amount of pre-auth is charged by the merchant. If Complete is not issued by the merchant within a predefined time interval (7-30 days), the sender’s wallet can issue a reverse transaction cancelling the pre-auth.  

### LYRA Plastic Payment and Cold Wallet Cards
The fact that LYRA updates the current account balance for each block/transaction allows very lightweight implementation of spending cards. The smart card has to store only one recent transaction in order to be able to create a new spending transaction and trace the account balance correctly. The card does not need to use any external “help” in order to be able to construct the spending transaction since there is always only one input (the recent balance) used in the transaction. Also, the most recent incoming transaction (receive block), if the card is “bi-directional”, can be easily requested through the payment terminal without any violation of privacy as all the account’s blocks/transactions are encrypted. 

## Conclusion

LYRA combines the best ideas and technologies currently available in the crypto space and payment industry, and applies them to the financial payment network space. Given the limitations of PoW and blockchain, DPoS and block lattice ultimately provide the best features which are crucial for the modern payment platform.  

## References

1. Nano: A Feeless Distributed Cryptocurrency Network. Colin LeMahieu. https://nano.org/en/whitepaper

2. CryptoNote V2.0. Nicolas van Saberhagen. https://cryptonote.org/whitepaper.pdf 

3. Ring Confidential Transactions. Shen Noether, Adam Mackenzie and Monero Core Team. https://lab.getmonero.org/pubs/MRL-0005.pdf


 

 







 
