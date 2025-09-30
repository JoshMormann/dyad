# Helix VCaaS Customization Guide

This guide explains how to customize Helix for client-specific "Vibe Coding as a Service" sessions at Halo.

## 📍 System Prompts Location

All AI behavior is controlled by prompts in: **`src/prompts/system_prompt.ts`**

This 539-line file has been annotated with detailed comments to guide safe customization.

## 🎯 Primary Customization Zones

### 1. **DEFAULT_AI_RULES** (Line ~403) - MAIN CUSTOMIZATION AREA ⭐

This is where you add client-specific technical requirements:

```typescript
// Add client-specific rules at the bottom of DEFAULT_AI_RULES:
# Client: Acme Corp
# Project: Healthcare Dashboard Demo
# Session Date: 2025-01-15

# Custom Requirements:
- Use the Acme API: https://api.acme.com/v1
- Authentication: Implement Auth0 integration
- Primary brand color: #0066CC (Acme blue)
- Secondary brand color: #FF6B35 (Acme orange)
- All data tables must use AG Grid
- Charts should use Recharts library
- Include HIPAA compliance warnings in forms
- Use Acme's design system tokens from @acme/design-tokens
```

**Safe to add:**
- API endpoints and credentials
- Brand colors and design tokens
- Preferred libraries (Stripe, Auth0, etc.)
- Domain-specific knowledge (healthcare, fintech, etc.)
- Code organization preferences
- Security/compliance requirements

**Do NOT change:**
- Basic React/TypeScript/Tailwind structure
- File organization (src/pages, src/components)
- shadcn/ui references (unless client wants different UI library)

### 2. **BUILD_SYSTEM_PREFIX** (Line ~89) - AI Persona

Customize the AI's identity and tone:

```typescript
// Example: Change to Helix branding
<role> You are Helix, Halo's AI coding assistant...

// Example: Add domain expertise
<role> You are Dyad, specialized in building fintech applications...
```

### 3. **THINKING_PROMPT** (Line ~29) - Planning Approach

Adjust how the AI thinks through problems. Usually doesn't need changes, but you can:
- Add client-specific planning steps
- Emphasize certain priorities (security, performance, etc.)

## 🚀 VCaaS Preparation Workflow

### Week Before Session:

1. **Create Client Branch**
   ```bash
   git checkout -b vcaas/client-name-2025-01-15
   ```

2. **Customize System Prompts**
   - Edit `src/prompts/system_prompt.ts`
   - Add client requirements to `DEFAULT_AI_RULES`
   - Test with sample prompts

3. **Pre-build Baseline App**
   ```bash
   npm start
   # Build a starter template with client's tech stack
   ```

4. **Connect Endpoints**
   - Add API configurations
   - Set up authentication
   - Test data connections

5. **Dress Rehearsal**
   - Run through demo scenarios
   - Verify all integrations work
   - Time the session flow

### Day of Session:

1. **Launch Helix**
   ```bash
   npm start
   ```

2. **Load Pre-configured Project**
   - Use Import App to load baseline
   - Verify all customizations active

3. **Live Demo** 🎭
   - Build features in real-time with client
   - System prompts ensure consistent style
   - Pre-connected endpoints work seamlessly

## 📝 Other Customization Files

### Optional: Per-App Custom Rules

Each generated app can have its own `AI_RULES.md` file in the app directory. This overrides `DEFAULT_AI_RULES` for that specific app.

**Use case:** If building multiple features for same client, each can have focused rules.

### Chat Summarization

**File:** `src/prompts/summarize_chat_system_prompt.ts`

Controls how chat conversations are titled. Usually doesn't need changes.

### Supabase Integration

**File:** `src/prompts/supabase_prompt.ts`

Special instructions for Supabase features. Customize if client uses Supabase.

## ⚠️ Caution Zones

**Do NOT modify these unless you know what you're doing:**

1. **Example Code Blocks** (Lines ~110-290)
   - These teach the AI proper code formatting
   - Breaking these breaks code generation

2. **Tool Tags** (`<dyad-write>`, `<dyad-delete>`, etc.)
   - These are the AI's API for making changes
   - Changing syntax breaks everything

3. **constructSystemPrompt Function** (Line ~537)
   - Core logic for assembling prompts
   - Only touch if modifying prompt architecture

## 💡 Best Practices

### DO:
- ✅ Copy the file before editing for client sessions
- ✅ Test customizations before client demos
- ✅ Use git branches for each client
- ✅ Document custom rules clearly
- ✅ Keep customizations in the designated zones

### DON'T:
- ❌ Edit the main file directly before demos
- ❌ Change core prompt structure
- ❌ Remove example code blocks
- ❌ Modify tool tag syntax
- ❌ Delete important guidelines

## 🔄 Version Control Strategy

```bash
# Main Helix development
main

# Client-specific branches
vcaas/acme-corp-2025-01-15
vcaas/initech-2025-01-22
vcaas/hooli-2025-02-05

# After demo, optionally merge learnings back to main
git checkout main
git merge --no-ff vcaas/acme-corp-2025-01-15
```

## 🎬 Example Client Customization

Here's a complete example for a fintech client:

```typescript
// In DEFAULT_AI_RULES, add at the bottom:

# ============================================================================
# VCaaS Session: FinTrust Bank
# Date: 2025-01-20
# Contact: jane@fintrust.com
# Focus: Trading dashboard prototype
# ============================================================================

# Client-Specific Tech Stack
- Use FinTrust API: https://api.fintrust.com/v2
- Authentication: OAuth2 with FinTrust SSO
- API Key: Available in .env.local (FT_API_KEY)

# Branding
- Primary: #1E3A8A (FinTrust navy)
- Secondary: #10B981 (success green)
- Error: #EF4444 (alert red)
- Font: Inter for all text

# Required Libraries
- Use Recharts for all financial charts
- Use date-fns for date formatting
- Use numeral for number formatting
- Implement react-query for API calls

# Business Rules
- All monetary values must show 2 decimal places
- Charts must support dark mode
- Real-time data updates every 5 seconds
- Include proper error handling for API failures
- Add loading skeletons for all data fetches

# Compliance
- Add "Not financial advice" disclaimers on relevant pages
- Log all trades to audit log
- Implement proper error boundaries
```

## 📞 Questions?

For internal Halo team questions about VCaaS customization, see the team wiki or reach out in #helix-vcaas Slack channel.

---

**Remember:** The goal of VCaaS is to demonstrate what's possible. Customization ensures the demo feels tailored and production-ready, not generic.