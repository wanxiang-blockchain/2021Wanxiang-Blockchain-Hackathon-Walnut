# 2021Wanxiang-Blockchain-Hackathon-Walnut

## 1  Introduction
一直以来，无论是在传统社区还是区块链社区里，社区运营者都苦恼于如何使社区能够活跃起来，最初因为区块链通证经济的兴起，社区会选择发行自己的社区代币，以激励参与到社区里的用户，促使社区能在社区代币的驱动下拥有更高的活跃度，更高的价值捕获。比如，一个运行共享应用软件的社区会发行自己的代币，共享和租赁物品都可以获取到社区的代币，通过这种方式，社区成员在使用产品的同时，也获取到了额外的经济激励。

For a long time, whether in traditional communities or blockchain communities, community operators have been distressed about how to make the community active. Initially due to the rise of the blockchain token economy, the community will choose to issue its own community tokens to incentivize users participating in the community, and promote the community to have a higher degree of activity and value capture driven by the community tokens. For example, a community running a sharing application issues its own tokens, which can be earned by both sharing and renting items. In this way, community members receive additional financial incentives when using the product.

然而就目前来看，社区只是发行自己的代币是远远不够的。社区发行自己的代币后，短期能够起到刺激社区活跃度、提高社区价值的作用，长期来看，社区代币最终往往因为缺乏一个完整的价格支撑体系或者说没有形成良好的经济内循环，而不能给社区带来实质性的改变。因此让社区代币能够真正的在社区里健康的流通起来成为了行业急需解决的难题。

For now, however, it is not enough for the community to simply issue its own tokens. After the community issues its own tokens, it can play a role in stimulating community activity and increasing community value in the short term. But in the long run, community tokens often fail to bring substantial changes to the community due to the lack of a complete price support system or the lack of a good internal circulation of the economy. Therefore, enabling community tokens to truly circulate in the community has become a problem that the industry urgently needs to solve.

PoS共识算法数学公式: $ [1] $的流行给我们提供了一套新的解决思路。PoS 共识算法用来解决区块链网络在原有的 PoW 共识算法数学公式: $ [2] $下 TPS 低，系统可扩展性差等问题。不同于 PoW 共识算法任何人只要提供硬件设备便可以接入区块链网络成为验证者，在基于 PoS 共识算法的区块链网络中，用户需要抵押一定数量的网络资产，然后再成为了验证者后通过验证区块获取奖励；当退出作为验证者时，仍然可以取回自己抵押的资产。在 PoS 共识系统下，参与到网络中节点不用再进行硬件竞赛，以至于耗费大量的电力资源。这种抵押区块链网络原生资产并在此基础上获取收益的经济模型，具有良好的经济闭环，能够使区块链网络在一个健康的经济循环下长久稳定的运行下去。

The popularity of the PoS consensus algorithm数学公式: $ [1] $ provides us with a new set of solutions. The PoS consensus algorithm is used to solve the problems of low TPS and poor system scalability under the original PoW consensus algorithm 数学公式: $ [2] $ of the blockchain network. Unlike the PoW consensus algorithm, which enables anyone who provides hardware device can access the blockchain network to become a validator, in a blockchain network based on the PoS consensus algorithm, users need to stake a certain amount of network assets, and then become a validator to obtain rewards by verifying the block. When you exit as a validator, you can still get back your staked assets. Under the PoS consensus system, nodes participating in the network no longer need to compete in hardware, which consumes a lot of power resources. This economic model that stakes the original assets of the blockchain network and obtains income on this basis has a good economic closed loop and can make the blockchain network operate stably for a long time under a healthy economic cycle.

遗憾的是目前这种经济模式只被用于区块链网络本身的共识系统，它并没有为运行在区块链网络中的应用即背后所代表的一个个区块链应用社区带来直接的价值。而 Nutbox 要做的，便是构建一个开放的资产质押协议，能够让区块链社区在基于 PoS 共识算法的区块链网络中，为自己的社区资产构建质押经济模型。

Unfortunately, this economic model is currently only used in the consensus system of the blockchain network itself. It does not bring direct value to the applications, that is, the communities running in the blockchain network.
What Nutbox is trying to do is to build an open asset staking protocol that allows the blockchain community to build an economic model of the staking for its community assets in a blockchain network based on the POS consensus algorithm.

图片: https://uploader.shimo.im/f/cctoTMHXX4Ngpfts.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc
图 1 一个运行在 PoS 区块链网络中的 Staking 工厂
Figure1, A Staking Factory Runing In PoS Blockchain Network

## 2  Background
Nutbox 最终的目的是支持多个 PoS 链的资产抵押，并让区块链社区能够在基于各自所运行的 PoS 链的质押模型上构建自己的质押经济业务。因此，Nutbox 协议需要部署到支持跨链互操作的区块链网络中，而我们发现，这正是 Polkadot 所做的事情。polkadot 由 ethereum 黄皮书起草者，parity 公司创始人 Gavin Wood 博士创立，与 ethereum2.0 专注于采用分片技术提高网络可扩展性不同，polkadot 引入 relaychain 和 parachain，relaychain 由 parity 公司开发运营，所有人可以加入成为网络验证者，网络基于 NPoS 算法数学公式: $ [3] $选择每一个 session 的验证者集合，被选中的验证者负责本轮区块的验证，并获取奖励；parachain 由任意团队或个人开发，与一般区块链网络不同的是，parachain 没有自己的共识系统，parachain 区块由 relaychain 进行验证，parachain 区块构建后，将其以 PoV 格式广播给 relaychain 的验证者，通过验证后的区块将会被存储在 parachain 的网络中。Polkadot Relaychain 像每个 Parachain 的安全管家，负责各个 Parachain 的共识安全，让 Parachain 可以专注自己的业务。

