# Legal AI Contract Intelligence Platform

A comprehensive legal intelligence platform designed to simplify contract analysis and comprehension. This project is a personal learning initiative exploring the integration of Large Language Models (LLMs), RAG (Retrieval-Augmented Generation), and full-stack development.

---

## 🚀 Overview

Legal documents are notoriously lengthy, dense, and rich in specialized jargon. This project leverages a robust AI stack combining **Google Gemini** and **LangChain** to provide automated analysis, risk detection, and interactive chat capabilities for legal contracts.

It serves as a practical implementation of:

- **RAG (Retrieval-Augmented Generation)** for context-aware document chat.
- **OCR Integration** for processing scanned documents.
- **Full-Stack Architecture** using Next.js and Node.js.

---

## 🏆 Key Features

- **🔐 Login & Access:** Secure Google/OTP authentication.
- **📄 Contract Upload:** Upload contracts (PDF/images) for instant analysis.
- **📊 Analysis & Red Flag Detection:** OCR extracts text; LangChain + Gemini identify clauses, potential risks, and compliance issues.
- **💬 Contract Chat Interface:** Chat with your document using Gemini-powered semantic chat, with contextual Q&A.
- **📥 PDF Export:** Export chat transcripts and insights as polished PDFs.
- **🧠 Domain-Aware Chatbot:** General legal assistant for broader queries.

---

## 🧑‍💻 Tech Stack

- **Frontend:** Next.js, React, Tailwind CSS
- **Backend:** Node.js, Express, MongoDB, Passport.js
- **AI:** Google Gemini, LangChain
- **OCR:** Tesseract, PyMuPDF, Python integration
- **PDF:** pdfkit

---

## 🛠️ Installation & Setup

### 1. Clone the repository

```powershell
git clone <repo-url>
cd briefai
```

### 2. Install dependencies

#### Frontend

```powershell
cd client
npm install
```

#### Backend (Node.js)

```powershell
cd ../server
npm install
```

#### Backend (Python OCR)

```powershell
# inside server/
pip install -r requirements.txt
```

### 3. Install Tesseract OCR

- **Windows:** Download from [here](https://github.com/UB-Mannheim/tesseract/wiki) and add to PATH.
- **macOS:** `brew install tesseract`
- **Linux:** `sudo apt-get install tesseract-ocr`

### 4. Environment Variables

- Copy `.env.example` to `.env` in both `client` and `server` folders and fill in required keys (Google, Cloudinary, MongoDB, Gemini, etc).

### 5. Start the servers

```powershell
# In /server
npm start
# In /client
npm run dev
```

---

## 📖 API Documentation (Backend)

### Authentication

- `POST /api/auth/send-otp` — Send OTP to email
- `POST /api/auth/verify-otp` — Verify OTP, get JWT
- `GET /api/auth/me` — Get user info (JWT required)
- `GET /api/auth/google` — Google OAuth login

### OCR & Document Upload

- `POST /api/ocr/upload-single` — Upload and OCR a single file
- `POST /api/ocr/upload-multiple` — Upload and OCR multiple files
- `GET /api/ocr/result/:fileId` — Get OCR result by fileId
- `GET /api/ocr/chunks/:fileId?page=1&limit=10` — Paginated text chunks
- `GET /api/ocr/history` — User's OCR upload history

### Legal Analysis

- `POST /api/legal/analyze/:fileId` — Analyze contract for legal structure, risks, compliance, red flags
- `POST /api/legal/summary/:fileId` — Executive summary
- `POST /api/legal/entities/:fileId` — Extract key entities/terms

### Chatbot

- `POST /api/legal/initialize` — Start chat session
- `POST /api/legal/ask` — Chat with legal AI (contextual)
- `GET /api/legal/history` — Get chat history
- `POST /api/legal/clear` — Clear chat history

### PDF Generation

- `POST /api/document/generate` — Generate PDF summary of consultation

---

## 🧩 Python OCR Service

- **Script:** `server/ocr.py`
- **Install dependencies:**
  ```powershell
  pip install -r requirements.txt
  ```
- **Run as part of backend Node.js service (auto-invoked)**
- **Libraries:**
  - `pytesseract`, `Pillow`, `PyMuPDF`, `langchain-text-splitters`, `langchain-core`
