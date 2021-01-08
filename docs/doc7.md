---
id: doc7
title: Creating Feature Transactions Using Metadata
sidebar_label: Feature Transactions
---

## The *Metadata* parameter

Recall that `TokenParams` is an optional parameter in `txParams` when calling `createTransaction`. When `TokenParams==null`, a PRV transaction will be created. If you want to transfer a pToken, just pass in an object like following:
```json
{
    "TokenID": "ABC",
    "TokenInputs": []
}
```

- `SenderSK`: base64-encoded form of the 32-byte private key for your spending coins
- `PaymentInfo`: array of receivers, each of which must have *PaymentAddress* and *Amount*
- `InputCoins`: the coins that will be spent
- `Fee`: transaction fee (must be in PRV)
- `TokenID`: identifier for the token being spent (default: *PRV*)
- `Metadata`: extra information used for special types of transaction such as pDex / Staking feature transactions
- `Info`: an optional message from sender
- `CoinCache`: an array of random (encrypted) coins in the Incognito network, used to hide sender identity
- `TokenParams`: some more parameters, exclusive to `pToken` transactions

> Remember to still include a PRV input since the TX fee needs to be in PRV

Example:

## Some example `Metadata`

Staking: stake 1750 of your PRV to participate in consensus.

```json
{
    //...
    "Type" : 0,
    "TokenName" : "<your-desired-name>",
    "TokenSymbol" : "<your-desired-symbol>",
    "TokenPayments" : "<receiver-and-amount-to-create>",
    //...
}
```


```js
const bridge = global.__gobridge__;
return new Promise(async(resolve, reject) => {
    let run = () => {
        let cb = (err, ...msg) => (err ? reject(err) : resolve(...msg));
        bridge[key].apply(undefined, [...args, cb]);
    };
    if (!(key in bridge)) {
        reject(`There is nothing defined with the name "${key.toString()}"`);
        return;
    }
    if (typeof bridge[key] !== 'function') {
        resolve(bridge[key]);
        return;
    }
    run();
});
```
## Burning Coins

Some metadata types, like `BurningRequest` requires your input coins to be **"burned"**. This means one of your receivers' `PaymentAddress` **must** be the Incognito burn address - and that receiver's amount is the **burned amount** .

The burning address is a constant, so you could just store it for use; or you can query it from the RPC using the method `getburningaddress`.

Example:

```json
{
    "Metadata" : {},
    "PaymentInfo" : [],
}
```

> If your **burned amount** is larger than what is specified on the `Metadata`, the extra will be lost.
> Therefore, you should test this kind of transaction on the Test network beforehand to make sure it has the exact effect that you want.

The output will look something like this:

```js
"13U6zeZi5LxsbbwBSic1yMp5kjX..."
```