The ultimate goal of Nutbox is to support the collateralization of assets across multiple PoS chains and to enable the blockchain community to build their own staking economic business based on the staking model of the PoS chains they are running. Therefore, the Nutbox protocol needs to be deployed into a blockchain network that supports cross-chain interoperability, and we found that this is exactly what Polkadot does.
Polkadot was founded by Dr. Gavin Wood, creator of Ethereum Yellow Book and founder of Parity Inc. Unlike Ethereum2.0, which focuses on using sharding数学公式: $ [15] $technology to improve network scalability, Polkadot introduces relaychain and parachain.
Relaychain is developed and operated by Parity , and everyone can join as a network validator. The network selects the set of validators for each session based on the NPoS algorithm数学公式: $ [3] $. The selected validators are responsible for the verification of the block in this round and get rewards.
Parachain is developed by any team or individual. Unlike general blockchain networks, parachain does not have its own consensus system, and parachain blocks are verified by Relaychain. After the parachain block is constructed, it will be broadcast to the Relaychain validator in PoV format, and the verified block will be stored in the parachain network. Polkadot Relaychain is like the security steward of each Parachain, responsible for the consensus security of each Parachain, so that Parachain can focus on its own business.

图片: https://uploader.shimo.im/f/WhPXv7TdA8wZI8Gm.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc

图 2 Polkadot Parachain Framework
Figure2, A Staking Factory Runing In PoS Blockchain Network

Nutbox 将以”Nutbox Contracts“或”Nutbox Parachain“两种方式的一种模式运行。Nutbox Contracts 模式是在 Nutbox blockchain 尚未开发完成，并且没有成功获取到 Polkadot 的平行链插槽时的运行方式，它将作为智能合约部署到支持EVM的区块链网络中；Nutbox Parachian 模式是当 Nutbox blockchain 通过 Polkadot 平行链插槽拍卖获取到了平行链插槽（slot）后，以 Polkadot 平行链身份接入到区块链网络，将不会有自己的共识模块，而是由 Polkadot 提供共识安全并验证 Nutbox blockchain 的区块。Nutbox 在两种模式下都将支持多个 PoS 链资产的抵押，只是两种模式下的实现方式有些许差异。

Nutbox will run in either mode of "Nutbox Contracts" or "Nutbox Parachain".
The Nutbox Contracts mode is the operating mode when the Nutbox blockchain has not been developed and the Parachain slot of Polkadot has not been successfully obtained. It will be deployed as a smart contract to the blockchain network that supports EVM.
The Nutbox Parachian mode is that when the Nutbox blockchain obtains a Parachain slot through the Polkadot Parachain slot auction, it connects to the blockchain network as the Polkadot Parachain. It will not have its own consensus module. Instead, Polkadot provides consensus security and validates the blocks of the Nutbox blockchain.
Nutbox will support collateralization of multiple PoS chain assets in both modes, with slightly different implementations in both modes.

Nutbox Contracts
当 Nutbox 未能以 Polkadot 平行链的形式运行时，它将以合约的形式部署在一条支持 EVM 虚拟机的区块链网络中。这个时候所有跨链的功能都将由 LTBSV 跨链桥协议提供支持。并且在 Nutbox 设计初期便会考虑到从合约到平行链的无缝迁移。

When the Nutbox doesn't run as a Polkadot Parachain, it will be deployed as a contract on a blockchain network that supports EVM virtual machines. At this point all cross-chain functions will be supported by the LTBSV cross-chain bridge protocol. And in the early stage of Nutbox design, seamless migration from contract to Parachain will be considered.

Nutbox Parachain
当 Nutbox 作为运行在 Polkadot 生态里的 parachain 时，Nutbox 的部分跨链资产转移将直接采用 Polkadot 的跨链消息协议 XCM数学公式: $ [4] $来实现。假如 Nutbox 支持的另外一条链恰好也是一条 Polkadot 平行链，那么两条链之间将直接通过 XCM 协议的指令完成跨链转账；如果另一条链不
是 Polkadot 平行链，那么 Nutbox 将使用下文描述的 LTBSV 跨链桥协议实现资产跨链转移。

When Nutbox runs as a Parachain in the Polkadot ecosystem, part of Nutbox's cross-chain asset transfer will be implemented directly using Polkadot Cross-Consensus Message protocol, namely XCM数学公式: $ [4] $. If the other chain supported by Nutbox happens to be a Polkadot Parachain, then the two chains will directly complete the cross-chain transfer through the instructions of the XCM protocol. If the other chain is not a Polkadot Parachain, then Nutbox will use the LTBSV cross-chain bridge protocol described below to achieve cross-chain transfer of assets.

## 3  Open Community Staking Protocol(OCSP) Contract
OCSP是一套标准的合约模板，用于部署用户的资产质押业务。借助于OCSP合约，创建基于tToken的资产兑换网关和cToken的分发器，即用户进行原生资产和tToken的兑换，以及基于tToken的抵押获取cToken收益的业务逻辑。在这里，tToken和cToken均代表Nutbox网络中的两种资产类别，并非指特定的一个资产。

OCSP is a standard set of contract templates for deploying a user's asset staking business. With the OCSP contract, a tToken-based asset exchange gateway and a cToken distributor are created, that is, the business logic for users to exchange underlying assets and tTokens, as well as obtain cToken income through tToken-based staking. Here, both tToken and cToken represent two asset categories in the Nutbox network and do not refer to a specific asset.

### 3.1 Contract Topology
图片: https://uploader.shimo.im/f/nVRNfCNWUtNrm4ue.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc
图3 Contract Topology
Figure2, Contract Topology

如上图所示，OCSP主要由Registration、StakingTemplate、StakingFactory、BridgeProxy四个主要模块组成。
Registration
Registration合约用于个人或组织向Nutbox提交注册信息。
StakingTemplate
StakingTemplate合约模块包含了Nutbox实现的基于tToken的Staking经济模型，借助于该合约模板，可以创建抵押tToken或者为tToken-cToken交易对提供流动性挖cToken的抵押业务。
StakingFactory
StakingFactory工厂合约用于产生StakingTemplate合约模板实例。
BridgeProxy
BridgeProxy合约根据区块链网络的实现各有不同，在支持智能合约的区块链网络中将通过智能合约实现，比如以太坊网络中是一段solidity合约，而在Steem网络中就只是一个Steem网络中的账号。主要被跨链桥用于获取原区块链网络中与Nutbox相关的资产转移行为。

