# AI Text Moderation, Toxicity, Aspects & Sentiment Analyzer

## Overview
The **AI Text Moderation, Toxicity, Aspects & Sentiment Analyzer API** is a next‑generation multilingual engine designed to understand, evaluate, and protect your content in real time. Built on our **uniquely trained AI model**, powered by **billions of raw text samples and petabytes of linguistic data**, this API delivers unmatched precision across sentiment, emotion, toxicity, aspect-based analysis, and moderation tasks.

<p align="center">
  🆓 <b>FREE API</b> — use instantly on 
  <a href="https://rapidapi.com/vintarok-vintarok-default/api/ai-text-moderation-toxicity-aspects-sentiment-analyzer" target="_blank"><b>RapidAPI</b></a> 🚀
</p>

<p align="center">
  <a href="https://rapidapi.com/vintarok-vintarok-default/api/ai-text-moderation-toxicity-aspects-sentiment-analyzer">
    <img src="logo.png" width="120" alt="AI Text Moderation & Sentiment Analyzer API Logo">
  </a>
</p>

Our system doesn’t just classify text — it *comprehends* it. Whether you’re analyzing customer reviews, moderating social media platforms, or measuring emotional tone in user feedback, this API adapts seamlessly to your use case.

---

## Key Features
- 🌍 **Multilingual Support** — Works automatically across dozens of languages without configuration.
- 💬 **Sentiment Analysis** — Detects polarity (positive, neutral, negative, mixed) with weighted confidence scores.
- ⚡ **Toxicity Detection** — Identifies hate speech, harassment, violence, self‑harm, sexual or graphic content, and spam with fine‑grained category scores.
- ❤️ **Emotion Recognition** — Recognizes primary human emotions like joy, trust, anger, sadness, fear, disgust, and surprise.
- 🔍 **Aspect-Based Insights** — Extracts and analyzes opinions about specific entities, features, or topics in text.
- 🧠 **Smart Moderation** — Automatically evaluates safety, flags violations, or masks harmful content depending on configuration.
- 🧩 **Flexible Modes** — Choose between **Full Mode** for in‑depth text analytics and **Light Mode** for the fastest possible evaluation when speed is critical.

---

## Modes Explained
### 🔹 Full Mode
Full Mode provides the most comprehensive breakdown of textual content. It includes:
- Complete **sentiment**, **toxicity**, **emotion**, and **aspect-based** analysis.
- Integrated **moderation layer** with detailed violation spans.
- Balanced reasoning for nuanced text understanding.

Ideal for research, enterprise monitoring, and applications requiring the **highest analytical accuracy**.

### 🔹 Light Mode
Light Mode is engineered for **instant evaluation** — it focuses on **sentiment and toxicity detection only**, making it the fastest mode available while maintaining high reliability.

Best suited for chat moderation, quick API pipelines, or real-time user feedback checks.

---

## Use Cases
This API fits seamlessly into any application where text understanding, emotion detection, and moderation matter:

- 🧑‍💼 **Customer Support & Feedback Analysis** — Identify user sentiment and improve response strategies.
- 💬 **Community & Chat Moderation** — Automatically filter out harassment, hate speech, or explicit content.
- 🛍️ **E‑Commerce Reviews & Ratings** — Detect hidden sentiment or emotional tone in product feedback.
- 🧾 **Media & Journalism** — Monitor reader tone or comment toxicity for editorial control.
- 📊 **Brand Monitoring** — Measure emotional resonance and brand reputation in multilingual environments.
- 🎮 **Gaming & Social Apps** — Maintain safe spaces with live toxicity filtering.

---

## Highlights
- ⚙️ **No setup required** — Plug & play integration with simple JSON requests.
- 🔒 **Privacy‑First Design** — No data storage, all processing done in real time.
- 🌐 **Adaptive Understanding** — Works with slang, emojis, abbreviations, and multilingual input.
- 🧭 **Consistent Structure** — Unified output schema for easy parsing and analytics integration.

