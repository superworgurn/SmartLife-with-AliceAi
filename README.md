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
**SmartLife-with-AliceAi** is a smart personal assistant workflow running on **n8n**. "Alice" is designed to be a cute, highly polite AI who helps you manage your daily life and schedules via your **LINE Official Account (Messaging API)**. She effortlessly connects your chats to Google Calendar and provides friendly reminders exactly when you need them.

### 🚀 Features
- **Natural Language Calendar Management:** Tell Alice your plans using natural language (including Thai contexts like "พรุ่งนี้", "มะรืน", "2 ทุ่ม"). The system will smartly extract the activity name, date, and time to automatically create an event in your Google Calendar.
- **Past-Time Protection:** Alice is smart enough to know she can't time travel! If you attempt to schedule an event in the past, she will politely decline and ask for a valid future time.
- **Smart 30-Minute Reminders:** The system checks your calendar and notifies you via LINE **30 minutes** before an event starts. 
- **Special Encouragement:** If your scheduled activity includes words like "Exam", "Test", or "สอบ", Alice will send you a special, heartwarming encouraging message to boost your confidence!
- **Data Logging:** All successfully scheduled events are seamlessly logged into **Google Sheets** for your personal records and tracking.
- **Local AI Powered:** Uses **Ollama** (powered by the `qwen2.5:7b` model) for intelligent conversation, complete privacy, and local processing.

### 🛠️ Tech Stack & Architecture
- **Workflow Automation:** n8n
- **Local LLM:** Ollama (qwen2.5:7b)
- **Messaging Platform:** LINE Official Account (Messaging API)
- **Database & Scheduling:** Google Calendar & Google Sheets
- **Expose Localhost:** Cloudflare Tunnel (`cloudflared`)
- **Containerization:** Docker

### ⚙️ Installation & Setup

To keep this guide clean and easy to follow, we have separated the setup instructions into dedicated documentation files. Please follow the steps below:

