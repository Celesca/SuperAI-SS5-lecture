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

## Convolutional Neural Network

* CNN จริงๆมันเป็น Operation นึงใน Maths แต่มันใช้ Cost
Signal มันคือการกลับข้าง จับ up down แล้ว implement

ถ้าเรียน AI เขาไม่ค่อยสน Pure math แต่มันเป็น Universal Language

![image](https://github.com/user-attachments/assets/f162a09b-0b16-42d2-8962-a303174b1584)

ตระกูล Pooling ทำให้ Deeper ใหญ่ขึ้น แต่ว่าไม่มี Parameters

Diff Max pooling อันไหนไม่ได้เอา เส้นที่ไม่เอาก็เป็น 0 แต่ถ้า Average pooling ก็จับเท่ากัน ถึงแม้จะ Diff ตรงๆ ไม่ได้ แต่ก็หา Backpropagation

Cost Correlation - เขาไม่ค่อยเรียกกัน ดังนั้นมันก็เลยชื่อ Convolutional Neural Network

![image](https://github.com/user-attachments/assets/37214459-f758-49b8-b2fa-b8f7da2f93ba)

มัน Pure Convolution Network สนใจเฉพาะ Convolution เขาเชื่อในความสวยงามของ CNN ก็คือไม่มี Flatten

![image](https://github.com/user-attachments/assets/f167de59-0aaf-44d2-a4ba-8c375a8a7188)

![image](https://github.com/user-attachments/assets/88e987be-54d1-4384-ad28-100967a9be14)

Convolutional vs Fully Connected

![image](https://github.com/user-attachments/assets/dde7b4c2-cb32-45d2-91da-d0d508df312e)

ถ้าเราเทรนด์มิติพอ ก็คือมันไม่ได้ลากเส้น 15 เส้น แต่มันทำ 9 เส้น โดยที่เราใช้ Kernel = 3 
หมายถึง Output 1 ตัวรับ 3 ตัวที่ใกล้ๆกัน แล้วก็ให้ตัวนึงเป็น Filter อันนึง มันจะแชร์ Weights กัน

ทำให้ CNN มันปรับง่ายขึ้นเพราะ

1. มีเส้นให้ปรับน้อยลง (คล้ายกับการขับเครื่องบินมีอะไรให้ปรับเยอะ มันก็ยิ่งยาก)
2. เส้นไหนอยากแชร์ Weights ก็ให้ชี้ไป Memory เดียวกัน มันเป็น Neural Network ที่ง่ายลงกว่าเดิม

![image](https://github.com/user-attachments/assets/0ee26885-ca18-4dab-9e02-73f505671d8d)

Autoencoder เป็น UNsupervised Input เป็นรูป Output เป็นรูประบายสี เช่นเป็น Segmentation ระบายสี

ResNet Inspired ระบบประสาท มัน Filter ข้อมูลที่หาย มันก็จะยิง ข้อมูลที่หายกลับมาด้วย แล้วก็เอา Segment รวม Script Connection

![image](https://github.com/user-attachments/assets/5dedd12e-cae8-4162-8c6a-0cc9e556b116)

U-Net มันเป็นส่วนสำคัญของพวกรูป เช่น Stable Diffusion

ResNet ที่มี Script Concatenation ถ้ามันไม่มี ข้อมูลมันก็จะหายไป เราก็เลย

![image](https://github.com/user-attachments/assets/ce64dc91-614b-409d-8671-16b31c03cb04)

ตัวนึงเอาไว้สร้างของเลียนแบบ อีกตัวนึงเอาไว้จับผิด จริงๆ มันสร้างได้จาก Autoencoder แล้ว

Super Resolution (SRGAN) - กู้คืนภาพ

![image](https://github.com/user-attachments/assets/4bb40624-fefe-4dda-af03-606aecf03e92)

เรากู้คืนข้อมูลไม่ได้จริง ซึ่งของในรูปเรามันมีความเหมือนกันอยู่แล้ว Integrate แล้วกำหนดให้รูปที่เกิดมาใหม่

Training อยู่ที่การขยายรูปได้ 4 เท่า

## VAE (Variational Autoencoder)

* Autoencoder

![image](https://github.com/user-attachments/assets/23b8b17f-d974-4c3c-ad69-1aa5c4786d34)

![image](https://github.com/user-attachments/assets/b1c24105-3270-459a-8d60-164fafe28d97)

พบว่าแต่ละ Row มันจะไม่ซ้ำกันเลย 8 อัน จริงๆมันคือ Binary Code แต่มันไม่เรียง ซึ่งมันเป็น Blackbox จาก 8 เหลือ 3 มิติ

Limitation of Autoencoder เป็น Unsupervised สมมติว่านี่คือ Latent space ที่เป็นมิติตรงกลาง พอเรามาพล็อตเป็นจุด

อาจจะเป็น 100 มิติ เราก็จะใช้ 1024 มิติ แต่ว่ารอบนี้มันวาดเป็น 1024 ไม่ได้ พอเราไปพล็อตดูมิตินี้ควรจะเป็นยังไง มันก็จะกองๆ อยู่ตรงนี้
ซึ่งมันทำได้ ปัญหาคือ Space ที่ดีพอ เส้นนี้มันจะต้อง Represent การ Transform ถ้าผมเดินตามเส้นนี้ มันควรจะค่อยๆ เปลี่ยนจาก 5 เป็น 0
เราแค่อยากได้จุดที่จุดบน Space ให้มันมีความหมาย เพราะผมอยากทำ Generative AI แล้วเจนอะไรก็ได้ มันถึงต้องทำเป็น Continuous
เราต้องมี Meaningful all spaces

เพราะเราอยากให้ทุกอนูของ Latent space มีความหมาย ถ้าผมจิ้มไปตรงนี้มันควรมีความหมาย อาจออกมาเป็นเลข 8 ก็ได้

![image](https://github.com/user-attachments/assets/d3b4fc03-5f3e-41fc-97bc-cf46be5f48eb)

ฉะนั้นเราจะเปลี่ยน Sigma ที่เป็นผลรวม (Discrete) ให้กลายเป็น Integrate แทน (Continuous)

ให้เราจินตนาการถึง Props stats พวกระฆังคว่ำc เราก็จะ Props และคูณด้วยค่า x แล้วบวกมันตั้้งแต่ -ตี้ ถึง อนันต์

![image](https://github.com/user-attachments/assets/213c9548-8d54-4172-9366-fa226cc70dec)

มันจึงเป็นที่มาของสิ่งนี้ ให้มันเกิด Meaning ทั้งหมดใน Space ผมจิ้มไปจุดไหนก็ต้องมี Meaning (Variational Autoencoder)

![image](https://github.com/user-attachments/assets/395d3bdc-5bb7-41e3-8921-9004b084a6a5)

เราจะเปลี่ยนจาก Deterministics -> มันคาดการณ์ได้ มันรู้ค่าได้ แต่เราไม่เอา เราจะเปลี่ยนเป็น Stochastics มันคือ Random แบบไม่รู้ค่า

แล้วเราเปลี่ยน Encoder แทนที่จะ Predicted Z ที่เป็น Latent Space ให้เป็น Predicted เป็น Distribution การกระจายตัวของ Data แล้วก็ไป Decode Z แบบนี้

ที่ไปที่มาของ Loss ค่อนข้างยาก Log likelihood ก็จะเป็น Bianry cross entropy จากการพิสูจน์หนักหน่วง เราพบว่า Reconstruction loss คือ loss ของ encoder เดิม จะเป็น MSE ได้
แล้วบวกกับสิ่งใหม่คือ KL Divergence ยาวไปถึง Stable Diffusion โดยหน้าที่ Loss KL Divergence

Reconstruction loss -> ทำให้ x' output มีค่าเหมือนๆกับ x ที่สุด 

KL Divergence loss -> เป็นการหาความต่างของ distribution ซึ่งอันไหนไม่รู้ Force ให้มันกลายเป็น Normal distribution พยายามให้มันเป็นการกระจายตัว Normal distribution

สมมติเราหยิบมาสักตัวนึง ก็จะได้ Prob ของค่านั้น

เราต้องใช้ Backpropagation ซึ่งมันเป็น Deterministics ค่ามัธยฐานมันดิฟไม่ได้ เพราะเราอยากได้ Continuous เราพยายามทำ ส่วนที่ดิฟไม่ได้ออกไปจาก Backpropogation

![image](https://github.com/user-attachments/assets/d91da27d-84b5-4f08-92dc-f596d2e81661)

พอมัน Backprop ไปเจอ z ซึ่งมัน Diff ไม่ได้กลับไปไม่ได้ จบข่าวมันก็คงเลิกทำ แต่นักคณิตศาสตร์บอกว่า เราก็เอา Stochastics ออกมาจาก Process ให้ได้ เช่น สมมติเจอสัญลักษณ์ N (Normal Distribution)
เป็น Gaussian Curves เส้นโค้งปกติ มันสามารถเขียนได้อยู่สองแบบก็คือ

x ~ N( u, sigma) ช้างบนมันใส่ค่าเท่ากับไม่ได้ ก็คือ x มันสุ่มมาจาก Normal Distribution

N(x; u, sigma) = q

เราจะต้องเปลี่ยนตัวนี้ให้กลายเป็น Algebra พีชคณิตธรรมดา
z~N(u, sigma) ให้กลายเป็น z = u + epsilon (sigma)

ถ้าหาก epsilon เป็น 2 ก็จะสุ่มมาทางขวา มันทำให้เราได้ z ทุกตัวที่อยู่บน Normal Curve โดยการเปลี่ยนสมการ เป็น

Reparameterization trick

![image](https://github.com/user-attachments/assets/bb173fb2-1a94-4daa-a189-0cd5ca180579)

แล้วพอเราไป Build graph เป็น Back propagation z มันเกิดจาก u + epsilon (sigma) แต่มันเหลือแค่ Epsilon เป็น Stochastics แล้วส่วนอื่นเป็น Deterministics
มันสามารถแตกไปที่ มันไม่สามารถ Backpropagation Epsilon ได้ มันเป็นหลักการ Generative Neural Network เช่น Stable Diffusion

ยังคงมี Gradient ตรงกับไปปรับ Weight ได้ มันไม่สนใจตัว Epsilon



