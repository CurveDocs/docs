---
id: overview
title: Llamalend
sidebar_label: Overview
---

import GuideCardGrid from '@site/src/components/GuideCardGrid';
import ThemedImage from '@theme/ThemedImage';

## What is Llamalend?

Llamalend is Curve's lending platform that combines two distinct lending products under a unified interface:

- **Mint Markets**: Allow users to mint crvUSD against approved collateral types (voted in by the DAO)
- **Lending Markets**: Traditional lending markets where users borrow funds against collateral supplied by other users

## How to Use Llamalend

Llamalend offers two main ways to participate in the platform:

- **Borrowing**: Borrow crvUSD or other assets by providing collateral. Available in both mint markets and lending markets, allowing you to access liquidity while maintaining exposure to your crypto assets.

- **Supplying**: Supply assets to earn yield by lending them to borrowers. Only available in **lending markets** - mint markets don't offer supply opportunities since crvUSD is minted rather than borrowed from existing liquidity.

Whether you want to borrow for leverage or supply for yield, Llamalend provides a comprehensive platform for both use cases with isolated markets that keep risk contained.

**Market Structure**: All markets on Llamalend are **isolated one-way markets**, meaning each market only has one collateral token and one borrowable token. This design keeps risk contained within each market and makes it easier to understand your exposure. Unlike some other protocols where risks can spread across multiple assets, Llamalend's isolation ensures that problems in one market don't affect others.

## Mint vs Lending Markets

**Mint Markets** enable users to **mint** crvUSD directly against specific collateral types approved by the DAO. This is a direct minting process where new crvUSD tokens are created against deposited collateral.

**Lending Markets** operate like traditional DeFi lending protocols, where users **borrow** existing funds from vaults. No new tokens are minted - users borrow from the supply provided by other participants in the market.

All lending markets must include crvUSD as either a collateral token or the borrowable token, ensuring integration with Curve's stablecoin ecosystem.

From a user interface and usage perspective, both products function identically. The primary operational difference is in how borrow rates behave between mint markets and lending markets.

<GuideCardGrid guideKeys={['howToBorrow', 'howToLend']} />

## Key Advantages

Unlike traditional DeFi lending protocols like Aave or Compound, Llamalend leverages a unique **LLAMMA (Lending-Liquidating AMM)** system that provides enhanced flexibility and protection during market volatility.

**Key Benefits:**
- **Gradual Liquidations**: More gradual liquidations compared to traditional protocols, reducing the risk of cascading liquidations during market stress
- **Better Price Discovery**: Integration with Curve's AMM technology provides more efficient capital utilization
- **Permissionless Markets**: Anyone can create new lending markets, allowing for organic growth of the ecosystem
- **Isolated Risk**: Each market is isolated, preventing risk from spreading across multiple assets

---

## Navigating the UI

The Llamalend interface provides comprehensive market discovery and filtering capabilities to help users find the right lending opportunities. The main markets view displays all available lending markets with key metrics and real-time data.

The main interface displays a comprehensive table of all lending markets with key metrics including collateral-borrow pairs, current borrow rates, supply yields, market utilization, available liquidity, and total value locked. Each market row shows real-time data with visual indicators like progress bars for utilization rates.

<figure>
<ThemedImage
    alt="Llamalend UI Overview"
    sources={{
        light: require('@site/static/img/user/llamalend/ui/overview-light.png').default,
        dark: require('@site/static/img/user/llamalend/ui/overview-dark.png').default,
    }}
    style={{ width: '1000px', display: 'block', margin: '0 auto' }}
/>
</figure>

The interface provides powerful search and filtering capabilities to help users find specific markets. Users can search by market name or contract address, toggle between mint markets and lending markets, and apply filters for specific chains, tokens, or numerical ranges like liquidity and TVL. Additional customization options allow users to show or hide specific data columns and organize their view according to their preferences.


<figure>
<ThemedImage
    alt="Llamalend Filter"
    sources={{
        light: require('@site/static/img/user/llamalend/ui/filter1-light.png').default,
        dark: require('@site/static/img/user/llamalend/ui/filter1-dark.png').default,
    }}
    style={{ width: '1000px', display: 'block', margin: '0 auto' }}
/>
</figure>

<figure>
<ThemedImage
    alt="Llamalend Filter"
    sources={{
        light: require('@site/static/img/user/llamalend/ui/filter2-light.png').default,
        dark: require('@site/static/img/user/llamalend/ui/filter2-dark.png').default,
    }}
    style={{ width: '150px', display: 'block', margin: '0 auto' }}
/>
</figure>