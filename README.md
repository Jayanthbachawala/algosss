# AI Trading SaaS Platform — Final Master Project (V2.0)

## Product Definition
**Adaptive AI Trading Intelligence SaaS Platform**

A production-ready platform that:
- Detects opportunities using OI + Greeks
- Generates explainable alerts
- Supports user-controlled execution (SEBI-compliant)
- Learns via paper-trading feedback loops
- Improves continuously through phased AI maturation
- Scales to thousands of users

## Core System Flow
`Market Data → Strategy Engine → Signal Engine → UI Alert → User Execute → Journal → AI Learning → Improvement`

## Strategy Engine
### Inputs
- Price (OHLC)
- Volume
- Open Interest (OI)
- Change in OI
- Option chain
- Greeks (IV, Delta, Theta)

### Logic Layers
- Trend filters (ADX, VWAP)
- OI buildup detection
- Option chain support/resistance
- Greeks filters
- Price timing (RSI/breakout)

### Signal Rule
- Generate alert when **Score ≥ 7**

## Risk Management
- Risk per trade: 1%
- Daily loss cap: 3%
- Max trades/day: 3–5
- Kill switch enabled

## Paper Trading Engine
- Executes all generated signals (unlimited)
- Purpose: unbiased dataset creation + AI model training

## AI Learning Lifecycle
`Paper Trades → Dataset → Training → Prediction → Strategy Improvement`

### Maturation Phases
1. **Phase 1 (0–90 days): AI Shadow Mode** (no impact on live logic)
2. **Phase 2: AI Assist Mode**
3. **Phase 3: AI Filtering Mode**

Promotion criteria:
- 1000+ paper trades
- Demonstrated, statistically meaningful improvement

## Journal System
Tracks:
- Paper trades
- Live trades
- User notes

Outputs:
- Win rate
- PnL
- Performance insights

## Admin Dashboard
- User management
- Subscription control
- Signal analytics
- Risk monitoring
- Global kill switch

## SaaS Plans
- Free
- Basic
- Pro
- Premium

Feature access is plan-gated.

## Search System
Unified search for:
- Stocks
- Indices
- Options

## Compliance Rules (India)
- Manual execution only (`Execute` click required)
- Daily broker TOTP login
- Mumbai-region deployment target
- Earnings/news event filters
- Failover systems

## Data Architecture
| Data Tier | Storage |
|---|---|
| Hot | Redis |
| Warm | PostgreSQL |
| Cold | S3 |

## Messaging & Delivery
`Signal → Queue → Workers → Users`

Goals:
- Parallel fan-out
- Low-latency alerting

## Broker Integration Hub
- API key connection flow
- Broker status indicators
- Secure credential/session storage

## Database Core
Tables:
- users
- subscriptions
- signals
- trades
- paper_trades
- journal
- orders
- instruments
- broker_sessions

Critical additions:
- `live_orders` for compliance metadata (`user_ip`, `device_info`, `approval_timestamp`)
- `users.telegram_chat_id` for alert routing
- `daily_portfolio_snapshots` for dashboard acceleration

## Operational Rules
- Expiry rollover: ignore current expiry 24h before expiry
- Execution staggering: max 5 orders/sec
- Pre-trade margin validation mandatory
- SEBI-safe UX language:
  - Buy → Execute
  - Sell → Exit
  - Call → Alert

## Daily Reporting
Include:
- Win rate
- Performance
- Insights

Narrative format: `WHY → WHAT → HOW`

## Frontend (Pro Terminal)
### Layout
- Top bar
- Left panel (signals)
- Center panel (chart/search)
- Right panel (execution)

### Design System
- Minimal, low-clutter UI
- Dark mode default; light mode optional
- Palette:
  - Background `#0B0F14`
  - Text `#E6EDF3`
  - Green `#00C853`
  - Red `#FF5252`

### Responsive
- Desktop: multi-panel terminal
- Mobile tabs: `Signals | Trade | Journal | Account`

## Key Risks
- Market unpredictability
- AI overfitting
- Latency
- Regulatory constraints

## Differentiators
- OI + Greeks hybrid model
- Learning loop via paper trades
- Institutional-style journaling
- SaaS monetization framework
- Scalable infra with compliance-first design

## Build Order (Start Now)
1. Database schema
2. Auth system
3. Signal engine
4. Frontend dashboard

## Final Directive
- Do not redesign
- Do not add features
- Build → Test → Improve

---
This repository now contains the finalized build blueprint for implementation.
