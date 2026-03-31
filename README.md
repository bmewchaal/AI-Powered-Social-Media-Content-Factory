# 🚀 AI-Powered Social Media Content Factory

An automated workflow that generates high-quality, platform-specific social media content using AI.

Built with **n8n**, **Groq API**, and **webhooks**, this system takes a simple input (topic, link, hashtags) and produces optimized posts for:

* LinkedIn (professional)
* Instagram (casual + emojis)
* X (short & impactful)
* Facebook (friendly)

---

## 🧠 How It Works

1. A **Webhook** receives input data:

   * Topic
   * Link
   * Hashtags

2. The data is sent to an **AI model (Groq - LLaMA 3)**

3. The AI generates structured JSON content for each platform

4. Output can be:

   * Reviewed
   * Stored
   * Posted automatically (future upgrade)

---

## ⚙️ Tech Stack

* n8n (workflow automation)
* Groq API (LLM inference)
* Postman (testing)
* Webhooks (trigger system)

---

## 🔌 Example Input

```json
{
  "topic": "Why n8n is the best",
  "link": "https://n8n.io",
  "hashtags": ["n8n", "automation"]
}
```

---

## 📤 Example Output

```json
{
  "LinkedIn": {
    "text": "...",
    "hashtags": ["..."],
    "cta": "..."
  },
  "Instagram": {
    "caption": "...",
    "hashtags": ["..."],
    "emojis": ["🔥"],
    "cta": "..."
  }
}
```

---

## 🚀 Features

* Multi-platform content generation
* Structured JSON output
* Fully automatable workflow
* Easy integration with APIs

---

## 🛠️ Setup

1. Clone the repo
2. Import the workflow into n8n
3. Add your Groq API key
4. Run the webhook
5. Send a POST request via Postman

---

## 🔮 Future Improvements

* Auto-post to social media APIs
* Add image generation
* Add approval system
* Dashboard for content preview

---

## 📌 Notes

This project is a learning and experimentation tool for:

* AI automation
* Workflow orchestration
* API integrations

---

## 👨‍💻 Author

Built by Mechaal Abderrahmane
