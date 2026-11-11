---
title: "LLM API Pricing Comparison 2026: Official vs Actual Cost"
description: "Compare 2026 LLM API prices per 1M tokens for GPT, Claude, Gemini & Grok - official list rates vs what gateways actually charge. Verified Nov 10, 2026."
slug: /blog/llm-api-pricing-comparison
author: NewtonRouter Team
date: 2026-11-10
---

<!-- JSON-LD: Article + BreadcrumbList + FAQPage -->

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Article",
      "headline": "LLM API Pricing Comparison 2026: Official vs Actual Cost",
      "description": "Compare 2026 LLM API prices per 1M tokens for GPT, Claude, Gemini & Grok - official list rates vs what gateways actually charge. Verified Nov 10, 2026.",
      "inLanguage": "en",
      "author": { "@type": "Organization", "name": "NewtonRouter Team" },
      "publisher": {
        "@type": "Organization",
        "name": "NewtonRouter",
        "logo": { "@type": "ImageObject", "url": "https://newtonrouter.com/logo.png" }
      },
      "datePublished": "2026-11-10",
      "dateModified": "2026-11-10",
      "mainEntityOfPage": { "@type": "WebPage", "@id": "https://newtonrouter.com/blog/llm-api-pricing-comparison" }
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        { "@type": "ListItem", "position": 1, "name": "Blog", "item": "https://newtonrouter.com/blog" },
        { "@type": "ListItem", "position": 2, "name": "LLM API Pricing Comparison 2026", "item": "https://newtonrouter.com/blog/llm-api-pricing-comparison" }
      ]
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {
          "@type": "Question",
          "name": "How much does an LLM API cost per 1 million tokens in 2026?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "There is no single price. As of 2026-11-10, official list rates per 1M tokens run from GPT-6 Luna $0.10/$0.50 up to GPT-6 Astra $10.00/$50.00 (openai.com/api/). A third-party tracker puts the blended range across hundreds of models at $0.02-$285.00 per 1M (tokenando.ai, October 2026), a landscape estimate, not an official rate. Output tokens usually cost several times more than input, so read both columns. Rates change; verify on the provider's pricing page before committing budget."
          }
        },
        {
          "@type": "Question",
          "name": "What is the difference between an official list price and what a gateway actually charges?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Three numbers. The official list price is the provider's published per-1M-token rate. The gateway listed rate is what a gateway's rate card shows, a pass-through of list price or a vendor-claimed discount. The effective take-home price adds every fee on your token mix. OpenRouter passes through provider list prices with no per-token markup but charges a 5.5% credit-purchase fee on Standard and 8% on Business (openrouter.ai/pricing, verified 2026-11-10)."
          }
        },
        {
          "@type": "Question",
          "name": "How is LLM API cost calculated?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Cost = (input / 1M x input rate) + (output / 1M x output rate). Then add cached-input tokens at their own lower rate, apply batch or long-context adjustments, and layer on platform fees, tool charges, and retries. Divide the total by total token volume for your effective rate per million tokens (tokenmath.net, moneydeck.io). A homepage percentage is no substitute for this arithmetic."
          }
        },
        {
          "@type": "Question",
          "name": "Why is my LLM API bill higher than the published price table suggests?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "A rate card prices one successful call at one tier. Your invoice adds output tokens priced above input, reasoning tokens billed at output rates, long-context and regional uplifts, credit-purchase and BYOK fees, subscriptions and log overages, tool calls, failed or aborted requests that some providers still bill, taxes, and currency conversion. Log the model and channel behind each request so you can separate these lines (therouter.ai, ai-rockstars.com)."
          }
        },
        {
          "@type": "Question",
          "name": "Do prompt caching and batch processing actually lower LLM API costs?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Yes, with preconditions. OpenAI lists cached input at roughly 10% of standard input and Batch at 50% of standard rates; Anthropic lists Batch at 50% savings (platform.openai.com/docs/pricing, claude.com/pricing, verified 2026-11-10). Caching pays off only when a stable prompt prefix is reused and hits, and Batch requires asynchronous work that can wait up to 24 hours. Check each provider's own documentation for the exact figure."
          }
        },
        {
          "@type": "Question",
          "name": "Can the same model cost different amounts on different gateways?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Yes. A third-party aggregator tracking 235 providers found the same open-weight model priced 13.2x to 31.3x apart across 96-126 hosts (llmpricing.dev, data synced 2026-11-09). The spread comes from channel tiers, volume purchasing, multiple hosts serving open-weight models, promotional windows, and platform fees layered on top. Compare the effective take-home price on your own prompts, not the headline rate."
          }
        }
      ]
    }
  ]
}
</script>

