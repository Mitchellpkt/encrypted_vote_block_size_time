# encrypted_vote_block_size_time
Coupling dynamic block sizes (and times?) to Nakamoto consensus.

Notes from MRL to clean up later:

17:00 Normally, users (txn volum) set block size. If users set it too high, protocol intervenes. If protocol drifts too high, miners intervene. 
17:00 (e.g. picture a few years in the future, when cryptokitties accepts XMR. Users are generating 4 GB txns per 2 minutes, and protocol limits block size to 3 GB txns per 2 minutes, but the network can only handle 2 GB txns per 2 minutes)
17:00 The usual response is “well, if miners can only handle 2 GB blocks, they’ll self-limit to 2 GB”. In other words, we fallback to miners vetoing the difference between the protocol limit and practical limit.
17:00 So I perceive the block size chain of command to be [Users] < [Protocol] < [Miners]
17:00 (with the obvious caveat that miners can only veto the protocol limit when mining smaller blocks, and cannot arbitrarily exceed the protocol limit)
17:00 So, operating on that last-ditch assumption that the majority of miners will act in the best interest of the network, maybe we *want* to approach it from this angle from the start!
17:00 After all, Nakmoto consensus is very well defined and studied, so we can think through it somewhat formally. Likewise for privacy-preserving voting systems. Considering that framework:
17:00 Each miner casts one [encrypted] vote per block on whether or not to increase the block size. Value of `1` is a vote in favor of increasing block size, and a  value of `0` is a vote against increasing.
17:00 Every 100 blocks a new voting window begins. At the end of the window, the encrypted votes are tallied. If >=51 of 100 miners voted in favor of the increase, it passes. Otherwise, block size does not increase.
17:00 Thus we’ve reduced the matter to Nakamoto consensus, which is both 1) the practical fallback anyways, and 2) the main security requirement and guarantee for Monero anyways. 
17:00 So framed this way, if the voting system is “gamed” then it implies a violation of the assumption that 51% of miners are acting in the best interest of Monero.
17:00 Anyways, I’m rambling. You could consider variations like voting on block time as well, or having an option to vote for a decrease as well, etc etc. 
17:00 Also, I’ve only thought this halfway through, lots of edge cases and whatnot. Again, not proposing that we do this now. 
