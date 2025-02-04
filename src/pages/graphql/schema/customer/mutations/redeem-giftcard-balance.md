---
title: redeemGiftCardBalanceAsStoreCredit mutation
edition: ee
---

# redeemGiftCardBalanceAsStoreCredit mutation

The `redeemGiftCardBalanceAsStoreCredit` mutation converts the entire balance of a gift card to store credit. The gift card must be redeemable and cannot have a balance of 0 at the time you run the mutation. After successfully running the mutation, the value of the gift card changes to 0.

<InlineAlert variant="info" slots="text" />

Run this mutation on behalf of logged-in customers only. [Authorization tokens](../../../usage/authorization-tokens.md) describes how to send a request as a customer.

## Syntax

```graphql
mutation {
  redeemGiftCardBalanceAsStoreCredit(
    input: GiftCardAccountInput
  ) {
    GiftCardAccount
  }
}
```

## Example usage

The following example redeems the gift card with code `"056MHP57TJ5C"`.

**Request:**

```graphql
mutation {
  redeemGiftCardBalanceAsStoreCredit(
    input: {
      gift_card_code: "056MHP57TJ5C"
    }
  ) {
    balance {
      currency
      value
    }
    code
    expiration_date
  }
}
```

**Response:**

```json
{
  "data": {
    "redeemGiftCardBalanceAsStoreCredit": {
      "balance": {
        "currency": "USD",
        "value": 0
      },
      "code": "056MHP57TJ5C",
      "expiration_date": null
    }
  }
}
```

## Input attributes

### GiftCardAccountInput object

The `GiftCardAccountInput` object must contain the following attribute:

Attribute | Data Type | Description
--- | --- | ---
`gift_card_code` | String! | The gift card code

## Output attributes

The `GiftCardAccount` object contains the following attributes:

Attribute |  Data Type | Description
--- | --- | ---
`balance` | Money | The remaining balance of the gift card, including the currency
`code` | String | The gift card code
`expiration_date` | String | The date when the gift card expires, if any

## Errors

Error | Description
--- | ---
`Gift card not found` | The specified `gift_card_code` value does not exist in the `giftcardaccount` table or the amount has been already redeemed.
`Field GiftCardAccountInput.gift_card_code of required type String! was not provided` | The value specified in the `GiftCardAccountInput.gift_card_code` argument is empty.
