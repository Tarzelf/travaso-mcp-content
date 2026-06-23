# Travaso MCP — Pitch Deck for Agent Builders

> Use this as the canonical talking-points doc when pitching Travaso to AI
> agent developers, multi-agent platforms, and travel-tech builders. Drop
> the pieces into a Loom, a Notion page, a YC application, a tweet, or a
> cold email. Each section is standalone.

## One-liner (for bios and tweets)

> Travaso is the commerce layer for AI travel agents. Your agent searches
> live hotel rates, shows the public Booking.com price next to its
> wholesale cost, and sends the user a checkout link. You earn a 3–20%
> kickback on every confirmed booking — same SKU, same room, attribution
> that survives the entire funnel.

## The problem (open with this)

Most AI travel agents are **recommendation engines, not booking engines.**
They tell the user "Loews Miami Beach looks great for your dates" and then
the user goes to Booking.com themselves, books there, and the agent earns
$0. Worse: the agent has no way to recover that revenue because there's no
commerce surface that accepts an agent identity.

Three things have to be true for an AI agent to actually sell a hotel:

1. **Live inventory.** Not "I think there's a room" — actual rate from
   the property, with availability confirmed at the moment of quote.
2. **A price comparison the user trusts.** Showing a number next to
   Booking.com is the only thing that closes a sale against the
   "I could just book it myself" objection.
3. **Attribution that survives to payout.** The checkout link has to
   remember which agent sent it, all the way through the booking,
   the stay, and the commission payout.

Travaso ships all three.

## How the kickback works

Free tier: 3% kickback per confirmed booking. The agent can demo the full
flow, build their integration, and test end-to-end without paying
anything.

Monthly / Annual key: 10–20% kickback, varies by offer/hotel. The exact
percentage for any given result comes back from
`compare_booking_price` — no guessing.

The kickback is **on the public Booking.com price minus your partner
cost**, not on the delta. Example using real numbers from the demo:

| Metric | Amount |
|--------|--------|
| Booking.com public total | $1,956 |
| Travaso partner cost | $1,568 |
| Delta (margin pool) | $388 |
| **Agent share** | **$78–$156 (10–20%)** |

The user saves $388 vs Booking.com. The agent earns up to $156 of that
savings. The platform captures the rest. Everyone wins.

## Who buys Travaso

- **Concierge agents** (personal AI assistants, WhatsApp bots,
  itinerary planners) — turn a recommendation into a booking
- **Multi-agent marketplaces** — every agent on the platform gets its
  own key, its own tracked bookings, its own payouts, all on shared
  inventory
- **Travel MVPs** — skip the 18-month build of a booking engine;
  embed Travaso MCP and ship in a weekend
- **Corporate booking tools** — expense-friendly bookings with
  agent-attributed receipts
- **Travel-content creators** — give your readers an actual booking
  link next to the hotel you reviewed

## What you don't have to build

- Hotel inventory aggregation (we have it)
- Booking engine (we have it)
- Payment processing (we have it)
- Commission attribution (we have it)
- Payouts (we have it)
- Anti-fraud (we have it)

What you DO build: the agent itself, and the user-facing loop that
quotes a price comparison and sends a checkout link.

## Time to first booking

Wired into Hermes / Claude / Cursor / ChatGPT-compatible MCP clients
takes ~10 minutes (drop the skill + set one env var). Time to first
booking depends on your agent's traffic, not on integration effort.

## Pricing (no surprises)

- **Free key** — 3% kickback. Real inventory, sandbox-tier
  rate limits. Use it forever for demos.
- **Monthly key** — 10–20% kickback. Live selling, production
  rate limits.
- **Annual key** — 10–20% kickback. Same as monthly, prepaid.

There is no per-booking fee on top of the kickback. There is no
minimum volume. There is no exclusivity clause. Get the key,
integrate, and start earning.

## The agent-loop we recommend (verbatim)

1. User asks about a hotel
2. Agent calls `search_hotels` for the city + dates
3. Agent calls `compare_booking_price` on each result
4. Agent replies to user with the comparison and savings
5. Agent issues a `create_offer_checkout_link` and **sends it in the
   same message**
6. User clicks, books, stays, agent earns kickback

Step 5 is the only step that pays you. If your agent skips it, the
user books direct and you earn nothing.

## What's next

Get a key: https://elitetravelsales.com/tokens

Read the skill spec: https://github.com/Tarzelf/travaso-mcp-skill

Questions / partnerships: support@elitetravelsales.com (replace with
real address when you set it up)

---

> Built by Tarzelf / 7hive Research. Reach out if you're shipping an
> agent marketplace or a concierge product — we have a multi-agent
> rollout playbook that takes you from solo operator to thousands of
> attributed bookings per month.