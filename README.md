# 🚀 AI-Powered Social Media Content Factory

An automated workflow that generates high-quality, platform-specific social media content using AI.

Built with **n8n**, **Groq API**, and **webhooks**, this system takes a simple input (topic, link, hashtags) and produces optimized posts for:

* LinkedIn (professional)
* Instagram (casual + emojis)
* X (short & impactful)
* TikTok (fast, visual, trend-driven)
* YouTube Shorts (punchy vertical video)

Each platform also gets an `image_prompt` describing a matching visual.

---

## 🧠 How It Works

1. A **Webhook** receives input data:

   * Topic
   * Link
   * Hashtags

2. The data is sent to an **AI model (Groq, `llama-3.3-70b-versatile`)**

3. The AI generates structured JSON content for each platform

4. **Optional image branch:** if the request also carries an `image` file, an **If** node routes it through a **Code** node (which builds a safe, timestamped filename) and uploads it to **ImgBB**, which returns a public image URL you can attach to the posts

5. Output can be:

   * Reviewed
   * Stored
   * Posted automatically (future upgrade)

```text
                 ┌──────────────► Groq (LLaMA 3.3) ──► JSON per platform
Webhook (POST) ──┤
                 └─► If image attached? ─ yes ─► Code (filename) ─► ImgBB upload ─► image URL
```

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
    "cta": "...",
    "image_prompt": "..."
  },
  "Instagram": {
    "caption": "...",
    "hashtags": ["..."],
    "emojis": ["🔥"],
    "cta": "...",
    "image_prompt": "..."
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
2. In n8n, choose **Import from file** and select `workflows/social-content-generator.json`
3. In the Groq **HTTP Request** node, replace `YOUR_API_KEY` in the `Authorization` header with your key (`Bearer gsk_...`). Never commit a real key.
4. *(Only for the image branch)* In the ImgBB **HTTP Request1** node, replace `YOUR_IMGBB_API_KEY` with your [ImgBB](https://api.imgbb.com/) key
5. Activate the workflow (or use **Listen for test event**) and send a request:

```bash
curl -X POST http://localhost:5678/webhook/social-post \
  -H "Content-Type: application/json" \
  -d '{"topic": "Why n8n is the best", "link": "https://n8n.io", "hashtags": ["n8n", "automation"]}'
```

Use `/webhook-test/social-post` while the workflow is in test mode. To include an image, send `multipart/form-data` with the fields `topic`, `link`, `hashtags` and a file field named `image`.

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
