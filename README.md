# Agent Wesley — Multi-Agent Architecture

> Sistem multi-agent terstruktur untuk audit, redesign, dan optimasi produk SaaS kanban/task management.

## Tentang

Agent Wesley adalah framework kerja multi-agent yang dirancang untuk mengaudit dan meningkatkan kualitas web app manajemen proyek bergaya Kanban. Sistem ini terdiri dari 5 agent internal dengan peran yang jelas, saling berbeda, dan tidak overlap.

## Target Produk

- **Aplikasi:** Web app kanban/Trello-like (New Trello)
- **Stack:** SvelteKit + Cloudflare Workers + D1 + Firebase Auth + Google Sheets backup
- **Target:** Desktop & Mobile
- **Arah visual:** Premium, modern, clean — terinspirasi Linear/Height/Stripe

## Tim Agent

| # | Agent | Kode | Peran |
|---|-------|------|-------|
| 1 | Chief Orchestrator | CO | Memimpin, memutuskan, menyintesis |
| 2 | Repo & Product Auditor | RPA | Audit codebase & flow produk |
| 3 | Benchmark & UX Research | BRA | Riset produk lain & pola UX |
| 4 | Cloudflare Performance Architect | CPA | Audit kecepatan & efisiensi |
| 5 | Design System & Color Harmony | DSA | Sistem visual & warna harmonis |

## Struktur Repository

```
agent-wesley/
├── README.md
├── docs/
│   ├── architecture.md
│   ├── operating-model.md
│   ├── rules.md
│   ├── agents/
│   │   ├── chief-orchestrator.md
│   │   ├── repo-product-auditor.md
│   │   ├── benchmark-ux-research.md
│   │   ├── cloudflare-performance.md
│   │   └── design-system-color.md
│   └── phases/
│       ├── phase-1-audit.md
│       ├── phase-2-crossref.md
│       ├── phase-3-synthesis.md
│       └── phase-4-execution.md
└── outputs/
    ├── audit-results/
    ├── benchmarks/
    ├── design-system/
    └── performance-report/
```

## Cara Kerja

Baca [`docs/architecture.md`](docs/architecture.md) untuk arsitektur lengkap dan [`docs/operating-model.md`](docs/operating-model.md) untuk urutan kerja.

## Lisensi

Private — untuk penggunaan internal tim Wesley.
