<!-- ═══════════════ HEADER ═══════════════ -->
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:00ff9c&height=200&section=header&text=Ayishik%20Das&fontSize=60&fontColor=ffffff&animation=twinkling&fontAlignY=35&desc=AI%20Agents%20%E2%80%A2%20LLM%20Infra%20%E2%80%A2%20RAG%20%E2%80%A2%20Backend&descAlignY=58&descSize=18" />
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00FF9C&center=true&vCenter=true&width=720&lines=Built+a+UPI-style+payments+engine+from+scratch+%F0%9F%92%B8;Then+came+back+and+broke+it+on+purpose+%F0%9F%94%93;Now+building+memory+for+AI+agents+%F0%9F%A7%A0;0.1ms+vector+search+at+1M+nodes+%E2%9A%A1;GenAI+POCs+%40+an+MNC+%7C+2nd+in+internal+AI+challenge+%F0%9F%8F%86" />
</p>

<p align="center">
  <a href="https://ad-folio.vercel.app"><img src="https://img.shields.io/badge/Portfolio-0f2027?style=for-the-badge&logo=vercel&logoColor=00ff9c" /></a>
  <a href="https://linkedin.com/in/ayishik-das"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="mailto:ayishikofficial@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" /></a>
</p>

---

### `$ whoami`

```yaml
name:        Ayishik Das
role:        System Engineer @ MNC  # GenAI POCs for enterprise clients
focus:       [AI agents, LLM infrastructure, RAG systems, backend engineering]
flagship:    PayP  # payments engine, v1 → v6, still evolving
shipped_at_work:
  - 3 GenAI POCs (Claude + Python, integrated with PeopleSoft)
  - ~70% reduction in manual processing
  - 🥈 2nd place, company-wide AI challenge
belief:      "AI is only as good as the backend underneath it"
languages:   [C++20, Python, JavaScript/TypeScript, C, Java]
location:    Kolkata, India 🇮🇳
status:      open_to(["AI infra", "backend", "founding engineer"])
```

---

### 💸 Flagship: [PayP](https://github.com/AyishikD/PayP) — a UPI-style payment platform, built from scratch

> My first serious backend, written by hand before AI tools were part of how I work.
> Two years later I came back, audited it like an attacker, and rebuilt the parts that would have lost real money.

