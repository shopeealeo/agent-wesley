# Arsitektur Multi-Agent Wesley

## Diagram Sistem

```
┌─────────────────────────────────────────────────────────────┐
│                    CHIEF ORCHESTRATOR (CO)                    │
│          Memimpin · Memutuskan · Menyintesis · Veto          │
└──────┬──────────┬──────────────┬──────────────┬─────────────┘
       │          │              │              │
┌──────▼───┐ ┌────▼─────┐ ┌─────▼──────┐ ┌────▼──────┐
│   RPA    │ │   BRA    │ │    CPA     │ │    DSA    │
│  Repo &  │ │Benchmark │ │Cloudflare  │ │  Design   │
│ Product  │ │  & UX    │ │Performance │ │  System   │
│ Auditor  │ │ Research │ │ Architect  │ │  & Color  │
└──────────┘ └──────────┘ └────────────┘ └───────────┘
```

## Diagram Cara Kerja Sama (Mermaid)

```mermaid
flowchart TD
    Owner[/"👤 Product Owner (Brief)"/]
    CO["🎯 CHIEF ORCHESTRATOR\n(memimpin, memutuskan, menyintesis)"]
    RPA["📂 RPA\n(Repo & Product Auditor)"]
    BRA["🔍 BRA\n(Benchmark & UX Research)"]
    CPA["⚡ CPA\n(Cloudflare Performance)"]
    DSA["🎨 DSA\n(Design System & Color)"]
    Plan[/"📋 Master Plan & Final Output"/]

    Owner -->|brief| CO
    CO -->|task: audit repo| RPA
    CO -->|task: riset produk lain| BRA
    CO -->|task: audit performa| CPA
    CO -->|task: audit visual| DSA

    RPA -->|temuan repo| CO
    BRA -->|temuan benchmark| CO
    CPA -->|temuan performa| CO
    DSA -->|temuan desain| CO

    CO -->|resolve konflik\nputuskan tradeoff\nprioritaskan| Plan
```

## Diagram Alur Fase Kerja (Mermaid)

```mermaid
flowchart LR
    F1["Fase 1\nParallel Audit"]
    F2["Fase 2\nCross-Reference"]
    F3["Fase 3\nSynthesis & Decision"]
    F4["Fase 4\nExecution Plan"]

    F1 -->|semua agent submit temuan| F2
    F2 -->|CO resolve konflik| F3
    F3 -->|Master Plan ready| F4

    subgraph "Fase 1 (Parallel)"
        direction TB
        A1["RPA: audit repo"]
        A2["BRA: riset produk"]
        A3["CPA: audit performa"]
        A4["DSA: audit visual"]
    end

    subgraph "Fase 2 (CO)"
        direction TB
        B1["Identifikasi konflik"]
        B2["Resolve disagreement"]
        B3["Gap analysis"]
    end

    subgraph "Fase 3 (CO)"
        direction TB
        C1["Prioritas High/Med/Low"]
        C2["Timeline realistis"]
        C3["Risk assessment"]
    end

    subgraph "Fase 4 (Semua)"
        direction TB
        D1["RPA: refactor plan"]
        D2["BRA: UX adaptasi"]
        D3["CPA: perf checklist"]
        D4["DSA: design tokens"]
    end
```

## Diagram Resolusi Konflik (Mermaid)

```mermaid
flowchart TD
    Conflict["⚠️ Konflik antar Agent"]
    CO_Check{"CO: Evaluasi"}
    Security["🔒 Keamanan?"]
    Speed["⚡ Kecepatan User?"]
    Maintain["🔧 Maintainability?"]
    Visual["🎨 Visual Polish?"]
    Feature["✨ Fitur Baru?"]
    Decision["✅ Keputusan Final"]

    Conflict --> CO_Check
    CO_Check --> Security
    Security -->|Ya, prioritas 1| Decision
    Security -->|Bukan| Speed
    Speed -->|Ya, prioritas 2| Decision
    Speed -->|Bukan| Maintain
    Maintain -->|Ya, prioritas 3| Decision
    Maintain -->|Bukan| Visual
    Visual -->|Ya, prioritas 4| Decision
    Visual -->|Bukan| Feature
    Feature -->|Prioritas 5| Decision
```

## Prinsip Arsitektur

### 1. Separation of Concerns
Setiap agent punya domain yang jelas. Tidak ada agent yang mengerjakan tugas agent lain.

### 2. Parallel Execution
Agent RPA, BRA, CPA, dan DSA bekerja bersamaan di Fase 1. Tidak perlu menunggu satu sama lain.

### 3. Conflict Resolution via CO
Ketika dua agent memberikan rekomendasi yang bertentangan, CO yang memutuskan berdasarkan:
- Realitas stack (Cloudflare + Firebase + D1)
- Budget waktu dan effort
- Impact terhadap user experience
- Production readiness

### 4. Production-First Mindset
Semua rekomendasi harus bisa diimplementasikan di:
- Cloudflare Pages (frontend hosting)
- Cloudflare Workers (backend API)
- Cloudflare D1 (database SQLite)
- Firebase Auth (autentikasi Google)
- Google Sheets (backup via Apps Script)

Tidak ada rekomendasi yang membutuhkan infrastruktur tambahan di luar stack ini.

## Aliran Data

```
Input (Brief dari Owner)
    │
    ▼
CO memecah brief → Task per agent
    │
    ├──→ RPA: "Audit repo, peta domain, identifikasi debt"
    ├──→ BRA: "Riset Trello + Linear + repo GitHub"
    ├──→ CPA: "Audit performa, bundle, query"
    └──→ DSA: "Audit visual, identifikasi masalah desain"
    │
    ▼
Semua agent submit temuan ke CO
    │
    ▼
CO: Cross-reference, resolve konflik
    │
    ▼
CO: Master Plan (prioritas + timeline)
    │
    ▼
Eksekusi bertahap
```

## Batasan Sistem

| Constraint | Alasan |
|-----------|--------|
| Tidak boleh tambah database lain | D1 adalah satu-satunya DB |
| Tidak boleh ganti auth provider | Firebase Auth sudah production |
| Tidak boleh pakai framework lain | SvelteKit sudah dipilih |
| Tidak boleh tambah CDN lain | ImgBB + ImageKit sudah cukup |
| Semua harus edge-first | Cloudflare Workers = no cold start |
| Budget dependency minimal | Setiap npm install harus justified |