As shown in the figure above, OCSP is mainly composed of four main modules: Registration, StakingTemplate, StakingFactory, and BridgeProxy.
Registration contract is used by individuals or organizations to submit registration information to Nutbox.
StakingTemplate contract contains the tToken-based staking economic model implemented by Nutbox. With this contract template, it is possible to create a staking tToken or provide liquidity for tToken-cToken trading pairs to mine cToken staking business.
StakingFactory contract is used to generate the StakingTemplate instances.
BridgeProxy contract varies according to the implementation of the blockchain network. In a blockchain network that supports smart contracts, it will be implemented through smart contracts. For example, in the Ethereum network it is a Solidity contract, while in the Steem network it is just an account in the Steem network. It is primarily used by cross-chain Bridges to capture Nutbox-related asset transfer behavior in the original blockchain network.


### 3.2 Multi-Chain tToken
在 Nutbox 上，用户抵押原有 PoS 区块链网络的资产，获取 Nutbox 网络中对应的 tToken，tToken 与原有资产 1：1 兑换。例如，用户在 Nutbox 网络里将持有的 DOT 兑换为 tDOT，tDOT 可以参与 Nutbox 网络里所有 Polkadot 生态的项目的质押挖矿，即抵押 tDOT，获取对应社区的代币 cToken。Nutbox 将结合跨链桥技术和 polkadot XCM 支持多个 PoS 区块链网络的资产兑换。

On Nutbox, users stake the assets of the original PoS blockchain network to obtain the corresponding tTokens in the Nutbox network, which are exchanged 1:1 with the underlying assets. For example, a user in the Nutbox network can exchange DOT holdings for tDOT, which can participate in the Nutbox staking mining of all Polkadot ecological projects, i.e., stake tDOT to obtain the corresponding community's cTokens. Nutbox will combine cross-chain bridge technology and Polkadot XCM to support asset exchange across multiple PoS blockchain networks.

#### 3.2.1 tToken Exchange Gateway（TEG）
TEG contract(Nutbox 作为合约部署)和TEG pallet数学公式: $ [5] $(Nutbox 作为 Polkadot Parachain 时)负责实现 Nutbox 网络的跨链资产兑换网关。

TEG contract (Nutbox is deployed as a contract) and TEG pallet数学公式: $ [5] $ (Nutbox is used as Polkadot Parachain) are responsible for implementing the cross-chain asset exchange gateway of the Nutbox network.

图片: https://uploader.shimo.im/f/YUB5Ko5CDiNkuIo9.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc
图 4 tToken Exchange Gateway
Figure4, tToken Exchange Gateway

如上图所示，当用户用原生资产兑换tToken时，原生资产将会被锁在TEG Contract内，LTBSV验证用户资产的锁定状态【详见Deposit proof章节】，验证通过将产生对应数量的tToken到用户Nutbox账户中；用户赎回时TEG合约验证用户的tToken燃烧状态【详见tToken Buning Contract章节】，验证通过后将解锁用户锁定在TEG Contract中的原生资产。

As shown in the figure above, when a user exchanges a native asset for tToken, the native asset will be locked in the TEG Contract, and LTBSV verifies that if the user's asset is locked [shown in the Deposit proof section for details], when the verification is passed,it will generate a corresponding amount of tToken to the user In the Nutbox account; the TEG contract verifies the user’s tToken burning status when the user redeems it [shown in the tToken Burning Contract section for details], and when the verification is passed, the user’s native assets locked in the TEG Contract will be unlocked.

#### 3.2.2 Bridge Proxy Contract
桥代理合约为 Nutbox 部署到原区块链网络中的智能合约，负责存储并转移原区块链网络中的资产。资产转移完全去中心化，任何人需要从 Proxy Contract 转出资产都需要提供 Withdraw proof。经过验证后方可从合约转移资产到自己的账户中。
The bridge proxy contract is a smart contract deployed by Nutbox to the original blockchain network and is responsible for storing and transferring assets in the original blockchain network. Asset transfer is completely decentralized. Anyone who needs to transfer assets from Proxy Contract needs to provide Withdraw proof. After verification, you can transfer assets from the contract to your own account.

#### 3.2.3 tToken Issue Contract
tToken 的发行需要用户提供 Deposit proof【见 4.2.3】，Deposit proof 由 Nutbox 在用户将原区块链资产存入 Nutbox 代理合约时由LTBSV颁发给用户。用户提交Deposit proof 后，TEG的tToken Issue Contract首先验证 Deposit proof 的签名信息，经过验证的 Deposit proof 被解析为 Deposit MetaData，后者包含用户抵押的原区块链资产的金额。TEG 的tToken Issue Contract随后发行对应数额的 tToken，兑换网关为此创建一个 tToken Issurance Pair，包含了发行的 tToken 数额，用户公钥，解锁时间。处于锁定期的 tToken 将不能兑换为原区块链网络中的代币。

The issuance of tToken requires the user to provide a deposit proof [shown in 4.2.3]. The deposit proof is issued by the LTBSV to the user when the user deposits the original blockchain assets into the Nutbox proxy contract. After the user submits the Deposit proof, TEG's tToken Issue Contract verifies the signature information of the Deposit proof firstly, and the verified Deposit proof is parsed as Deposit MetaData, which contains the amount of the original blockchain assets staked by the user. TEG's tToken Issue Contract then issues the corresponding amount of tToken, and the exchange gateway creates a tToken Issurance Pair for this , which contains the amount of tToken issued, the user's public key, and the unlock time. The tTokens in the lock-up period cannot be exchanged for tokens in the original blockchain network.

图片: https://uploader.shimo.im/f/qaoVaWw1GiHknEj1.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc
图 5 tToken Issurance
Figure5, tToken Issurance

#### 3.2.4 tToken Burning Contract
用户持有的 tToken 在解锁期限到达后，可以在任何时候选择赎回自己未被锁定的 tToken（用户使用 tToken 参与 Nutbox 上的社区代币挖矿同样会被锁定）。用户选择销毁一定数额 tToken 后，TEG的tToken Burning Contract会燃烧掉同等数额 tToken，同时Nutbox向用户颁发 Withdraw proof，代理合约会验证 Withdraw proof 签名信息，验证通过后解析出 Withdraw MetaData，后者包含用户需要解锁的 tToken 数额以及用户在原区块链网络中的账户公钥。随后，代理合约将指定数额的原区块链资产转移到用户原区块链网络账户中。

