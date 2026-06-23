# Travaso MCP — Sales Landing Copy

> Three variants of the /tokens landing page, ranked by likely conversion
> for three different audiences. The current /tokens page is a hybrid
> technical-and-developer pitch; these variants give you something to
> A/B test against once you have traffic.

---

## Variant A: Developer-First (current page, tightened)

**H1:** Sell hotels from any agent.

**Sub:** Travaso MCP gives your AI agent live hotel inventory, a price
comparison against Booking.com, and a checkout link that pays you a
3–20% kickback on every confirmed booking.

**Primary CTA:** Get a free key
**Secondary CTA:** See the docs

**Hero proof:** Inline terminal mock — agent searches Miami Beach, gets
12 commissionable hotels, shows the public Booking.com price next to the
Travaso partner cost, issues a tracked checkout link.

---

## Variant B: Multi-Agent Marketplace / Platform Buyer

**H1:** Give every agent on your platform a checkout button.

**Sub:** Travaso is the hotel-commerce layer behind AI travel agents.
Each agent gets its own API key, its own tracked bookings, its own
payouts. Inventory is shared, attribution is per-agent.

**Primary CTA:** Book a 15-min demo
**Secondary CTA:** See the agent economics

**Hero proof:** A 3-agent marketplace dashboard — agent 1 made 14
bookings this month, agent 2 made 9, agent 3 made 22. All tracked,
all attributed, all paying out.

**Body sections:**
1. **One integration, every agent.** Drop Travaso MCP into your
   multi-agent runtime and every agent gets its own key. No per-agent
   plumbing to write.
2. **The kickback math.** Show the agent the margin per booking. Show
   the platform the take rate. Both are clear, both are real-time.
3. **Attribution that survives the funnel.** The checkout link
   remembers the agent through the booking, the stay, and the payout.
   No "did this booking come from us?" arguments.
4. **Case study box:** *(when you have one)* "[Platform X] shipped
   Travaso to 200 agents in 30 days and saw $Y in attributed bookings."

---

## Variant C: AI Travel Agent Builder (solo founder)

**H1:** Your travel agent deserves a kickback.

**Sub:** Right now your AI travel agent is a recommendation engine.
Travaso makes it a booking engine. Same hotel, same room — your user
saves vs Booking.com, you earn 3–20%, the room is the same.

**Primary CTA:** Wire up in 10 minutes
**Secondary CTA:** See the economics

**Hero proof:** $1,956 → $1,568 with a single MCP call. Booking.com
public price vs your agent's Travaso partner rate. Same hotel.

**Body sections:**
1. **The conversion loop, drawn.** "User asks → you quote → you send
   the link → user books → you earn. Five steps, three MCP calls."
2. **What you stop building.** Hotel inventory, booking engine,
   payment processing, commission attribution, payouts. All yours to
   skip.
3. **Three integration options.** Hermes Agent (drop the skill),
   Claude Desktop (paste the JSON), custom backend (REST endpoints).
   Pick the one that matches your stack.
4. **The honest math.** Solo founder with 1,000 conversations/month,
   5% close on hotel quotes, $300 average savings per booking,
   15% kickback = **$2,250/month** in attributed revenue from a
   weekend of integration work. Upgrade from there.

---

## Conversion instrumentation to add

Whichever variant you ship, instrument these:

- **Pricing tier page-view** — how many users reach the free vs
  monthly CTA. If monthly CTR < 5%, the pricing copy needs work.
- **Free key request rate** — if < 30% of pricing page views lead to a
  key request, the value prop isn't landing.
- **Time from key request to first MCP call** — if > 24 hours, the
  setup docs are confusing.
- **Time from first MCP call to first checkout link** — if > 5 minutes,
  the agent isn't getting clear next steps.
- **Checkout link → booking rate** — the conversion metric that
  actually pays you. If < 10%, the price-comparison copy needs work.

Instrumentation first, optimization second. Don't iterate copy in the
dark.

---

## SEO keywords to target

Long-tail, low-competition, high-intent:

- "AI agent hotel booking"
- "MCP server for hotels"
- "agent kickback booking"
- "AI travel agent commerce"
- "agent hotel commission API"
- "Booking.com price comparison API"
- "agent-tracked checkout link"

Use these in:
- /tokens page H1 + sub
- README and skill.md H1 + meta
- A `blog/` directory with one long-form post per keyword cluster
- Twitter/X threads (post + reply strategy)