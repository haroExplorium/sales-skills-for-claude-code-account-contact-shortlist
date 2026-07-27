# Sales Skills for Claude Code: Account Contact Shortlist

> A Claude Code skill that builds a ranked shortlist of contacts at a target company for prospecting, deal acceleration, or renewal/expansion plays.

## What This Skill Does

The **Account Contact Shortlist** skill pulls the right people at a target account and ranks them for outreach. It uses a use-case lens — new business, active deal, or renewal — and performs a reachability check so you always know who is actually contactable.

**Use it when you want to:**
- Find the buying committee at a prospect account
- Accelerate an in-flight deal by identifying the economic buyer and technical evaluator
- Expand or renew by surfacing the right executive sponsor and product owners
- Build a prioritized outreach list for an SDR or AE

## Installation

Install the [Explorium CLI](https://github.com/explorium-ai/cli) and add this skill to your Claude Code agent:

```bash
# Install the Explorium CLI
pip install explorium-cli

# Configure your API key
explorium config init -k YOUR_API_KEY
```

Then copy `SKILL.md` into your Claude Code agent's skills directory, or reference it via the Explorium plugin.

## Usage

Invoke this skill from Claude Code with a natural-language prompt:

```
Build a contact shortlist for stripe.com, focus on VP+ in Finance and Engineering for deal acceleration.
```

```
Give me the top 25 contacts at Salesforce for a renewal play — prioritize product owners and executive sponsors.
```

```
Account contact shortlist for notion.so, prospecting use case, Director+ in Marketing and Product.
```

## Input Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| Company name or domain | ✅ Yes | — | The target account (e.g. `stripe.com` or `Stripe`) |
| Use case | No | `prospecting` | One of: `prospecting`, `deal acceleration`, `renewal`, `expansion` |
| Seniority focus | No | All levels | e.g. `C-level`, `VP+`, `Director+`, or a function like `RevOps` |
| Shortlist size | No | `25` | Number of contacts to return (max 100) |

## Output

The skill returns a structured brief containing:

- **Target Account** — Company name, domain, industry, headcount, revenue range, HQ, public/private
- **Use Case Frame** — The resolved use case and what the shortlist optimizes for
- **Ranked Shortlist** — Full name, job title, seniority, department, professional email, phone, LinkedIn, and a one-line reason for inclusion
- **Coverage Read** — Breakdown by department and seniority; reachability stats (email, phone coverage)
- **Engagement Priority** — Top 5 contacts to reach first, with outreach order suggestion
- **Next Steps** — Recommended follow-on actions (account context enrichment, event signals, etc.)

## How It Works

The skill follows a structured workflow powered by the [Explorium AgentSource API](https://explorium.ai):

1. **Resolve the account** via `match-business` to get a verified `business_id`
2. **Pull firmographics** for industry, headcount, revenue, and HQ
3. **Map the use case** to a persona blueprint (buying committee for prospecting, economic buyer + technical evaluator for deals, product owners + exec sponsor for renewal)
4. **Fetch candidates** from Explorium's prospect database, scoped to the account and filtered by seniority and department
5. **Enrich contacts** with verified emails, phone numbers, and LinkedIn profiles
6. **Rank and group** by persona fit, reachability, and tenure signals

## Powered by Explorium

This skill uses the [Explorium AgentSource API](https://explorium.ai) — a B2B data platform with 350M+ people and 80M+ companies. Explorium provides real-time firmographics, technographics, funding signals, hiring trends, and verified contact data.

## Related Skills

- [Account Research](https://github.com/explorium-ai/Agent-skills/tree/main/skills/account-research) — Full intelligence brief on a target company
- [List Builder](https://github.com/explorium-ai/Agent-skills/tree/main/skills/list-builder) — Build a targeted list from a natural-language audience brief
- [Personalize Email](https://github.com/explorium-ai/Agent-skills/tree/main/skills/personalize-email) — Assemble a personalization signal pack for outreach
- [Meeting Prep](https://github.com/explorium-ai/Agent-skills/tree/main/skills/meeting-prep) — Prepare a decision-ready brief for an upcoming sales meeting

## License

MIT — see [LICENSE](LICENSE)
