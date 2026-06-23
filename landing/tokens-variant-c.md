# Travaso MCP — Tokens Variant C

Audience: solo founders building AI travel agents.

Source guardrail: this copy only claims what is documented in the current Travaso MCP skill and the current tool list. Pricing, commission, and proof points stay as placeholders until `/tokens/setup` and `facts.md` exist.

---

## Hero

**Eyebrow:** Travaso MCP by 7hive.com

**H1:** Turn your AI travel agent into a hotel checkout flow.

**Subheadline:** Travaso gives your agent the hotel-commerce loop: search live hotel quotes, compare against public pricing, create a tracked checkout link, and check offer status after checkout.

**Primary CTA:** Get a Travaso key

**Secondary CTA:** Read setup docs

**Pricing line:** Monthly: [PRICE_MONTHLY] · Annual: [PRICE_ANNUAL] · Paid keys earn [COMMISSION_RANGE].

---

## Why this exists

Most solo-founder travel agents stop at recommendations.

The user asks for a hotel. The agent suggests options. Then the user leaves to book somewhere else.

Travaso adds the commerce step your agent was missing: a Stripe-backed checkout link tied to the agent key.

---

## The current loop

1. Capture the trip and traveler fields.
2. Call `search_competitive_hotel_quotes`.
3. Show the public Booking.com-style price next to the Travaso cost.
4. Wait for the traveler to choose a specific option.
5. Call `create_offer_checkout_link`.
6. Store the returned `offerId`.
7. Use `get_offer_status` for follow-up.

Cancellation exists, but it is operator-initiated only: `cancel_offer`.

---

## What you get

### Search

`search_competitive_hotel_quotes` returns commissionable hotel options and `recommendationId` values your agent can pass into checkout.

### Checkout

`create_offer_checkout_link` returns a Stripe-backed checkout URL. The link is the attribution step.

### Status

`get_offer_status` checks payment, booking, earning, and payout readiness for an offer.

### Operator control

`cancel_offer` cancels eligible offers only when the operator explicitly asks.

---

## What you do not have to invent

- A hotel quote surface
- A checkout handoff
- Agent-level booking attribution
- Offer-status follow-up
- A cancellation command for operator workflows

You still own the product experience: the agent, the trip intake, the recommendation logic, and the user-facing copy.

---

## Pricing

| Key | Price | Commission |
| --- | --- | --- |
| Monthly | [PRICE_MONTHLY] | [COMMISSION_RANGE] |
| Annual | [PRICE_ANNUAL] | [COMMISSION_RANGE] |

Commission is tracked through the Travaso offer flow. Payout timing should be described exactly as documented in the current setup page before publishing.

---

## Final CTA

**Build the agent. Let Travaso handle the hotel-commerce step.**

Get a key, connect the MCP server, and test the full quote-to-checkout loop.

**CTA:** Get a Travaso key

**Footer note:** Travaso MCP is a 7hive.com product.
