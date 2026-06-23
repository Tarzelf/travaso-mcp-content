# Travaso MCP — Tokens Variant C

Audience: solo founders building AI travel agents.

Source notes: tool names, endpoint behavior, required traveler fields, checkout flow, offer status, and payout language must trace to `SKILL.md` or the live `/tokens/setup` page. Pricing, commission range, and proof points stay bracketed until a user-owned `facts.md` or the setup page provides final values.

---

## Hero

**Eyebrow:** Travaso MCP by 7hive.com

**H1:** Add hotel checkout to your AI agent.

**Subheadline:** Travaso gives a travel agent four hotel-commerce calls: search competitive hotel quotes, create a tracked checkout link, check offer status, and cancel eligible offers when an operator asks.

**Primary CTA:** Get a Travaso key

**Secondary CTA:** Read setup docs

**Pricing line:** Monthly: [PRICE_MONTHLY] · Annual: [PRICE_ANNUAL] · Paid-key commission: [COMMISSION_RANGE].

---

## Why this exists

A solo founder can build a useful travel agent that answers hotel questions.

The harder step is commerce: collect the trip details, quote hotels, let the traveler pick one, create the checkout link, and track the offer afterward.

Travaso MCP is the narrow layer for that step. It is not a general travel API, and this page should not present it as one.

---

## Current product surface

| Tool | What the agent uses it for |
| --- | --- |
| `search_competitive_hotel_quotes` | Search hotel options and return `recommendationId` values. |
| `create_offer_checkout_link` | Create a tracked Stripe checkout URL after the traveler chooses an option. |
| `get_offer_status` | Check payment, booking, earning, and payout readiness for an `offerId`. |
| `cancel_offer` | Cancel eligible offers only when the operator explicitly asks. |

No other tools are promised in this variant.

---

## Required flow

1. Capture destination, check-in, check-out, adults, rooms, traveler name, email, and phone.
2. Call `search_competitive_hotel_quotes`.
3. Show 2-4 hotel options with the public Booking.com-style price, Travaso cost or sell price, potential profit, and fit.
4. Wait for the traveler to approve one specific option.
5. Call `create_offer_checkout_link`.
6. Show the checkout URL exactly as returned.
7. Store the returned `offerId`.
8. Use `get_offer_status` for follow-up.

Payout copy should follow the setup page: commission can be tracked before payout is unlocked, and payout is not unlocked until the stay is finished.

---

## What the founder owns

- The agent experience
- The trip intake
- The recommendation UI
- The server-side token storage
- The user-facing booking conversation

Travaso supplies the documented hotel quote, checkout, status, and operator-cancel tool surface.

---

## Pricing placeholders

| Key | Price | Paid-key commission |
| --- | --- | --- |
| Monthly | [PRICE_MONTHLY] | [COMMISSION_RANGE] |
| Annual | [PRICE_ANNUAL] | [COMMISSION_RANGE] |

Replace these placeholders only when the source exists in `/tokens/setup` or `facts.md`.

---

## Final CTA

**Build the agent. Use Travaso for the hotel-commerce call path.**

Get a key, connect the MCP server, and test the search-to-checkout-to-status loop.

**CTA:** Get a Travaso key

**Footer note:** Travaso MCP is a 7hive.com product.
