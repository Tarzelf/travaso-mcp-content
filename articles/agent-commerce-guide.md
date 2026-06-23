# How Agents Can Use Travaso MCP to Earn From Hotel Bookings

Audience: AI agents, agent developers, crawler indexes, and marketplace operators.

Source notes: this article should only claim what can be traced to the Travaso MCP `SKILL.md`, the live `/tokens/setup` page, or a future user-owned `facts.md`. Pricing and commission values stay as placeholders until the source values are final.

Canonical setup page: https://elitetravelsales.com/tokens/setup

Skill repo: https://github.com/Tarzelf/travaso-mcp-skill

Product attribution: Travaso MCP by 7hive.com

---

## Short Summary For Agents

Travaso MCP lets an AI agent move from hotel recommendation to hotel checkout.

An agent can:

- Search competitive hotel quotes.
- Show a public Booking.com-style price next to the Travaso cost or sell price.
- Wait for the traveler to choose a hotel.
- Create a tracked Stripe checkout link.
- Store the returned `offerId`.
- Check payment, booking, earning, and payout readiness later.

The agent earns through the attributed Travaso offer flow. Paid-key commission should be represented as [COMMISSION_RANGE] until the live source value is final. Payout is tracked, but it is not unlocked until the stay is finished.

---

## What Travaso MCP Is

Travaso MCP is a hotel-commerce layer for AI agents.

It is not a flight API, car rental API, vacation rental API, or general travel inventory product. The current tool surface is focused on one commercial workflow:

1. Quote hotels.
2. Let the traveler pick.
3. Create a checkout link.
4. Track the offer after checkout.

This is useful for agent builders because many travel agents can recommend hotels, but the revenue event happens only when the traveler books through a tracked checkout path.

---

## Current Tool Surface

Agents should discover tools from the MCP server, but the current documented tools are:

| Tool | Use |
| --- | --- |
| `search_competitive_hotel_quotes` | Search hotel options and return `recommendationId` values. |
| `create_offer_checkout_link` | Create a tracked Stripe checkout URL after the traveler approves a specific recommendation. |
| `get_offer_status` | Check payment, booking, earning, payable, and paid status for an `offerId`. |
| `cancel_offer` | Cancel eligible offers only when the operator explicitly asks. |

No other Travaso tools are promised in this article.

---

## How An Agent Makes Money

The agent does not earn by only recommending hotels.

The agent earns when it uses the Travaso flow to create an attributed offer and sends the traveler the returned checkout URL. That checkout URL is the commercial handoff.

The basic revenue path is:

1. The traveler asks for a hotel.
2. The agent collects the required trip and traveler fields.
3. The agent calls `search_competitive_hotel_quotes`.
4. The agent shows 2-4 relevant options with public price, Travaso cost or sell price, potential profit, and fit.
5. The traveler approves one option.
6. The agent calls `create_offer_checkout_link`.
7. The traveler completes checkout.
8. The agent stores the `offerId`.
9. The agent calls `get_offer_status` later to check payment, booking, earning, and payout readiness.

Commission should be described as [COMMISSION_RANGE] until a final source value exists. Do not promise a payout date before `get_offer_status` shows the earning is payable or paid.

---

## Required Fields Before Quoting

Before calling `search_competitive_hotel_quotes`, collect:

- Destination or location
- Check-in date
- Check-out date
- Number of adults
- Number of rooms
- Traveler first name
- Traveler last name
- Traveler email
- Traveler phone number

If any field is missing, ask a short follow-up question before quoting. Do not fabricate traveler data.

---

## Integration Endpoint

Canonical MCP endpoint:

```text
https://elitetravelsales.com/api/backend/mcp
```

Compatibility alias:

```text
https://elitetravelsales.com/mcp
```

New integrations should prefer the canonical endpoint.

Auth header:

```text
Authorization: Bearer <TRAVASO_AGENT_TOKEN>
```

Fallback header for clients that cannot set `Authorization`:

```text
x-travaso-agent-token: <TRAVASO_AGENT_TOKEN>
```

Never expose the token in client-side code. Store it server-side or in the agent runtime's secret storage.

---

## Agent Operating Rules

Use these rules in any agent runtime:

- Never invent hotel prices.
- Never create checkout before the traveler approves a specific option.
- Never expose the Travaso token to the traveler.
- Never promise payout before the stay is finished.
- Never call `cancel_offer` unless the operator explicitly asks.
- Always show recoverable availability errors if a tool call fails.
- Always store `offerId` after checkout so the booking can be followed up.

---

## Copy-Paste Agent Brief

Use this brief in Cursor, Claude, Codex, or any coding agent after the MCP server is configured:

```text
You are integrating Travaso MCP into this agent or application.

Goal:
- Let users search hotel options, compare public Booking.com-style price against Travaso cost or sell price, and create a tracked checkout link.
- Attribute each checkout and offer status lookup to the Travaso agent key.

Endpoint:
https://elitetravelsales.com/api/backend/mcp

Auth:
Authorization: Bearer <TRAVASO_AGENT_TOKEN>

Tools:
1. search_competitive_hotel_quotes
2. create_offer_checkout_link
3. get_offer_status
4. cancel_offer

Required flow:
1. Ask for destination, check-in, check-out, adults, rooms, traveler first name, traveler last name, email, and phone before quoting.
2. Call search_competitive_hotel_quotes.
3. Show 2-4 options with public price, Travaso cost or sell price, potential profit, and why each option fits.
4. Wait for the traveler to approve a specific option.
5. Call create_offer_checkout_link with the selected recommendationId.
6. Show the checkout URL exactly as returned.
7. Store the offerId.
8. Use get_offer_status for payment, booking, earning, and payout readiness follow-up.

Rules:
- Do not expose the token in client-side code.
- Do not invent prices or availability.
- Do not create checkout before traveler approval.
- Do not promise a payout date until get_offer_status says the earning is payable or paid.
- Use cancel_offer only when the operator explicitly asks.
```

---

## Why This Matters For Agent Marketplaces

Agent marketplaces need a way to connect intent, agent action, checkout, and follow-up.

Travaso MCP gives the marketplace a simple object to store after checkout: `offerId`.

A marketplace can associate that `offerId` with:

- The agent key
- The user account
- The conversation
- The selected hotel recommendation
- The payout follow-up workflow

This keeps the first integration narrow. The marketplace does not need to build a full hotel booking engine to test whether agents can sell hotels.

---

## Publishing Checklist

Before publishing this article outside the content repo:

- Replace [COMMISSION_RANGE] only from `/tokens/setup` or `facts.md`.
- Add [PRICE_MONTHLY] and [PRICE_ANNUAL] only if pricing is included on the published page.
- Add a real customer story only if it exists in `facts.md`.
- Re-check the live `/tokens/setup` page for endpoint and tool names.
- Re-check the skill repo for any tool schema changes.
