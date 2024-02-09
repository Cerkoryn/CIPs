---
CPS: ?
Title: Incentivize Active Delegation
Status: Open
Category: Ledger
Authors:
    - "Cerkoryn <ByteBanditLLC@proton.me>"
Proposed Solutions:
  - CIP-Incentivize Active Delegation
  - CIP-50
Discussions:
  - https://github.com/Cerkoryn/CIPs/discussions
  - https://matrix.to/#/#cardano-space:matrix.org
  - https://forum.cardano.org/t/pcp-k-parameter-earncoinpool/122701
Created: 2024-01-15

---
> [!IMPORTANT]  
> TODO: This draft is still very much a work-in-progress.  Feel free to contribute via discussions or by submitted a PR.

> [!IMPORTANT]  
> TODO: Explore how these same problems will apply to inactive voter delegation after the Voltaire hardfork.  It is potentially even more of a problem because the self-interest of chasing a yield via staking ADA does not > apply with delegating voting power.

## **Abstract**

The Cardano blockchain, leveraging the innovative architecture of Ouroboros, is celebrated for its state-of-the-art, non-custodial, liquid staking mechanism. Despite its significant strides in blockchain technology, the Cardano implementation of the Ouroboros protocol faces notable challenges, especially within its Reward Sharing Scheme (RSS). This Cardano Problem Statement (CPS) aims to delineate and analyze these challenges in depth, seeking to spark the development of Cardano Improvement Proposals (CIPs) that can tactically and strategically address them both individually and holistically.

## **Problem**

This CPS defines this broader problem by breaking it into five individual challeges that are each heavily interconnected:

 - Dormant/Inactive Stake
 - Ensuring Fair Competition for Small/New SPOs
 - SPO Decentralization
 - Insignificance of Pledge
 - Sustainability of Staking Rewards

### **Challenge 1 - Dormant/Inactive Stake**

> [!IMPORTANT]  
> TODO: Need data showing stake that hasn't moved.  Perhaps a chart with epoch on the x-axis and the amount of ADA in delegation Txs from just that epoch.  I imagine that would show a downward trend due to stake that was delegated during Shelley Era and then left untouched. Maybe some other charts focusing on pools instead?  Pools who have raised fees or lowered pledge on their delegates?  ADA delegate to retired pools?  Other charts or data?

Of the five challenges, it may benefit to tackle the issue of dormant/inactive stake first because stake may be stake needs to be "non-myopic", active, and free of "rational ignornance" to support the security assumptions of Ouroboros and the RSS whitepaper. It is possible that this change alone may cause enough stake to in such a way that pledge becomes more important, multi-pool operators consolidate, K converges closer to the intended number of pools, reward distribution for active stakeholders improves, and the depletion rate of the reserves becomes more sustainable.

> [!NOTE]
> According to [Reward Sharing Schemes for Stake Pools(2020)](https://arxiv.org/ftp/arxiv/papers/1807/1807.11218.pdf) p.23:
> 
> "Players who play myopically and Rational Ignorance. Myopic play is not in line with the way we
> model rational behavior in our analysis. We explain here how it is possible to force rational parties to
> play non-myopically. With respect to pool leaders we already mentioned in Section 2.3 that rational
> play cannot be myopic since the latter leads to unstable configurations with unrealistically high
> margins that are not competitive. Next we argue that it is also possible to force poolmembers to play
> non-myopically. The key idea is that the effect of delegation transactions should be considered only in
> regular intervals (as opposed to be effective immediately) and in a certain restricted fashion. This can
> be achieved by e.g., restricting delegation instructions to a specific subset of stakeholders at any given
> time in the ledger operation and making them effective at some designated future time of the ledger’s
> operation. Due to these restrictions, players will be forced to think ahead about the play of the other
> players, i.e., stakeholders will have to play based on their understanding of how other stakeholders
> will as well as the eventual size of the pools that are declared... 

Myopic play is assumed not to be rational because delegators need to be on their toes about where to switch their delegation to maximize their returns.  In practice however, most pools provide extremely similiar returns and so delegators are not interested in moving their stake around as they should.  Myopic play has indeed become rational behavior as the returns across pools have normalized.

Additionally, in some sense it is expected that inactive delegators should have their rewards lowered via parameter change:
> [!NOTE]
> ...A related problem is that of rational ignorance, where there is some significant inertia in terms of 
> stakeholders engaging with the system resulting to a large amount of stake remaining undelegated. 
> This can be handled by calibrating the total rewards R to lessen according to the total active stake delegated, 
> in this way incentivising parties to engage with the system."

### **Challenge 2 - Ensuring Fair Competition for Small/New SPOs**

- minPoolCost disproportionally affects pools that mint fewer blocks.
- Most of the community seems favorable toward minMargin instead.
- Many early SPOs attracted delegation during the Shelley area that appears to have never moved, giving them a strong advantage over new pools.
- Threshold to create blocks can be a large obstacle for pools starting out.
- Current pledge benefit from a0 gives greater returns to SPOs with more ADA to pledge (rich-get-richer problem)

### **Challenge 3 - SPO Decentralization**

- Number of pools not converged on K as designed (need citation)
- K is related to number of pools, not number of SPOs.
- SPOs are what count for MAV, not pools.
- More pools likely means worse network latency (need data/citation? https://www.essentialcardano.io/article/an-analysis-of-the-research-underpinning-cardanos-scalability )

### **Challenge 4 - Insignificance of Pledge**

> [!NOTE]
> It follows that using # we can control the disparity created by the reward mechanism by choosing a0 closer to 0, 
> with the choice 0 achieving a perfectly “egalitarian” effect where rich pools and poor pools of the same size are 
> receiving exactly the same rewards, something that does not affect the relative stake from epoch to epoch if we do
> not take into account margins. Note that while this completely equalises the power of a “rich dollar”
> versus a “poor dollar” (cf. [23]) it comes with the downside of a reduction of the system’s resilience to
> Sybil attacks. Given we have no way of guaranteeing the independence of the players as declared in
> the stake pool game, we offer a tradeoff between egalitarianism and Sybil resilience.
> [Reward Sharing Schemes for Stake Pools(2020)](https://arxiv.org/ftp/arxiv/papers/1807/1807.11218.pdf) p.24

- Pledge relied on to prevent Sybil Attacks
- There are many pools with high stake and zero or near-zero pledge.
- "Nothing at Stake" problem

### **Challenge 5 - Sustainability of Staking Rewards**

- Rewards for delegators/SPOs are mediocre at best.
- Many rewards come from the reserce, but eventually it will be depleted, how will operations be sustained then?
- Block rewards vs number of pools (data?)

## **Goals**

> [!IMPORTANT]  
> TODO: Finish this part

## **References**

[Reward Sharing Schemes for Stake Pools(2020)](https://arxiv.org/ftp/arxiv/papers/1807/1807.11218.pdf)


