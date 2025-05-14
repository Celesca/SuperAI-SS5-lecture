# LLMs

## Recap LLM

Temperature -> 0.5 มันจะสุ่มกลางๆ แต่ถ้า 1 สุ่มหมดเลย ในขณะที่ 0 คือตรงตัวสุด most probable

Top-K is the "hard cut off" เช่น k = 5 ถ้าหากมี 14 tokens เราจะสุ่มแค่ top 5 ของ tokens แพ็คนั้นเท่านั้น

Top P is = 1 คือเอาทุกตัว, 0.5 เอาจนกว่า probability จะมากกว่า 0.5 และ Top-P 0.01 คือ

Top-P คือเอา Token มารวมทุกตัวแล้วไม่เกินไหน

* Token Probability and Parameters

![image](https://github.com/user-attachments/assets/ee4303c7-0561-40ea-b927-2f3d058cc4c3)

* ตัว Sampling ให้โมเดลมัน Creative

เราอาจจะทำ Dynamic Sampling และพอ Temp เยอะขึ้น Creative เยอะขึ้น Accuracy ก็จะต่ำลง

* หากมีปัญหา อย่าพึ่งไป Tune parameter แต่ไปปรับที่ Prompt ก่อน

* Example settings from DeepSeek R1 (โดยเฉพาะโมเดลที่เป็น Reasoning - เราจะต้องเซ็ต temperature ไว้สูงหน่อย เพราะต้องการให้มันคิด อยู่ประมาณ 0.6-0.7)
แต่ถ้าเป็นโมเดลปกติให้เซ็ต Temperature = 0.0 ดีกว่าเพื่อเป็น Baseline ในการคิด

## Prompt Engineering