When the unlocking time is reached, users can choose to redeem their unlocked tTokens at any time (users who use tTokens to participate in community token mining on Nutbox will also be locked). After the user chooses to burn a certain amount of tToken, TEG’s tToken Burning Contract will burn the same amount of tToken, and Nutbox will issue a Withdraw proof to the user. The proxy contract will verify the Withdraw proof signature information. After the verification is passed, the Withdraw MetaData will be parsed out, which contains the amount of tTokens that the user needs to unlock and the user's public key in the original blockchain. Then, the proxy contract transfers the specified amount of original blockchain assets to the user's original blockchain network account.

图片: https://uploader.shimo.im/f/hq8QJCei4ywGEBiS.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc
图 6 tToken Burning
Figure6, tToken Burning

### 3.3 Community Token(cToken) Mining & Distribution
cToken为任何组织或个人创建自己staking economy时指定的社区代币，一个基本的分发策略便是抵押tToken挖cToken，Nutbox支持多种cToken分发策略，用户可以自己指定。
cToken的挖矿算法中，我们引入了两个主要的变量因子

cToken is the community token specified when any organization or individual creates their own staking economy. A basic distribution strategy is to stake tToken to mine cToken. Nutbox supports a variety of cToken distribution strategies, which users can specify by themselves.
In the cToken mining algorithm, we have introduced two main variable factors.

shareAccumulate
共享累计因子，全局变量因子，所有用户的奖励计算都将使用到，用pool.shareAcc表示。其中pool对应为一个抵押资产种类，例如抵押tDOT和抵押tDOT- USDT交易对的LP Token分别对应两个pool，每个pool的分润比例可以设置。

Shared cumulative factors, global variable factors, will be used  for all user reward calculations , represented by pool.shareAcc. The pool corresponds to one type of staking asset. For example, staking tDOT and staking the LP of the tDOT-USDT trading pair correspond to two pools respectively, and the profit sharing ratio of each pool can be configured.

debtRewards
用户私有变量因子，表示计算该用户奖励时需要剔除的奖励额度，用user.debtRewards表示。

User private variable factor, which represents the amount of reward that needs to be excluded when calculating the user's reward,  represented by user.debtRewards. 


其中
数学公式: $ shareAcc_{pool} = shareAcc_{pool} + \frac{f_{rewards}\left\{ from, to \right\}}{totalStakingAsset_{pool}} $
其中数学公式: $ shareAcc_{pool} $初始值为0，数学公式: $ f_{rewards}\left\{ from, to \right\} $代表一定区块高度所新产生的cToken，该值在创建staking economy时指定。数学公式: $ totalStakingAsset_{pool} $表示当前pool总的抵押资产数额。
数学公式: $ user.debtRewards = user.amount * shareAcc_{pool} $
其中user.amount表示用户抵押资产数额
数学公式: $ user.rewards = user.amount*shareAcc_{pool} - user.debtRewards $
其中数学公式: $ user.rewards $表示用户在当前区块下所能获得的cToken奖励。
设置好cToken的分发策略后参与抵押的用户将会按区块获取对应数额的cToken奖励。


数学公式: $ shareAcc_{pool} = shareAcc_{pool} + \frac{f_{rewards}\left\{ from, to \right\}}{totalStakingAsset_{pool}} $
In the above formula, the initial value of 数学公式: $ shareAcc_{pool} $ is 0  and 数学公式: $ f_{rewards}\left\{ from, to \right\} $ represents the newly generated cToken at a certain block height. This value is specified when creating a staking economy. 数学公式: $ totalStakingAsset_{pool} $ represents the total amount of staking assets in the current pool.
数学公式: $ user.debtRewards = user.amount * shareAcc_{pool} $
In the above formula, user.amount represents the amount of staking assets of the user.
数学公式: $ user.rewards = user.amount*shareAcc_{pool} - user.debtRewards $
In the above formula, 数学公式: $ user.rewards $represents the cToken rewards that the user can get under the current block.
After setting up the cToken distribution strategy, the users participating in the staking will get the corresponding amount of cToken rewards according to the block.

## 4 Crosschain Bridge
Nutbox 需要处理多个区块链网络中资产的相互转移，由于不同的区块链网络区块共识算法以及区块验证逻辑都不同，Nutbox 需要分别去验证每一个区块链网络中的交易的合法性以实现跨链资产抵押。Nutbox 的跨链桥服务专门用于不同区块链网络的数据验证以及作为跨链资产转移的基础设施。

Nutbox needs to handle the bi-directional transfer of assets in multiple blockchain networks. Since different blockchain networks have different block consensus algorithms and block verification logic, Nutbox needs to verify the legitimacy of transactions in each blockchain network to achieve cross-chain asset staking.Nutbox's cross-chain bridge service is specifically used for data verification of different blockchain networks and as an infrastructure for cross-chain asset transfer.

### 4.1  What Is Crosschain Bridge
跨链桥是一种沟通两个不同区块链网络的一种技术手段。通过跨链桥，用户可以在不同的区块链网络中实现资产转移。例如，用户将 1BTC 兑换为以太坊上的 ERC20 资产 xBTC（假如 1BTC = 1xBTC），用户的比特币账户将减少 1BTC，与此同时以太坊网络中该用户账户下的 ERC20 资产将增加 1xBTC。用户可以在未来某个时候将 ERC20 资产兑换成 BTC。跨链桥技术根据应用场景的不同，有多种实现方式，每种方式的技术实现细节和去中心化程度也不一样。Nutbox 采用基于 LTBSV（如下文）实现的跨链桥技术实现跨链资产的转移和区块的数据的验证。

A cross-chain bridge is a technical means to communicate between two different blockchain networks. Through the cross-chain bridge, users can transfer assets in different blockchain networks. For example, if a user exchanges 1BTC for ERC20 assets xBTC on Ethereum (if 1BTC = 1xBTC), the user's Bitcoin account will be reduced by 1BTC, and at the same time the ERC20 assets under the user's account in the Ethereum network will increase by 1xBTC.Users can exchange ERC20 assets into BTC at some point in the future.The cross-chain bridge technology has multiple implementation methods according to different application scenarios, and the technical implementation details and degree of decentralization of each method are different. Nutbox adopts cross-chain bridge technology based on LTBSV (as below) to realize the transfer of cross-chain assets and the verification of block data.

