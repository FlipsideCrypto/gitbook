# NonFungible Tokens Label Type

An `nft` label type represents any nonfungible token project or a nft marketplace.

`label_type` = `nft`

### Label Subtypes

| Subtype             | Description                                                                    |
| ------------------- | ------------------------------------------------------------------------------ |
| `token_contract`    | ERC-20 token (fungible token) contract owned by the nft project or marketplace |
| `nf_token_contract` | NonFungible token contract owned by the nft project or marketplace             |
| `contract_deployer` | A contract used by the project to create other contracts                       |
| `fee_contract`      | A contract used by the project to collect fees                                 |
| `marketplace`       | A contract used by a marketplace to facilitate sales and trades of nft's       |
| `general_contract`  | A contract controlled by the nft project or marketplace                        |

