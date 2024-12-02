# flextrs

Fork of [https://github.com/Blockstream/electrs](https://github.com/Blockstream/electrs) which can be configured for an arbitrary Bitcoin compatible system.

Blockstream electrs API documentation [is available here](https://github.com/blockstream/esplora/blob/master/API.md).

Documentation for the database schema and indexing process [is available here](doc/schema.md).

## Usage

flextrs inherits its flags and usage from electrs, but the following flags are now added and required to initialize:

- `--magic <hex digits for the magic bytes for the block>`
- `--p2sh_prefix <number representing the p2sh magic byte>`
- `--p2pkh_prefix <number representing the p2pkh magic byte>`
- `--bech32_prefix <prefix for bech32 encoding>`
- `--auth <USERNAME:PASSWORD>`

`--auth` can be used to use Basic credentials to the target Bitcoin RPC, if a `.cookie` file is not used.

The `--bech32_prefix` should not have a leading `0x` and should be the bytes in little endian representing the u32 value for the magic bytes for the Bitcoin fork.

And the slight difference for the usage of `--network`
- `--network <directory within the bitcoin data directory to search for blocks>`

Example `--network` could be either `testnet3` or `testnet4` instead of supplying `testnet` as was the case with the Blockstream electrs implementation.

## Author

flex

## License

MIT