### 4.2  Light Trustless Blokchain State Verification(LTBSV)
LTBSV 是一种去信任的区块数据验证协议，无需信任任何第三方区块数据源便可以对区块数据进行验证。即对于任何新的区块数学公式: $ Block_{n} $,使用已经被验证的最新区块数学公式: $ VBlock_{n-1} $,以及 LTBSV 验证器数学公式: $ f_{LTBSV} $则可以验证最新区块是否合法：
数学公式: $ VBlock_{n} = $数学公式: $ f_{LTBSV}\left\{ VBlock_{n-1},Block_{n} \right\} $
LTBSV 不同于区块链网络里的全节点，不需要存储整个区块数据，也不需要对区块里的每一笔交易进行验证。它和轻节点唯一不同的是不需要具备钱包功能即不需要存储任何用户的转账信息，也不需要维护像比特币这种基于 UTXO 账本模型的账户余额。LTBSV 包含以下组成部分：

LTBSV is a trustless block data verification protocol that can verify block data without trusting any third-party block data source. That is, for any new block数学公式: $ Block_{n} $, the latest block数学公式: $ VBlock_{n-1} $ that has been verified, and the LTBSV validator数学公式: $ f_{LTBSV} $ can verify whether the latest block is legal:
数学公式: $ VBlock_{n} = $数学公式: $ f_{LTBSV}\left\{ VBlock_{n-1},Block_{n} \right\} $
LTBSV is different from the full nodes in the blockchain network. It does not need to store the entire block data, nor does it need to verify every transaction in the block. The only difference from the light node is that it does not need to have a wallet function, which means, it does not need to store any user's transfer information, and it does not need to maintain an account balance based on the UTXO ledger model like Bitcoin. LTBSV includes the following components:

#### 4.2.1 Block Fetcher
从任何第三方获取最新的区块数据，无需信任第三方数据源。通常只需要提供给 Block Fetcher 对应区块链网络的全节点链接，Block Fetcher 将按照设置好的频率轮询最新的区块。如果由于某种原因 Block Fetcher 暂停后重启，依旧会从上次验证的最新区块开始根据区块高度获取截止到网络最新区块的所有区块数据并挨个验证每一个区块的合法性。如果新的区块数据与原有区块数据无法相匹配，也会验证失败。

Get the latest block data from any third party without trusting the third-party data source. Usually only need to provide Block Fetcher corresponding to the full node link of the blockchain network, Block Fetcher will poll the latest block according to the set frequency. If for some reason Block Fetcher is suspended and restarted, it will still obtain all block data up to the latest block of the network based on the block height from the latest block verified last time and verify the legitimacy of each block one by one. If the new block data cannot match the original block data, the verification will fail.

#### 4.2.2 Block Validator
Block Validator 负责区块数据的验证。由于 LTBSV 不关心区块里每一笔交易，某种程度上它只关心代理合约相关的交易，因此 LTBSV 结合交易 Merkle root hash，只对区块头进行验证。在轻节点中，需要存储所有区块头，即当节点启动后需要同步之前的所有区块头，即使只是同步区块头，对大多数现有的区块链网络来说，也需要耗费几个小时的时间。LTBSV 采用 Check Point 机制，它最早在比特币系统中引入，比特币钱包 electrum 即采用了 Check Point 机制数学公式: $ [11] $，即开发者事先硬编码已经被验证的区块头，在比特币系统中，由于难度值每 2016 个区块调整一次，因此，只需要编码区块高度是数学公式: $ 2016 $数学公式: $ * $数学公式: $ n $数学公式: $ \left\{ n = 1,2,3,,,n \right\} $的区块 hash 和对应的难度值数学公式: $ [12] $。采用 Check Point 机制后，LTBSV 启动后几分钟时间便可完成最新区块的验证。

Block Validator is responsible for the verification of block data. Since LTBSV does not care about every transaction in the block, it only cares about the transactions related to the proxy contract to some extent, as a result, LTBSV only verifies the block header in combination with the Merkle Root Hash of the transaction. In light nodes, all block headers need to be stored, that is, when the node is started, all previous block headers need to be synchronized. Even just synchronizing the headers would take several hours for most existing blockchain networks. LTBSV uses the Check Point mechanism, which was first introduced in the Bitcoin system. The Bitcoin wallet electrum uses the Check Point mechanism数学公式: $ [11] $, that is, developers hard-code the verified block header in advance. In the Bitcoin system, due to the difficulty, the value is adjusted every 2016 blocks, therefore, only the block hash with the block height of 数学公式: $ 2016 $数学公式: $ * $数学公式: $ n $数学公式: $ \left\{ n = 1,2,3,,,n \right\} $ and the corresponding difficulty value数学公式: $ [12] $ are needed to encode the block height. After adopting the Check Point mechanism, the verification of the latest block can be completed within a few minutes after LTBSV is started.

#### 4.2.3 Deposit Proof
LTBSV 完成区块数据验证后，对有效的交易数据颁发 Deposit proof。LTBSV采用ECDSA的椭圆曲线加密算法数学公式: $ [14] $来对数据进行签名。Deposit proof 用于证明用户在特定区块链网络中的资产抵押行为，即当用户抵押资产给 Nutbox 在该区块链网络中的 Proxy Contract，需要提供自己的对抵押金额和账户 nonce 值的数据签名数学公式: $ sig_{\left( amount, nonce \right)} $，此处
数学公式: $ sig_{\left( amount, nonce \right)} = f_{signer}\left\{ sha3\left\{ \left( amount, nonce \right) \right\} \right\} $
Proxy Contract 将验证用户签名数据，并解析出数学公式: $ amount $，如果数学公式: $ amount $等于收到的用户转账数额，则交易成功，否则交易失败。
随后 LTBSV 从区块中解析出该笔抵押交易的具体内容，包含用户签名和抵押资产数额。然后附加上自己的签名数据数学公式: $ sig_{LTBSV} $，
数学公式: $ sig_{LTBSV} = f_{signer}\left\{ sha3\left\{ currentBlock + confirmedBlock \right \} \right\} $

最终构成 Deposit proof，
数学公式: $ proof_{LTBSV} = \left( sig_{\left( amount, nonce \right)}, sig_{LTBSV} \right) $

