# 🤖 Toki-chan: High-Precision AI Streamer Companion (RAG)
โปรเจกต์พัฒนาระบบ Retrieval-Augmented Generation (RAG) สำหรับเป็นสมองและฐานข้อมูลความรู้ให้กับ โทคิจัง (Toki-chan) AI VTuber ส่วนตัว ระบบนี้ถูกออกแบบมาให้ประมวลผลข้อมูลบริบท (Context) ได้อย่างแม่นยำภายใต้บุคลิกภาพที่ถูกกำหนดไว้

## 🌟 Key Features
- Persona-Driven RAG: การดึงข้อมูลที่ไม่ได้ให้แค่คำตอบ แต่ยังรักษาบุคลิกภาพแบบ Stoic และ Comically Serious ของโทคิจังไว้ 
- Multi-lingual Semantic Search: ใช้ BGE-M3 Model ที่รองรับภาษาไทยได้อย่างดีเยี่ยมในการทำ Embedding
- Cloud-Native Vector Store: จัดเก็บและค้นหาข้อมูลด้วย Supabase (pgvector) เพื่อลดภาระการทำงานของเครื่อง Local 
- High-Speed Inference: เชื่อมต่อกับ Groq API เพื่อการตอบสนองที่รวดเร็ว (Low Latency) เหมาะสำหรับการใช้งานระหว่างสตรีม

## 🛠 Tech Stack
- Language: Python 3.13+
- Embedding Model: BAAI/bge-m3 (1024 Dimensions)
- Vector Database: Supabase (PostgreSQL + pgvector)
- LLM Engine: Groq (llama-3.1-8b-instant)
- Environment: Dotenv for secure credential management

## 📁 Project Structure

```plaintext
RAG-FINAL-PROJECT/
├── data/
│   ├── Toki-chan.txt        # Raw Persona & Knowledge base
│   └── toki_rag_chunks.json # Processed JSON chunks with metadata
├── assets/                  # Project diagrams & images
├── RAG.ipynb                # Core development & testing notebook
├── .env                     # API Keys (Excluded from Git)
└── requirements.txt         # Project dependencies
```
## ⚙️ System Architecture
1. Data Ingestion: แปลงไฟล์ความรู้เป็น JSON Chunks พร้อมกำหนด Metadata เช่น interaction, donation 
2. Vector Indexing: ใช้ BGE-M3 ทำ Content Hashing และสร้าง Embedding เพื่อ Upsert ลง Supabase 
3. Retrieval: เมื่อได้รับ Input ระบบจะทำ Similarity Search ผ่าน RPC Function ใน Supabase
4. Generation: รวม Context ที่ได้เข้ากับ System Prompt ของโทคิจัง แล้วส่งให้ Groq ประมวลผล

## 📈 Workflow
![RAG](Assets/RAG-workflow.png)

# 🚀 Getting Started
### 1. Clone the repo
```
git clone https://github.com/Kantheephob/Toki-chan-AI-Streamer-Companion-RAG-System.git
```

### 2. install dependencies
```
pip install -r requirements.txt
```

### 3. Setup Environment Variables <br> สร้างไฟล์ .env และเพิ่ม Key ดังนี้:
```
SUPABASE_URL=your_project_url
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
GROQ_API_KEY=your_groq_api_key
```