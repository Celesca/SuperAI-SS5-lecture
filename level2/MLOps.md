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