---

## Conclusion
The **AI Text Moderation, Toxicity, Aspects & Sentiment Analyzer API** redefines what text intelligence can achieve. Whether you need fast classification or deep emotional and contextual insights — this API provides the **most flexible, multilingual, and precise** solution available.

---

# 📘 AI Text Moderation & Sentiment Analyzer API

Comprehensive multilingual AI service for analyzing and moderating user-generated text. Supports **sentiment**, **toxicity**, **emotion**, and **aspect** detection with integrated moderation logic.

Our AI model is uniquely trained on **billions of raw text samples** and **petabytes of language data**, providing exceptional accuracy, context understanding, and cross-language adaptability.

All data is processed **in real time only** — nothing is stored or logged.

---


## ⚙️ Endpoints

### 1. **POST `/analyze.php`**
Performs full text analysis — sentiment, toxicity, emotion, aspects — with moderation check.

#### Description
Analyzes text or batches of text items, detecting emotions, sentiment polarity, toxicity intensity, and domain-specific aspects (topics). Supports **Full** and **Light** detail levels.

#### Content-Type
`application/json`

#### Request Fields

| Field | Type | Required | Default | Description |
|-------|------|-----------|----------|-------------|
| `text` | string | One of (`text` or `items`) | — | Single text to analyze (≤ 1000 chars). |
| `items` | array&lt;object&gt; | One of (`text` or `items`) | — | Batch analysis. Each item must include `id` and `text`. Max 10 items. |
| `modes` | array&lt;string&gt; | No | All | Subset of analysis modules to include: `sentiment`, `toxicity`, `emotion`, `aspects`. |
| `detail_level` | string | No | `full` | Determines analysis depth:<br>• `full` → full sentiment + toxicity + emotion + aspects<br>• `light` → fastest, only sentiment + toxicity |
| `moderation` | object | No | — | Pre-moderation settings (see below). |
| `metadata` | object | No | — | Any custom data, echoed back in response. |

#### Moderation Object

| Field | Type | Required | Default | Description |
|--------|--------|-----------|----------|-------------|
| `enforce` | string | No | `soft` | Moderation enforcement: `soft` (return results even if flagged) or `hard` (block request if flagged). |
| `sensitivity` | string | No | `normal` | Sensitivity: `normal`, `strict`, or `custom`. |
| `thresholds` | object | No | — | Used when `sensitivity = custom`. Per-category threshold values (0..1) for `hate_speech`, `insults_and_bullying`, `threats_or_violence`, `self_harm`, `sexual_content`, `graphic_violence`, `spam`. |
| `return_spans` | boolean | No | true | Whether to include evidence spans/snippets for detected violations. |

#### Example Request (Full Mode)
```json
{
  "text": "The product quality was excellent but shipping was slow.",
  "detail_level": "full",
  "metadata": { "request_id": "demo-01" }
}
```

#### Example Response
```json
{
  "ok": true,
  "data": {
    "detail_level": "full",
    "items": [
      {
        "id": "item-1",
        "safe": true,
        "sentiment": {
          "label": "positive",
          "scores": { "positive": 0.83, "neutral": 0.12, "negative": 0.05 },
          "magnitude": 0.77
        },
        "toxicity": {
          "overall": 0.02,
          "dimensions": {
            "hate_speech": 0.00,
            "insults_and_bullying": 0.00,
            "threats_or_violence": 0.00,
            "self_harm": 0.00,
            "sexual_content": 0.00,
            "graphic_violence": 0.00,
            "spam": 0.01
          }
        },
        "emotion": {
          "top": ["joy", "trust"],
          "scores": {
            "joy": 0.71, "trust": 0.62, "anger": 0.05, "sadness": 0.06, "fear": 0.03, "disgust": 0.02, "surprise": 0.11
          }
        },
        "aspects": [
          {
            "aspect": "shipping",
            "sentiment": { "label": "negative", "score": 0.84 },
            "evidence": [
              { "start": 36, "end": 50, "snippet": "shipping was slow" }
            ]
          }
        ],
        "moderation": {
          "allowed": true,
          "decision": "allow",
          "violations": []
        },
        "processing_ms": 1392
      }
    ],
    "processing_ms": 1433,
    "metadata": { "request_id": "demo-01" }
  }
}
```

