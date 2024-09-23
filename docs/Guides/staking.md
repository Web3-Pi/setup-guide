Solo Staking is the most straightforward way to realize profit from the Ether (ETH tokens) you own.
At minimum, it only requires you to deposit 32 ETH into an official staking deposit smart contract
and to run a validator on your full Ethereum node, while ensuring the node stays connected 
to the Internet.

By running your validator on the Ethereum mainnet, you become part of the most crucial component 
of the Ethereum ecosystem - the layer which maintains the consensus of the blockchain, 
and therefore ensures its resilience against attacks.

While helping secure the Ethereum mainnet by validating the transaction blocks, you gain
a small fee every epoch (~6 minutes) as long as your validator is able to sign and sent the required
attestation in time for it to be included in the chain.

## Solo-staking on Web3 Pi 

Web3 Pi provides all the necessary components required to allow you to start staking on the Ethereum
mainnet. It runs both the execution layer client (`geth`) and the consensus layer client (`nimbus`).
Once it's set-up and the clients are synchronized, the only remaining steps are creation of the
staking deposit keys, depositing the Ether tokens and adding the created keys to your the consensus
layer client.

The good news is that you're not even limited to a single validator and a single 32 ETH stake. 
Even if you'd like to stake larger amounts, our tests have shown it should be possible to run
as many validators as you require on a single Raspberry Pi 5.

In this guide we'll show you how easy it is.

### Prerequisites

* 32 Ether
* a fully-synced node
* Metamask installed and paired with the wallet you wish to stake ETH from

Also, while we enumerate all the critical steps, needed to start staking with Web3 Pi,
ultimately, it's your Ether, your wallet and your node. Therefore, you are still responsible for 
your own education on this matter, to ensure you take all the necessary precautions to keep your
wallet, the tokens and your validator keys safe and secure. While following the steps, please
don't skip any recommended reading or cut corners when asked for actions that aim to make the
process safe. 

Moreover, we don't claim to be the source of knowledge and expertise on the topic nor do we
intend for this guide to be exhaustive source of information.
If you're uncertain of any aspect of running your own Ethereum node,
staking ether or anything else we're about to discuss, by all means, we encourage you to do 
your own research.
You're also free to share your newly-acquired wisdom with us if you think our guide misses some
crucial bit of information on the topic.

### Create the deposit

#### 1. Go to https://launchpad.ethereum.org/

Visit https://launchpad.ethereum.org/ and click on "Become a validator".

![](../assets/staking/launchpad_main.png "The Ethereum Staking Launchpad website")

#### 2. Proceed through the advisories checklist

Make sure to read all the contents carefully before proceeding through each step.
Don't skip anything unless you're perfectly sure what each step entails.

![](../assets/staking/advisories.png "Checklist of advisories screen")

#### 3. Choose your clients

The launchpad is aimed at a general user and there are various considerations for choosing
specific execution and consensus layer clients. Due to mechanics of the global staking ecosystem,
to strengthen the network and limit the impact of potential attacks, it's generally recommended 
to choose a minority client.

So, while the launchpad enables you to choose any of the available clients,
the default, battle-tested configuration for the Web3 Pi includes `geth` and
`nimbus` specifically and that's what you should choose unless you're ready to
set up and run any other of the available clients on your own.

![](../assets/staking/execution_choice.png "Choice of the execution client screen")

![](../assets/staking/consensus_choice.png "Choice of the consensus client screen")

#### 4. Generate key pairs

