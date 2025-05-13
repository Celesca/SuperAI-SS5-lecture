## BERTs Game

ตระกูล BERT -> นิยมเอาทำ Embeddings พวก Encoder-only

BERT รับได้แค่ 512 Tokens 

มี Start token มีตัวแรก เราสามารถใช้ตัวเดียวเพื่อ Represent ทั้งประโยค

ตัว BERT จะใช้ Start token <cls> (Represent Token) เพื่อที่จะ Represent ทั้งประโยคดึงมาเฉพาะตัวหน้า

ตัวที่ทำให้คำคำนึงต่างกันคือ บริบท Context (เช่นฉันกินแอปเปิ้ล กับ ซื้อ ipad จาก apple)
และนับจาก Cosine Similarity เพื่อวัดความใกล้เคียงเช่น องศา


