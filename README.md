Nouns are an experimental attempt to improve the formation of on-chain avatar communities. While projects such as Cryptopunks have attempted to bootstrap digital community and identity, Nouns attempt to bootstrap identity, community, governance, and a treasury that can be used by the community. Degen Vibes are NFTs that stream DeFi tokens to holders in real-time. Degen Vibes are minted and sold via auction, one at a time. A portion of auction proceeds are invested in DeFi and streamed to collectors. A portion of proceeds are kept in the treasury, controlled by a DAO of Degens. The initial plan is for the auction cadence to settle at one per 24 hours after the first 50. But this ongoing cadence could be changed by the DAO if members vote to do so. Streamonomics refers to the tokenomics of streaming tokens to multiple recipients as an incentive mechanism.

# Degen Vibes

Degen Vibes combine NFTs with DeFi. The degenerative art is inspired by Cryptopunks. The treasury aspect is inspired by Nouns. The DeFi and money streams aim to explore a new community that collides the worlds of NFTs and DeFi. Grab your Dog and join the Club.

Degen Vibes is powered by Superfluid, Uniswap, Chainlink, Compound, DAI by Maker, and hosted on Skynet. The website (dapp) are modified from Nounds DAO, as is the Auction House contract, which was itself modified from the Zora Auction House contract.

## Daily Auctions

The Degen Auction Contract will act as a self-sufficient noun generation and distribution mechanism, auctioning one noun every 24 hours, as long as there are degens needing a new home.

Each time an auction is settled, the settlement transaction will also cause a new degen to be minted and a new auction to begin.

While settlement is most heavily incentivized for the winning bidder, it can be triggered by anyone, allowing the system to trustlessly auction degens as long as Ethereum is operational and there are interested bidders.

## Degens do DeFi?

Degen Vibes is an experiment that combines NFTs and DeFi. The proceeds of each auction are sent to the treasury. That's when the Degen magic starts:

- The ETH from the winning bid is swapped on Uniswap for DAI
The resulting DAI is then deposited in Compound Finance, and begins to earn yield
- A portion of the Compound tokens (cDAI) representing the deposits are then upgraded to "Super Tokens" in the Superfluid protocol.
- Then Degen Super Tokens then begin streaming -- every second -- back to Dog owners:
- 10% of of the proceeds of the auction stream back to the Degen Owner over the next 365 days. If the Degen is sold or transfered, the stream switches to the new owner.
- 40% of the proceeds of each auction are shared by all current Degen owners and streamed to them over the next 365 days.
- 20% of the proceeds for each auction go to the owner of the 10th Degen before this one. For example, 20% of the proceeds of the auction for Degen 11 will get streamed to the owner of Degen 1, over the next 365 days.
- In future, the Club may decide to change the DeFi investments and distributions in interesting ways.

## Degen DAO?

Degen Vibes are currently on testnet. The plan for a mainnet launch would include a DAO to manage the Club and treasury. To start, this might be comprised of a small number of Degenfathers, with all Degen owners automatically joining the DAO. LFG

## Degen Traits

They represent the brand DNA we cultivated over the past 25 years with LiveTheLifeTV. They showcase our passion for surf, film, photography, etc, ... These characters are playful, they appeal to our culture code, & they tap into our deep-seated love of DAOs, NFTs, and DeFi. They hold the visions of the Degen Vibes we enjoy. We generated a 10K collection based on the Nouns traits that are fully aligned with the LiveTheLifeTV brand DNA: surf, skate, wine, film, and photography. We tweaked the backgrounds with photography-based visuals, and color-graded them through a "multiply" layer. 

## Degenerative Artwork

Degen Vibes are degens in the same spirit as the Cryptopunks. We call it _degenerative art_.

Art Work may be submitted and voted on by the club, with winning artists earning a cut. Stay tuned.

cc0 places emphasis on our ability to communicate a story, build a world and bring others along.

The Nouns brand and artwork are in the public domain or “CC0″. This essentially means that you can do whatever you want with it without worrying about any kind of copyright infringement. Not only does the Nouns DAO allow you to repurpose the artwork and brand, but it actually encourages you do to so — and may even pay you for it! All the money generated from the Nouns auctions goes directly to the DAO treasury. The treasury currently holds more than 27,000 ETH. The treasury exists for Nouns DAO participants to allocate resources for the long-term growth and prosperity of the Nouns ecosystem.

## Roadmap

These Degens are just getting started. Possible next steps and additonal features include:

- Gas cost optimizations
- Feature: every 52 days, a prize from the treasury earned by a random Degen owner.
- Feature: a pre-auction tool where artists can submit Art and the community can vote on which Degns are minted to the collection (portion of proceeds to artists).
- Explore other DeFi options (OlympusDAO, JonesDAO, Dopex, Aave, Balancer, etc.)
- Explore and simulate incentivized tokenomics models
- Smart contract refinements to support fully decentralized operation
- DAO governance implementation (Tally Integration)
- Support for resale auctions in the dapp (V1/V2 marketplace mvp)
- Mainnet launch! 🐻⛓️ thoon

## Technical Details

Degen Vibes is composed of two smart contracts and a front-end dapp that manages periodic NFT minting and auctioning Degens to the highest bidder.