[![Swagger](https://img.shields.io/badge/API_Docs-Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](https://payp.onrender.com/api-docs/)
[![Postman](https://img.shields.io/badge/Tested_in-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)](https://www.postman.com/mission-geologist-4118891/payp/collection/za1hjme/routes-payp)
[![Medium](https://img.shields.io/badge/Write--up-Medium-000000?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@ayishikad/payp-revolutionizing-payment-integration-with-custom-api-b63a6a329b97)
![Node](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Postgres](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

<sub>Swagger runs on a free tier — the first load can take ~50s to wake up.</sub>

```text
 client ──► Express ──► rate limiter ──► JWT auth ──► controller
                                                          │
                              verify PIN (bcrypt) ◄───────┤
                                                          ▼
                              ┌──────────────────────────────────────┐
                              │  BEGIN                               │
                              │    SELECT … FOR UPDATE  (row locks)  │
                              │    debit / credit  DECIMAL(14,2)     │
                              │    write transaction log             │
                              │  COMMIT                              │
                              └──────────────────────────────────────┘
                                                          ▲
 cron ──► AutoPay scheduler ──► due mandates ─────────────┘──► mandate events
```

#### 🔓 v6: I attacked my own v1 code

| Bug in my 2024 code | What could go wrong | Fix in v6 |
|---|---|---|
| Money stored as floats | Rounding errors on real balances | `DECIMAL(14,2)` + strict amount validation |
| Two payments at the same time | Race condition → double spend | DB transaction + row-level locks on every balance change |
| PINs stored as plain text | One DB leak exposes every PIN | bcrypt-hashed PINs (existing ones migrated) |
| Any user could read any log | IDOR: see other people's transactions | Ownership checks on logs and mandates |
| JWTs never expired | A stolen token works forever | 1-hour expiry, old tokens rejected |
| Login said "email not found" | Attackers can list who has an account | Generic errors + stricter auth rate limits |
| AutoPay after downtime | Charge a user for every missed cycle at once | Skip missed cycles, log failures, auto-expire mandates |

#### 🗺️ How it grew

```mermaid
timeline
    title PayP
    Dec 2024 : v1 · accounts, PIN, transfers, JWT + bcrypt, Postgres
    Jan 2025 : v5 · products, project payments, transaction logs, Swagger
    Jun 2025 : AutoPay · recurring mandates, pause/cancel/expire, event logs
    Oct 2026 : v6 · security + money-correctness overhaul, tests, Docker
```

---

### 🧬 How I've evolved

```mermaid
timeline
    title From web apps to AI infrastructure
    2023 – 24 : Web foundations : Shopify clone · ADgov · ADapp
    2024 – 25 : Down to the metal : MyShell (C) · Linux system monitor · PayP v1 → AutoPay
    2025      : Systems & performance : Vault (Redis-compatible KV) · FluxTrade (68.9 ns matching)
    2026      : AI infrastructure : GenAI POCs @ MNC · Recallix · ModelLogger · PayP v6
```

---

### ⚡ Other things I've built

| | Project | What it does | Numbers / stack |
|---|---|---|---|
| 🧠 | **[Recallix](https://github.com/AyishikD/Recallix)** | Shared persistent memory for AI agents | **~0.1 ms** search @ 1M nodes · C++ HNSW + Python · [demo](https://recallix.vercel.app) |
| 📊 | **[ModelLogger](https://github.com/AyishikD/xlogger)** | Research memory OS for AI/ML teams: turns experiment activity into a searchable memory graph, with autonomous agents | FastAPI · pgvector · Redis · LiteLLM · [demo](https://xlogger.vercel.app) |
| 📈 | **[FluxTrade](https://github.com/AyishikD/FluxTrade)** | Exchange simulator: order book + matching engine | **68.9 ns**/match · C++20 |
| 🗄️ | **[Vault](https://github.com/AyishikD/vault)** | Redis-compatible versioned KV store | C++ · RESP protocol |
| 🔎 | **[MiniAI](https://github.com/AyishikD/MiniAI)** | Web search → LLM summary → follow-up Q&A | Groq · Llama 3 70B · [demo](https://miniai.streamlit.app) |
| 📦 | **[alldbconnect](https://www.npmjs.com/package/alldbconnect)** | One npm API for many databases | published on npm |

<details>
<summary><b>🕹️ Low-level side quests (click to expand)</b></summary>
<br>

- **[MyShell](https://github.com/AyishikD/myshell)** — Linux shell from scratch in C: pipes, redirection, background jobs, history, tab completion
- **[Crux](https://github.com/AyishikD/crux)** — C command-line tool for Linux
- **Linux system monitor** — reads `/proc` directly, pure C
- **[Shopify clone](https://github.com/AyishikD/shopify)** — full-stack e-commerce platform ⭐ 10 · [demo](https://shopify-silk.vercel.app)

</details>

---

### 🛠️ Arsenal

<p align="center">
  <img src="https://skillicons.dev/icons?i=cpp,c,python,ts,js,java&theme=dark" /><br>
  <img src="https://skillicons.dev/icons?i=fastapi,nodejs,express,postgres,redis,sqlite,mongodb&theme=dark" /><br>
  <img src="https://skillicons.dev/icons?i=nextjs,react,tailwind,docker,linux,git,vercel&theme=dark" />
</p>

<p align="center"><b>AI / LLM:</b> RAG · HNSW · pgvector · LLM agents · Claude · Llama · prompt engineering</p>

---

### 📡 Live telemetry

<p align="center">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username=AyishikD&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" />
  <img height="170" src="https://streak-stats.demolab.com?user=AyishikD&theme=tokyonight&hide_border=true" />
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=AyishikD&theme=tokyo-night&hide_border=true&area=true" />
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/AyishikD/AyishikD/output/github-contribution-grid-snake-dark.svg" />
    <img src="https://raw.githubusercontent.com/AyishikD/AyishikD/output/github-contribution-grid-snake.svg" />
  </picture>
</p>

---

### 🏅 Side achievements
`🥈 MNC-wide AI challenge` · `🥇 CxthSense 2.0` · `🥇 TechQuisitive 5.0` · `⭐⭐⭐⭐⭐ HackerRank C++ & Java` · `🧑‍🏫 Mentor @ GirlScript Summer of Code`

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ff9c,50:203a43,100:0f2027&height=100&section=footer" />
</p>
