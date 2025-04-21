## LLM-Powered RAG

by พี่กนธี

RAG มีสองประเภท

1.) Structured RAG

![image](https://github.com/user-attachments/assets/e6e58ff5-67bb-484d-8611-8f6a08f0ddfb)

1. Question มันก็จะเอาไปรวมกับคำถามเดิม
2. มันเอาโค้ดที่เจนได้ไปรันจริงๆใน Database
3. เอาผลลัพธ์ที่ได้จาก SQL ออกมาไปรวมกับคำถามแล้วเจนข้อความออกมา

ตัวอย่าง

![image](https://github.com/user-attachments/assets/307aeaec-fdaa-48ac-b237-dda133af2bab)

Postgres, Oracle อะไรก็ได้ ที่จะนำมาต่อ

* คำถาม GPT มันเจน SQL ได้แม่นยังไง เพราะมันมีคำถาม sql-create-context ขึ้นมาเพื่อเทรนด์ มันเจน SQL ได้หมดแล้ว

![image](https://github.com/user-attachments/assets/17d936c5-96ab-4a7e-9401-de6f5f99ba95)

เดี๋ยววันนี้จะมาลอง Llama 4 

เวลาเราทำ เราจะให้ GPT ต่อตรงกับ Database

เสร็จแล้วเราอยากให้ปริ้นท์ DB ออกมาว่ามี Fields อะไรออกมาบ้าง แล้วก็มีตัวอย่างอะไรออกมาบ้าง โดยวิธีการเชื่อมเราจะใช้ Langchain

![image](https://github.com/user-attachments/assets/af40757e-42d1-4d84-9132-88fba828de2f)

การทำ RAG รูปแบบนี้ เราให้โมเดลไปเจน SQL ไปรัน แล้วก็เอาข้อมูลที่ได้มาบอก

สำหรับ Workshop นี้จะใช้ Groq เพื่อเรียก API และใช้ Langchain
