merkle-airdrop-cli
==================

This is a helper client shipped along contract.
Use this to generate root, generate proofs and verify proofs

## Installation

```shell
yarn install
yarn link
```

Binary will be placed to path.

## Airdrop file format

```json
[
  { "index": "1", "address": "juno1q4aw0vtcydtn7lqmkfprm4ncmr4jdj70ggc6sp", "amount": "1000000000"},
  { "index": "2", "address": "juno1wnr06m7s66syagzd0zvgsu2qzsh4htqup2njz5", "amount": "502000000"},
  { "index": "3", "address": "juno1qesady6wm5v7yh497xgq6uu8hnayr03u8ucrud", "amount": "105000000"}
]
```


## Commands

**Generate Root:**
```shell
merkle-airdrop-cli generateRoot --file ../testdata/airdrop_stage_2_list.json
```

**Generate proof:**
```shell
merkle-airdrop-cli generateProofs --file ../testdata/airdrop_stage_2_list.json \
  --index 1 \
  --address juno1q4aw0vtcydtn7lqmkfprm4ncmr4jdj70ggc6sp \
  --amount 1000000000
```

**Verify proof:**
```shell
PROOFS='[ "27e9b1ec8cb64709d0a8d3702344561674199fe81b885f1f9c9b2fb268795962","280777995d054081cbf208bccb70f8d736c1766b81d90a1fd21cd97d2d83a5cc","3946ea1758a5a2bf55bae1186168ad35aa0329805bc8bff1ca3d51345faec04a"
]'
merkle-airdrop-cli verifyProofs --file ../testdata/airdrop.json \
  --index 1 \
  --address juno1q4aw0vtcydtn7lqmkfprm4ncmr4jdj70ggc6sp \
  --amount 1000000000 \
  --proofs $PROOFS
```
