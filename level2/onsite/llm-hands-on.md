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
conda activate <>

pip install -U "huggingface_hub[cli]"

![image](https://github.com/user-attachments/assets/44b0203b-f850-4dda-9945-92a5ad0d4b27)

เลือก Template ได้

ตัว Example

train_lora -> llama_3_lora_sft_ds3.yaml เราจะเซ็ต deepspeed หรือ stage ที่เราอยากเทรนด์

Stage: sft, finetune: lora, lora_rank 8 ฉะนั้นมันอยากที่จะแบ่งตัว Optimizer ได้ มันจะแบ่งตัว Gradient กับ Weight ได้

ds_z2_config.json

แล้วก็ Dataset

dataset

dataset: Train_alpaca

ปกติเราจะใช้แค่ train กับ export

ในการที่เราทำ LoRA เราควร Merge Adapter ตัวหลักเข้ากับ Model weight ก่อน เพราะว่าเราไปเทรนด์ Low-rank adaption แทน

export LD_LIBRARY_PATH = /project/ai901506-ai25tn/cache

1 Node - มี 4 ใบ ถ้าเซ็ตเกินไป มันอาจจะกิน Resource เยอะเกิน
