# clone-lin-bitcoin-core-dust

Experimental LIN clone of Bitcoin Core v27.1 `GetDustThreshold` / `IsDust`.

**Not a wallet. Not consensus. Class: EXPERIMENTAL.**

- Upstream: [bitcoin/bitcoin](https://github.com/bitcoin/bitcoin) tag `v27.1` commit `1088a98f5aad080cc6cca2da174f206509fcda6c` (MIT)
- Full proofs and Compiler 0 receipts: [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open) (`src/lin_bitcoin_core_dust.lin`, `test/prove_bitcoin_core_dust_external.py`)

Default `DUST_RELAY_TX_FEE = 3000` sat/kvB:

| output | script_len | nSize | dust (sat) |
|---|---|---|---|
| P2PKH | 25 | 182 | 546 |
| P2WPKH | 22 | 98 | 294 |
| P2TR / P2WSH | 34 | 110 | 330 |
| P2SH | 23 | 180 | 540 |

P2TR uses Core's P2WPKH 107-byte dummy spend ([PR 22779](https://github.com/bitcoin/bitcoin/pull/22779)), not BIP340 keypath weight. `IsDust` is `nValue < threshold` (545 sat P2PKH is dust; 546 is not).

This repository is the LIN copy only. Recompute claims in lin-open with C11 Compiler 0 (`transpile/c/bin/lin_c0`).
