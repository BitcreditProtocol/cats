# Identifiers and Keys

## Ids

There are two categories of internal identifiers in Bitcredit-Core:

* NodeId (used for identities and companies)
* BillId (used for bills)

Both of these Ids have the prefix `bitcr` and a character that designated the network
the Id was created in. It uses the following mapping:

* m => Mainnet
* t => Testnet
* T => Testnet4
* r => Regtest

### NodeId

The node id has a prefix, the network designation and a string representation of a
Secp256k1 public key.

Format:

```
PREFIX|NETWORK|Secp256k1PublicKey
```

Example (Testnet):

```
bitcrt039180c169e5f6d7c579cf1cefa37bffd47a2b389c8125601f4068c87bea795943
```

### BillId

The bill id has a prefix, the network designation and a base58 encoded sha256 hash
of the bill Secp256k1 public key.

Format:

```
PREFIX|NETWORK|Base58(Sha256(Secp256k1PublicKey))
```

Example (Testnet):

```
bitcrtGgLTAAVDYaoPC5b45MVzdmMBhTNm5AHtm6izEquzWdDV
```

## Keys

We use the [Secp256k1](https://docs.rs/secp256k1/latest/secp256k1/) key scheme (like Bitcoin) with the [ECIES](https://docs.rs/ecies/latest/ecies/) encryption scheme to encrypt data.

We use [base58](https://docs.rs/bs58/latest/bs58/) to encode binary data and [sha256](https://docs.rs/sha2/latest/sha2/) to create hashes.

## Nostr

Beyond the internal Ids, we also use Nostr npubs for our transport layer, which can be derived from the Secp256k1 public key.
