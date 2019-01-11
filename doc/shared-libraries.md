Shared Libraries
================

## Starchainconsensus

The purpose of this library is to make the verification functionality that is critical to Starchain's consensus available to other applications, e.g. to language bindings.

### API

The interface is defined in the C header `Starchainconsensus.h` located in  `src/script/Starchainconsensus.h`.

#### Version

`Starchainconsensus_version` returns an `unsigned int` with the API version *(currently at an experimental `0`)*.

#### Script Validation

`Starchainconsensus_verify_script` returns an `int` with the status of the verification. It will be `1` if the input script correctly spends the previous output `scriptPubKey`.

##### Parameters
- `const unsigned char *scriptPubKey` - The previous output script that encumbers spending.
- `unsigned int scriptPubKeyLen` - The number of bytes for the `scriptPubKey`.
- `const unsigned char *txTo` - The transaction with the input that is spending the previous output.
- `unsigned int txToLen` - The number of bytes for the `txTo`.
- `unsigned int nIn` - The index of the input in `txTo` that spends the `scriptPubKey`.
- `unsigned int flags` - The script validation flags *(see below)*.
- `Starchainconsensus_error* err` - Will have the error/success code for the operation *(see below)*.

##### Script Flags
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_NONE`
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_P2SH` - Evaluate P2SH ([BIP16](https://github.com/Starchain/bips/blob/master/bip-0016.mediawiki)) subscripts
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_DERSIG` - Enforce strict DER ([BIP66](https://github.com/Starchain/bips/blob/master/bip-0066.mediawiki)) compliance
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_NULLDUMMY` - Enforce NULLDUMMY ([BIP147](https://github.com/Starchain/bips/blob/master/bip-0147.mediawiki))
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_CHECKLOCKTIMEVERIFY` - Enable CHECKLOCKTIMEVERIFY ([BIP65](https://github.com/Starchain/bips/blob/master/bip-0065.mediawiki))
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_CHECKSEQUENCEVERIFY` - Enable CHECKSEQUENCEVERIFY ([BIP112](https://github.com/Starchain/bips/blob/master/bip-0112.mediawiki))
- `Starchainconsensus_SCRIPT_FLAGS_VERIFY_WITNESS` - Enable WITNESS ([BIP141](https://github.com/Starchain/bips/blob/master/bip-0141.mediawiki))

##### Errors
- `Starchainconsensus_ERR_OK` - No errors with input parameters *(see the return value of `Starchainconsensus_verify_script` for the verification status)*
- `Starchainconsensus_ERR_TX_INDEX` - An invalid index for `txTo`
- `Starchainconsensus_ERR_TX_SIZE_MISMATCH` - `txToLen` did not match with the size of `txTo`
- `Starchainconsensus_ERR_DESERIALIZE` - An error deserializing `txTo`
- `Starchainconsensus_ERR_AMOUNT_REQUIRED` - Input amount is required if WITNESS is used

### Example Implementations
- [NStarchain](https://github.com/NicolasDorier/NStarchain/blob/master/NStarchain/Script.cs#L814) (.NET Bindings)
- [node-libStarchainconsensus](https://github.com/bitpay/node-libStarchainconsensus) (Node.js Bindings)
- [java-libStarchainconsensus](https://github.com/dexX7/java-libStarchainconsensus) (Java Bindings)
- [Starchainconsensus-php](https://github.com/Bit-Wasp/Starchainconsensus-php) (PHP Bindings)
