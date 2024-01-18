# Flotsam Label Type

Label category reserved for junk, scams, and other known addresses that do not belong to a "legitimate" project but also should not be assumed to be "users". Some labels are descriptive (i.e. "upbit hack") in this category and some are not (i.e. "phishing scam").

`label_type` = `flotsam`

### Label Subtypes

| Subtype             | Description                                              |
| ------------------- | -------------------------------------------------------- |
| `toxic`             | Scams, pyramid schemes, bad bots, attacks, hackers, etc. |
| `token_contract`    | ERC-20 token (fungible token) contract                   |
| `general_contract`  | A general contract                                       |
| `contract_deployer` | A contract used to create other contracts                |
| `donation_address`  | Addresses used to collect donations                      |
