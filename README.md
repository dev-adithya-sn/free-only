# free-only

A Claude skill that answers "how do I run / build / deploy / host this" questions using **only genuinely free pathways** — open-source tools, free-forever tiers, and student packs. No paid services, no trials that bill you later.

## What it does

When you ask Claude how to accomplish a technical goal that normally costs money (hosting, databases, LLM APIs, domains, storage, email, CI, etc.), this skill makes Claude answer with a path that costs ₹0 / $0 out of pocket. Every step that would normally need a credit card gets swapped for a free alternative. If a step has no free option, Claude says so plainly and gives the cheapest real option instead of pretending.

## When it triggers

Automatically, on questions like:

- "how can I run this"
- "how do I build / deploy / host this"
- "what do I need to do X"
- "cheapest way to…" / "free way to…" / "do this on zero budget"

It fires even when you don't say the word "free" — most build/deploy questions have a hidden cost dimension. It stands down only if you've already said you're fine paying.

## How "free" is ranked

The skill prefers options in this order, because each tier is harder to revoke than the next:

1. **Open-source / self-hostable** — runs on your machine or a free host, can't be taken away (Postgres, SQLite, Ollama, Caddy).
2. **Free-forever tiers** — real perpetual plans, not trials (Vercel, Cloudflare, Supabase, Neon, Groq, Render).
3. **Student / promo packs** — GitHub Student Developer Pack, free .me/.tech domains, student credits.

It explicitly rejects free **trials** and "free tier but requires a card" as fake-free, and flags any card requirement loudly.

## The honesty rule

Every free option comes with its catch named in one line — Render free services sleep after 15 min idle, free Postgres tiers pause on inactivity, GitHub Actions is free only for public repos, free email tiers have daily caps. A free path you don't understand will bite you mid-build, so the skill won't hide the tradeoff.

## Install

1. Download `free-only.skill`.
2. In Claude: **Settings → Capabilities → Skills → Upload skill**.
3. Select the file. Done — it's active in future chats.

## Limitations

Skills only fire for tasks Claude can't trivially answer in one step. A bare question like "how do I host a static site" may get answered directly without the skill. The more substantive the question, the more reliably it triggers.

## Files

```
free-only/
└── SKILL.md    # the skill definition (description = trigger, body = behavior)
```

To edit behavior or triggering, change `SKILL.md` and re-upload. The `description` field controls *when* it fires; the body controls *how* Claude answers.
