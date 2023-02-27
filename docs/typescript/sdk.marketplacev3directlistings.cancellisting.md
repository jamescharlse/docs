---
slug: /sdk.marketplacev3directlistings.cancellisting
title: MarketplaceV3DirectListings.cancelListing() method
hide_title: true
displayed_sidebar: typescript
---

<!-- Do not edit this file. It is automatically generated by API Documenter. -->

# MarketplaceV3DirectListings.cancelListing() method

Cancel Direct Listing

## Example

```javascript
// The listing ID of the direct listing you want to cancel
const listingId = 0;

await contract.directListings.cancelListing(listingId);
```

**Signature:**

```typescript
cancelListing(listingId: BigNumberish): Promise<TransactionResult>;
```

## Parameters

| Parameter | Type         | Description |
| --------- | ------------ | ----------- |
| listingId | BigNumberish |             |

**Returns:**

Promise&lt;[TransactionResult](./sdk.transactionresult.md)&gt;

## Remarks

Cancel a direct listing on the marketplace