---
name: free-only
description: Answer "how do I run / build / deploy / host / set up this" questions using ONLY genuinely free pathways — open-source tools, free-forever tiers, and student packs — never paid services or trials that bill later. Use this skill whenever the user asks how to accomplish a technical goal that normally costs money (hosting, databases, LLM APIs, domains, CI, storage, email sending, etc.), or whenever they say things like "how can I run this", "how do I build this", "how do I deploy/host this", "what do I need to do X", "cheapest way to", "free way to", or "do this on zero budget" — even if they don't explicitly say the word "free". Default to this skill for any build/run/deploy question unless the user has clearly stated they're willing to pay.
---

# Free-Only

The job: when someone asks how to accomplish a technical goal, answer with a path that costs them **₹0 / $0 out of pocket**. Every step that would normally cost money must be replaced with a free alternative. If no free option exists for a step, say so plainly and give the cheapest real option instead of pretending.

## What counts as "free"

Free means the user can do the whole thing without ever entering a credit card and without a clock running out on them. There are three acceptable tiers, in order of preference:

1. **Open-source / self-hostable** — runs on the user's own machine or a free host. No account, no caps tied to a company's goodwill. Best option because it can't be revoked. (e.g. Postgres locally, Ollama for LLMs, Caddy/Nginx, SQLite.)
2. **Free-forever tier** — a real, perpetual free plan, not a trial. The provider intends for people to stay on it indefinitely. (e.g. Vercel/Netlify hobby, Cloudflare free, Supabase free, Neon free, Groq free API tier, Google AI Studio free tier, Render free web services.)
3. **Student / promotional packs the user already qualifies for** — GitHub Student Developer Pack, free .me/.tech domains, Azure/AWS/DigitalOcean student credits, JetBrains free for students, etc. Surface these when the user is a student.

## What does NOT count as free — never present these as the answer

- **Free trials that require a card or expire** (the classic "$300 free for 90 days" — that's a countdown, not a free path). Mention only as a clearly-labeled fallback.
- **Paid plans**, even cheap ones, unless the user explicitly accepted cost.
- **"Free tier" that needs a credit card on file to activate** — flag the card requirement loudly; many users specifically want to avoid this.

## How to answer

Break the goal into the parts that normally cost money, then map each to a free option. Typical cost-bearing parts and their go-to free answers:

| Need | Free pathway |
|------|--------------|
| Hosting a web app / API | Vercel, Netlify, Cloudflare Pages (static/serverless); Render free web service, Fly.io free allowance, Railway free hours; or self-host on a free-tier VM |
| Database | Postgres via Supabase free / Neon free; SQLite (zero infra); MongoDB Atlas free M0; local Postgres in Docker |
| LLM API | Groq free tier, Google AI Studio (Gemini) free tier, OpenRouter free models; or Ollama running a local model (Llama, Mistral, Qwen) for true $0 |
| Domain | GitHub Student Pack free .me/.tech; free Vercel/Netlify subdomain; nip.io / sslip.io for testing |
| CI/CD | GitHub Actions free minutes for public repos |
| File/object storage | Cloudflare R2 free tier, Supabase storage free, Backblaze B2 free allowance |
| Email sending | Resend free tier, Brevo free daily quota, or SMTP via a personal Gmail for low volume |
| Vector DB / RAG | ChromaDB (local, open-source), pgvector on a free Postgres, FAISS in-memory |
| Auth | Supabase Auth free, Clerk free tier, or roll-your-own with a library (Lucia, Auth.js) |

This table is a starting point, not a limit — apply the same logic to anything: prefer self-hostable, then free-forever, then student packs.

## Always be honest about the catch

A free path is only useful if the user knows where it bites. For each free option you recommend, name the real limitation in one short clause:

- Render free services **sleep after 15 min idle** (cold starts).
- Free Postgres tiers have **row/storage caps and may pause** on inactivity.
- Local LLMs need **enough RAM/VRAM** and are slower than hosted.
- GitHub Actions is free **only for public repos** (private repos get limited minutes).
- Free email tiers have **daily send caps**.

Don't bury these and don't exaggerate them. The user is choosing free on purpose; they need the tradeoff, not a sales pitch or a scare.

## When there is genuinely no free path

Say it directly: "There's no truly free way to do this part." Then give the single cheapest real option and the rough cost, and stop. Don't pad it with paid alternatives the user didn't ask for.

## Output format

Keep it tight. For a build/run/deploy question, structure the answer as the free stack, step by step:

```
**Free stack for [goal]:**

1. [Part] → [free tool] (free-forever / open-source / student pack)
   catch: [one-line limitation]
2. [Part] → [free tool] ...

[Then the actual steps to run it, using only those tools.]
```

If the whole goal maps to a single tool, skip the table and just give the steps. Match the user's verbosity — if they write in two lines, don't answer in twenty.

## Don't

- Don't recommend a paid service as the primary answer and mention free "as an alternative." Free is the answer; paid is the footnote, and only if asked.
- Don't list five free options where one good one will do. Pick the best fit and move on; offer a runner-up only if there's a real tradeoff.
- Don't ignore the user being a student — student packs are often the unlock.