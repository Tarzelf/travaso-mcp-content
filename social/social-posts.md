# Travaso MCP — Social Content Kit

> Ready-to-post copy for X/Twitter, LinkedIn, and dev communities
> (HN, r/MCP, indie hackers). Each piece is calibrated to the platform
> and links back to elitetravelsales.com/tokens.

---

## X / Twitter

### Thread 1: "How AI agents should sell hotels" (8 tweets)

**1/8:** Your AI travel agent has a conversion problem. It tells users
"Loews Miami Beach looks great for your dates" — and the user goes to
Booking.com themselves. You earn $0. Here's how to fix it. 🧵

**2/8:** Most travel agents are recommendation engines. They don't have:
- Live inventory with availability confirmed
- A price comparison the user trusts
- Attribution that survives to payout

Without those three things, every recommendation is a leak.

**3/8:** Live inventory means actual rate from the property at the
moment of quote. Not "I think there's a room." Not a cached result from
last week.

**4/8:** The price comparison is the only thing that closes against
the "I could just book it myself" objection. Show Booking.com's price
next to your rate. Same hotel. Same dates. The savings is real and
visible.

**5/8:** Attribution is the step everyone forgets. If your checkout
link doesn't carry the agent's identity all the way to payout, the
booking might as well have come from anywhere.

**6/8:** That's why I built Travaso MCP. It's the commerce layer for
AI travel agents. One MCP server, three calls, kickback on every
booking.

- `search_hotels` — live commissionable inventory
- `compare_booking_price` — Booking.com price vs partner rate
- `create_offer_checkout_link` — attributed checkout URL

**7/8:** The numbers from a real quote: Booking.com $1,956, Travaso
partner $1,568. Same hotel, same room. User saves $388. Agent earns
$78–$156 (10–20% kickback). The room is identical.

**8/8:** Free key earns 3%. Monthly/Annual earns 10–20%. Get a key,
drop the skill, send a checkout link. Every confirmed booking pays you.

https://elitetravelsales.com/tokens

---

### Thread 2: "MCP commerce primitives" (5 tweets)

**1/5:** I think MCP is going to give us a new layer of agent
primitives — the same way HTTP gave us REST APIs. One pattern I'm
watching: commerce. 🧵

**2/5:** A "commerce MCP" is just a server that exposes:
- search (find inventory)
- quote (price comparison)
- checkout (attributed link)
- status (did the booking pay out)

Same shape for hotels, flights, restaurants, anything bookable.

**3/5:** The kicker is the checkout link. It has to carry the agent's
identity end-to-end, so the booking attributes back. That's the piece
HTTP-only commerce APIs struggled with — agents had to pass tokens
manually, get lost in redirects, etc.

**4/5:** I built one for hotels. Travaso MCP. Same primitive pattern:
search → quote → checkout → status. Hotel inventory, Booking.com
price comparison, kickback per booking.

**5/5:** If you're building an agent that sells anything bookable, the
shape is the same. Drop me a line if you want to talk about a
non-hotel version — restaurants, flights, experiences. The pattern
travels.

https://elitetravelsales.com/tokens

---

### Single-tweet (high-frequency, A/B test these)

> AI travel agents that don't earn commission on bookings are
> recommendation engines with extra steps. Travaso MCP turns yours into
> a booking engine in 10 minutes. Free key, 3–20% kickback.
> https://elitetravelsales.com/tokens

> Most travel agents stop at "you should book Loews." Travaso makes
> yours stop at "here's your checkout link." Same room, lower price,
> you earn the spread. https://elitetravelsales.com/tokens

> I built a commerce MCP for hotels. Three calls — search, quote,
> checkout — and your agent earns a kickback per booking. Free key to
> start. https://elitetravelsales.com/tokens

---

## LinkedIn (longer-form, more professional)

**Title:** Why AI travel agents need a commerce layer

The first wave of AI travel agents are essentially recommendation
engines with a chat interface. They tell the user "Loews Miami Beach
looks great for your dates" and the user immediately opens Booking.com
in another tab, books there, and the agent has earned exactly $0.

This is a conversion problem masquerading as a product problem. Three
things have to be true for an AI agent to actually sell a hotel:

1. **Live inventory.** Not "I think there's a room" — actual rate
   from the property, availability confirmed at the moment of quote.
