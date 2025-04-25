## AI and Trends ในปัจจุบัน

* LLM (Large Language Model)

![image](https://github.com/user-attachments/assets/0bf6e3f4-638c-4012-9886-add4d4055a7b)

* LLM - Omni (Multimodal)

แต่ก่อนมันรับ Text ได้อย่างเดียว สมัยนี้เป็น Input Output เป็น Text, Voice ได้หมดเลย

![image](https://github.com/user-attachments/assets/d2ec9d0b-6f43-4d47-895d-3fc0f35add8e)

ไปทำ ASR ได้เลย พลังการคำนวณมหาศาล

* LLM - Reasoning

ให้ AI มันสามารถ มีเหตุผลคุยกับตัวเองว่าสิ่งที่มันตอบกลับมา มันถูกแค่ไหน ทบทวนว่ามันเป็นแบบนั้นไหม
LLM หลักๆ สกิลที่เราควรมีคือ Prompt Engineering ซึ่งอาจมี Prompt Style ที่ต่างกันได้

![image](https://github.com/user-attachments/assets/728fa109-66e9-46ac-abb9-3323b4e18bca)

มันสำคัญที่จะสั่งให้ตัวโมเดลทำงานให้เราได้อย่างต้องการ

* RAG - Retrieval-Augmeneted Generation

ถ้ามี Data มหาศาล แล้วเราอยากจะตอบคำถามหนังสือเล่มนั้น แต่เราไม่สามารถ Feed Text Input โมเดลได้
เพราะว่า token มันไม่พอ มันมีการจำกัดอยู่ เราจะทำยังไงให้มันตอบคำถามจากทั้ง Document ที่มันมีได้
มันจะทำการ Encode Documents ให้กลายเป็น Vector (ทำ Embedding) แล้วไปเก็บใน Vector Database
เช่น บทที่ 2 กล่าวว่าอะไร มันก็จะไปเสิร์จใน Vector Database แล้วก็จะได้

![image](https://github.com/user-attachments/assets/f4aa135f-b2eb-49e9-89b5-4a7fdbfb2473)

Data เยอะอาจจะใช้ KNN น่าจะช้า แล้วเราจะพร้อมพ์โมเดลยังไงให้มันเจอ Data document ที่มันมีได้ด้วย

* Vector Database

เพราะว่า RAG นิยมมากเลยในช่วงนี้ ก็จะเป็น Vector Database ซึ่งมันมาจากการ Raw Data ไปผ่านตัว Embedding Models

![image](https://github.com/user-attachments/assets/512c06fe-64d4-4aac-9b4d-c464cda9f191)

เขาก็จะให้ Similarity Search

PostgresQL, Mongodb, Elasticsearch ก็ลองรับ

* Agentic AI (Multi Agents)

การให้ LLM ตัวนึงเป็น Agent ในการทำงาน ทำเว็บ Agent ให้มันลองมาคุยกันเองว่า เราจะสั่งงานยังไง

* MCP

MCP Hosts จะลิ้งค์ไปหา Platform มันก็จะเอา MCP Server จากเจ้าอื่น ที่สามารถเสียบได้เลย ไม่ต้องผ่าน Public Key ก็จะสะดวกแล้วนำไปใช้ต่อได้วง่ายกว่า

---

หลักการในการ Ai/ML API ก็จะทำ Cache Model / Cache Reference
Point cloud Files แต่พวก Generative มันไม่ค่อย Cache กันเพราะว่ามีเรื่องของ Temperature

เราสามารถเขียน Piepline File ได้จาก Python เลย

![image](https://github.com/user-attachments/assets/6228d137-e3ce-45b1-87f2-ee58ccd6a4ac)

มันสามารถเรียก Toggle ได้หลายไฟล์

![image](https://github.com/user-attachments/assets/05f1951a-b131-405e-ad49-f432908ba28d)

เราก็จะแปลงเป็น pkg แปลงเป็นกราฟ

## Careers

![image](https://github.com/user-attachments/assets/09548b02-6901-4d27-b4ad-e5fd69a8e5a9)

![image](https://github.com/user-attachments/assets/f1d8ad95-d997-4caf-bd29-20d2dc75a4a2)

Data Engineer -> มี Data Source ขนาดใหญ่ เอามาคลีน Validate, ETL, ELT เก็บ Data ให้พร้อมใช้งาน

Data Scientist -> เอามาวิเคราะห์สร้างโมเดล

ML Engineer -> เอาโค้ด Data Scientist มา Optimize มาทำ Docker Deploy ก็ว่ากันไป

![image](https://github.com/user-attachments/assets/0ace74b4-6bf4-4546-b0e2-8505441dbb43)

เจอมาบางที่ใช้ Data Analyst, Full Loop Requirements ก็ลองอ่าน JD ให้ละเอียด 

![image](https://github.com/user-attachments/assets/d68c68d7-9c92-4281-a172-819161a01fb9)

AI Engineer -> ก็ทำ RAG มากกว่าในตลาด

หลักๆ ควรได้พวก Linux Cloud Docker Kubernetes / มันทับซ้อนกับ DevOps ทำ CI/CD Pipeline มันแล้วแต่ที่เลยว่าเขา Requires แค่ไหน
ส่วนใหญ่จะทำงานกับ Startups เป็นส่วนใหญ่ ก็กระจายหลายด้าน

สนใจ Deployment / Cloud / Ops เขาต้องเข้าใจ ML Model มากขึ้น เพราะว่า DevOps มา Deploy เอง
ปกติเขาจะต้องเก็บโค้ด เก็บโมเดล Database ประมาณนั้น แต่พอเป็น ML มันก็จะมี Model Versioning / Data Versioning โมเดลใหญ่ๆไว้ตรงไหน Load เอาไว้ตรงไหน

* จำเป็นต้องรู้ด้าน Security หรือไม่

ไม่ได้ดูด้าน Expert มันควร Security In mind คือมันไม่ต้องรู้เท่ากับ Expert

ส่วนใหญ่ที่เจอมาจะเป็นเรื่องของ Push secret keys ขึ้น git หรือใส่ env หรือรหัส Database ก็ต้องดูไม่ให้มัน Leaked
อาจจะโดน Github ไปเทรนด์พวกโมเดล ระวัง Memory Leaked เช่น โมเดลเรารับ Data มา แล้ว Data Image ใช้เมมเยอะ พอมันบวม มันก็จะ
Overmem แล้วก็พังไปได้

สิ่งที่น่าสนใจคือ AI Sec Ops
