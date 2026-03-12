<p align="center">
  <img src="https://img.shields.io/badge/Solana-Mainnet-9945FF?style=for-the-badge&logo=solana&logoColor=white" />
  <img src="https://img.shields.io/badge/AI-Grok--4-000000?style=for-the-badge&logo=x&logoColor=white" />
  <img src="https://img.shields.io/badge/Next.js-16-000000?style=for-the-badge&logo=next.js&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-22+-339933?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Prisma-5.x-2D3748?style=for-the-badge&logo=prisma&logoColor=white" />
  <img src="https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge" />
</p>

<p align="center">
  <img src="logo.png" width="200" alt="Grok Bot Logo" />
</p>

<h1 align="center">Grok Bot</h1>

<p align="center">
  <strong>The world's first AI-powered live-streaming memecoin trading robot dog on Solana</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-live-brightgreen?style=flat-square" />
  <img src="https://img.shields.io/badge/trades-autonomous-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/stream-24%2F7-orange?style=flat-square" />
  <img src="https://img.shields.io/badge/robot-PiDog-purple?style=flat-square" />
</p>

---

## What Is This?

Grok Bot is an autonomous trading agent that discovers and trades memecoins on Solana in real-time — narrated by Grok AI with TTS, animated by a real robot dog, and streamed live on OBS. It combines AI decision-making, blockchain execution, community engagement, and physical robotics into a single entertainment + trading system.

---

## Architecture Overview

```mermaid
graph TB
    subgraph Discovery["🔍 Token Discovery"]
        ST[SolanaTracker]
        BE[Birdeye]
        HL[Helius]
        PA[PumpAPI Stream]
        WW[Wallet Watcher]
    end

    subgraph Brain["🧠 Grok-4 AI Brain"]
        CF[Candidate Filter]
        RG[Risk Gate]
        AI[AI Decision Engine]
        PS[Position Sizer]
    end

    subgraph Execution["⚡ Solana Execution"]
        PP[PumpPortal]
        JU[Jupiter]
        RPC[Solana RPC]
    end

    subgraph Show["🎬 Live Stream"]
        OBS[OBS Scenes]
        TTS[Kokoro TTS]
        OV[Browser Overlays]
    end

    subgraph Robot["🐕 Robot Dog"]
        PD[PiDog]
        CH[Choreography]
    end

    subgraph Community["💬 Community"]
        PC[PumpFun Chat]
        TG[Telegram]
        DB[Dashboard]
    end

    subgraph Data["💾 Data Layer"]
        PG[(PostgreSQL)]
        MEM[In-Memory Portfolio]
    end

    ST & BE & HL & PA & WW --> CF
    CF --> RG --> AI
    AI --> PS --> PP
    PP -. fallback .-> JU
    PP & JU --> RPC

    AI --> OBS & TTS & OV
    AI --> PD --> CH
    AI --> PC & TG
    RPC --> PG & MEM
    PG --> DB
```

---

## How It Works

### 1. Token Discovery

The system continuously scans multiple data providers for tradeable tokens:

- **SolanaTracker** — trending tokens, fresh gems, search queries
- **Birdeye** — token metadata, real-time price WebSocket feeds
- **Helius** — mint watching, transaction parsing
- **PumpAPI Stream** — real-time new token events
- **Wallet Watcher** — smart money tracking

```mermaid
graph LR
    A[Raw Candidates] --> B[Candidate Filter]
    B --> C[Risk Gate]
    C --> D[Filter Presets]
    D --> E[Qualified Candidates]
    E --> F[Grok AI]

    B -.- B1["Market cap, volume, age, momentum"]
    C -.- C1["Holder concentration, rug signals, liquidity"]
    D -.- D1["Conservative → Aggressive profiles"]
```

### 2. AI Decision Engine

Every **45 seconds**, the trading loop builds a rich context for Grok-4:

- Current portfolio (open positions, P&L, trailing stops)
- SOL balance and risk metrics
- Filtered token candidates with metadata
- Recent trade history and performance

Grok-4 returns a structured decision:

| Decision | Action |
|----------|--------|
| **BUY** | Enter new position with sized allocation |
| **SELL** | Exit position (take profit or cut loss) |
| **HOLD** | Maintain current positions |
| **ROTATE** | Sell underperformer → buy better opportunity |

### 3. Trade Execution

```mermaid
graph TD
    A[Grok Decision] --> B[Position Sizer]
    B --> C{PumpPortal}
    C -->|success| E[Solana RPC]
    C -->|fallback| D[Jupiter Aggregator]
    D --> E
    E --> F[Transaction Confirmed]
    F --> G[Portfolio Update]
    F --> H[Telegram Notification]
    F --> I[PostgreSQL Record]

    B -.- B1["SOL amount based on conviction + risk"]
    C -.- C1["Direct DEX swap"]
    D -.- D1["Best-route swap"]
    G -.- G1["Entry price, amount, trailing stop"]
```

### 4. Real-Time Price Monitoring

A separate **reactive price loop** runs continuously:

- Subscribes to Birdeye WebSocket for live price ticks
- Monitors **trailing stops** — auto-sells when price drops from peak
- Triggers reactive sells *before* the next trading loop cycle
- Configurable presets: `TIGHT`, `MEDIUM`, `WIDE`, `MOONBAG`