# LLM API Pricing Comparison 2026: Official List Prices vs What You Actually Pay

*By NewtonRouter Team · Published November 10, 2026 · Last verified November 10, 2026*

**An LLM API pricing comparison 2026 that stops at the published rate tells you only a third of the story.** The official list price is not the gateway listed rate, and neither is the number on your invoice. Those are three separate figures. A rate quoted per 1M tokens splits into input and output prices, then picks up gateway fees, caching, and context tiers before it becomes a bill.

Elena, a backend engineer at a twelve-person SaaS, budgeted $400 a month for a customer-support bot and got a $1,180 invoice. Nothing was broken. She had compared one model's input price and missed three things: output tokens cost several times more than input, her long system prompt was never cached, and buying credits carried a fee the rate card never showed.

If you have put two pricing pages side by side and given up, you are not the problem: they measure different things. This guide gives you one worksheet that works on any provider, then applies it across the four major model families and the fee structures between them. You will get a source-linked 2026 price table, the mechanics behind token billing, a provider-by-provider breakdown, the gap between list price and take-home price, hidden costs, a worked three-path example, a seven-point checklist, and six price FAQs. Price is one axis of the decision; once you know what you will pay, you still need to choose a provider and deployment model, so [compare OpenRouter alternatives](openrouter-alternatives-2026.md) for that side of the question.