用户随后提交 Deposit proof 给TEG模块验证，TEG模块将会解析出用户抵押交易的区块高度，并结合当前高度进行比对，如果当前高度没有在设定的确认区块高度之后，则交易失败。验证通过后将会分发等额 tToken 到用户的 Nutbox 账户中。

After LTBSV completes block data verification, it issues a deposit proof for valid transaction data. LTBSV uses ECDSA's elliptic curve encryption algorithm数学公式: $ [14] $ to sign data. Deposit proof is used to prove the user's asset staking behavior in a specific blockchain network, that is, when the user stake assets to Nutbox's Proxy Contract in the blockchain network, they need to provide their own data signature数学公式: $ sig_{\left( amount, nonce \right)} $ for the staking amount and the account nonce value, here
数学公式: $ sig_{\left( amount, nonce \right)} = f_{signer}\left\{ sha3\left\{ \left( amount, nonce \right) \right\} \right\} $
Proxy Contract will verify the user's signature data and parse out数学公式: $ amount $. If 数学公式: $ amount $ is equal to the received user transfer amount, the transaction is successful, otherwise the transaction fails.
Then LTBSV parsed the specific content of the staking transaction from the block, including the user's signature and the amount of staking assets. Then attach their own signature data数学公式: $ sig_{LTBSV} $
数学公式: $ sig_{LTBSV} = f_{signer}\left\{ sha3\left\{ currentBlock + confirmedBlock \right \} \right\} $
and finally constitute Deposit proof，
数学公式: $ proof_{LTBSV} = \left( sig_{\left( amount, nonce \right)}, sig_{LTBSV} \right) $
The user then submits a deposit proof to the TEG module for verification. The TEG module will analyze the block height of the user's staking transaction and compare it with the current height. If the current height is not below the set confirmation block height, the transaction will fail. After the verification is passed, the equal amount of tToken will be distributed to the user's Nutbox account.

## 5  Nutbox As Parachain
Nutbox Blockchain 基于 substrate FRAME数学公式: $ [6] $框架构建，采用 substrate 构建区块链网络，能够复用很多已经成熟且稳定可靠的功能模块，并且具备可升级的 Runtime。可升级的 Runtime 意味着区块链网络不再需要硬分叉来达到升级系统的目的，保证了区块链网络的稳定性。当 Nutbox 通过公开插槽拍卖获取到 parachain 卡槽后，可以直接接入 polkadot 平行链网络。

Nutbox Blockchain is built on the framework of substrate FRAME数学公式: $ [6] $, and uses substrate to build a blockchain network. It can reuse many mature, stable and reliable functional modules, and has an upgradeable Runtime. Upgradable Runtime means that the blockchain network no longer needs a hard fork to achieve the purpose of upgrading the system, ensuring the stability of the blockchain network. After Nutbox obtains the parachain card slot through the public slot auction, it can directly access the polkadot parachain network.

### 5.1  Nutbox Collator
在 Polkadot 网络中，Collator 不同于 Polkadot relaychain 全节点或者 Validator，Collator 用于运行平行链网络，它不包含自己的共识系统（PoA 或者 NPoS），内置 Polkadot Relaychain 全节点，同时打包 Parachain 的交易生成区块的 PoV 数据发送给 relaychain，经过 relaychain 验证的 PoV 数据所对应的区块才被认为是一个有效的 Parachain 区块被最终存储于 Parachain 自己的区块数据库里。
Nutbox Collator 启动后，任何人可以加入 Nutbox 网络运行 Nutbox Collator 节点，虽然不需要验证区块数据，运行节点也同样会获得奖励。

In the Polkadot network, Collator is different from the Polkadot relaychain full node or Validator. The Collator is used to run the parachain network. It does not contain its own consensus system (PoA or NPoS). It has a built-in Polkadot Relaychain full node, and it packets the PoV data of Parachain's transactions to send to Relaychain.The block corresponding to the PoV data verified by the relaychain is considered a valid Parachain block and is finally stored in Parachain's own block database.
After the Nutbox Collator is launched, anyone can join the Nutbox network to run the Nutbox Collator node. Although the block data does not need to be verified, the node will also be rewarded for running it.

### 5.2  XCM Based Transfer
一旦Nutbox接入polkadot平行链网络便可以基于XCM协议实现跨链资产转移。对于同样接入平行链网络的其他区块链网络，通过如下方式便可以再彼此之间实现跨链资产转移：
使用XCM指令构造一条跨链转账的XCM消息
配置XCM Executor执行 XCM指令并通过UMP或HRMP将xcm消息转发给目标平行链
目前XCM V0/V1已经实现并运行在Rococo测试网络，在V0版本中，资产被描述为MultiAsset，平行链网络中某个地址被描述为MultiLocation。其中MultiAsset既可以是一个concrete资产也可以是unconcrete资产；可以是fungible资产也可以是unfungible资产。MultiLocation既可以用来表示一个平行链网络也可以用来表示网络中的一个账户甚至是部署在网络中的一段智能合约。

Once Nutbox is connected to the polkadot parachain network, it can realize cross-chain asset transfer based on the XCM protocol. For other blockchain networks that are also connected to the parachain network, cross-chain asset transfers can be realized between each other through the following methods:
Use XCM instructions to construct an XCM message for cross-chain transfer
Configure XCM Executor to execute XCM instructions and forward xcm messages to the target parachain through UMP or HRMP
At present, XCM V0 has been implemented and running on the Rococo test network. In the V0/V1 version, the asset is described as MultiAsset, and an address in the parachain network is described as MultiLocation. Among them, MultiAsset can be either a concrete asset or an unconcrete asset; it can be a fungible asset or an unfungible asset. MultiLocation can be used to represent a parachain network, it can also be used to represent an account in the network or even a smart contract deployed in the network.

## 6  Asset Price Oracle
### 6.1 Price Oracle Algorithm
由上文可知Asset的种类是多种多样的，这个章节我们暂时只针对Fungible Asset的价格进行讨论。价格获取预言机一直以来都是行业内一个非常值得探索的技术分支，通常包含价格计算和喂价两个阶段。目前有很多实现能够满足基本的业务需求，Nutbox对资产价格获取参考了Uniswap的Price Oracle实现数学公式: $ [7] $。对于一般资产例如BTC、ETH，我们可以通过Uniswap交易对来推导出对应资产的价格。由于在Uniswap中，交易对拥有恒定乘积数学公式: $ K $，每一个交易对都可以最终被推导为其相对于USDT的交易对，

