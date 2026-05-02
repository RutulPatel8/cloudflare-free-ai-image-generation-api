# ✨ Free AI Image Generation API (100,000 Calls/Day) ⚡

<div align="center">

**🚀 Spin up your own AI image generation API in minutes — at zero cost!**

</div>

This project helps you quickly create a **text-to-image generation API** powered by Cloudflare Workers. With support for up to **100,000 free requests per day**, you can generate high-quality images from prompts using models like Stable Diffusion XL. 🎨

## ✨ Features
- 🆓 **100,000 daily free requests** via Cloudflare Workers AI
- ⚡ **High-speed generation** from simple text prompts
- 🛠️ **Quick setup process** with minimal effort
- 🔒 **Protected endpoints** using API key authentication
- 🎯 **Flexible model support** for different use cases

---

## 🚀 How It Works
- 📤 Deploy the provided `worker.js` file as a Cloudflare Worker  
- 🌐 The Worker acts as an API endpoint for generating images  
- 🔐 Access is controlled through your custom API key  
- 🤖 Cloudflare Workers AI processes prompts and returns images  

---

## 📋 Setup Instructions

### 1. 🌟 Create a Cloudflare Account
- Register at https://dash.cloudflare.com/sign-up if you don’t already have an account  

### 2. ⚡ Create Your Worker
- Open the Cloudflare Workers dashboard  
- Click **"Create application"**  
- Select **"Create Worker"**  
- Name it something like `ai-image-api`  
- Click **"Deploy"** to initialize it  

### 3. 🔧 Update the Worker Code
- Open the worker editor  
- Replace the default code with the `worker.js` from this repository  
- Click **"Save and Deploy"**  

### 4. 🔑 Add Environment Variables
- Go to **"Settings"** → **"Variables"**  
- Add a new variable:
  - Name: `API_KEY`  
  - Value: `your-secret-api-key`  
- Save and deploy  

### 5. 🤖 Activate Workers AI
- Navigate to **"Workers & Pages"** → **"AI"**  
- Enable Workers AI (free tier works fine)  

### 6. 🔗 Configure AI Binding
- Return to your worker settings  
- Open **"Variables"**  
- Scroll to **"Service bindings"**  
- Add a binding:
  - Variable: `AI`  
  - Service: **Workers AI**  
- Save and deploy  

> ⚠️ **Important:** Without this binding, your worker won’t be able to generate images.

### 7. 🌐 Access Your API
- Your endpoint will look like:  
  `https://<your-worker-name>.<your-subdomain>.workers.dev`  
- You can copy it from the dashboard  

---

## 🎯 Usage

### 🖥️ cURL Example
```bash
curl -X POST https://<your-worker-name>.<your-subdomain>.workers.dev \
  -H "Authorization: Bearer your-secret-api-key" \
  -H "Content-Type: application/json" \
  -d '{"prompt": "A robot making coffee in a modern kitchen"}' \
  --output output.jpg
```

### 🌐 JavaScript Example
```js
const response = await fetch("https://<your-worker-name>.<your-subdomain>.workers.dev", {
  method: "POST",
  headers: {
    "Authorization": "Bearer your-secret-api-key",
    "Content-Type": "application/json",
  },
  body: JSON.stringify({ prompt: "A floating city above the clouds at sunset" }),
});

const imageBlob = await response.blob();
const image = document.createElement("img");
image.src = URL.createObjectURL(imageBlob);
image.style.height = "500px";
document.body.appendChild(image);
```

---

## 📝 Notes
- 🆓 **Free Tier:** Allows up to 100,000 requests daily (check Cloudflare docs for updates)  
- 🎨 **Model Selection:** You can modify the model inside `worker.js`  
- 🔒 **Security Tip:** Keep your API key private and rotate it if needed  

---

## 📄 License
MIT License ⭐

---

<div align="center">

**⭐ If this helped you, consider starring the repo! ⭐**

</div>