The auction house contract is a modified version of the Zora Auction House contract. While the idea is for auctions to last 24 hours, minting one Degen each day, it is currently set to 10 minutes for development and demo purposes. Once the contract is deployed and initialized, it calls the ERC721 contract to mint a new Degen. At this point the Degen is not transferred to the Auction House but is held by the ERC721 contract pending the outcome of the auction. When the auction is over, a transaction to settle the auction triggers the transfer of the Degen to the winner and the transfer of the ETH proceeds to the ERC721 contract, which also acts as a treasury. That's when the DeFi starts...

The Degen contract leverages OpenZeppelin contracts to provide standard ERC721 functions, but also doubles as a treasury that not only holds funds, but invests them in DeFi and streams the result back NFT holders via Superfluid Finance. When an is won, the Degen contract transfers the Degen to the winner and receives the ETH proceeds. Immediately, the following is triggered:
- The Degen contract calls the Chainlink price feed oracle for ETH/DAI to get the latest price for DAI.
- Using the Chainlink data to set a reasonable slippage margin, the ETH is then swapped for DAI using Uniswap v3.
- The DAI is then immediately deposited in Compound Finance, where is starts to earn yield and COMP token rewards for the treasury. The contract now holds cDAI tokens representing the deposited DAI.
- A subset of the cDAI is then "upgraded" to cDAIx via the Superfluid protocol.
- Multiple streams of cDAIx being streaming -- every second -- back to the auction winner, and also to other Degen owners, according the following formula: 10% of auction proceeds stream back to the holder of that NFT over 365 days, PLUS 40% of the proceeds are divided among all Degen owners at the time, and streamed to them over 365 days, PLUS 20% of the proceeds are streamed to owner of the 10th degen prior, over 365 days (proceeds from Degen 10 stream to the owner of Degen 0, proceeds from Degen 11 stream to Degen 1, etc.)
- After 365 days, anyone can act as a "closer", and send a transaction to close the streams that are eligible. An instant (not streamed) reward equivalent to 30 days of flow is earned.
- When a Degen is sold or transferred, the streams are redirected automatically to the new owner.

The front-end dapp is hosted on Fleek decentralized storage. (Alternatively, the "Deploy to Skynet" Github Action can make deploying the dapp super-easy!)

The dapp primarily interfaces with the Auction House contract. User can connect their wallet, submit bids and settle auctions, which triggers the minting of a new Degen and starts a new auction. The dapp also displays the cDAI balances of the treasury and connected user, showing the real-time changes as funds are streamed out of the treasury to Degen owners.

The goal of the project is merge NFTs and DeFi in a way that hopefully provides some incentivizing tokenomics that could fuel an active community of Degen owners. A future feature could be a way for artists to submit new Art Works, and the community can vote for which Art will get minted as part of the collection, with a portion of auction proceeds streaming to artists. A governing Dog DAO might decide to change the investment and stream distribution strategies.

## Founder Rewards

Because 100% of Degen Dog auction proceeds are split between streams to Dog owners, donations to charitable causes, and the DAO treasury, founder(s) are compensated with Degen Dogs. Every 11th Dog for the first year of the project (ids #0, #11, #22, #33 and so on) will be automatically sent to the dogMaster multisig to be shared among the founding members of the project. Founder distributions don't interfere with the cadence of auctions. Dogs are sent directly to the dogMaster Multisig, and auctions continue on schedule with the next available ID.

## Governance

To submit a proposal to the DAO, you must hold at least 0.25% of the total Degen supply. This equates to 1 Degen up until the supply reaches 400 Degens. Examples of proposals include:
- funding Degen community projects
- compensating DAO members or 3rd parties for services that benefit the DAO
- investing treasury funds through onchain governance

A quorum is the minimum number of total votes -- whether for, against, or abstain -- needed for a proposal to succeed. The quorum threshold is 20% -- a value that can be changed by DAO. This means that at least 20% of minted Dogs (at the time the proposal was made) must submit a vote. Proposals that do not meet this threshold will not be executed, regardless of the number of votes for and against the proposal.

Voting can begin immediately after a proposal is created, although the DAO could implement a delay between proposal creation and the start of voting, if desired. The voting period is approximately 7 days. 

A Timelock is a delay between the end of the voting period for a successful proposal and when the proposed transaction(s) actually can be executed. This delay gives DAO members time to react before execution. For example, a DAO member who is unhappy with a proposal may decide to sell their token or take other steps they deem appropriate. The timelock delay for Degen Dogs is 2 days.

The thresholds and time periods mentioned above are settings that can be adjusted by the DAO via proposals. For example, the DAO may decide to change the proposal threshold or the length of the voting period in future.

Initially, the Degen DAO governance grants veto power to the founder(s) of the project. A key reason is that, due to the one-at-a-time auction process, the total supply of minted Dogs is very low in the early days. This could enable a single person to execute successful proposals before the community has had chance to grow and develop.  The goal is for the veto power to be renounced (on-chain) at the appropriate time -- feedback and suggestions are welcomed in this regard.

Tally provides a governance UI that DAO can use to submit and vote on proposals. Proposals and votes submitted via Tally get submitted on-chain to Degen DAO governance contracts and are subject to the above thresholds and time periods. 

## Treasury 

The Degen Treasury is contracts that holds the tokens of the DAO and executes the transactions approved by the DAO, after the timelock delay has passed.  For these reasons, the contract can also be referred to a Timelock or Executor. The contract itself is based on the timelock/executor contract of Nouns DAO, which in turn is is a modified version of Compound Lab's Timelock. The "admin" of the Treasury is set to the DAO Governance contract, meaning that a successful governance proposal is required for all transactions. 