### 5. Risk Management & Guardrails

| Guardrail | Purpose |
|-----------|---------|
| Max position size | Caps SOL per trade |
| Max open positions | Limits portfolio exposure |
| Stop-loss percentage | Hard floor on losses |
| Trailing stop presets | Locks in gains dynamically |
| SOL reserve | Always keeps gas money |
| Slippage limits | Prevents sandwich attacks |
| Dry-run mode | Test without real trades |
| Token blacklist | Never trade flagged tokens |

### 6. The Show (Live Stream)

Every trade triggers a coordinated production:

```mermaid
graph LR
    A[Trade Executed] --> B[ShowQueue]
    B --> C[Grok Commentary]
    B --> D[Kokoro TTS]
    B --> E[OBS Scene Switch]
    B --> F[PiDog Choreography]
    B --> G[Overlay Update]

    A --> H[Telegram Notify]
    A --> I[PostgreSQL Write]

    C --> D
    D --> E
    E --> F
    F --> G
```

### 7. Chat Engagement

Every **15 seconds**, the chat loop:

1. Fetches messages from PumpFun token chat
2. Sends to Grok-4 for personality-driven responses
3. Updates emotion/sentiment score
4. Triggers TTS narration + robot animations

---

## Monorepo Structure

```
grok-bot/
├── apps/
│   ├── brain/          # Trading engine (Node.js/TypeScript)
│   │   ├── loops/      # Trading, chat, price monitoring, cleanup
│   │   ├── services/   # External API integrations
│   │   ├── discovery/  # Token filtering & risk analysis
│   │   └── state/      # Portfolio, queue, stats management
│   │
│   ├── web/            # Dashboard & API (Next.js/React)
│   │   ├── app/        # Pages: hero, dashboard, leaderboard
│   │   ├── api/        # REST endpoints (state, events, blacklist)
│   │   └── prisma/     # Database schema & migrations
│   │
│   ├── pidog/          # Robot control service (Python/FastAPI)
│   │   └── actions/    # Choreography routines
│   │
│   └── kokoro-tts/     # Text-to-speech service (Python/FastAPI)
│
├── packages/
│   └── shared/         # Shared TypeScript types
│
└── scripts/            # Deployment scripts
```

---

## Data Flow

```mermaid
graph TD
    SOL[🔗 Solana Blockchain]

    SOL --> BE[Birdeye<br/>Prices]
    SOL --> HL[Helius<br/>Mints]
    SOL --> ST[SolanaTracker<br/>Discovery]

    BE & HL & ST --> BRAIN[🧠 Brain<br/>Filter → AI → Execute]

    BRAIN --> PG[(PostgreSQL)]
    BRAIN --> DASH[📊 Dashboard<br/>Next.js]
    BRAIN --> STREAM[🎥 Stream<br/>OBS + TTS]
    BRAIN --> DOG[🐕 PiDog<br/>Robot]
    BRAIN --> CHAT[💬 Community<br/>Chat + Telegram]

    PG --> DASH
```

---

## Database Schema

| Table | Purpose |
|-------|---------|
| **Trade** | Every buy/sell with mint, amounts, P&L, tx signature |
| **Burn** | Token burn events tracked on-chain |
| **BalanceSnapshot** | Periodic portfolio value + SOL price snapshots |
| **ChatEvent** | AI chat interactions with sentiment tracking |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **AI Brain** | Grok-4 (via OpenRouter / xAI) |
| **Backend** | Node.js, TypeScript, Zod |
| **Frontend** | Next.js 16, React 19, Tailwind CSS, Spline 3D |
| **Database** | PostgreSQL + Prisma ORM |
| **Blockchain** | Solana Web3.js, SPL Token, PumpPortal, Jupiter |
| **Data Feeds** | Birdeye (REST + WS), SolanaTracker, Helius |
| **Streaming** | OBS WebSocket, Kokoro TTS, Browser Overlays |
| **Robotics** | PiDog (Python FastAPI) |
| **Community** | PumpFun Chat, Telegram Bot API |
| **Infra** | Railway (deploy), npm workspaces (monorepo) |

---

## Key Loops

| Loop | Interval | Purpose |
|------|----------|---------|
| **Trading Loop** | 45s | Discover → Filter → AI Decide → Execute |
| **Chat Loop** | 15s | Read chat → AI respond → TTS → Animate |
| **Reactive Price Loop** | Real-time | WebSocket price monitoring + trailing stops |
| **Burn Monitor** | Periodic | Detect and record token burns |
| **Summary Loop** | Daily | Aggregate performance statistics |
| **Wallet Cleanup** | Periodic | Sweep dust positions and stale tokens |

---

## Deployment

| Service | Platform |
|---------|----------|
| Brain | Cloud / Local |
| Web Dashboard | Cloud |
| PiDog | Raspberry Pi / Local |
| Kokoro TTS | Local GPU |
| PostgreSQL | Cloud |

---

<p align="center">
  <sub>Built with Grok AI on Solana — autonomous, live, unfiltered.</sub>
</p>