2. **A price comparison the user trusts.** Showing the public
   Booking.com price next to the agent's rate is the only thing that
   closes against the "I could just book it myself" objection.
3. **Attribution that survives to payout.** The checkout link has to
   remember which agent sent it, through the booking, the stay, and
   the commission payout.

I built Travaso MCP to ship all three as a single MCP server. Your
agent calls `search_hotels`, gets commissionable inventory. Calls
`compare_booking_price`, gets the Booking.com public price next to
the partner rate. Calls `create_offer_checkout_link`, gets an
attributed checkout URL to send the user.

Every confirmed booking pays the agent a 3–20% kickback depending on
the tier (free, monthly, annual). Same hotel, same room, the user
saves vs Booking.com.

The shape of this pattern — search, quote, checkout, status — is
going to travel to every bookable vertical. Flights, restaurants,
experiences, anything that has inventory, a price, and a checkout
flow. Hotel is just the first one I shipped.

If you're building an agent that sells anything bookable, drop me a
line. The MCP commerce primitive is the same shape across verticals
and I'd rather build the second one with a partner than the third
one in a vacuum.

Get a free key: https://elitetravelsales.com/tokens
Read the spec: https://github.com/Tarzelf/travaso-mcp-skill

---

## Hacker News (Show HN)

**Title:** Show HN: Travaso MCP – Sell hotels from any AI agent (3-20% kickback)

**Body:**

Travaso MCP is the commerce layer for AI travel agents. Your agent
gets live hotel inventory, a Booking.com price comparison, and a
tracked checkout link. Every confirmed booking pays the agent a
3-20% kickback depending on the tier (free, monthly, annual).

The shape is search → quote → checkout → status, all MCP tool calls.
Three of them live (`search_hotels`, `compare_booking_price`,
`create_offer_checkout_link`); two of them are read-side
(`get_booking_status`, `list_my_bookings`).

The interesting design choice was the price comparison. Showing
Booking.com's public price next to the agent's rate is what closes a
sale against the "I could just book it myself" objection. Without it,
the agent is just recommending a hotel and the user leaves.

Free keys earn 3%, which is enough to demo the full flow. Monthly /
Annual keys earn 10-20% depending on the offer.

Wired into Hermes Agent / Claude / Cursor / ChatGPT-compatible MCP
clients takes about 10 minutes — drop the skill, set one env var.
Happy to talk about the multi-agent marketplace version where every
agent gets its own key and its own payouts.

Stack: Next.js for the marketing surface, MCP over HTTP for the
commerce surface. Built solo over the last few months.

Looking for feedback on:
- The kickback math — is 10-20% the right range?
- The MCP tool surface — am I missing anything?
- The attribution model — anyone solved this differently?

Skill repo (MIT): https://github.com/Tarzelf/travaso-mcp-skill
Get a key: https://elitetravelsales.com/tokens

---

## r/MCP / r/LocalLLaMA / Indie Hackers

**Title:** I built a commerce MCP for hotels — search, quote,
attributed checkout, kickback per booking

**Body:**

Sharing a small project. Travaso MCP is an MCP server that lets any
agent search live hotel rates, show the Booking.com price next to
the agent's wholesale rate, and issue an attributed checkout link.

The kickback math: Booking.com public total $1,956, Travaso partner
total $1,568. User saves $388. Agent earns 10-20% of that delta
($78-$156). Same hotel, same room.

It's the same commerce primitive across verticals — search, quote,
checkout, status — and I think hotel is a useful first wedge because
the inventory is well-understood and the Booking.com price
comparison is the conversion lever.

Free key, 3% kickback — enough to demo. Monthly/Annual, 10-20% —
production rate limits.

Skill repo: https://github.com/Tarzelf/travaso-mcp-skill
Landing: https://elitetravelsales.com/tokens

Happy to talk to anyone shipping an agent that needs a checkout
button. Especially interested in non-hotel verticals — the primitive
shape travels.

---

## Posting cadence

- **X / Twitter:** 1 thread per week + 1-2 standalone tweets
- **LinkedIn:** 1 long-form post per week
- **Hacker News:** 1 Show HN at launch, then comment-only on related
  threads
- **Dev communities:** Share on relevant launches (r/MCP, indie
  hackers, MCP Discord) when you ship a meaningful update

Don't spam. Quality > quantity. Each post should make a specific
argument that helps one specific reader.