From the above, we can see that there are various types of Assets. In this chapter, we will only discuss the price of Fungible Asset.
The price acquisition oracle has always been a branch of technology that is worth exploring in the industry. It usually includes two stages: price calculation and price feed. There are many implementations that can meet basic business needs. Nutbox refers to Uniswap's Price Oracle implementation for asset price acquisition数学公式: $ [7] $. For general assets such as BTC and ETH, we can derive the price of the corresponding asset through Uniswap trading pairs. Since trading pairs in Uniswap have a constant product 数学公式: $ K $, each trading pair can be finally deduced as a trading pair relative to USDT.

因此此时资产价格可以表示为：
数学公式: $ price_{token} = pairInstance.token0Price $
资产余额表示为：
数学公式: $ f_{balance} = token.balanceOf\left( address \right) $
创建一个交易对，
数学公式: $ pairInstance = f_{pair}\left\{ f_{balance}(f_{pairAddress\left( token, usdt \right)}) * USDT, f_{balance}(f_{pairAddress\left( token, usdt \right)}) \right\} $
上式中，数学公式: $ f_{pair} $和 数学公式: $ f_{pairAddress} $来源于Uniswap V2 SDK数学公式: $ [8] $。计算得到价格后，通过延时喂价数学公式: $ n_{block} $策略将价格写入链上合约。由于Nutbox需要支持多个区块链网络的资产价格获取，不同区块链网络的出块速度不尽相同，因此数学公式: $ n_{block} $需要根据该区块链网络的出块速度数学公式: $ t_{newBlock} $进行设置，则有
数学公式: $ n_{block} = \frac{t_{delay}}{t_{newBlock}} $

Nutbox不仅支持一般资产的抵押，也支持LP token的抵押。LP token抵押依赖LP token的价格预言机，而在价格预言机实现中LP token的价格获取有一定的特殊性。通常LP token的价格计算表示为：
数学公式: $ price_{lptoken} = \frac{r_{0} * price_{0} + r_{1} * price_{1}}{totalSupply} $
其中，数学公式: $ r0 $,数学公式: $ r1 $ 分别为 Uniswap 对应交易对中两种资产的数量，数学公式: $ price0 $，数学公式: $ price1 $ 分别对应 数学公式: $ r0 $ 和 数学公式: $ r1 $ 对应代币的价格。上面的公式简单来说就是算出交易对中两种代币的总价值之和，然后除以 LP Token 的总数量，由此得到LP token的价格。而实践中这种价格计算方式容易被黑客攻击，因为黑客能够很容易的通过交易池交易来操纵数学公式: $ r0 $和数学公式: $ r1 $。因此参考Alpha Finance的LP Token价格获取算法数学公式: $ [9] $，一个更好的LP Token价格获取算法表示为：
数学公式: $ price_{lptoken} = 2\frac{\sqrt{r0\ast r1} \ast \sqrt{price_{0}\ast price_{1}}}{totalSupply} $
由上式可以看出，黑客针对r0和r1的攻击导致的后果从数学公式: $ r0 + r1 $ 减少到数学公式: $ \sqrt{r0} $+ 数学公式: $ \sqrt{r1} $。该算法实现基于Uniswap的交易对曲线恒定乘积数学公式: $ K $，因此只适用于基于此交易模型的交易对LP Token价格计算。

Therefore, the asset price can be expressed as:
数学公式: $ price_{token} = pairInstance.token0Price $
The asset balance can be expressed as:
数学公式: $ f_{balance} = token.balanceOf\left( address \right) $
Create a trading pair,
数学公式: $ pairInstance = f_{pair}\left\{ f_{balance}(f_{pairAddress\left( token, usdt \right)}) * USDT, f_{balance}(f_{pairAddress\left( token, usdt \right)}) \right\} $
In the above formula, 数学公式: $ f_{pair} $ and 数学公式: $ f_{pairAddress} $ are from Uniswap V2 SDK数学公式: $ [8] $. After the price is calculated, the price is written into the contract on the chain through the delayed price feed 数学公式: $ n_{block} $ strategy. Since Nutbox needs to support asset price acquisition of multiple blockchain networks, the block generation speed of different blockchain networks is not the same, so 数学公式: $ n_{block} $ needs to be set according to the block generation speed 数学公式: $ t_{newBlock} $, then there is
数学公式: $ n_{block} = \frac{t_{delay}}{t_{newBlock}} $
Nutbox not only supports the staking of general assets, but also the staking of LP tokens. LP token staking relies on the price oracle of LP token, and the price acquisition of LP token in the realization of the price oracle has certain peculiarities. Usually the price calculation of LP token can be expressed as:
数学公式: $ price_{lptoken} = \frac{r_{0} * price_{0} + r_{1} * price_{1}}{totalSupply} $
In the formula, 数学公式: $ r0 $ and 数学公式: $ r1 $ are the quantities of the two assets in Uniswap's corresponding trading pair, and price0 and price1 correspond to the prices of the tokens represented by 数学公式: $ r0 $ and 数学公式: $ r1 $.The above formula is simply to calculate the sum of the total value of the two tokens in the trading pair, and then divide it by the total number of LP Tokens to get the price of LP tokens. In practice, this price calculation method is easy to be attacked by hackers, because hackers can easily manipulate 数学公式: $ r0 $ and 数学公式: $ r1 $ through trading pool transactions. Therefore, referring to Alpha Finance's LP Token price acquisition algorithm数学公式: $ [9] $, a better LP Token price acquisition algorithm can be expressed as:
数学公式: $ price_{lptoken} = \frac{r_{0} * price_{0} + r_{1} * price_{1}}{totalSupply} $
It can be seen from the above formula that the consequences of hackers' attacks on 数学公式: $ r0 $ and 数学公式: $ r1 $ are reduced from 数学公式: $ r0 + r1 $ to 数学公式: $ \sqrt{r0} $ + 数学公式: $ \sqrt{r1} $. This algorithm realizes the constant product K of the trading pair curve based on Uniswap, so it is only applicable to the price calculation of the trading pair LP Token based on this trading model.

