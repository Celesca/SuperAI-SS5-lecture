## LLM

* Base model - ยังไม่ได้เทรนด์ เหมาะกับ Large datasets




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

Batch Size ประมาณ 1000 ขึ้นไป ของ Pretrained แต่ถ้า Fine-tune อาจจะน้อยกว่านั้น

Gradient Accumulation - เวลาเทรนด์ เราจะไม่ได้บวกเลยทันที แต่เราจะเทรนด์ต่อแล้วบวกกัน มันก็จะเท่ากับการ Train หลายๆรอบ ตัวใหญ่บวกกัน

