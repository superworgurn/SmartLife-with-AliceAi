<div align="center">
  <h1>🌸 SmartLife-with-AliceAi 🌸</h1>
  <p>Your Cute and Polite AI Personal Assistant on LINE</p>
  
  <p>
    <img src="https://img.shields.io/badge/n8n-FF6C37?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />
    <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
    <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white" alt="Ollama" />
    <img src="https://img.shields.io/badge/Cloudflare_Tunnel-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare Tunnel" />
    <img src="https://img.shields.io/badge/LINE_Messaging_API-00C300?style=for-the-badge&logo=line&logoColor=white" alt="LINE" />
  </p>
</div>

<br>

## 🇬🇧 English Version

### 🌟 Introduction
**SmartLife-with-AliceAi** is a smart personal assistant workflow running on **n8n**. "Alice" is designed to be a cute, highly polite AI who helps you manage your Google Calendar events and sends you friendly reminders via **LINE Official Account (Messaging API)** 2 minutes before your events start. 

### 🚀 Features
- **Natural Language Calendar Management:** Tell Alice to create an event, and she will automatically extract the date, time, and summary to save it to your Google Calendar.
- **Smart Reminders:** Automatically notifies you via LINE 2 minutes before an event starts. She even gives special encouraging messages for "Exams" or "Tests"!
- **Math Capabilities:** Equipped with a calculator tool to help you solve math problems.
- **Local AI Powered:** Uses **Ollama** for complete privacy and local processing.

### 🛠️ Tech Stack & Architecture
- **Workflow Automation:** n8n
- **Local LLM:** Ollama 
- **Messaging Platform:** LINE Official Account (Messaging API)
- **Expose Localhost:** Cloudflare Tunnel (`cloudflared`)
- **Containerization:** Docker

### ⚙️ Installation & Setup

#### 1. Start Ollama (with GPU Support)
```bash
docker run -d \
  --gpus all \
  -v ollama_storage:/root/.ollama \
  -p 11434:11434 \
  -e OLLAMA_ORIGINS="*" \
  --name ollama \
  ollama/ollama
```

_Download the required models (Note: Model AI Size > 4b is recommended):_

**Example**

```
docker exec -it ollama ollama pull llama3.1
docker exec -it ollama ollama pull gemma3:4b
```

#### 2. Start Cloudflare Tunnel (If you don't have a personal domain name)

_For n8n:_

Bash

```
docker run -it --rm --name cloudflare-quick-tunnel \
  cloudflare/cloudflared \
  tunnel --url http://host.docker.internal:5678
```

_For Ollama:_

Bash

```
docker run -it --rm --name ollama-tunnel \
  cloudflare/cloudflared \
  tunnel --url http://host.docker.internal:11434
```

#### 3. Start n8n

Replace `<YOUR_TUNNEL_URL>` with the URL provided by the Cloudflare tunnel in step 2.

Bash

```
docker run -it -p 5678:5678 -v n8n_data:/home/node/.n8n -e WEBHOOK_URL=https://<YOUR_TUNNEL_URL> -e N8N_HOST=<YOUR_TUNNEL_URL> -e N8N_PROTOCOL=https -e N8N_PORT=5678 -e N8N_EDITOR_BASE_URL=https://<YOUR_TUNNEL_URL> n8nio/n8n
```

#### 4. Import Workflow

-   Open your n8n instance.
    
-   Import the `SmartLife-with-AliceAi.json` file.
    
-   Update your Credentials for **Ollama**, **LINE Messaging API**, and **Google Calendar OAuth2**.
    
-   For n8n connecting to Ollama, use `http://host.docker.internal:11434` as the host.
    

### 📄 License

