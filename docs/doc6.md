---
id: doc6
title: Upgrading to Privacy-v2
sidebar_label: Upgrading
---

## Converting your **PRV** coins

The big change in Privacy protocol means coin owners will need to convert their current coins to version 2. Our `App` will handle this automatically.

You can also create a converting transaction using `privacy.wasm`. Use the function `createConvertTx` and pass your *version 1* `PRV` coins as input.
```js
{
    "PaymentInfo": [{
        "PaymentAddress":"15pABFiJVeh9D5uiQEhQX4SVibGGbdAVipQxBdxkmDqAJaoG1EdFKHBrNfs",
        "Amount":"100"
    }],
    "InputCoins":["<some-coin>"],
    "TokenID":"699a3006d1865ebdc437053b33df6a62c6c7c2f554f2fd0adf99a60f5117f945",
    "CoinCache":{}
}
```

Example:

## Converting your **pToken** coins

Your parameters need to specify what token you want (`TokenID`) and which coins to convert (`TokenInputs` - in *version 1*)

> Some PRV for fee is needed for this transaction. And the PRV **must** be *version 2*. So convert your PRV before converting tokens.

Example:

## Creating a custom token

The Incognito network allows creation of custom token, as long as their name & symbol do not conflict with existing ones. Simply set

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

inside your `TokenParams`.

Example: