# Copilot Proxy - Complete Model Reference

Data sourced from:
1. **Proxy API** (`GET /v1/models`) - exact model IDs, context windows, families
2. **GitHub Pricing Docs** - per-model credit costs, tiers, cache pricing
3. **GitHub Supported Models** - capabilities (1M ctx, reasoning, vision), categories
4. **GitHub Model Comparison** - use cases, task recommendations

All prices in **AI credits per 1M tokens** (1 credit = $0.01 USD).

## Complete Model Catalog (20 models)

### Anthropic - Claude

| Model | ID | Category | Context | In | Out | Cache Read | Cache Write | 1M Ctx | Reasoning | Vision | Use Case |
|-------|-----|----------|---------|-----|------|------------|-------------|--------|-----------|--------|----------|
| Claude Opus 5 | `claude-opus-5` | Powerful | 935K | 500 | 2500 | 50 | 625 | Yes | Yes | Yes | Deep reasoning, complex problem-solving |
| Claude Opus 4.8 | `claude-opus-4.8` | Powerful | 935K | 500 | 2500 | 50 | 625 | Yes | Yes | Yes | Deep reasoning, complex problem-solving |
| Claude Opus 4.7 | `claude-opus-4.7` | Powerful | 935K | 500 | 2500 | 50 | 625 | Yes | Yes | Yes | Deep reasoning, complex problem-solving |
| Claude Sonnet 5 | `claude-sonnet-5` | Versatile | 935K | 200 | 1000 | 20 | 250 | Yes | Yes | Yes | General-purpose, agent tasks |
| Claude Sonnet 4.6 | `claude-sonnet-4.6` | Versatile | 935K | 300 | 1500 | 30 | 375 | Yes | Yes | Yes | General-purpose, agent tasks |

### OpenAI - GPT

| Model | ID | Category | Context | In | Out | Cache Read | Cache Write | 1M Ctx | Reasoning | Vision | Use Case |
|-------|-----|----------|---------|-----|------|------------|-------------|--------|-----------|--------|----------|
| GPT-5.6 Terra | `gpt-5.6-terra` | Versatile | 922K | 200 | 1200 | 20 | 250 | Yes | Yes | Yes | Balanced everyday coding |
| GPT-5.6 Sol | `gpt-5.6-sol` | Powerful | 922K | 200 | 1000 | 20 | 250 | Yes | Yes | Yes | Deep reasoning, large codebases |
| GPT-5.6 Luna | `gpt-5.6-luna` | Lightweight | 922K | 20 | 120 | 2 | 25 | Yes | Yes | Yes | Fast, cost-efficient tasks |
| GPT-5.5 | `gpt-5.5` | Powerful | 922K | 500 | 3000 | 50 | 0 | Yes | Yes | Yes | Complex reasoning, architecture |
| GPT-5.4 | `gpt-5.4` | Versatile | 922K | 250 | 1500 | 25 | 0 | Yes | Yes | Yes | Multi-step problem solving |
| GPT-5.4 mini | `gpt-5.4-mini` | Lightweight | 272K | 75 | 450 | 7.5 | 0 | No | Yes | Yes | Agentic, codebase exploration |
| GPT-5.3-Codex | `gpt-5.3-codex` | Powerful | 272K | 175 | 1400 | 17.5 | 0 | No | Yes | Yes | Agentic, LTS fallback |
| GPT-5 mini | `gpt-5-mini` | Lightweight | 128K | 25 | 200 | 2.5 | 0 | No | No | Yes | General-purpose, completions |

### Google - Gemini

| Model | ID | Category | Context | In | Out | Cache Read | Cache Write | 1M Ctx | Reasoning | Vision | Use Case |
|-------|-----|----------|---------|-----|------|------------|-------------|--------|-----------|--------|----------|
| Gemini 3.7 Flash | `gemini-3.7-flash` | Versatile | 936K | 75 | 375 | 7.5 | 0 | No | Yes | Yes | Fast, lightweight coding |
| Gemini 3.6 Flash | `gemini-3.6-flash` | Versatile | 936K | 75 | 375 | 7.5 | 0 | No | Yes | Yes | Fast, lightweight coding |
| Gemini 3.5 Flash | `gemini-3.5-flash` | Lightweight | 936K | 150 | 900 | 15 | 0 | No | No | Yes | Fast, lightweight coding |

