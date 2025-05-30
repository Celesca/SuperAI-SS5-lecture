## LLM Training Hands-on by พี่นิว (Thinking Machines)

* Base model - ยังไม่ได้เทรนด์ เหมาะกับ Large datasets
* Instruct model - เทรนด์แล้ว เหมาะกับ Small datasets

300 - 1,000 Rows:
Instruct or Base
1,000+ Rows: Base 

เขาไปดูอัลกอริทึมใหม่ของการ์ดจอ มันเลยเปลี่ยนวิธีคูณในการ์ดจอพวก Nvidia H100 แต่ตัวเลขเหมือนเดิม แต่รันแล้วมันเร็วขึ้นมาก เวลาเราใช้กับการ Hack 

วิธีการทำ Multi-GPU

![image](https://github.com/user-attachments/assets/4bff4247-f569-4d1c-b150-6e77e7d4fb88)


ทำ Data Paralleling และ Sharding

* Zero Sharding DeepSpeed Zero Optimizer - โยนไปไม่ให้เหมือนกัน วิธีนี้แทบไม่ส่งผลเลย 
ปกติเราจะใช้ Stage 2 ในการเทรนด์กัน แต่ถ้าหาก CUDA Out of Memory ให้เลื่อนไปหา Stage 3

ถ้าเทรนด์โมเดลใหญ่จริงๆ แล้ว Resource ไม่พอให้ไปใช้ Special Mode Offload แทน

* Pipeline Parallelism

แทนที่จะ Auto ทุกอย่าง ซึ่งเราจะสามารถโหลด Weight ล่วงหน้าก่อนที่ Data จะไหลมมาโดยใช้เทคนิค Scheduling ตัวเปเปอร์คือ G-Pipe
Pipeline Parallelism 

* Tensor Parallelism - เขาปรับ Transformer Architecture ใหม่ ปรับ Attention ใหม่
Megatron-LM ของ Nvidia ที่เขาทำขึ้นมา

* What to adjust when training LLM จะต้องปรับ Batch Size, Learning Rate

ถ้าคุณเพิ่ม batch size ก็ต้องเพิ่ม learning rate ตามด้วย

2. Batch Size ประมาณ 1000 ขึ้นไป ของ Pretrained แต่ถ้า Fine-tune อาจจะน้อยกว่านั้น

Gradient Accumulation - เวลาเทรนด์ เราจะไม่ได้บวกเลยทันที แต่เราจะเทรนด์ต่อแล้วบวกกัน มันก็จะเท่ากับการ Train หลายๆรอบ ตัวใหญ่บวกกัน
แล้วก็ไปสเกลบวกลบให้เท่ากัน

3. Sequence Length - ยาวแค่ไหน เราจะต้องเอา Tokenizer ไปตัด แล้วกิน Token ได้แค่ไหน เช่น 10 Tokens, 100 Tokens
เราก็ควรจะเซ็ตให้น้อยๆ นอกจากจะทำให้เทรนด์ช้าลงแล้วก็จะน้อย มันไปอัพเดท weight โมเดลใหญ่ที่ไหนบ้าง

เวลาเราเอาไปเทรนด์
1. <Hello> <we> <are> <superai>
2. <Hello> <we> <are> <superai>
3. <Hello> <we> <are> <superai> <Hello> <we> <are> <superai>

คือ 1,2 มันจะทำ Padding Token ให้เต็มเหมือนกับ 3. ถ้าเซ็ตเยอะไป ก็ Tag เยอะเกิน แต่ถ้าน้อยไป มันจะตัดคำบางคำออก

EDA - ใช้กี่ Tokens ถ้ามันมีหลุดๆมาบ้าง เราก็อาจจะตัดคำนั้นทิ้งเลยก็ได้ แล้ว Example มันใช้เท่าไหร่ ก็ลองไปดูบ้าง

## Hands-on Fine-tuning

* Llama-Factory -> เอาไว้

Reward Modeling -> พวก GRPO

AG News -> Datasets

* Steps 1 :

ml Mamba
conda env list
conda activate myenv

pip install -e ".[torch, metrics]"

pip install -U "huggingface_hub[cli]"

![image](https://github.com/user-attachments/assets/44b0203b-f850-4dda-9945-92a5ad0d4b27)

เลือก Template ได้
ตัว Example
train_lora -> llama_3_lora_sft_ds3.yaml เราจะเซ็ต deepspeed หรือ stage ที่เราอยากเทรนด์

Stage: sft, finetune: lora, lora_rank 8 ฉะนั้นมันอยากที่จะแบ่งตัว Optimizer ได้ มันจะแบ่งตัว Gradient กับ Weight ได้
ds_z2_config.json

แล้วก็ Dataset
dataset: Train_alpaca

ปกติเราจะใช้แค่ train กับ export

ในการที่เราทำ LoRA เราควร Merge Adapter ตัวหลักเข้ากับ Model weight ก่อน เพราะว่าเราไปเทรนด์ Low-rank adaption แทน

export LD_LIBRARY_PATH = /project/ai901506-ai25tn/cache

1 Node - มี 4 ใบ ถ้าเซ็ตเกินไป มันอาจจะกิน Resource เยอะเกิน

![image](https://github.com/user-attachments/assets/149c2306-61d0-45cf-baf7-26ec6556c35a)

Apply Chat Template ให้เรียบร้อยแล้ว แต่ว่าเราจะมีส่วนที่เรียกว่า

## Reasoning Model - พวก ChatGPT, Gemini มันก็จะกด Think มาก่อนแล้วค่อยตอบ

วิธี Fine-tune Reasioning ก็คือมันจะอยู่ใน Reasoning อยู่ใน input เลย มันหาค่อนข้างยากมาก Scale รอบสาม เพื่อทำให้ Reasoning มันเก่งขึ้นอีก

เทคนิค GRPO โดยสีแดงเป็น input และสีฟ้าเป็น output

การที่จะทำให้โมเดลมันเป็น Reasoning เราจะต้องเขียนพร้อมพ์ลงไป ก่อนจะตอบช่วยคิดไว้ แล้วก็ใส่ Bracket ที่ชื่อว่า Think แล้วใส่ target ไว้ใน Answer
มัน Think แล้วตอบ มันอาจจะไม่ได้ออกมาเป็น answer ที่เราต้องการรวมกับคนอื่นได้

ตรงกลางการกระทำ ไม่รู้จะทำยังไง แต่บอกได้ว่าตอนจบมันต้องเป็นแบบนี้ แล้วก็บอกให้มันเป็น Think เองตรงกลาง

การเซ็ต Reward Model สำคัญมาก ไม่งั้นโมเดลมันจะไม่ Learn Reward ง่ายสุดคือการเช็คคำตอบจากการ Generated มา โมเดลมันไม่คิดเลยแล้วพ่นคำตอบออกมา
อยากให้โมเดลมันปิด Tag ถูกป่าว แล้วใส่ Answer ออกมาเป็นการเซ็ต Reward

## GRPO - การทำงานลงยังไง

อย่าลง maths ใน RL - ใส่เข้าไปใน LLM พอได้คำตอบหลายรอบ เราก็จะเอาไปเทรนด์ตัว LLM ของเรา

LoRA พยายามหาความสัมพันธ์ของ Vector -> ซึ่งมันมีความสัมพันธ์ได้ว่า
เหมือนเขาจะเทรนด์เฉพาะคอลัมน์ที่มีความสัมพันธ์กัน ซึ่งเขาเรียกว่า RANK=1

เขาพยายามตามหาความสัมพันธ์ 2 ก็พยายามหาสองความสัมพันธ์ใหญ่ๆ จาก Decomposition จะทำให้เหลือจาก 3x3 = 3x1 + 1x3
เราลองไปหาดีเทล มันพยายาม Decomposite ให้กลายเป็น Matrix A and B

## TRL - การทำ Inference

เวลาที่เรารัน generate huggingface มันไม่ได้ถูก optimize มาสำหรับการ generate แต่มันจะใช้ตัว vLLM Mode เขา optimize กระบวนการ attention ข้างใน แล้วทำเป็น API ได้ด้วย

Lanta เยอะ อีก Nodes เอาไว้เซ็ตอัพ Lanta แล้วก็อีกโหนด Train Nodes ค่อยมาคิด reward แล้วพอเทรนด์เสร็จอัพเดทลง vllms อยู่กับดาต้าจริง ซึ่งโค้ดที่จะแจกมันเซ็ตอัพ
เพราะโดยปกติเราจะรันเป็นฐานสอง ซึ่งแถม 1 node เข้ามา เช่น จะเทรนด์ 14 โหนด แล้วมีอีก 1 โหนด ทำ inference
