# flextrs

Fork of [https://github.com/Blockstream/electrs](https://github.com/Blockstream/electrs) which can be configured for an arbitrary Bitcoin compatible system.

Blockstream electrs API documentation [is available here](https://github.com/blockstream/esplora/blob/master/API.md).

Documentation for the database schema and indexing process [is available here](doc/schema.md).

## Usage

flextrs inherits its flags and usage from electrs, but the following flags are now added and required to initialize:

- `--magic <hex digits for the magic bytes for the block>`
- `--p2sh-prefix <number representing the p2sh magic byte>`
- `--p2pkh-prefix <number representing the p2pkh magic byte>`
- `--bech32-prefix <prefix for bech32 encoding>`
- `--genesis-hash <blockhash hex>
- `--auth <USERNAME:PASSWORD>`

`--auth` can be used to use Basic credentials to the target Bitcoin RPC, if a `.cookie` file is not used.

The `--bech32_prefix` should not have a leading `0x` and should be the bytes in little endian representing the u32 value for the magic bytes for the Bitcoin fork.

And the slight difference for the usage of `--network`
- `--network <directory within the bitcoin data directory to search for blocks>`

Example `--network` could be either `testnet3` or `testnet4` instead of supplying `testnet` as was the case with the Blockstream electrs implementation.

A full example of invocation for dogecoin:

```sh
./flextrs/target/release/flextrs --network dogecoin --daemon-db-dir ~/.dogecoin --db-dir ~/.dogecoin-flextrs --auth 'dogecoinrpc:dogecoinrpc' --daemon-rpc-addr 127.0.0.1:22555 --p2sh-prefix 22 --p2pkh-prefix 30 --bech32-prefix dc --magic c0c0c0c0 --genesis-hash 1a91e3dace36e2be3bf030a65679fe821aa1d6ef92e7c9902eb318182c355691
```

## Author

flex

## License

MIT
