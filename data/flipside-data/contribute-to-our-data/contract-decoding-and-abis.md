# Contract Decoding & ABIs

### Adding a contract for decoding <a href="#adding-a-contract-for-decoding" id="adding-a-contract-for-decoding"></a>

To add a contract for decoding, please visit [here](https://science.flipsidecrypto.xyz/abi-requestor/).

Assuming the submitted ABI is valid, records will be decoded within 24 hours. If records are not decoded within 24 hours, or for any ABI updates, please submit a ticket within our Discord.

#### General Process Overview <a href="#general-process-overview" id="general-process-overview"></a>

The majority of our ABIs have been sourced from Etherscan, and we are constantly asking Etherscan for new ABIs. However, this is not comprehensive, and therefore we must also rely on our users to submit ABIs for decoding. If we are unable to locate an ABI for the contract from either Etherscan or our users, we will attempt to match the contract to a similar ABI. This is done by comparing the contract bytecode to a list of known contract bytecodes. If we are able to match the contract to a similar ABI, we will decode the contract using the similar ABI. You can see the source of each ABI in the `dim_contract_abis` table within the `abi_source` column.

Once ABIs have been verified, events within the last day of blocks will be decoded within approximately 90 minutes. Events older than 1 day will be decoded within 24 hours in the majority of cases. The exception here is if the contract has a massive number of events, in which case it may take longer.
