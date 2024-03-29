# Station Solidity Exercise

**Goal:** Create a credibly neutral mechanism for evaluating Solidity talent.

**Rules**

1. Candidates are allowed (and encouraged) to reference external internet resources for completing the exercise
2. Where relevant, candidates must make inline comments in reference to resources used in their implementation
3. Candidates are **not** allowed to publicize or discuss their submission with anyone
   - applies during the exercise when creating their solution
   - also applies after the exercise is submitted to preserve the integrity of the exercise being unknown to future applicants

**Notes**

- Candidates will not be considered if they cannot pass the minimum requirements. Beyond that, it is up to you to differentiate your abilities through more advanced implementations or otherwise.
- Requirements are kept vauge intentionally, and we believe you have all the context you need to solve the problem while filling in the gaps on your own. That said, asking questions will not impact your candidacy so please do not hesitate to reach out.
- Code quality matters. If everyone gets the same exercise, we have to split hairs on the readability and performance of each candidate's submission.
- We like creativity and breaking assumed, but not required, constraints.
- If you happen to extend the functionality of the exercise beyond its core requirements, please do so in another contract so that we can cleanly evaluate meeting our needs first and then look at your new ideas with a more open mind.
- The exercise ideally takes 1-4 hours to complete. Longer times are more likely if you are less familiar with the mechanisms requested as you will have to learn them and then implement them. We would additionally appreciate if you note how long your implementation takes you when submitting

## Exercise

**You will be implementing an ERC721 NFT for an identity use case**. Using NFTs to represent identity has many potential use cases; for example, distributing employee cards that enable automatic token-gating on the organization's internal tooling.

The main constraint of our identity is that one human should only ever own one NFT. The EVM doesn't know what a human is so the best it can do is enforce that an address can only own one NFT. To make the implicit explicit, humans and addresses are not one-to-one or equivalent.

The `ERC721ID` contract has the following **minimum requirements**:

- Admins
  - admins can add or remove other admins
  - admins can revoke NFTs
- Mint
  - mint via call by an admin
  - mint with a merkle proof that was approved by an admin
  - mint with a signature from an admin (e.g. admin signs for A, B, and C to claim tokens on their own time with their own gas)
- Transfer
  - transfers are not allowed without guarantee that the new wallet is the same human
- Owners
  - given an address, return the `tokenId` that it owns

While important, testing is not a part of the minimum requirements for respect of your time. Adding tests, especially for the more complicated mint functions can help differentiate your submission.

There are also two optional challenges for gas optimization:

- Make your mint functions cost under 50k gas
  - must still preserve all existing functionality and adhere to the constraints
- Enable transfering the NFT while still staying below the 50k gas limit for minting
  - don't concern yourself with a mechanism for authenticating if the transfer should be allowed

## Instructions

1. Fork this repo as a new private repo owned by you (again, no one else should see your submission)
2. On exercise completion, invite `ilikesymmetry` to your private repo
3. On exercise completion, message your contact that you are done (dm [@ilikesymmetry](https://twitter.com/ilikesymmetry) if you do not have a contact)
