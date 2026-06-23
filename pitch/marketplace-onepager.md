# Travaso MCP — Multi-Agent Marketplace One-Pager

Source notes: this draft uses only the current Travaso MCP skill surface plus placeholders for pricing, commission, and customer proof. Replace bracketed values only after `/tokens/setup` or a user-owned `facts.md` provides the source value.

---

## One-line summary

Travaso MCP is a hotel-commerce layer for multi-agent marketplaces: an agent can search hotel quotes, create a tracked checkout link, and follow offer status through the current Travaso tool surface.

Built by 7hive.com.

---

## Marketplace problem

For a marketplace where agents already handle hotel intent, recommendation is not the end of the workflow.

The documented Travaso flow gives the agent a way to move from quote to traveler-approved checkout link to offer status, with the returned offer ID available for the marketplace to store.

---

## Current tool surface

| Tool | Marketplace use |
| --- | --- |
| `search_competitive_hotel_quotes` | Search hotel options and return `recommendationId` values for an agent-owned quote flow. |
| `create_offer_checkout_link` | Create a Stripe-backed tracked checkout URL from a selected recommendation. |
| `get_offer_status` | Check payment, booking, earning, and payout readiness by `offerId`. |
| `cancel_offer` | Cancel eligible offers when the operator explicitly asks. |

No additional Travaso features are assumed in this draft.

---

## How it fits a marketplace

### 1. One commerce layer

Your marketplace keeps the agent experience. Travaso supplies the documented hotel quote, checkout, status, and operator-cancel calls.

### 2. Per-agent attribution

The checkout link is created from a Travaso recommendation. The marketplace can store the returned offer ID against the agent, user, or conversation.

### 3. Status after checkout

`get_offer_status` lets the marketplace check what happened after the checkout link was sent.

### 4. Operator cancellation

`cancel_offer` exists for explicit operator-initiated cancellation workflows. It should not be called automatically.

---

## Economics

| Plan | Price | Commission |
| --- | --- | --- |
| Monthly | [PRICE_MONTHLY] | [COMMISSION_RANGE] |
| Annual | [PRICE_ANNUAL] | [COMMISSION_RANGE] |

Use the live `/tokens/setup` page or `facts.md` to replace these placeholders before this one-pager is sent externally.

---

## Customer story placeholder

[CASE_STUDY_PLACEHOLDER]

Suggested format once facts exist:

> A marketplace connected Travaso MCP to its agent runtime, issued tracked hotel checkout links from selected recommendations, and used offer status to follow bookings after checkout.

Do not publish a named customer, volume metric, revenue metric, or conversion claim until it exists in `facts.md`.

---

## Buyer fit

Travaso is a fit for marketplaces where:

- Agents already handle travel or itinerary requests
- The marketplace wants a checkout step after hotel recommendations
- The team can store returned `offerId` values
- The operator wants explicit control over cancellation

It is not positioned here as a flights, cars, vacation rentals, or general travel inventory product.

---

## Recommended next step

Give one internal agent a Travaso key, connect the MCP endpoint, and test the quote-to-checkout-to-status loop.

Keep the first integration narrow:

1. Search.
2. User chooses.
3. Checkout link.
4. Offer status.

Then decide whether to roll it out to more agents.
