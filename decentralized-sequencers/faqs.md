# FAQs

**What are the risks associated with sequencer mining?**

In case of bad performance or malicious acting, the particular sequencer pool participant’s locked tokens would be slashed.

**In what cases a particular sequencer is considered malicious?**

Cases would include but not limited to:

1. Transaction manipulation (MEV or sandwiching)
2. Malicious Execution Result Modification: If a node modifies the execution result of a block, it will fail validation by other sequencers. This will cause other sequencers to stop producing blocks. The node will then be forced to produce a new block with the correct execution result.

**How is “bad performance” defined?**\
Cases would include but not limited to:

1. Failing to produce a block during a certain period of time
2. Slow performance: if the sequencer fails to produce the blocks vastly behind the average timing of other sequencers
3. Multiple Node Outages: If multiple nodes go offline at the same time, and they are all malicious, they should be punished more severely. This includes nodes that represent more than 1/3 of the total number of sequencers
4. Accumulated Unpacked Blocks:

If a node does not pack a block for a certain number of transactions, other sequencers can vote to slash it.
