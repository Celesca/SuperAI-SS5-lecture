# Introduction to Deep Learning (Theory)

ถ้าเราใช้ Distance บาง Task อาจจะไม่เหมาะสม เช่น Iris Dataset ก็จะต้องวัดพวกดอกก่อน

แต่ถ้าหาก Convolution เราจะต้องเปลี่ยนเป็น Fix Vector ยกตัวอย่างเช่น Word Embedding

![image](https://github.com/user-attachments/assets/e6d1e051-f071-4c82-b7f7-f1c61f4f37eb)

Knowledge Based - Loss function ทำให้เกิด Language Model ขึ้นมา

สมัยนี้เราตัด Sentence Pieces เขาจะดูอักขระไหนที่ติดกันบ่อยๆ โดยไม่สนใจการเว้นวรรค อะไรที่อยู่ด้วยกันบ่อยๆ ซึ่งจะต้องดูบริบทข้างเคียงเสมอ ขอแค่ตัดตรงกัน

จริงๆใครทำ RAG เราใช้ 4-byte context window อาจจะใช้ประตูบานเดียวกันก็ได้ แต่ถ้าไม่มีก็ไม่เป็นไร

![image](https://github.com/user-attachments/assets/9ef18ae2-9fe2-42ee-b88d-f56c6189c68f)

Encoder - มันจะลดมิติ (ซึ่งจริงๆจะแปลงให้ใหญ่ก็ได้) แต่ส่วนใหญ่มันจะเล็กลง

![image](https://github.com/user-attachments/assets/8ad7adfe-6282-4957-b4e9-f1fc05cfdf36)

![image](https://github.com/user-attachments/assets/53405f9d-c3b3-4966-af55-4543f6e8e5a5)

เป็นอะไรที่เราชอบแปลงมันเล็กๆ เพราะว่ามันทำให้มันคล้ายกันมากขึ้น เช่นรูปเลข 1

![image](https://github.com/user-attachments/assets/1b836c09-eb7c-4881-a259-2be88fbbdb9e)

สมัยปัจจุบันนี้ การตัด token ที่แม่นยำ ยังมีผลต่อการทำงานต่อไปไหมครับ - ถ้าเราใช้ Fix Vector เราทำเป็น Vector เปลี่ยนรูปตลอด แต่ถ้ามาคำเดียวเลยจะมีปัญหาแน่นอน เช่น คำว่าตากลม

## เครื่องประมาณค่าแห่งจักรวาล Neural Network

![image](https://github.com/user-attachments/assets/ba3e407a-60c2-4331-bd8e-2c0b23703b39)

มันเวิร์คในทั่วไป เราก็ยังใช้ Backpropagation แบบปกติในสมัยนี้ เพราะว่ามันเป็น Generalized ใช้ได้ทุกอัน

ยุคนั้น CNN ยังไม่บูม เพราะว่า Computational ยังไม่พอ แต่ SVM 1992 ก็ได้ Citation paper เยอะ เช่น SVC, SVR

2012 : AlexNet จุดกำเนิดการเล่นเกม GPU GeForce 2 ใบรันขนานกัน

2015 : AlphaGO ตอนแรกเป็น Neural Network ไม่ใช่ Reinforcement Learning

2017 : Google พยายามจะจด Transformers นี่ตายเลย สมัยนี้ Based-on Transformer หมด

2022 : ChatGPT , Stable Diffusion โดยที่ Stable Diffusion เข้าใจเพราะ Maths มันเยอะกว่า Transformer 

* Feature Extractor แล้วทำให้มันใหญ่ขึ้น มันมีผลกับบางกรณีที่ทำแล้วดีขึ้น (โดยปกติคือมันสุ่มเลขมั่วๆขึ้นมาในอีกมิติหรือเปล่า)

## Artificial Neural Network

* Activation

มันไม่ Continuous ทำให้มัน Diff ไม่ได้ ทำให้ค่าอนันต์ เปลี่ยนแปลงฉับพลัน ดิฟค่าออกมาไม่ได้

![image](https://github.com/user-attachments/assets/cfcac4e5-e610-4cc6-b8fc-1df90aff3b81)

![image](https://github.com/user-attachments/assets/3f88d36f-63f6-4c3b-ab4b-f56d48d8bdac)

Hyperplane จะมี Normal Vector ตั้งฉากเสมอ ไม่ว่ามันจะหมุนไปทางไหนก็ตามซึ่งรูปนี้เป็น ปริภูมิ 2 มิติ เราจะตั้งชื่อนี้ว่า w โดยเราไม่สนใจเส้นนี้

Normal vector represents hyperplane ฉะนั้น เราจะ Random Normal vector ขึ้นมา 1 ตัว ส่วนใหญ่เราไม่รู้ Scale Data

ไอ้ตัวที่ทำมุมป้านพอดี ตัวปัญหา เวกเตอร์สีฟ้าทำมุมแหลมขึ้นมารึยัง

![image](https://github.com/user-attachments/assets/b536434b-953d-4da4-a48e-5808a5112db4)

โดยปกติมันมาจากสมการแต่ถ้าเรามองในมุมของ Vector ก็จะทำ Classification ได้ดังนี้

* How to find the optimal weights

![image](https://github.com/user-attachments/assets/1b38b7ed-ba50-455b-93f8-008104fa40c4

จุดต่ำสุดสมบูรณ์ของกราฟ Loss function โดยกราฟนี้ หาจุดต่ำสุดโคตรง่าย เพราะเราจับ Slope = 0 เราลากผ่านจุดจะได้เส้นแนวนอนเสมอ

แต่ในความเป็นจริง Neural Networks สมการที่แท้จริงของ Loss function คือมันใช้ Distance แต่ว่าถ้าเราอยากใช้ MSE
x ทุกตัว มันเปลี่ยนไปเรื่อย ๆ มันเหมือนเป็นหมอก Continuous เพราะนั้นในความเป็นจริง มันยุ่งกว่าเส้นประอีก ฉะนั้น

อย่าไปหวังเลยว่ามัน Global local เพราะว่าเราไม่มี data ในทุก ๆ ปัญหา

![image](https://github.com/user-attachments/assets/ad7d76b9-aa84-4025-90ab-87d556230d16)

Aggregration - บวก หรือเทค action นึงมาทำ

![image](https://github.com/user-attachments/assets/7a89057e-b2cd-4170-8a65-e6a3d5adfb80)

1 Epoch มันจะยัด Data เข้าไปทีเดียว แต่ว่า

![image](https://github.com/user-attachments/assets/10ae11b9-6dd4-4b50-9ae2-95db94d503c8)

มันจะ Random จิ้มค่าลงเหว Global minimum พอดี

![image](https://github.com/user-attachments/assets/ff94bcc7-20ee-4dc3-ba54-c12e922da4dd)

เราจำเป็นต้องใช้ Perceptron (MLP) มากกว่า 1 ชั้น

![image](https://github.com/user-attachments/assets/4563730c-1859-4950-aaf8-0d6f1fc0b4e5)

ถ้าเรามองมันคือ Feature Space นึงไปอันนึง

โดยปัญหาตัวนี้มันลากเส้นเดียวไม่ได้เลย 

![image](https://github.com/user-attachments/assets/af78e133-7499-4ac5-b080-1da31653d397)

มันจะ Simplify ให้เข้า Feature Space ใหม่เรื่อย ๆ และเป็น HyperSpace โค้งๆได้

![image](https://github.com/user-attachments/assets/78d4a3a1-15eb-473d-95ea-fafad9e7fabf)

แต่ปัญหา Weights ไม่เปลี่ยน เหตุผลเพราะมันมีค่าน้อยเกินไปก็จะเกิด Vanishing Gradient ปกติซ้อนกันเป็น 100 เพราะ Double point มันหายไป

* มันไม่ใช่การพับแต่มันเป็นเปลี่ยน Feature Space มันสร้างมิติใหม่เรื่อยๆ จนกว่าจะได้ Linear อยู่คนละจักรวาล





