---
id: api1
title: API Reference
sidebar_label: All Functions
---


## createTransaction

```js
createTransaction(txParams, lockTime=0, cb)
```
Parameters:

- `SenderSK` : `string` - base64-encoded 32-byte private key
- `PaymentInfo`: `Array` of receivers
- `InputCoins`: `Array` of coins to spend
- `Fee`: `Number` - transaction fee (PRV)
- `TokenID`: `string` - token ID being spent
- `Metadata`: `Object` - extra information
- `Info`: `string` - optional base64-encoded message
- `CoinCache`: `Object` - other coins for hiding sender identity
- `TokenParams`: `Object` - parameters for pToken

Usage:

```js
createTransaction()
```

## createConvertTx

## decryptCoin

## createCoin

## signWithdrawTx

## Other functions

Visit *Incognito*'s [GitHub](https://github.com/incognitochain/incognito-chain) for more details & source code.