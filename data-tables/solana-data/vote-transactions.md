# Vote Transactions

## Solana.vote\_transactions

This table contains the full set of vote transactions that are submitted by validators to vote on a block. It can be joined with the non-vote transactions table above to get a full breakdown of all transactions. It has the same schema as the main transactions table.

An example query that demonstrates that is available here: [Solana transactions past 30 days](https://dune.xyz/queries/389976/743760)

| Column Name                      | Column Type                   | Description                                                                                                                                                                                                                           |
| -------------------------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| block\_slot                      | bigint                        | This block’s slot index in the ledger                                                                                                                                                                                                 |
| block\_time                      | timestamp                     | The (estimated) time this block was produced                                                                                                                                                                                          |
| block\_date                      | date                          | Event date                                                                                                                                                                                                                            |
| index                            | bigint                        | Index into the block’s transactions                                                                                                                                                                                                   |
| fee                              | bigint                        | Fee this transaction was charged, as paid by first account                                                                                                                                                                            |
| block\_hash                      | string                        | The hash of this block, base-58 encoded                                                                                                                                                                                               |
| error                            | STRUCT error                  | NULL if success is true.                                                                                                                                                                                                              |
| required\_signatures             | bigint                        | The total number of signatures required to make the transaction valid.                                                                                                                                                                |
| readonly\_signed\_\_\_accounts   | bigint                        | The last readonly\_signed\_accounts of the signed keys are read-only accounts.                                                                                                                                                        |
| readonly\_unsigned\_\_\_accounts | bigint                        | The last readonly\_unsigned\_accounts of the unsigned keys are read-only accounts.                                                                                                                                                    |
| id                               | string                        | The first signature in the transaction                                                                                                                                                                                                |
| success                          | boolean                       | The transaction was valid and thus committed.                                                                                                                                                                                         |
| recent\_block\_\_\_hash          | string                        | The hash of a recent block in the ledger, used to prevent transaction duplication and to give transactions lifetimes                                                                                                                  |
| instructions                     | array\<STRUCT instructions>   | Instructions to execute (in order)                                                                                                                                                                                                    |
| accountKeys                      | array\<string>                | The account keys used in the transaction                                                                                                                                                                                              |
| log\_messages                    | array\<string>                | The log messages emitted by the transaction                                                                                                                                                                                           |
| pre\_balances                    | array\<bigint>                | Array of account balances before the transaction was processed. The i-th balance is the balance of the i-th account key in account\_keys                                                                                              |
| post\_balances                   | array\<bigint>                | Array of account balances after the transaction was processed. The i-th balance is the balance of the i-th account key in account\_keys                                                                                               |
| pre\_token\_balance              | array\<STRUCT token\_balance> | List of [token balances](https://docs.solana.com/developing/clients/jsonrpc-api#token-balances-structure) from before the transaction was processed or omitted if token balance recording was not yet enabled during this transaction |
| post\_token\_balance             | array\<STRUCT token\_balance> | List of [token balances](https://docs.solana.com/developing/clients/jsonrpc-api#token-balances-structure) from after the transaction was processed or omitted if token balance recording was not yet enabled during this transaction  |
| signatures                       | array\<string>                | A list of base-58 encoded signatures applied to the transaction. Always of length numRequiredSignatures                                                                                                                               |
| signer                           | string                        | The initial value from the account\_keys array that initiates the transaction and pays the transaction fee                                                                                                                            |