### 6.2 Offchain Worker Based Price Oracle Flow
目前的substrate提供了Offchain Worker数学公式: $ [10] $机制，可以让节点通过http获取外部数据，执行复杂计算如加解密等。Offchain Worker拥有Offchain Storage，runtime可以直接访问；在Offchain Worker的pallet里可以访问其他pallet，同时Offchain Worker也可以通过Signed Transaction和Unsigned Transaction来提交需要共识验证的数据。

基于Offchain Worker模块的价格预言机利用http协议从第三方价格提供者那获取价格信息，并依照价格计算算法计算出资产价格，然后将价格提交到Nutbox网络中。

The current substrate provides the Offchain Worker数学公式: $ [10] $mechanism, which allows nodes to obtain external data through http and perform complex calculations such as encryption and decryption. Offchain Worker has Offchain Storage, which can be accessed directly by runtime, and other pallets can be accessed in Offchain Worker's pallet. At the same time, Offchain Worker can also submit data that requires consensus verification through Signed Transaction and Unsigned Transaction.
The price oracle based on the Offchain Worker module uses the http protocol to obtain price information from a third-party price provider, calculates the asset price according to the price calculation algorithm, and then submits the price to the Nutbox network.

图片: https://uploader.shimo.im/f/CWngXOLQoKRiEUQ5.png!thumbnail?accessToken=eyJhbGciOiJIUzI1NiIsImtpZCI6ImRlZmF1bHQiLCJ0eXAiOiJKV1QifQ.eyJhdWQiOiJhY2Nlc3NfcmVzb3VyY2UiLCJleHAiOjE2MzQ4ODgxNTUsImciOiJXVGdEWERkcHRLZ1BZV2dDIiwiaWF0IjoxNjM0ODg3ODU1LCJ1c2VySWQiOjIyOTY4MDkyfQ.PMHyeguszgV_wfP1-N6fKiQabDJ-_ozXxBP1bNrDCwc
图 7 Offchain Worker Based Price Oracle Flow
Figure6, Offchain Worker Based Price Oracle Flow

## 7  Nutbox Governance Contracts
Nutbox DAO将通过链上治理的方式运作，在项目稳定运行后所有有关项目的决策都将进行链上投票。Nutbox Governance的实现由一系列相关合约模块组成，其中：

Nutbox DAO will operate through on-chain governance. After the stable operation of the project, all decisions related to the project will be voted on-chain. The implementation of Nutbox Governance consists of a series of related contract modules, including:

### 7.1 Democracy
Democracy Contract 实现Nutbox链上提案投票系统，是链上治理的主要模块。Democracy包含两个Proposal Queue，Internal Proposal Queue和External Proposal Queue。Nutbox官方提交的提案进入Internal Proposal Queue，用户发起的Proposal进入External Proposal Queue。两中类型提案可设置不同的投票策略。

Democracy Contract can implement Nutbox's on-chain proposal voting system and is the main module of on-chain governance. Democracy contains two Proposal Queues, namely Internal Proposal Queue and External Proposal Queue. Proposals submitted by Nutbox will enter the Internal Proposal Queue, and user-initiated Proposal will enter the External Proposal Queue. Different voting strategies can be set for the two types of proposals.

### 7.2 Collective
Collective  Contract维护了一个账户集合，只有Collective集合中的账户才具有投票资格。

Collective Contract maintains a set of accounts and only accounts in the Collective set are eligible to vote.

### 7.3 Elections
Elections Contract实现基于动态权重的去中心化投票系统。用户的投票权重由Staking资金量以及其他条件组合而成。

Elections Contract can implement a decentralized voting system based on dynamic weights. The user's voting weight is a combination of the amount of staking funds and other conditions.

### 7.4 Membership
Membership Contract管理Collective Contract账户集合中的账户，以及设置能够成为Collective账户集合中的限制条件。

Membership Contract manages the accounts in the Collective Contract account set and sets the restrictions in the Collective account set.

### 7.5 Treasury
Treasury Contract负责管理Nutbox DAO的资金，每一笔资金都需要由Nutbox相关Multisig账号签名。

Treasury Contract manages the funds of Nutbox DAO and each fund needs to be signed by the relevant Nutbox Multisig account.

### 7.6 Multisig
Multisig数学公式: $ [13] $ Contract实现Nutbox多重签名账号。

Multisig 数学公式: $ [13] $ Contract is used to implement Nutbox's multi-signature accounts.

### 7.7 Sudo
Nutbox Sudo用于管理并设置Nutbox合约，比如用于配置LTBSV、TEG签名验证器等。

Nutbox Sudo is used to manage and set up Nutbox contracts, such as configuring LTBSV, TEG signature verifier, etc.

## 8  References
[1] PoS Consens Algorithm https://en.wikipedia.org/wiki/Proof_of_stake
[2] PoW Consens Algorithm https://en.wikipedia.org/wiki/Proof_of_work
[3] NPoS Consens Algorithm https://w3f-research.readthedocs.io/en/latest/polkadot/NPoS/
[4] XCM https://github.com/paritytech/xcm-format
[5] Substrate Pallet https://substrate.dev/docs/en/knowledgebase/runtime/pallets
[6] Substrate FRAME https://substrate.dev/docs/en/knowledgebase/runtime/frame
[7] Uniswap Oracles https://uniswap.org/docs/v2/core-concepts/oracles/
[8] Uniswap SDK https://uniswap.org/docs/v2/API/overview/
[9] Alpha Finance LP Price https://blog.alphafinance.io/fair-lp-token-pricing/
[10] Substrate Offchain Worker https://substrate.dev/docs/en/knowledgebase/runtime/off-chain-workers
[11] Eelectrum Check Point https://electrumx.readthedocs.io/en/latest/protocol-basics.html#block-headers
[12] Bitcoin Check Point Format https://github.com/spesmilo/electrum/blob/master/electrum/checkpoints.json
[13] Multi Signature https://en.bitcoin.it/wiki/Multisignature
[14] EllipticCurve  Cryptography https://en.wikipedia.org/wiki/Elliptic-curve_cryptography
[15] Ethereum Sharding https://eth.wiki/sharding/ethresearch-sharding-compendium