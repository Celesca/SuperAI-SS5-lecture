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

Prompt Engineering vs Fine-tuning

Fine-tuning ใช้เวลานาน

บางบ้านใช้ GRPO

## Reasoning Model

ใช้ Base Model (V3) ตอบคำถามได้ ทำให้เป็น Emergent

R1-Zero: มันถูกเทรนด์ด้วย Reinforcement Learning ให้คิดเอง (RL) สิ่งที่มันจะยากคือ Accuracy

* Prompting Reasoning models provided

o3, o4 คุณต้องคิดว่ามันเป็น Senior co-worker มันคิดเองได้ ไว้ใจมัน นอกเหนือจาก Junior co-worker เช่น o1
คุรจะเขียนเป็นเป้าหมาย Don't write prompts: write briefs. Take the wheel and feel the AGI

## AI agents (Tool Use)

Agentic กับ Tool Use เราสามารถให้โมเดลมันสามารถเรียกใช้ฟังก์ชันได้ 

อีกอันที่นิยมคือการให้ Agent ติดต่อกับ Database ได้ เช่น Maintain dictionary

## Agentic LLM (2025 Agentic Year)

* Building effective agents - Blog post ที่จะสร้าง คุณจะต้องแยกให้ออกว่าอันไหนคือ agent หรือไม่ใช่ agent

* Workflows vs. Agents

Building block: The augmented LLM

Sequencial Workflows

1. Workflow: Prompt chaining

![image](https://github.com/user-attachments/assets/2f8ef0e8-0067-48fb-a640-06046e841d35)

มีการดราฟ Outline เป็น Workflows แบบง่าย ๆ 

2. Workflow: Routing

เป็นตัวที่แยก Prompt ไป ระหว่างคำถามง่ายกับยาก คำถามไหนง่ายก็ไปใช้โมเดลเล็กตอบ แต่ถ้าคำสั่งไหน Complex ก็จะส่งไปตัวใหญ่หน่อย
อันไหนง่ายก็ต่อ Haiku ตัวกลางก็ Sonnet

3. Workflow: Parallelization

4. Workflow: Orchestrator-workers

เอาแต่ละงานมารวมกัน อาจจะแบ่งงานได้หลายแบบ มันเป็นแบบ Clear workflows ไม่ได้ติดลูปอะไร

5. Workflow: Evaluator-optimizer

จนกว่าจะตอบถูกและพอใจ  LLM Call Evaluator, Generator

![image](https://github.com/user-attachments/assets/8911c269-a2c4-4e66-bfa5-cb7b8cd9117b)

ให้เราเชื่อใจมันให้มันติดลูปมันเอง

