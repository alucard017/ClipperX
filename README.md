# ✂️ ClipperX – Clip X/Twitter Videos Seamlessly

[![Frontend – Vercel](https://img.shields.io/badge/Frontend-Vercel-blue?logo=vercel)](https://clipper-x-mu.vercel.app)
[![Backend – Render](https://img.shields.io/badge/Backend-Render-brightgreen?logo=render)]
[![yt-dlp](https://img.shields.io/badge/yt--dlp-enabled-orange?logo=youtube)]
[![FFmpeg](https://img.shields.io/badge/FFmpeg-integrated-lightgrey?logo=ffmpeg)]

**ClipperX** is a blazing-fast video clipping tool built to extract clips from **Twitter (X.com)** videos with custom start/end times, using open-source video processing tools like `yt-dlp` and `ffmpeg`.

---

## 🔗 Live Demo

- 🎬 Frontend: [https://clipper-x-mu.vercel.app](https://clipper-x-mu.vercel.app)
- ⚙️ Backend: Render-hosted API (automatically connected to frontend)

---

## 🚀 Features

✅ Paste any **Twitter/X** video link  
✅ Specify **start & end** timestamps (HH:MM:SS)  
✅ High-speed clipping via **FFmpeg**  
✅ Auto-deletes clips after 30 seconds  
✅ Modern UI (built with **Next.js**, **Tailwind**, **Framer Motion**)  
✅ Deployed on **Vercel (frontend)** + **Render (backend)**  
✅ Dockerized backend with `yt-dlp` and `ffmpeg` preinstalled

---

## 📦 Project Structure

```bash
ClipperX/
├── ClipperX-frontend/     # Vercel-deployed frontend (Next.js, Tailwind)
├── ClipperX-backend/      # Dockerized backend (Express + yt-dlp + ffmpeg)
└── README.md
```
---

## 🧩 Technologies Used
| Frontend         | Backend            | Infrastructure       |
|------------------|--------------------|-----------------------|
| Next.js 14       | Express.js         | Vercel (frontend)     |
| Tailwind CSS     | ffmpeg             | Render (backend)      |
| Framer Motion    | yt-dlp             | Docker                |
| TypeScript       | Node.js            |                       |


---

## 🖥️ How It Works
- User submits a Twitter/X video URL and time range via the frontend
- Backend (Node.js) uses yt-dlp to download the video
- FFmpeg clips the video between the requested time
- The user receives a temporary download link valid for 30 seconds

---

## ✅ TODO (Future Improvements)
- ⬜ Add support for other platforms (YouTube, Instagram, etc.)
- ⬜ Allow download in different formats (.webm, .mp3)
- ⬜ User authentication & clip history
- ⬜ Persistent storage (option to save clips)

---

## 🔧 Backend Setup (ClipperX-backend)
#### 🐳 Docker Build & Run
```bash
git clone https://github.com/yourusername/ClipperX.git
cd ClipperX/ClipperX-backend

# Build Docker image
docker build -t clipperx-backend .

# Run the container
docker run -p 8000:8000 clipperx-backend
```
#### 🛠 Environment Variables
Create a .env file in ClipperX-backend/:
```env
PORT=your_port or 8000 if locally running
BASE_URL= your_backend_url or http://localhost:8000 if locally running
```
#### 🧪 Test API (locally)
```bash
curl -X POST http://localhost:8000/clip \
  -H "Content-Type: application/json" \
  -d '{
    "tweetUrl": "https://x.com/username/status/123456789",
    "start": 30,
    "end": 60
  }'
```
---
## 🌐 Frontend Setup (ClipperX-frontend)
### 🧪 Local Development
```bash
cd ClipperX/ClipperX-frontend
npm install
npm run dev
```
### 🌍 Deployed via Vercel
Change the API_BASE_URL(optional)
```ts
export const API_BASE_URL = "your_backend_url";
```
Change the rewrites
```json
{
  "rewrites": [
    {
      "source": "/clip",
      "destination": "your_backend_url/clip"
    }
  ]
}
```
---
## 📁 Dockerfile (Backend)
```Dockerfile
FROM node:18-slim

# Install FFmpeg and Python
RUN apt-get update && \
    apt-get install -y ffmpeg python3 python3-pip && \
    pip install --break-system-packages yt-dlp && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Create app directory
WORKDIR /app

# Copy files
COPY . .

# Install deps and run
RUN npm install

EXPOSE 8000
CMD ["node", "server.js"]
```
---

## 🛡️ License
MIT © 2025 Apurba Sundar Nayak

---

## 🙋‍♂️ Contributors Welcome!
```diff

Let me know if you'd like me to:
- Fill in your GitHub username and actual repo links
- Add usage GIFs/screenshots
- Make a CLI version or webhook-ready backend
- Extend the backend for YouTube or Instagram

Just say the word!
```






