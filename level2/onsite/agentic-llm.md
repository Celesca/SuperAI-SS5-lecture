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

prompt ให้ดีมันก็ไม่ได้ง่ายขนาดนั้น เราจะมาพูดให้ฟังเผื่อเป็นประโยชน์มาก เช่น Mindset ในการใช้กับ LLM ในปัจจุบัน
Prompt คือ Input (Context) ที่ใส่เข้าไปในโมเดล

LLM จะรู้แค่ Training data กับ Prompt เท่านั้น

Prompt Structure: API

System Prompt -> user & assistant

* Context Window -> Working memory จำนวน token ที่เราใส่เข้าไปได้ เช่น

Claude 3 has 200k ใช้จริงๆ ไม่เกินหมื่นหรอก ซึ่ง Prompt มีขนาดจำกัด เพราะสุดท้ายก็ไม่ได้ใช้ Window Context ทั้งหมด

* Prompt Engineering คือการ optimize your model LLM responses โดยการ Controlling model behavior พารามิเตอร์ของ LLM เราสามารถ Adjust เพื่อตอบโจทย์ของสัปดาห์นี้
เราจะต้อง Prompt

* Prompting Basic

Think of LLMs LLMs มันไม่รู้ถ้าหากเราไม่ Prompt
Be clear, precise, detailed, break down yuor task, provided samples

ภาษาอังกฤษเราไม่เก่ง เราต้องเช็ค Typo ไม่งั้นมันจะแปลกๆได้

* Break down your tasks

Unclear Prompt - Please remove all personally identifiable information from these customer feedback messages: {{feedback_data}}

Clear Prompt - Instructions: 1. Replace all customer 2. Replace emails เราต้องเซ็ตไว้เป็นลำดับ

* Provide examples - ให้ตัวอย่างคือ Few-shot (In-context) ไม่ให้ตัวอย่างก็ Zero-shot

Few-shot/multishot prompting or `in-context learning (ICL)`

Effective in instructing "style" of the text

* Crafting effective examples -

Instruction - ให้เคลียร์สอดคล้อง

Clear -> ใช้ tags ได้ Organized prompt (SML tags) <example> tags Input: The new dashboard, Category:, Sentiment: Negative, Priority 

Diverse -> หลากหลายให้มันครบทุกเคส Cover edge cases and potential challenges, and vary enough

* Use XML tags to structure your prompts ได้ delimiter

เพราะว่าโมเดลมันอ่านเป็นคำยาวๆ มันจะไม่เข้าใจว่าอันไหน Instruction หรือ

* Give the model time (space) to think

Chain-of-thought (CoT) -> ใช้สำหรับ complex like problem-solving research, analysis
Examples : 
- Drawback ใช้ Token เยอะ คิดนาน increase cost and latency

โมเดลสมัยใหม่มันถูกเทรนด์มาให้คิดเองอยู่แล้ว พวก Reasoning Model

* Give a role (Adopt a persona) - สมัยนี้ไม่ค่อยดีแล้ว

ต้องบอกว่ามันคือ "Act as the CFO"

DeepSeek R1 มันไม่ได้เทรนด์มาใน System Prompt แต่มันเอมาเทรนด์ใน Prompt





