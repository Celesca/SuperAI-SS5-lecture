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