#### Example Error (Hard Block)
```json
{
  "ok": false,
  "error": {
    "code": "BLOCKED_BY_POLICY",
    "message": "Content violates policy.",
    "violations": [
      {
        "code": "insults_and_bullying",
        "label": "Insults And Bullying",
        "severity": "high",
        "score": 0.91,
        "spans": [ { "start": 3, "end": 18, "snippet": "idiot user" } ]
      }
    ],
    "hint": "Lower sensitivity or remove flagged segments."
  }
}
```

---

### 2. **POST `/moderate.php`**
Lightweight, fast moderation endpoint for real-time safety checks.

#### Description
Checks one or multiple texts for policy violations such as hate speech, bullying, violence, sexual or graphic content, and spam. Returns detailed scores and evidence spans.

#### Content-Type
`application/json`

#### Request Fields

| Field | Type | Required | Default | Description |
|-------|------|-----------|----------|-------------|
| `text` | string | One of (`text` or `items`) | — | Text to moderate (≤ 1000 chars). |
| `items` | array&lt;object&gt; | One of (`text` or `items`) | — | Batch of items with `id` and `text`. Max 10 items. |
| `sensitivity` | string | No | `normal` | Moderation sensitivity: `normal`, `strict`, or `custom`. |
| `thresholds` | object | No | — | Used only with `sensitivity = custom`. Custom thresholds for violation categories (0..1). |
| `return_spans` | boolean | No | true | Include evidence spans/snippets. |
| `metadata` | object | No | — | Any metadata passed through. |


#### Example Request
```json
{
  "items": [
    { "id": "1", "text": "I hate this app." },
    { "id": "2", "text": "Great service and helpful support." }
  ],
  "sensitivity": "normal",
  "return_spans": true,
  "metadata": { "source": "feedback-form" }
}
```

#### Example Response
```json
{
  "ok": true,
  "data": {
    "items": [
      {
        "id": "1",
        "allowed": false,
        "decision": "block",
        "confidence": 0.93,
        "violations": [
          {
            "code": "hate_speech",
            "label": "Hate Speech",
            "severity": "high",
            "score": 0.89,
            "spans": [ { "start": 2, "end": 6, "snippet": "hate" } ]
          }
        ],
        "processing_ms": 58
      },
      {
        "id": "2",
        "allowed": true,
        "decision": "allow",
        "confidence": 0.97,
        "violations": [],
        "processing_ms": 37
      }
    ],
    "processing_ms": 110,
    "metadata": { "source": "feedback-form" }
  }
}
```

#### Example Error
```json
{
  "ok": false,
  "error": {
    "code": "BAD_REQUEST",
    "message": "Either text or items[] must be provided."
  }
}
```

---

## 🧠 Notes
- **Multilingual:** Auto-detects and supports all major languages.
- **No storage:** No data is saved; analysis is performed in-memory.
- **Real-time:** Designed for instant moderation and analysis in chatbots, reviews, and social feeds.
- **Full Mode:** Deep semantic analysis (sentiment, toxicity, emotion, aspects).
- **Light Mode:** Fastest configuration (sentiment + toxicity only).
- **Custom thresholds:** Fine-tune detection strictness per category.

---

## 💡 Use Cases
- Social media and comment moderation.
- Customer feedback analysis.
- Chatbot safety and compliance filters.
- Product review scoring and trend detection.
- AI-powered community management systems.

---

**Free plan:** for testing and experimentation only. Commercial and production usage requires a paid plan.

© AI Text Moderation & Sentiment Analyzer API — All rights reserved.



With our model, you gain more than analysis — you gain **understanding, safety, and trust** in every word.

