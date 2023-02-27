---
slug: /sdk.marketplacev3directlistings
title: MarketplaceV3DirectListings class
hide_title: true
displayed_sidebar: typescript
---

<!-- Do not edit this file. It is automatically generated by API Documenter. -->

# MarketplaceV3DirectListings class

Handles direct listings

**Signature:**

```typescript
export declare class MarketplaceV3DirectListings<TContract extends DirectListingsLogic> implements DetectableFeature
```

**Implements:** DetectableFeature

## Constructors

| Constructor                                                                                   | Modifiers | Description                                                                     |
| --------------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------- |
| [(constructor)(contractWrapper, storage)](./sdk.marketplacev3directlistings._constructor_.md) |           | Constructs a new instance of the <code>MarketplaceV3DirectListings</code> class |

## Properties

| Property                                                        | Modifiers | Type                                                                           | Description |
| --------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------ | ----------- |
| [encoder](./sdk.marketplacev3directlistings.encoder.md)         |           | [ContractEncoder](./sdk.contractencoder.md)&lt;DirectListingsLogic&gt;         |             |
| [estimator](./sdk.marketplacev3directlistings.estimator.md)     |           | [GasCostEstimator](./sdk.gascostestimator.md)&lt;DirectListingsLogic&gt;       |             |
| [events](./sdk.marketplacev3directlistings.events.md)           |           | [ContractEvents](./sdk.contractevents.md)&lt;DirectListingsLogic&gt;           |             |
| [featureName](./sdk.marketplacev3directlistings.featurename.md) |           | "DirectListings"                                                               |             |
| [interceptor](./sdk.marketplacev3directlistings.interceptor.md) |           | [ContractInterceptor](./sdk.contractinterceptor.md)&lt;DirectListingsLogic&gt; |             |

## Methods

| Method                                                                                                                                                   | Modifiers | Description                                                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [approveBuyerForReservedListing(listingId, buyer)](./sdk.marketplacev3directlistings.approvebuyerforreservedlisting.md)                                  |           | Approve buyer for a reserved direct listing                                                                                                                                        |
| [approveCurrencyForListing(listingId, currencyContractAddress, pricePerTokenInCurrency)](./sdk.marketplacev3directlistings.approvecurrencyforlisting.md) |           | Approve a currency for a direct listing                                                                                                                                            |
| [buyFromListing(listingId, quantityDesired, receiver)](./sdk.marketplacev3directlistings.buyfromlisting.md)                                              |           | Buy direct listing for a specific wallet                                                                                                                                           |
| [cancelListing(listingId)](./sdk.marketplacev3directlistings.cancellisting.md)                                                                           |           | Cancel Direct Listing                                                                                                                                                              |
| [createListing(listing)](./sdk.marketplacev3directlistings.createlisting.md)                                                                             |           | Create new direct listing                                                                                                                                                          |
| [currencyPriceForListing(listingId, currencyContractAddress)](./sdk.marketplacev3directlistings.currencypriceforlisting.md)                              |           | Check price per token for an approved currency                                                                                                                                     |
| [getAddress()](./sdk.marketplacev3directlistings.getaddress.md)                                                                                          |           |                                                                                                                                                                                    |
| [getAll(filter)](./sdk.marketplacev3directlistings.getall.md)                                                                                            |           | Get all direct listings                                                                                                                                                            |
| [getAllValid(filter)](./sdk.marketplacev3directlistings.getallvalid.md)                                                                                  |           | <p>Get all valid direct listings</p><p> A valid listing is where the listing is active, and the creator still owns &amp; has approved Marketplace to transfer the listed NFTs.</p> |
| [getListing(listingId)](./sdk.marketplacev3directlistings.getlisting.md)                                                                                 |           | Get a single direct listing                                                                                                                                                        |
| [getTotalCount()](./sdk.marketplacev3directlistings.gettotalcount.md)                                                                                    |           | Get the total number of direct listings                                                                                                                                            |
| [isBuyerApprovedForListing(listingId, buyer)](./sdk.marketplacev3directlistings.isbuyerapprovedforlisting.md)                                            |           | Check if a buyer is approved for a specific direct listing                                                                                                                         |
| [isCurrencyApprovedForListing(listingId, currency)](./sdk.marketplacev3directlistings.iscurrencyapprovedforlisting.md)                                   |           | Check if a currency is approved for a specific direct listing                                                                                                                      |
| [revokeBuyerApprovalForReservedListing(listingId, buyer)](./sdk.marketplacev3directlistings.revokebuyerapprovalforreservedlisting.md)                    |           | Revoke approval of a buyer for a reserved direct listing                                                                                                                           |
| [revokeCurrencyApprovalForListing(listingId, currencyContractAddress)](./sdk.marketplacev3directlistings.revokecurrencyapprovalforlisting.md)            |           | Revoke approval of a currency for a direct listing                                                                                                                                 |
| [updateListing(listingId, listing)](./sdk.marketplacev3directlistings.updatelisting.md)                                                                  |           | Update a direct listing                                                                                                                                                            |