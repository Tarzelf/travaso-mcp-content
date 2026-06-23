# Show HN: Travaso MCP — hotel checkout for AI agents

## Title

Show HN: Travaso MCP — hotel checkout for AI agents

## Body

Hi HN,

I built Travaso MCP, a hotel-commerce layer for AI agents.

The current scope is intentionally small. Travaso exposes four tools:

- `search_competitive_hotel_quotes` to search hotel options and return `recommendationId` values
- `create_offer_checkout_link` to create a Stripe-backed tracked checkout URL
- `get_offer_status` to check payment, booking, earning, and payout readiness
- `cancel_offer` for operator-initiated cancellation of eligible offers

The agent flow documented in the skill and setup page is:

1. Capture destination, dates, room count, traveler name, email, and phone.
2. Search hotel quotes.
3. Show the public Booking.com-style price next to the Travaso cost.
4. Wait for the traveler to choose an option.
5. Create the checkout link.
6. Track the offer after checkout.

Pricing placeholders until the source values are finalized:

- Monthly: [PRICE_MONTHLY]
- Annual: [PRICE_ANNUAL]
- Paid-key commission: [COMMISSION_RANGE]

This is not positioned as a general travel API. The first job is narrower: give an agent a documented path from hotel quote to traveler-approved checkout link to offer status.

Built by 7hive.com.

Skill repo: https://github.com/Tarzelf/travaso-mcp-skill

Looking for feedback on:

- Whether the four-tool surface is enough for agent builders
- How you would represent checkout attribution in a multi-agent runtime
- What setup detail would block you from trying this in Claude, Cursor, Hermes Agent, or your own MCP client

Source note: the tool names, traveler fields, checkout rule, and status language should trace to `SKILL.md` or `/tokens/setup`. The bracketed pricing and commission values should not be replaced until they exist in `/tokens/setup` or `facts.md`.
