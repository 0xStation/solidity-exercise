# Station Solidity Exercise

**Goal:** Create a credibly neutral mechanism for evaluating Solidity talent.

**Rules**

1. Candidates are **not** allowed to publicize or discuss the contents of the exercise with anyone

- applies during the exercise when creating their solution
- also applies after the exercise is submitted to preserve the integrity of the exercise being unknown to future applicants

2. Candidates are allowed (and encouraged) to reference external internet resources for completing the exercise
3. Where relevant, candidates must make inline comments in reference to resources used in their implementation

**Recommendations**

- Candidates will not be considered if they cannot pass the minimum requirements, beyond that it is up to you to differentiate your abilities through more advanced implementations or otherwise.
- You should not feel pressured to complete _everything_ that this exercise implies is available to implement. This exercise is meant to have a "high ceiling" and have more things to implement than are practical for the time that should be allotted by a candidate.
- Code quality matters. If everyone gets the same exercise, we have to split hairs on the readability and performance of each candidate's submission.
- We like creativity and breaking assumed, but not required, constraints.
- If you happen to extend the functionality of the exercise beyond its core requirements, please do so in another contract so that we can cleanly evaluate meeting our needs first and then look at your new ideas with a more open mind.

## Exercise

**You will be implementing an ERC721 NFT for an identity use case**. Using NFTs to represent identity has many potential use cases; for example, distributing employee cards that enable automatic token-gating on the organization's internal tooling.

The main constraint of our identity is that one human should only ever own one NFT. The EVM doesn't know what a human is so the best it can do is enforce that an address can only own one NFT. To make the implicit explicit, humans and addresses are not one-to-one or equivalent.

The `ERC721ID` contract has the following **minimum requirements**:

- Admins
  - admins can add or remove other admins
  - admins can revoke NFTs
- Mint
  - mint from an admin wallet
  - mint with a signature from an admin wallet (EIP712 recommended)
  - mint with a merkle proof that was approved by an admin wallet
- Transfer
  - transfers are not allowed without guarantee that the new wallet is the same human
- Owners
  - given an address, return the `tokenId` that it owns

While important, testing is not a part of the minimum requirements for respect for time. Adding tests, especially for the more complicated mint functions can help differentiate your submission.

There also is a set of optional challenges for gas optimization:

- Make your mint functions sub 50k gas
  - still preserve all existing functionality and adhere to the constraints
- Enable transfering the NFT while still staying below the 50k gas limit for minting
  - don't worry about designing a mechanism for authenticating if the transfer should be allowed
