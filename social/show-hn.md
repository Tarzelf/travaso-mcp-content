# Show HN: Travaso MCP — hotel checkout for AI agents

## Title

Show HN: Travaso MCP — hotel checkout for AI agents

## Body

Hi HN,

I built Travaso MCP, a hotel-commerce layer for AI agents.

The problem: a travel agent can recommend a hotel, but recommendation alone does not create a booking. Travaso gives the agent a small commerce loop it can actually execute:

- `search_competitive_hotel_quotes` to search hotel options and return `recommendationId` values
- `create_offer_checkout_link` to create a Stripe-backed tracked checkout URL
- `get_offer_status` to check payment, booking, earning, and payout readiness
- `cancel_offer` for operator-initiated cancellation of eligible offers

The agent flow is:

1. Capture destination, dates, room count, traveler name, email, and phone.
2. Search hotel quotes.
3. Show the public Booking.com-style price next to the Travaso cost.
4. Wait for the traveler to choose an option.
5. Create the checkout link.
6. Track the offer after checkout.

Pricing placeholders for the launch page:

- Monthly: [PRICE_MONTHLY]
- Annual: [PRICE_ANNUAL]
- Paid-key commission: [COMMISSION_RANGE]

I am keeping the tool surface intentionally small. The current version is not trying to be a general travel API. It only exposes the four tools above, because the first useful job is getting an agent from quote to checkout without building a booking engine from scratch.

Built by 7hive.com.

Skill repo: https://github.com/Tarzelf/travaso-mcp-skill

Looking for feedback on:

- Whether the four-tool surface is enough for agent builders
- How you would represent checkout attribution in a multi-agent runtime
- What setup detail would block you from trying this in Claude, Cursor, Hermes Agent, or your own MCP client
