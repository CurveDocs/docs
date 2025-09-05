---
id: liquidation-protection
title: Liquidation Protection & Loan Health
sidebar_label: Liquidation Protection & Loan Health
---

import ThemedImage from '@theme/ThemedImage';
import CollateralConversion from '@site/src/components/CollateralConversion';

## What is Liquidation Protection?

Curve's liquidation mechanism works differently from other protocols. Instead of liquidating positions at fixed price points, positions are only liquidated when the loan's health reaches 0%.

**Key Point:** Your position's **health indicator** is critical. As long as health stays above 0%, your position remains protected.

This system gives you more time to act - you can repay debt, close the loan, or let the system protect your position automatically. Unlike traditional protocols where liquidation is instant and permanent, Curve's approach allows for recovery and gives you more control over your position.

---

## How Does Liquidation Protection Work?

When your collateral price drops into the [liquidation protection range](#what-is-the-liquidation-protection-range), the system automatically starts protecting your position by gradually converting your volatile collateral into stable crvUSD. This creates a safety buffer that reduces your exposure to price volatility. The further down the price goes, the more of your collateral will be converted into crvUSD.

When prices recover, the system automatically converts the crvUSD back to your original collateral, potentially restoring your position to its original state (minus some [losses](#what-are-the-losses-during-liquidation-protection) from the protection process).

<CollateralConversion />

---

## What is the Liquidation Protection Range?

The liquidation protection range is defined by two price points for your collateral asset: a high and a low. Your position enters protection mode when the collateral price drops into this zone.

**Range Positioning:**
- **The start of this range depends on the LTV of the loan**: The more you borrow, the closer the higher price point of the range will be to the current market price of the collateral. The less you borrow, the further away it is.

**Range Size:**
- **The size of this range depends on your bands**: The size of your liquidation protection zone depends on the number of bands you chose when creating your loan. The more bands you select (maximum 50, minimum 4), the bigger the protection zone. The fewer bands you choose, the narrower the zone.

**Band Impact:**
- **More bands = Wider protection zone = lower risk**
- **Fewer bands = Narrower protection zone = higher risk**

---

## What is Loan Health and How Does It Decrease?

**Health is the most important metric to monitor** because it determines when your loan will be fully liquidated. You should always keep track of your loan's health, regardless of market conditions.

**Health decreases due to:**
- **Collateral price drops**: The closer the price of your loan's collateral gets to the liquidation range, the lower the health will get
- **Borrowing more funds**: Taking on additional debt reduces your health
- **Interest accumulation**: Interest is "charged" every second by gradually increasing the debt you own, constantly decreasing health (albeit very slowly)

For tips on monitoring and preventing health issues, see [How Can I Monitor and Prevent Problems?](#how-can-i-monitor-and-prevent-problems).

---

## What are the Losses During Liquidation Protection?

When your position enters the liquidation protection zone, losses occur due to the constant change of your collateral composition. As the system gradually converts your volatile collateral into stable crvUSD, these composition changes result in losses that reduce the total value of your collateral.

These losses are hard to predict because they depend on multiple external factors such as market volatility, available liquidity, and the number of bands you chose. While volatility and liquidity are not easily influenced by you, **you have significant control over potential losses by choosing the number of bands when creating your loan**.

**Band Choice Impact:**
- **More bands = Fewer losses** in the liquidation protection zone
- **Fewer bands = Higher losses** in the liquidation protection zone

For example, having only 4 bands can result in quite high losses during liquidation protection, which can destroy your health very quickly. This is why band selection is such an important decision when creating your position.

Learn more about bands and how to customize them when creating a position [here](./guides/borrow/custom-bands.md).

:::info Do losses always occur?
No. Losses occur **only** when your position is within the liquidation protection zone. As long as your position remains outside this zone, no losses are incurred, regardless of market conditions.
:::

:::warning Important Note
These losses are not temporary - they are permanent reductions in your collateral value that occur during the liquidation protection process. The key is to monitor your position's health and take action before losses accumulate too much.
:::

---

## When Does My Loan Enter Liquidation Protection?

A loan enters liquidation protection when the price of the collateral asset is within the two prices defining the liquidation protection range.

<figure>
<ThemedImage
    alt="Liquidation protection range visualization"
    sources={{
        light: require('@site/static/img/user/llamalend/education/liquidation/liq_range_light.png').default,
        dark: require('@site/static/img/user/llamalend/education/liquidation/liq_range_dark.png').default,
    }}
    style={{ width: '400px', display: 'block', margin: '0 auto' }}
/>
</figure>

---

## What Can I Do When My Loan is in Liquidation Protection?

While a loan is in liquidation protection, the actions a user can take are limited. The most important metric to watch is the loan's health. If a loan is NOT in liquidation protection, users have all possibilities and there are no restrictions at all.

**Restricted Actions:**
- **Collateral actions**: Users cannot add or remove any collateral
- **Borrowing**: Users cannot borrow any more funds

**Available Actions:**
- **Debt repayment**: Users can repay some or all of the debt

**Important Understanding:**
Only repaying all of the debt and therefore fully closing the loan will get the user out of liquidation protection. Repaying some debt (even if it's 99% of all the user's debt) will only increase the health of the loan, but will not get the loan out of liquidation nor change the liquidation range.

---

## Can My Position Recover from Liquidation Protection?

:::info Recovery and Time Flexibility
**Important Understanding**: If prices recover while you're in liquidation protection, you can theoretically return to your original state (minus some losses due to the liquidation protection process). The system gives you more time to act because there's no instant liquidation, but there's actually no need to act at all.

**Key Point**: Users can theoretically stay in liquidation protection forever as long as they ensure their health stays above 0%. The system will continue protecting your position automatically, and if market conditions improve, your position can recover without any manual intervention.
:::

---

## How Do I Get Out of Liquidation Protection?

Because user actions during liquidation protection are partially restricted, the only way to get a loan out of liquidation protection mode is to fully repay the loan and open up a new one.

**Key Points:**
- Adding collateral is restricted
- Even repaying 99% of the debt will not get the loan out of liquidation protection
- Only full debt repayment and loan closure will exit liquidation protection mode

---

## What Happens When My Loan's Health Reaches 0%?

**Important**: Hard liquidation only occurs when health reaches exactly 0%. As long as your health stays above 0%, even by a tiny amount, your position remains protected and can potentially recover if market conditions improve.

When health reaches 0%, your loan will be fully liquidated, meaning all your collateral will be sold to repay the debt, and any remaining collateral will be returned to you.

---

## How Can I Change My Liquidation Protection Range?

The liquidation protection range can only be changed if a loan is currently not in liquidation. If a loan IS in liquidation mode, the only option is to fully repay the loan and create a new one.

**Collateral Actions:**
- **Adding more collateral**: Pushes the liquidation ranges down (e.g., from $1000-$900 to $800-$700)
- **Removing collateral**: Pushes the liquidation range further up (e.g., from $1000-$900 to $1100-$1000)

**Debt Actions:**
- **Borrowing more**: Pushes the liquidation range further up
- **Repaying some debt**: Pushes the liquidation range down
- **Repay all debt**: Fully closes the loan (no liquidation range anymore)

**Rule of Thumb**: The higher the LTV of the loan gets, the closer the liquidation range gets to the current market price.

---

## Why Are Actions Restricted in Liquidation Protection Mode?

Users are not able to add or remove collateral because the loan is already in liquidation protection and the collateral is currently being protected through LLAMMA. The nature of the system does not allow any collateral actions when the position is in liquidation range, as this is a unique situation where the collateral is being actively protected.

---

## How Can I Monitor and Prevent Problems?

While Curve's liquidation mechanism offers greater flexibility and safety, it is still crucial to monitor the health of a loan. **Positions can be fully liquidated once health reaches 0%.** To avoid this outcome, it is highly recommended to monitor loan status regularly and take action when needed.

To simplify this process, a dedicated [Telegram Bot](https://news.curve.fi/llamalend-telegram-bot/) has been developed to continuously track and monitor loan positions.

**Bot Features:**
- **Multi-Address Monitoring**: Track multiple wallet addresses simultaneously
- **Cross-Chain Coverage**: Monitor positions across Ethereum, Arbitrum, Fraxtal, and Optimism
- **Automated Health Checks**: Perform regular position checks every 5–10 minutes
- **Prompt Alerts**: Receive notifications when a loan enters liquidation protection (soft-liquidation) or becomes eligible for liquidation (hard-liquidation)
- **On-Demand Information**: Access current on-chain data for monitored positions

Check out this article for more information on how to set up the Telegram Bot: [Llamalend Telegram Bot](https://news.curve.fi/llamalend-telegram-bot/)