### xAI - Grok

| Model | ID | Category | Context | In | Out | Cache Read | Cache Write | 1M Ctx | Reasoning | Vision | Use Case |
|-------|-----|----------|---------|-----|------|------------|-------------|--------|-----------|--------|----------|
| Grok 4.6 | `grok-4.6` | Versatile | 372K | 200 | 600 | 50 | 0 | No | Yes | Yes | General-purpose, agent tasks |
| Grok 4.5 | `grok-4.5` | Versatile | 372K | 200 | 600 | 50 | 0 | No | Yes | Yes | General-purpose, agent tasks |

### Microsoft - MAI

| Model | ID | Category | Context | In | Out | Cache Read | Cache Write | 1M Ctx | Reasoning | Vision | Use Case |
|-------|-----|----------|---------|-----|------|------------|-------------|--------|-----------|--------|----------|
| MAI-Code-1-Flash | `mai-code-1-flash-picker` | Lightweight | 128K | 75 | 450 | 7.5 | 0 | No | No | No | Code completions, explanations |
| MAI-Code-1.1-Flash | `mai-code-1.1-flash` | Lightweight | 128K | 20 | 120 | 2 | 25 | No | No | Yes | Code completions, tool use |

## Cost Tiers

| Tier | In/1M | Out/1M | Models |
|------|-------|--------|--------|
| **Budget** | 20 | 120 | GPT-5.6 Luna, MAI-Code-1.1-Flash |
| **Low** | 25 | 200 | GPT-5 mini |
| **Mid** | 75 | 375-450 | Gemini 3.6/3.7 Flash, MAI-Code-1-Flash, GPT-5.4 mini |
| **Standard** | 150-200 | 600-1200 | Grok 4.5/4.6, GPT-5.6 Sol, Claude Sonnet 5, GPT-5.6 Terra, Gemini 3.5 Flash |
| **Premium** | 175-300 | 1400-1500 | GPT-5.4, GPT-5.3-Codex, Claude Sonnet 4.6 |
| **Expensive** | 500 | 2500-3000 | Claude Opus (all), GPT-5.5 |

## Models with 1M Token Context Window

Available in VS Code and Copilot CLI only:
- Claude Opus 5, 4.8, 4.7
- Claude Sonnet 5, 4.6
- GPT-5.6 Terra, Sol, Luna
- GPT-5.5, 5.4
- GPT-5.3-Codex (272K default, 1M extended)

## Models with Configurable Reasoning

Available in VS Code, CLI, and cloud agent:
- Claude Opus 5, 4.8, 4.7
- Claude Sonnet 5, 4.6
- GPT-5.6 Terra, Sol, Luna
- GPT-5.5, 5.4, 5.4 mini
- GPT-5.3-Codex
- Gemini 3.6 Flash, 3.7 Flash
- Grok 4.5, 4.6

## Active Promotions

- **GPT-5.6 Sol**: 50% off standard rates through Sep 3, 2026
- **Gemini 3.6/3.7 Flash**: promotional pricing through Dec 31, 2026

## Context Windows (Proxy API reported)

| Model | Context (proxy) | Rounded |
|-------|----------------|---------|
| Claude Opus/Sonnet | 935,793 | ~1M |
| GPT-5.4/5.5/5.6 | 921,793 | ~1M |
| Gemini 3.5/3.6/3.7 | 935,793 | ~1M |
| Grok 4.5/4.6 | 424,794 | ~372K official |
| GPT-5.4 mini, 5.3-Codex | 271,790 | ~272K |
| GPT-5 mini, MAI-Code | 127,790 | ~128K |

## Legacy/Internal Models (not recommended for proxy)

These appear in the proxy API but are internal/utility models:
- `gpt-4o-mini` - legacy, 12K context
- `auto` - auto-selection meta-model
- `copilot-utility-small` - internal utility
- `copilot-utility` - internal utility
- `copilot-dictation-cleanup-luna` - internal utility

## Notes

- 1 AI credit = $0.01 USD
- Code completions are unlimited and do not burn credits
- All models support tool/function calling via the proxy
- Models with cache write pricing incur additional cost on first token cache