This project is licensed under the MIT License - see the [LICENSE](https://www.google.com/search?q=LICENSE&authuser=4) file for details.

<hr>

## 🇹🇭 Thai Version (ภาษาไทย)

### 🌟 แนะนำโปรเจกต์

**SmartLife-with-AliceAi** คือระบบผู้ช่วยส่วนตัวอัจฉริยะที่รันบน **n8n** โดยมี "อลิซ (Alice)" เป็น AI ผู้ช่วยที่มีนิสัยน่ารัก เรียบร้อย และสุภาพ อลิซจะคอยช่วยเหลือคุณในการจัดการปฏิทิน (Google Calendar) และคอยแจ้งเตือนกิจกรรมผ่าน **LINE OA** ล่วงหน้า 2 นาทีก่อนเริ่มกิจกรรม

### 🚀 ฟีเจอร์หลัก

-   **จัดการปฏิทินด้วยภาษาพูด:** พิมพ์บอกอลิซให้ตั้งเตือนกิจกรรม ระบบจะสกัด วัน เวลา และชื่อกิจกรรม ไปบันทึกลง Google Calendar ให้โดยอัตโนมัติ
    
-   **แจ้งเตือนอัจฉริยะ:** ระบบจะส่งข้อความแจ้งเตือนผ่าน LINE ล่วงหน้า 2 นาที โดยมีเงื่อนไขพิเศษ เช่น หากเป็น "วันสอบ" อลิซจะพิมพ์ข้อความให้กำลังใจเป็นพิเศษ!
    
-   **ช่วยคำนวณ:** มีระบบ Calculator ช่วยคิดเลขเมื่อคุณต้องการ
    
-   **ประมวลผลในเครื่อง (Local AI):** ใช้ **Ollama** เพื่อความปลอดภัยของข้อมูลส่วนตัว
    

### 🛠️ เทคโนโลยีที่ใช้

-   **สร้าง Workflow:** n8n
    
-   **Local LLM:** Ollama
    
-   **แพลตฟอร์มแชท:** LINE Official Account (Messaging API)
    
-   **เปิดพอร์ตเครือข่ายให้เชื่อมต่อออนไลน์ได้:** Cloudflare Tunnel (`cloudflared`)
    
-   **จัดการสภาพแวดล้อม:** Docker
    

### ⚙️ การติดตั้งและการใช้งาน

#### 1. รัน Ollama (รองรับการใช้ GPU)

Bash

```
docker run -d \
  --gpus all \
  -v ollama_storage:/root/.ollama \
  -p 11434:11434 \
  -e OLLAMA_ORIGINS="*" \
  --name ollama \
  ollama/ollama
```

_ดาวน์โหลดโมเดลที่ใช้ (คำเตือน: ควรมีพื้นที่ว่างหรือสเปกที่รองรับโมเดลขนาดใหญ่กว่า 4b):_


**ตัวอย่าง**
```
docker exec -it ollama ollama pull llama3.1
docker exec -it ollama ollama pull gemma3:4b
```

#### 2. รัน Cloudflare Tunnel (กรณีไม่มี Domain ส่วนตัว)

_สำหรับ n8n:_

Bash

```
docker run -it --rm --name cloudflare-quick-tunnel \
  cloudflare/cloudflared \
  tunnel --url http://host.docker.internal:5678
```

_สำหรับ Ollama:_

Bash

```
docker run -it --rm --name ollama-tunnel \
  cloudflare/cloudflared \
  tunnel --url http://host.docker.internal:11434
```

#### 3. รัน n8n

นำ URL ที่ได้จาก Cloudflare Tunnel ในขั้นตอนที่ 2 มาแทนที่ `<YOUR_TUNNEL_URL>`

Bash

```
docker run -it -p 5678:5678 -v n8n_data:/home/node/.n8n -e WEBHOOK_URL=https://<YOUR_TUNNEL_URL> -e N8N_HOST=<YOUR_TUNNEL_URL> -e N8N_PROTOCOL=https -e N8N_PORT=5678 -e N8N_EDITOR_BASE_URL=https://<YOUR_TUNNEL_URL> n8nio/n8n
```

#### 4. การตั้งค่า Workflow

-   เข้าสู่ระบบ n8n ของคุณ
    
-   ทำการ Import ไฟล์ `SmartLife-with-AliceAi.json`
    
-   ตั้งค่า Credentials ของ **Ollama** (ใช้ URL: `http://host.docker.internal:11434`), **LINE Messaging API** และ **Google Calendar OAuth2** ให้เรียบร้อย
    

### 📄 License

โปรเจกต์นี้ได้รับการคุ้มครองสิทธิ์ภายใต้ MIT License สามารถอ่านรายละเอียดเพิ่มเติมได้ในไฟล์ [LICENSE](https://www.google.com/search?q=LICENSE&authuser=4)