1. **[Start Ollama (with GPU Support)](https://github.com/ShoperGamer/SmartLife-with-AliceAi/blob/main/Setting/ollama.txt)**: Instructions to run Ollama and download the required AI models.
2. **[Start Cloudflare Tunnel](https://github.com/ShoperGamer/SmartLife-with-AliceAi/blob/main/Setting/cloudflare_tunnel.txt)**: Instructions to expose your local n8n and Ollama to the internet (Useful if you don't have a personal domain name).
3. **[Start n8n](https://github.com/ShoperGamer/SmartLife-with-AliceAi/blob/main/Setting/n8n.txt)**: Instructions to run n8n via Docker or connect it to your Ollama instance.
4. **Import Workflow**:
   - Open your n8n instance.
   - Import the `SmartLife-with-AliceAi.json` file.
   - Update your Credentials for **Ollama**, **LINE Messaging API**, **Google Calendar OAuth2**, and **Google Sheets OAuth2**.

### 📄 License

This project is licensed under the MIT License - see the [LICENSE](https://www.blockdit.com/posts/67c70e1a64043ade0cce781a) file for details.

<hr>

## 🇹🇭 Thai Version (ภาษาไทย)

### 🌟 แนะนำโปรเจกต์

**SmartLife-with-AliceAi** คือระบบ Workflow ผู้ช่วยส่วนตัวอัจฉริยะที่ทำงานบน **n8n** โดยมี "อลิซ (Alice)" เป็น AI ผู้ช่วยที่มีนิสัยน่ารัก เรียบร้อย และสุภาพที่สุด อลิซจะคอยดูแลและช่วยเหลือคุณในการจัดการตารางชีวิตประจำวันผ่านทาง **LINE OA** เชื่อมต่อกับปฏิทินของคุณได้อย่างไร้รอยต่อ

### 🚀 ฟีเจอร์หลัก

- **จัดการปฏิทินด้วยภาษาพูด:** พิมพ์บอกอลิซด้วยภาษาธรรมชาติได้เลย ระบบรองรับคำระบุเวลาภาษาไทยอย่างเข้าใจ (เช่น "พรุ่งนี้", "มะรืน", "2 ทุ่ม", "บ่ายสาม") ระบบจะสกัด วัน เวลา และชื่อกิจกรรม ไปบันทึกลง Google Calendar ให้โดยอัตโนมัติ
- **ระบบป้องกันการนัดหมายย้อนหลัง:** อลิซรู้ว่าเธอย้อนเวลาไม่ได้! หากคุณเผลอสั่งให้จดตารางเวลาที่ผ่านไปแล้ว อลิซจะปฏิเสธอย่างนุ่มนวลและขอให้คุณระบุเวลาในอนาคตแทน
- **แจ้งเตือนล่วงหน้า 30 นาที:** ระบบจะคอยเช็คตารางงานของคุณ และส่งข้อความแจ้งเตือนความจำผ่าน LINE ล่วงหน้า **30 นาที** ก่อนเริ่มกิจกรรม
- **โหมดให้กำลังใจ:** หากกิจกรรมของคุณมีคำว่า "สอบ", "Exam" หรือ "Test" อลิซจะพิมพ์ข้อความอวยพรและให้กำลังใจคุณเป็นพิเศษก่อนเข้าสอบ!
- **เก็บบันทึกข้อมูลเป็นระเบียบ:** ทุกกิจกรรมที่ถูกบันทึกสำเร็จ จะถูกส่งไปเก็บไว้ใน **Google Sheets** เพื่อเป็นฐานข้อมูลให้คุณย้อนดูได้
- **ประมวลผลในเครื่อง (Local AI):** ใช้พลังของ **Ollama** (โมเดล `qwen2.5:7b`) ในการประมวลผลข้อความ ทำให้ข้อมูลส่วนตัวของคุณปลอดภัยและไม่ต้องพึ่งพา API ภายนอก

### 🛠️ เทคโนโลยีที่ใช้

- **สร้าง Workflow:** n8n
- **Local LLM:** Ollama (qwen2.5:7b)
- **แพลตฟอร์มแชท:** LINE Official Account (Messaging API)
- **ฐานข้อมูลและปฏิทิน:** Google Calendar และ Google Sheets
- **เปิดพอร์ตเครือข่ายให้เชื่อมต่อออนไลน์ได้:** Cloudflare Tunnel (`cloudflared`)
- **จัดการสภาพแวดล้อม:** Docker

### ⚙️ การติดตั้งและการใช้งาน

เพื่อให้คู่มือนี้อ่านง่ายและเป็นระเบียบ วิธีการตั้งค่าต่างๆ ได้ถูกแยกไว้ในโฟลเดอร์ `Setting` โปรดทำตามขั้นตอนดังต่อไปนี้:

1. **[การรัน Ollama (รองรับการใช้ GPU)](https://github.com/ShoperGamer/SmartLife-with-AliceAi/blob/main/Setting/ollama.txt)**: ดูคำสั่งรัน Ollama และดาวน์โหลดโมเดล
2. **[การตั้งค่า Cloudflare Tunnel](https://github.com/ShoperGamer/SmartLife-with-AliceAi/blob/main/Setting/cloudflare_tunnel.txt)**: สำหรับเปิดพอร์ต n8n หรือ Ollama ออกสู่อินเทอร์เน็ต (กรณีที่คุณไม่มี Domain ส่วนตัว)
3. **[การรัน n8n](https://github.com/ShoperGamer/SmartLife-with-AliceAi/blob/main/Setting/n8n.txt)**: คำสั่งรัน n8n ผ่าน Docker และการเชื่อมต่อกับ Ollama
4. **การนำเข้า Workflow**:
   - เข้าสู่ระบบ n8n ของคุณ
   - ทำการ Import ไฟล์ `SmartLife-with-AliceAi.json`
   - ตั้งค่า Credentials ของ **Ollama**, **LINE Messaging API**, **Google Calendar OAuth2** และ **Google Sheets OAuth2** ให้เรียบร้อย

### 📄 License

โปรเจกต์นี้ได้รับการคุ้มครองสิทธิ์ภายใต้ MIT License สามารถอ่านรายละเอียดเพิ่มเติมได้ในไฟล์ [LICENSE](https://www.blockdit.com/posts/67c70e1a64043ade0cce781a)