*Keep the [NewtonRouter pricing page](https://newtonrouter.com/pricing) open in a second tab as you read.*

> **Key Takeaways**
> - **One model, three numbers.** GPT-6 Astra's official list is `$10 input / $50 output` per 1M tokens ([openai.com/api/](https://openai.com/api/), verified 2026-11-10), but the gateway listed rate and your take-home bill are two other figures.
> - **Output dominates.** On GPT-6 Astra, output is 5× the input rate, so a low headline input price tells you very little about a monthly bill.
> - **No markup does not mean no fee.** OpenRouter passes through provider list prices with no per-token markup, yet charges a 5.5% credit-purchase fee on Standard and 8% on Business ([openrouter.ai/pricing](https://openrouter.ai/pricing), verified 2026-11-10).
> - **Every number here is traceable.** Official list prices come only from the four provider pricing pages; vendor claims and third-party estimates are labelled as such; every table carries an as-of date, a source URL, and a "rates change" disclaimer.
> - **The same model, 13× to 31× apart.** A third-party tracker found that spread across 96–126 hosts ([llmpricing.dev](https://llmpricing.dev/), synced 2026-11-09). Compare your own token mix, not a homepage card.

### In this guide
- [The 2026 LLM API Price Table](#the-2026-llm-api-price-table-verified-november-10-2026)
- [How LLM API Pricing Works](#how-llm-api-pricing-works-input-output-cached-and-reasoning-tokens)
- [Official List Prices by Provider](#official-list-prices-by-provider-openai-anthropic-google-xai)
- [Official List Price vs Gateway Take-Home Price](#official-list-price-vs-gateway-take-home-price-where-the-gap-comes-from)
- [The Hidden Costs a Price Table Will Not Show You](#the-hidden-costs-a-price-table-will-not-show-you)
- [Worked Example: One Workload, Three Access Paths](#worked-example-one-workload-three-access-paths)
- [How to Compare LLM API Prices Fairly](#how-to-compare-llm-api-prices-fairly-a-7-point-checklist)
- [FAQ](#faq)
- [Conclusion: Compare the Bill, Not the Headline Rate](#conclusion-compare-the-bill-not-the-headline-rate)

## The 2026 LLM API Price Table (Verified November 10, 2026)

Start with the answer most readers came for. This is a **quick-answer official list price table**, not a gateway ranking. Every figure is USD per 1M tokens, standard processing, short context, verified on the provider's own page on 2026-11-10.

### 1.1 Budget, mid, and flagship tiers

| Model (tier) | Official input / 1M | Official output / 1M | Cached input / 1M | Provider page |
|---|---:|---:|---:|---|
| GPT-6 Astra (flagship) | $10.00 | $50.00 | $1.00 | [openai.com/api/](https://openai.com/api/) |
| GPT-6.1 Sol (mid) | $2.00 | $10.00 | $0.10 | [openai.com/api/](https://openai.com/api/) |
| GPT-6 Luna (budget) | $0.10 | $0.50 | $0.01 | [openai.com/api/](https://openai.com/api/) |
| Claude Opus 5.5 (flagship) | $4.00 | $20.00 | $0.20 | [claude.com/pricing](https://claude.com/pricing) |
| Claude Sonnet 5.5 (mid) | $2.00 | $10.00 | $0.10 | [claude.com/pricing](https://claude.com/pricing) |
| Claude Haiku 5.5 (budget, ≤100K prompts) | $0.10 | $0.50 | $0.01 | [claude.com/pricing](https://claude.com/pricing) |
| Gemini 4 Argon (flagship, promotional) | $2.00 | $10.00 | $0.10 | [ai.google.dev](https://ai.google.dev/gemini-api/docs/pricing) |
| Gemini 3.5 Flash-Lite (budget) | $0.30 | $2.50 | $0.03 | [ai.google.dev](https://ai.google.dev/gemini-api/docs/pricing) |
| grok-4.6 (flagship, short context) | $2.00 | $6.00 | $0.50 | [docs.x.ai](https://docs.x.ai/developers/pricing) |

*as of 2026-11-10, source: each provider's official pricing page (URLs in the right column). All figures USD per 1M tokens, standard processing, short context. **Gemini 4 Argon `$2/$10` is promotional through 2026-11-30; from 2026-12-01 it becomes `$4/$20`** ([blog.google](https://blog.google/intl/zh-tw/products/explore-get-answers/introducing-gemini-4-argon)). Cached input is a separate rate dimension, not a discount applied at billing time. Rates change; verify on the provider's pricing page before committing budget.*

### 1.2 How to read this table

Three rules keep the numbers honest. **First**, read input and output as two separate prices; they are never a single blended figure on a real invoice. **Second**, note the tier and context threshold: Claude Haiku 5.5 moves from `$0.10/$0.50` to `$0.50/$2.50` above 100K-token prompts, and grok-4.6 roughly doubles at 200K tokens. **Third**, treat any promotional price as time-boxed. A rate with an expiry date is not a stable official list price.

The table shows only the **official list price**, the first of three numbers. The second is what a gateway lists, the third is what you actually pay. That distinction is the subject of [section 4](#official-list-price-vs-gateway-take-home-price-where-the-gap-comes-from). Here is its shape:

| The number | Where it comes from | Worked 2026-11-10 example |
|---|---|---|
| **Official list price** | The model provider's own pricing page | GPT-6 Astra `$10 input / $50 output` per 1M ([openai.com/api/](https://openai.com/api/)) |
| **Gateway listed rate** | What a gateway's rate card shows | The same `$10/$50` on a pass-through gateway (no per-token markup), or a vendor-claimed discount that needs verifying |
| **Effective take-home price** | List rate plus every fee on your token mix | `$10/$50` plus a 5.5% credit-purchase fee on Standard, before caching, batch, retries, or tools |

*as of 2026-11-10, source: [openai.com/api/](https://openai.com/api/), [openrouter.ai/pricing](https://openrouter.ai/pricing). The third row is illustrative arithmetic, not a quote. Rates change; verify on the provider's pricing page before committing budget.*

For the full model list behind these rates, see the [browseable model catalog](https://newtonrouter.com/models).

## How LLM API Pricing Works: Input, Output, Cached, and Reasoning Tokens

Most pricing pages show one number per model. Your bill is built from several, and the gap between the advertised one and the real one is where budgets break.

### 2.1 Input vs output

**Input tokens** are the prompt you send. **Output tokens** are what the model generates. Providers price output above input because generation is sequential work, while reading input can be batched in parallel. On GPT-6 Astra, output is `$50` against `$10` input, a 5× multiple. A summarization service with long inputs and short outputs has a completely different effective rate from a code agent with short prompts and long completions, even on the same model. Third-party surveys put the output-to-input ratio at 2–5× across most models ([tokenmath.net](https://tokenmath.net/llm-cost-calculator), [tokenando.ai](https://tokenando.ai/learn/how-ai-api-pricing-works), October 2026); treat those as structural guidance, not official rates.

### 2.2 Prompt caching

**Cached input tokens** are repeated prompt segments the provider can reuse, priced far below ordinary input. OpenAI lists cached input at roughly 10% of standard input ([platform.openai.com/docs/pricing](https://platform.openai.com/docs/pricing), verified 2026-11-10); Anthropic quotes caching on a five-minute TTL with separate read and write rates. It pays off only when a stable prefix is reused and actually hits.

> **Mini story: the cache nobody enabled.** In June 2026, a two-person documentation startup called Tidepool ran a support assistant with a 3,000-token system prompt repeated on every call. Founder Sam watched the bill climb and assumed the model was simply expensive. A week of request-level logging showed the opposite: 70% of input tokens were identical boilerplate, billed at the full input rate every time. Enabling prompt caching on that shared prefix cut the input line sharply without changing a single model. The rate card had never been wrong; the team had been paying to resend tokens it did not need to.

### 2.3 Batch processing

**Batch processing** trades latency for a published discount on inputs and outputs. OpenAI, Anthropic, and Google all list Batch at 50% of standard rates ([platform.openai.com/docs/pricing](https://platform.openai.com/docs/pricing), [claude.com/pricing](https://claude.com/pricing), [ai.google.dev](https://ai.google.dev/gemini-api/docs/pricing), verified 2026-11-10). It fits asynchronous work such as nightly classification or evaluation, not a live chat. Confirm the exact figure on each provider's own documentation before modelling it.

### 2.4 Reasoning tokens billed at output rates

Models that think before answering emit **reasoning tokens** typically billed at output rates, even though the user never sees them. A short visible answer can carry a large hidden output line. If you enable a reasoning tier, log its token count separately; it is the easiest way for a bill to double without a code change ([tokenmath.net](https://tokenmath.net/llm-cost-calculator)).

### 2.5 Long-context tiers, region, and FX

A model name is not a price. Providers vary rates by **context length**, **processing mode**, and **region**. OpenAI applies a 10% uplift to data-residency endpoints for models released on or after 2026-03-05; Anthropic applies 1.1× to US-only inference and 2× to fast mode; xAI roughly doubles the whole request once a prompt reaches 200K tokens; Google splits several models at a 200K threshold. Currency conversion and local taxes add another layer for teams billed outside USD. Hold these variables constant when you compare two gateways, or you are pricing a batch job against a priority request.

### 2.6 The cost formula

The arithmetic is simple once the buckets are separated:

```
bill = (input_tokens / 1M × input_rate)
     + (cached_input_tokens / 1M × cached_rate)
     + (output_tokens / 1M × output_rate)
     + tool_charges
     + platform_fee
effective_rate = bill / (total_tokens / 1M)
```

Two details matter more than the formula. **Use your own token mix**, since a benchmark prompt tells you nothing about a production agent loop. And **apply the platform fee to the whole bill**, not just the input line, because a percentage on credit purchases scales with everything you spend. This is the arithmetic behind every calculator site ([moneydeck.io](https://moneydeck.io/tools/ai-api-cost-calculator), [tokenmath.net](https://tokenmath.net/llm-cost-calculator)) and the worksheet used below.

## Official List Prices by Provider: OpenAI, Anthropic, Google, xAI

The only safe source for an official list price is the provider's own pricing page. Third-party databases and tutorial sites are useful for formulas and structure, but a number copied from them is not an official price. Each figure below was verified on 2026-11-10. See the [model catalog](https://newtonrouter.com/models) for how these map onto one unified API.

### 3.1 OpenAI

Standard processing, context under 272K, per 1M tokens USD: [GPT-6 Astra](https://openai.com/api/) `$10/$50`, GPT-6.1 Sol `$2/$10`, GPT-6.1 Terra `$1/$5`, GPT-6 Luna `$0.10/$0.50`. Cached input is roughly 10% of standard input, Batch is 50%, and data-residency endpoints carry a 10% uplift. *as of 2026-11-10, source: [openai.com/api/](https://openai.com/api/), [platform.openai.com/docs/pricing](https://platform.openai.com/docs/pricing). Rates change; verify on the provider's pricing page before committing budget.*

### 3.2 Anthropic

The live lineup, per 1M tokens USD: [Opus 5.5](https://claude.com/pricing) `$4/$20`, Sonnet 5.5 `$2/$10`, Fable 5.2 `$8/$40`, Haiku 5.5 `$0.10/$0.50` at ≤100K prompts and `$0.50/$2.50` above it. Batch saves 50%, US-only inference is 1.1×, and fast mode is 2×. The older Opus 5 `$5/$25` and the Sonnet 5 introductory window are legacy or expired on the live page; do not model against them. *as of 2026-11-10, source: [claude.com/pricing](https://claude.com/pricing). Rates change; verify on the provider's pricing page before committing budget.*

### 3.3 Google (Gemini)

Paid tier, Standard, per 1M tokens USD: Gemini 4 Argon `$2/$10` **promotional through 2026-11-30, then `$4/$20` from 2026-12-01**; Gemini 3.8 Flash `$0.75/$3.75` promotional through 2026-12-31 (then `$1.50/$7.50`); Gemini 3.5 Flash-Lite `$0.30/$2.50`. Google also offers a free tier on some models, a competitor entitlement rather than a universal API credit, and lists Batch at 50%. Gemini 2.5 Pro/Flash are deprecated and auto-route from 2026-12-01. *as of 2026-11-10, source: [ai.google.dev/gemini-api/docs/pricing](https://ai.google.dev/gemini-api/docs/pricing), [blog.google](https://blog.google/intl/zh-tw/products/explore-get-answers/introducing-gemini-4-argon). Rates change; verify on the provider's pricing page before committing budget.*

### 3.4 xAI (Grok)

Text API, per 1M tokens USD: [grok-4.6](https://docs.x.ai/developers/pricing) short context `$2 input / $0.50 cached / $6 output`, long context (≥200K) `$4/$1/$12`; grok-4.5 `$2/$6`, grok-4.3 `$1.25/$2.50` (short). The long-context threshold applies to the entire request once crossed. *as of 2026-11-10, source: [docs.x.ai/developers/pricing](https://docs.x.ai/developers/pricing). Rates change; verify on the provider's pricing page before committing budget.*

## Official List Price vs Gateway Take-Home Price: Where the Gap Comes From

This is the core of a useful **LLM API pricing comparison**: the difference between a published rate and the number on your invoice. Competitors almost always show one layer. A neutral comparison shows all three.

### 4.1 Three ways gateways charge

| How a gateway charges | Where the fee lands | Example (source) |
|---|---|---|
| Pass-through + credit-purchase fee | Applied when you buy credits, never on an individual request | OpenRouter: no per-token markup; 5.5% on Standard, 8% on Business, 5% crypto ([openrouter.ai/pricing](https://openrouter.ai/pricing)) |
| Flat markup on model cost | Scales with every token you send | Requesty: 5% markup on model cost, BYOK 0% ([requesty.ai](https://www.requesty.ai/)) |
| Monthly platform + per-request / per-log fee | Scales with request and log volume, not tokens | Portkey: Pro `$49/mo` for 100K requests, `$9` per additional 100K ([portkey.ai](https://portkey.ai/docs/product/product-feature-comparison)) |
| Self-hosted proxy | No platform fee; you own the infrastructure | LiteLLM: Open Source `$0 forever`, Enterprise never per token ([litellm.ai](https://www.litellm.ai/pricing)) |
| Prepaid reseller capacity | A vendor-claimed discount off official list | KissAPI and Crouter both advertise discounts; figures are vendor claims, self-reported and not independently verified |

*as of 2026-11-10, source: official pricing / docs pages linked in the right column; competitor discount claims are vendor claims, not independently verified, and require the model, tier, and date to be confirmed. Rates change; verify on the provider's pricing page before committing budget.*

Several of those are competitor entitlements rather than charges: LiteLLM's open-source build is free to self-host, Portkey offers a free developer tier of 10K requests per month, OpenRouter lists a monthly free allowance and 25+ free models, NanoGPT has a free model on its web tier, and Crouter states no free tier. These are competitor facts and do not imply any equivalent entitlement elsewhere. Keep them in their own column; a free tier (category four) is not a token price (category one).

### 4.2 The same model, 13× to 31× apart across hosts

The spread is not theoretical. A third-party aggregator tracking 235 providers and 9,000 quotes found the same open-weight model priced 13.2× apart across 126 hosts, 25.1× across 122, 31.3× across 113, and 30.4× across 96, with data synced 2026-11-09 ([llmpricing.dev](https://llmpricing.dev/)). That is a landscape observation from a third-party tracker, not an official price source. It tells you why "the price of model X" is not a well-formed question without naming the host. The tracker also publishes a blended price using an `input × 0.75 + output × 0.25` weighting, a **third-party estimation method**, not an official list price, and one that must never be mixed into a table labelled official.

### 4.3 A documented example: listed rate vs take-home

Take GPT-6 Astra at `$10/$50` per 1M tokens. On a pass-through gateway, the token line matches OpenAI's page exactly, with no per-token markup. The fee appears elsewhere. [OpenRouter's pricing page](https://openrouter.ai/pricing) states that inference is billed at the provider's list price on every plan and that its fee is charged when you buy credits: 5.5% on Standard, 8% on Business, never on individual requests. So a `$100` token bill on Standard consumes about `$105.50` of credits. BYOK traffic gets a monthly `$25,000` list-price-equivalent allowance free of the platform fee, then 5% above it ([openrouter.ai/docs/faq](https://openrouter.ai/docs/faq), verified 2026-11-10). The listed rate and the take-home price are both real; they are simply different numbers.

### 4.4 Why a lower listed rate is not automatically a lower bill

A rate card prices one successful call at one tier. Take-home pricing adds credit-purchase and BYOK fees, subscriptions and log overages, reasoning and long-context tokens, tools, retries, and taxes. It also adds a trust cost: if a request is quietly served by a cheaper stand-in, quality drops and your team burns hours debugging code that was never broken. A lower listed rate that arrives through a silent model downgrade is not a lower bill; it is a different product. The documentation explains how to verify the exact model and channel behind each request, and a gateway shortlist helps you check which providers log that identity at all.

## The Hidden Costs a Price Table Will Not Show You

A rate card tells you what one successful call costs. Your invoice tells you what a month of real traffic costs. The difference is mostly made up of these items.

### 5.1 Credit-purchase and BYOK fees

A percentage on top-ups applies to the entire balance, not a single request, so it scales with everything you spend. OpenRouter charges 5.5% on Standard credit purchases with a `$0.80` minimum, 5% on crypto, and 8% on Business; bring-your-own-key traffic is free of the platform fee up to `$25,000` of list-price-equivalent inference per month, then 5% ([openrouter.ai/pricing](https://openrouter.ai/pricing), [openrouter.ai/docs/faq](https://openrouter.ai/docs/faq)). Requesty adds a 5% markup on model cost but 0% on BYOK ([requesty.ai](https://www.requesty.ai/)). NanoGPT advertises "no markup" at list prices, with two opt-in exceptions: manually specifying a provider or using BYOK each add 5% ([nano-gpt.com](https://nano-gpt.com/pricing)). "No markup" is rarely unconditional; read the exceptions.

### 5.2 Subscriptions, log overages, and seat tiers

Some gateways barely touch tokens at all. Portkey's Pro plan is `$49/mo` for 100K requests with `$9` per additional 100K, and its free developer tier allows 10K requests per month with three-day log retention ([portkey.ai](https://portkey.ai/docs/product/product-feature-comparison)). NanoGPT's PRO subscription is `$12/mo` ([nano-gpt.com](https://nano-gpt.com/pricing)). LiteLLM's Enterprise plan is quoted annually and never bills per token ([litellm.ai](https://www.litellm.ai/pricing)). Here the cost curve tracks request and log volume as much as tokens, so a token-only spreadsheet will understate it.

### 5.3 Self-host infrastructure

Self-hosting removes the platform fee and replaces it with a database, a cache, release patching, on-call rotation, and capacity planning. For a team with platform engineers that trade is often right; for one without, the free software is the most expensive option on the list. Treat infrastructure and engineering time as a real line in any total-cost-of-ownership model, even though no rate card will show it ([therouter.ai](https://therouter.ai/blog/ai-model-router-pricing-cost-comparison-2026)).

### 5.4 Failed requests, retries, taxes, and minimum commitments

Billing policies differ. [OpenRouter states](https://openrouter.ai/pricing) that an attempt which errors is not charged for model tokens, so with fallback you pay only for the run that answers. Streaming cancellation is not honored by every upstream provider, so an aborted response on those routes can still incur cost. Agent loops that short-circuit early are a common source of this waste. Add tool charges (web search, file search, containers, images), regional uplifts, currency conversion, local taxes, and any minimum top-up or committed-spend terms before you compare two invoices ([ai-rockstars.com](https://ai-rockstars.com?p=12712/)).

> **Mini story: the failover that paid for itself.** A fintech backend team routed production traffic through a single provider and lost a Saturday to a regional outage. After moving behind a gateway with automatic failover and per-key budgets, their AI-incident pages dropped to zero over two quarters. The spend cap also caught a misconfigured agent loop that would have retried a failing call thousands of times overnight. They had chosen the gateway for reliability, but the line item it protected was the bill.

### 5.5 The silent-downgrade tax

If a gateway quietly serves a flagship request with a cheaper stand-in, the listed rate becomes meaningless: you are billed for one model and receiving another. There is no error and no flag, so latency and cost dashboards look normal while quality drifts. Insist on per-request metadata that records the exact model and channel, and treat documented zero-retention and no-silent-degradation policies as architecture, not homepage adjectives. The [documentation](https://newtonrouter.com/docs) covers what to log; for a fuller treatment of which providers expose that identity, see [which gateways are actually in the running](openrouter-alternatives-2026.md).

Once you know which fee layers apply to your volume, **[See plans →](https://newtonrouter.com/plans)** to review the available options before moving production traffic.

## Worked Example: One Workload, Three Access Paths

A formula is only useful if you can run it. Here is one workload priced three ways. **All assumptions are stated; every unit price is sourced and dated; the result is illustrative, not a quote.**

**Assumptions.** 10,000 requests per day for 30 days = 300,000 requests/month. Each request: 2,000 input tokens + 500 output tokens, no caching, standard processing, short context. Monthly volume: 600M input tokens, 150M output tokens. Model: GPT-6.1 Sol at official list `$2 input / $10 output` per 1M ([openai.com/api/](https://openai.com/api/), verified 2026-11-10).

| Cost line | A: direct to provider | B: pass-through gateway (Standard) | C: discounted reseller (vendor claim) |
|---|---:|---:|---:|
| Input (600M tokens) | $1,200.00 | $1,200.00 | $300.00 (hypothetical) |
| Output (150M tokens) | $1,500.00 | $1,500.00 | $375.00 (hypothetical) |
| Credit-purchase fee | — | $148.50 (5.5%) | — |
| **Monthly total** | **$2,700.00** | **≈ $2,848.50** | **≈ $675.00 (unverified)** |

*as of 2026-11-10, source: [openai.com/api/](https://openai.com/api/) (GPT-6.1 Sol list rates) and [openrouter.ai/pricing](https://openrouter.ai/pricing) (Standard 5.5% credit-purchase fee). These two official sources cover the Path A and Path B unit prices and the Standard fee only; they do not cover Path C. Illustrative arithmetic on the stated assumptions; USD. **Path C assumes a reseller lists the same model at $0.50 input / $2.50 output per 1M, a hypothetical figure that is not any vendor's published rate: a vendor claim, self-reported and not independently verified, shown here as a hypothesis to test rather than a price.** Rates change; verify on the provider's pricing page before committing budget.*

Path A is the official list arithmetic. Path B adds a documented 5.5% fee on Standard credit purchases; on Business it would be 8%, and BYOK up to `$25,000` of monthly list-price inference carries no platform fee. Path C looks smallest and is the only one you cannot audit from a public rate card: a discount is meaningful only with the model, tier, and date attached, and only if the response is actually served by the model you asked for.

> **Mini story: the discount that was not.** Marcus ran a solo developer-tools business and moved traffic to a reseller advertising a steep discount off official list. For six weeks his support replies felt weaker, but latency and cost dashboards looked normal. He finally logged raw responses and found roughly a third of his flagged-premium calls were being served by a cheaper model, with no error and no flag. On paper he was saving a percentage; in practice he was buying a different product and spending his own time investigating the drop. "I don't need a lower headline rate," he said. "I need the model I asked for." He moved to a gateway that logs the exact model and provider per request.

The lesson is not that discounts are bad. It is that a rate without a model name, a tier, and a date attached is not a rate you can verify. Build the worksheet first, then run your own top ten prompts through two or three shortlisted options and compare the resulting invoices.

## How to Compare LLM API Prices Fairly: A 7-Point Checklist

Before you commit budget, run these seven checks on every candidate.

1. **Normalize to USD per 1M tokens.** Convert every quote to the same unit and currency.
2. **List input and output separately.** Never collapse them into one blended number; read cached input as a third line.
3. **Cite the official page and the as-of date per row.** Official list prices come only from the provider's own pricing page; label third-party estimates and blended-price methods as such.
4. **Match the tier and context threshold.** Note standard vs batch, short vs long context, and any regional uplift.
5. **Add every fee outside the rate card.** Credit-purchase and BYOK fees, subscriptions, log overages, tools, retries, taxes, and FX.
6. **Verify the model identity per request.** Confirm the exact model and channel served, not just a green status dot.
7. **Re-test on your real prompts before launch.** Repeat the worksheet after any model, prompt, or routing change.

These checks prevent the most expensive outcome: rebuilding a budget around a number that was never real, then migrating a second time six months later.

## FAQ

**How much does an LLM API cost per 1 million tokens in 2026?**
There is no single price. As of 2026-11-10, official list rates per 1M tokens run from GPT-6 Luna `$0.10/$0.50` up to GPT-6 Astra `$10.00/$50.00` ([openai.com/api/](https://openai.com/api/)). A third-party tracker puts the blended range across hundreds of models at `$0.02–$285.00` per 1M ([tokenando.ai](https://tokenando.ai/learn/how-ai-api-pricing-works), October 2026), a landscape estimate, not an official rate. Output tokens usually cost several times more than input, so read both columns. Rates change; verify on the provider's pricing page before committing budget.

**What is the difference between an official list price and what a gateway actually charges?**
Three numbers. The **official list price** is the provider's published per-1M-token rate. The **gateway listed rate** is what a gateway's rate card shows, a pass-through of list price or a vendor-claimed discount. The **effective take-home price** adds every fee on your token mix. OpenRouter passes through provider list prices with no per-token markup but charges a 5.5% credit-purchase fee on Standard and 8% on Business ([openrouter.ai/pricing](https://openrouter.ai/pricing), verified 2026-11-10).

**How is LLM API cost calculated?**
`Cost = (input ÷ 1M × input rate) + (output ÷ 1M × output rate)`. Then add cached-input tokens at their own lower rate, apply batch or long-context adjustments, and layer on platform fees, tool charges, and retries. Divide the total by total token volume for your effective rate per million tokens ([tokenmath.net](https://tokenmath.net/llm-cost-calculator), [moneydeck.io](https://moneydeck.io/tools/ai-api-cost-calculator)). A homepage percentage is no substitute for this arithmetic.

**Why is my LLM API bill higher than the published price table suggests?**
A rate card prices one successful call at one tier. Your invoice adds output tokens priced above input, reasoning tokens billed at output rates, long-context and regional uplifts, credit-purchase and BYOK fees, subscriptions and log overages, tool calls, failed or aborted requests that some providers still bill, taxes, and currency conversion. Log the model and channel behind each request so you can separate these lines ([therouter.ai](https://therouter.ai/blog/ai-model-router-pricing-cost-comparison-2026), [ai-rockstars.com](https://ai-rockstars.com?p=12712/)).

**Do prompt caching and batch processing actually lower LLM API costs?**
Yes, with preconditions. OpenAI lists cached input at roughly 10% of standard input and Batch at 50% of standard rates; Anthropic lists Batch at 50% savings ([platform.openai.com/docs/pricing](https://platform.openai.com/docs/pricing), [claude.com/pricing](https://claude.com/pricing), verified 2026-11-10). Caching pays off only when a stable prompt prefix is reused and hits, and Batch requires asynchronous work that can wait up to 24 hours. Check each provider's own documentation for the exact figure.

**Can the same model cost different amounts on different gateways?**
Yes. A third-party aggregator tracking 235 providers found the same open-weight model priced 13.2× to 31.3× apart across 96–126 hosts ([llmpricing.dev](https://llmpricing.dev/), data synced 2026-11-09). The spread comes from channel tiers, volume purchasing, multiple hosts serving open-weight models, promotional windows, and platform fees layered on top. Compare the effective take-home price on your own prompts, not the headline rate.

## Conclusion: Compare the Bill, Not the Headline Rate

The most useful shift is a small one. Stop asking which page shows the smallest advertised number, and start asking what ten of your real prompts cost end to end. Separate input, cached input, and output tokens. Normalize to USD per 1M. Add every fee outside the rate card. Then run that identical mix on two or three options and compare the totals, with the model, tier, and date attached to each.

Once you have a number you trust, the rest gets easier. You will know whether a platform fee buys failover worth having, whether a self-hosted proxy is cheaper than the engineering time it consumes, and whether a discount comes with the model you actually asked for. No single provider wins on price for every workload; the answer depends on your token mix. The rate that wins on a pricing page is not always the one that wins on an invoice.

**Next steps:** price is one axis. When you are ready to weigh model breadth, stability, retention policy, and language support alongside cost, read [our OpenRouter alternatives roundup](openrouter-alternatives-2026.md) for the full gateway comparison.

Ready to test the arithmetic on your own traffic and log the exact model behind every request? **[First top-up: pay $1, get $5 credit →](https://newtonrouter.com/register)** Point one client at `https://newtonrouter.com/v1`, keep your existing SDK, and price your top ten prompts against what you pay today. Your future budget review will thank you.
