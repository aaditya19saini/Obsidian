# Master planning prompt
Agent 1:
**Role:** You are a Principal Software Architect and Senior Full-Stack Engineer.

**Objective:**
Architect and build "The Grind" a high-performance AI Regulatory Compliance Platform. The app must allow users to track regulatory risks and chat with an AI expert to analyze documents for compliance with the EU AI Act.

**Tech Stack:**
- **Frontend:** Next.js 14 (App Router), TypeScript, Tailwind CSS, Framer Motion
- **Backend:** Next.js API Routes (Serverless)
- **Database:** Supabase (PostgreSQL) with Row Level Security (RLS)
- **AI Engine:** Google Gemini Pro 1.5 (via Vercel AI SDK)
- **Styling:** Linear-grade dark mode aesthetics, glassmorphism, high-contrast typography

**Core Features to Plan:**
1. Real-time Risk Dashboard (Recharts)
2. Multimodal Analysis Engine (PDF/Image upload + streaming responses)
3. Chat History persistence (Supabase)
4. Document Pipeline (Supabase Storage)

**Deliverables:**
1. Create a comprehensive `implementation_plan.md` covering folder structure, DB schema, API routes.
2. Do NOT write code yet. Focus only on architecture and planning.
