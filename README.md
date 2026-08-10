# Servicing-Agent

###Architecture
┌──────────────────────────┐
│ Next.js UI │
│ Chat + Case Status │
│ Audit Timeline │
│ Human Handoff │
└────────────┬─────────────┘
│
REST / WebSocket
│
┌────────────▼─────────────┐
│ FastAPI API │
│ Auth / Sessions / Cases │
│ Rate limiting / RBAC │
└────────────┬─────────────┘
│
┌──────────────────▼──────────────────┐
│ Agent Orchestrator │
│ LangGraph │
│ │
│ Intent → Validate → Policy → │
│ Execute → Verify → Respond │
└───────┬──────────┬──────────┬──────┘
│ │ │
┌────────▼───┐ ┌────▼────┐ ┌──▼──────────┐
│ LLM / NLP │ │ Policy │ │ Card Tools │
│ Groq/etc. │ │ Engine │ │ Mock APIs │
└────────────┘ └─────────┘ └─────────────┘
│
┌──────────────────────┼──────────────┐
│ │ │
Fee Service Card Service Limit Service
│ │ │
└──────────────────────┼──────────────┘
│
┌────────▼────────┐
│ PostgreSQL │
│ Customers │
│ Cards │
│ Cases │
│ Transactions │
│ Audit Events │
└─────────────────┘
