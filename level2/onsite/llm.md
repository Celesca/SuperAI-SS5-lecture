## BERTs Game

ตระกูล BERT -> นิยมเอาทำ Embeddings พวก Encoder-only

BERT รับได้แค่ 512 Tokens 

มี Start token มีตัวแรก เราสามารถใช้ตัวเดียวเพื่อ Represent ทั้งประโยค

ตัว BERT จะใช้ Start token <cls> (Represent Token) เพื่อที่จะ Represent ทั้งประโยคดึงมาเฉพาะตัวหน้า

ตัวที่ทำให้คำคำนึงต่างกันคือ บริบท Context (เช่นฉันกินแอปเปิ้ล กับ ซื้อ ipad จาก apple)
และนับจาก Cosine Similarity เพื่อวัดความใกล้เคียงเช่น องศา

## LLMs

5 แสน - Pathumma

* Mixture-of-Experts (MoE) -> หลายหัวดีกว่าหัวเดียว - เอาตัวเล็กๆหลายๆตัว มาช่วยในการตอบ ฉะนั้นของจริงจะโหลดแค่ 1-2 ตัว ตัวที่เหลือจะอยู่ใน Memory
เอาตัวที่จะตอบมาอยู่ใน GPU โดย ตัว DeepSeek ใช้วิธีนี้จึงใช้และเคลมน้อยกว่า ตัว Llama4-Scout, Maverick

* Temperature - เปอร์เซ็นต์ความหัวร้อน ตอบนิ่งๆ ยิ่งค่าน้อย แต่ถ้า Temp เยอะ หัวร้อนมีความคิดสร้างสรรค์บางทีก็เพ้อเจ้อ แต่ละโมเดลใช้ Temp ไม่เท่ากัน
เวลาตอบต้องใส่ Temperature เหมือนเดิมเลย

* Knowledge Distillation - เอาตัวใหญ่มาสอนตัวเล็ก บางทีตัวใหญ่เรารันไม่ได้ เราก็เอามันมาสอนตัวเล็ก หรือเวลาทำ Synthetic data

## More words for LLM

* Bias and Fairness - LLM ที่ bias มีแต่ผลเสีย เช่น ใช้ LLM ในการคัดเลือกสมัครเข้างาน ถ้า LLM เลือกแต่คนหน้าสวยหล่อก็จะเลือก

* Explainability - การอธิบายได้ ต้องคิดก่อนตอบเช่น Chain-of-Thought Prompting, Reasoning - Typhoon, OpenThaiGPT, DeepSeekR1 มันจะคิดก่อนตอบ

* Few-shot, Chain of Thought -

## Inference Tools

n8n, OpenRouter.ai, LLama.cpp, vllm, 

## LLM News

* RAG - เหมือนห้องหนังสือ หยิบหนังสือมาทีละเล่ม
* Hallucation - เหมือนมันตอบแบบมั่วๆ วิธีแก้คือใช้ RAG เข้ามาช่วย
* Agent - เป็น AI ที่ทำงานเฉพาะเจาะจงมากยิ่งกว่านั้น
* Agentic - มันยังเป็น Human in the loop เราเป็นคนตัดสินใจของการที่มัน Generate ให้ แต่ Agentic คือการให้มันทำงานกันเอง ตัดสินใจจากข้อมูลที่มันหามันมาได้
* Multi-Agent - 
* MCP - ทำยังไงให้โมเดลคุยกับ Protocol ต่างๆได้ง่ายขึ้น เราก็แค่ดึงเข้ามาวาง มันก็จะสามารถอ่าน Gmail, Calendar ได้หมด มันมีสิ่งที่เรียกว่า Trigger

สิ่งที่ทำพวกนี้ได้ก็คือ ตัวโปรแกรมที่ชื่อว่า n8n (Make) เป็น No-code ลากวางได้

* Tool vs Function

