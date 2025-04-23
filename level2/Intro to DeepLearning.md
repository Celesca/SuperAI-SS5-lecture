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

## Reparameterization trick

![image](https://github.com/user-attachments/assets/bb173fb2-1a94-4daa-a189-0cd5ca180579)

แล้วพอเราไป Build graph เป็น Back propagation z มันเกิดจาก u + epsilon (sigma) แต่มันเหลือแค่ Epsilon เป็น Stochastics แล้วส่วนอื่นเป็น Deterministics
มันสามารถแตกไปที่ มันไม่สามารถ Backpropagation Epsilon ได้ มันเป็นหลักการ Generative Neural Network เช่น Stable Diffusion ถ้าเข้าใจทั้งหมด

ยังคงมี Gradient ตรงกับไปปรับ Weight ได้ มันไม่สนใจตัว Epsilon คือมันสุ่มมาจาก Normal เหมือนเดิม ขอแค่กราฟไม่ขาด แต่มีอันที่ขาด เพราะมันเป็น Normal Distribution ของมันนึง

Normal distribution = normal + normal เหมือนเดิม

z คือตัว latent representation เช่น Stable diffusion everything is vector ทั้งหมดเลย เพราะเราเขียนบนฟอร์มของเวกเตอร์ ข้อดีของการทำ Tensor คือ Sparse Relations

แต่ก็แค่ลากทุกอย่างเป็น Vector ฉะนั้นทุกการ Flattening มันคือมิติของ Vector ฉะนั้น Stable Diffusion จริงๆจะปรับ Fully Connected ได้ แต่ว่ามันไม่ดี เพราะ ตัวที่ปรับเยอะเกินไป

ค่า Backpropagation ที่เรามี ของเราน้อยก็ยิ่งดี แต่ในอนาคต ทุกอย่างเป็น Vector ไม่ใช่ Spatial ทุกอย่างมันก็เป็นรูปแบบของกราฟอยู่ดี

## Kullback-Leibler (KL) Divergence

![image](https://github.com/user-attachments/assets/0d1f65c2-3f02-490f-95d7-a0194c766630)

การที่จะทำตัว Generative เส้นโค้งค่านึง

Information Theory -> ในเรื่องของ Entropy ของศาสตร์วิศวะไฟฟ้า ของเสาอากาศ มันก็จะติดเรื่องของ Log
เราต้องการหา Distribution ที่ต่างกันของ P(x) และ Q(x)

ซึ่งปกติมันคำนวณอยาก เราจะต้องเทค log e เข้าไป ชีวิตจะง่ายเพราะเทค log ก็จะสนแค่ด้านบน

แต่เนื่องจากมันเป็น Stochastics value - มีค่าเยอะไปหมดเลย เราเลยทำ Expectation operator (ค่าคาดหมาย)

Expectation = sigma x * p(x) หรือ Integrate x f(x) มันคือ Aggregation Method ตัวนึงที่เปลี่ยนให้กลายเป็น Scaler

มันก็คือ Prob คูณด้วยตัวที่จะหาโดยใช้ x ทุกตัว ที่มาของสูตร ถ้าลบแล้วมันเหลืออันเดียวก็ใช้ Extension ถ้าทำวิจัยเกี่ยวกับมัน จริงๆเรา import transformer ก็จบ

## Transformers

เนื่องจาก Stable Diffusion ต้องใช้ Transformers

Attention Mechanism - Query, key, value ให้นึกถึง Database

Key คือ index primary key เราจะต้อง Access มันคือตัวเลขของ Array และ value ต่อไป

เวลาเราค้นหา เราจะมี Query และอยู่บน Space เดียวกับ key แต่ไม่ต้องอยู่บน space ของ Value ก็ได้

จริงๆ เราวิ่งไปหา Indexing มันทำให้ Access ได้เร็ว มันรู้ว่าจะวิ่งไปตรงไหน แล้วมันก็จะ Return value ออกไป

สมมติเราเอา Indexing ออกหมดเลย เรียงกันหมด คุณจะต้องเคาะประตูทีละห้อง ซึ่งมันโคตรช้า แต่ถ้าเราติดชื่อเป็นเบอร์หมายเลข ก็ยากอีก เพราะว่ามันต้องรู้ว่าใครอยู่ ถ้าหากตารางหาย เราก็ต้องมานั่งเคาะเหมือนเดิม

จะเป็นไปได้ไหมที่ Data ตัวมันเองบอกชื่อตัวมันเอง เราจะเรียกมันว่า Hash table (ไม่มีใครสอน Transformers รวมกับ Hash table) เช่น

ถ้าสมมติเรา Hash Table สมชายแล้วติดหน้าห้องสมชาย หมายความว่าเราก็ถอดรหัสด้วย Hashing functions โดยที่ไม่ต้องเคาะห้องเลย ผมไม่จำเป็นต้องมีตาราง Maths เลย เพราะผมรู้ว่า ใช้ชื่อผม
แล้วเอา Hash functions มาตัวนึง ซึ่งมีปัญหามากมายแต่ ถ้าเราอยากได้ Hash functions ดีๆสักตัวนึง ถ้าคิดดีก็ดี แต่คิดไม่ดีก็ชนกัน

ยัดคนลงไปในห้องเดียวกัน มันก็ไม่เวิร์ค แล้วเราจะมี neural network ไว้ทำไม ฉะนั้น เราก็เลยใช้ Neural network คิด hash functions Fully connected ตัวนึงมาใช้ QKV ให้เลย

เจ๋งอะดิ

![image](https://github.com/user-attachments/assets/d6e8aa59-981d-4a9d-8d16-7e19b4f4e0e4)

คำว่า มันคนละความหมาย เราไม่ควร return เป็น Fix vector

สูตร attention คุยกันรู้เรื่อง Distance เราก็ต้องลบและถอดรากที่สอง แล้วถ้าเราต้องใช้ Cosine มันจะ Simplify ได้ไหม ก็คือ cos = a dot b ซึ่งมันก็คือ Cosine Similarity

Similarity function จะบอกความคล้ายเช่น

![image](https://github.com/user-attachments/assets/0d12cf19-78db-412d-b99f-2112c1b426e2)

แทนที่เราจะ return คำนึงหมดแบบนี้

![image](https://github.com/user-attachments/assets/50aef071-520f-4850-8eb5-44ae5497ac5c)

แต่เราจะให้ความเหมือนมาคูณ แล้วเอามาบวกกัน ก็จะได้ Vector ขนาดเท่าเดิม เป็น Extension

![image](https://github.com/user-attachments/assets/c2000862-c2c5-4f65-a4ad-385a8aab8b29)

Query, Key, Value เพื่อที่จะ Return Query 1 ออก 1 ก็จริง แต่ไอ 1 Vector นั้นมันเป็นองค์ประกอบของ Token list ทั้งหมดที่เรามีเลย โดยที่บอก 

ใน Paper ใช้ Scale Dot-Product

![image](https://github.com/user-attachments/assets/3345be35-ef86-4026-8062-6d4bd9807053)

ใส่ Softmax ให้เขาเปรียบเทียบกันได้ แล้วคูณออกมาเป็นแบบนี้

![image](https://github.com/user-attachments/assets/a288ab0a-e39d-453d-bdc4-1e7da63d3811)

สุดท้ายตำแหน่งของคำ

## Positional Encoding - ตำแหน่งข้อมูลลงไปด้วย

![image](https://github.com/user-attachments/assets/057fc53d-127c-4623-9856-2b30f002c15f)

เขาจะใช้ Sine กับ Cosine ในการเข้ารหัส เอาไปประกบเข้าด้วย

ก็คือเข้า x แล้วบวก PE แล้วไปทำ Fully connected Linear

![image](https://github.com/user-attachments/assets/986c5430-2b8c-4d78-8232-f92f056866ee)

Attention vector ตัวเดียวไม่พอ

เราเลยทำ Multi-head attention

![image](https://github.com/user-attachments/assets/5a86f051-8308-4598-a22e-2189c6e8deb6)

รวมจนพอใจ แล้วเข้า Concatenate เราก็จะไม่เหมือนกันิเลย

ปกติเรา Batch Normalization ได้ค่าเก็บไว้ เราก็ Normalize แนวนี้เลย

![image](https://github.com/user-attachments/assets/7d1bc34d-d147-4f05-9685-c6b4a0edcd31)

มาตัวเดียว Normalize ตัวเดียว

ก็มีคนไปใช้ใน Vision Transformers

## Vision Transformers

![image](https://github.com/user-attachments/assets/248eadf7-f99c-4bac-a385-5f0a67104d7d)

ทำยังไงให้กลายเป็นประโยค ถ้าเราเอา Pixel มันไม่มีความหมาย

ตัดแล้วเรียงกันยาวเป็น 1 Meaning 1 patch แล้วก็ทำทุกอย่างเหมือนเดิม

![image](https://github.com/user-attachments/assets/4334b6b7-42af-412f-bbc6-e2212f02631a)

ทำ positioning และ multi-head ธรรมดา

ViT เป็น Backbone ถ้ามันมา JFT Efficient Net อาจจะดีกว่าก็ได้

![image](https://github.com/user-attachments/assets/b2cd2cc4-7ded-47df-bcf8-d1abea9d01ee)

ถามว่าดี แต่ว่าเราต้องการ Data เยอะมากๆในการเทรนด์ ViT ถ้าหากข้อมูลไม่ได้เยอะ ก็จะใช้ CNN ไปก่อน

## Vision-language models

จุดพลิกผันมาอยู่ที่นี่ มันพบว่ามี Embedding layers ของ Text, Image มันคุยกันได้ไหม

![image](https://github.com/user-attachments/assets/b722c387-4766-4a4e-bfd0-e8e74137d984)

เขาเทรนด์คู่ Image-text คำอธิบายภาพ กับภาพ เอามาเทรนด์โดยการเทรนด์

Contrastive Learning -> เป็นวิธีการ Learn ที่ดีที่สุด คือการสนใจแค่ 2 คลาสคือ Positive คำอธิบายถูกคู่ and negative pairs คำอธิบายผิดคู่

เราก็สุ่มหยิบคู่ โดยที่ไม่ต้อง Label คือเป็น Supervised Learning ที่ไม่ต้อง Label ประโยชน์ของมันคือการทำ Zero-shot classification ได้

คือมันไม่เคยรู้จัก class นั้นมาก่อนเลย ไม่เคยรู้เกี่ยวกับคลาสนั้นมาก่อน

One-shot learning คือเรามี 1 ตัวอย่าง เช่น เรามีรูปเดียว Few-shot อาจจะมีรูปเขาสัก 5 รูป

![image](https://github.com/user-attachments/assets/94f30cc9-ed99-4370-be46-a8fa80d6ec7e)

ตระกูล Language model คือทำ Zero-shot ได้หมดเลย ก็คือเราให้ตัวอย่างกับมันแบบนี้ A photo of a {object} เป็นคลาสที่สนใจในงานนั้น รถยนต์หมานก ก็ไปเอาสิ่งนั้นมา
เอาคำที่เราสนใจแล้วไปเข้า Text Encoder เราก็จะได้แบบนี้มา

สมมติเรามี รูปนึง เราอยากรู้ว่างานที่เราทำ มันมีอะไรบ้าง โดยที่เราไม่เคยเอา Data ไปเทรนด์เลย เราต้องรู้ว่าเรามี Label อะไรบ้าง ยิงเข้า Image Encoder
ไปหา Similarity แล้วตัวไหนคล้ายสุด มันคือ dog มันก็จบ ทั้งๆที่มันไม่เคย Train มาก่อนด้วย Contrastive Learning ซึ่งมันรู้ว่ามีอะไรบ้าง

ดังนั้น Zero-shot มันค่อนข้างจะมีประโยชน์ สมมติเราเจอ Hackathon แต่ว่ามันมีในธรรมชาติ เราก็ทำได้เลย

## BLIP

![image](https://github.com/user-attachments/assets/f6f6de3c-b2dc-409d-b30c-5c68b2f86be8)

Image Captioning -> Image เป็นรูป output เป็น text

ในขณะที่ CLIP ออกมาเป็นตารางกับความสัมพันธ์ งานหลักของ CLIP คือ Zero-shot ซึ่งมันอาจจะเป็น Fully connected ก็ได้

แต่ถ้า BLIP คือการหา Image Captioning มันอาจจะเป็น สมัยนี้จะเป็น BLIP 2

คือ Q-Former

![image](https://github.com/user-attachments/assets/aa8cbc69-0d77-4e4f-831c-8a0c4df0ab95)

ความสัมพันธ์ Image-text ถ้าจะทำ BLIP ให้ข้ามไป blip 2 แล้วก็มี

![image](https://github.com/user-attachments/assets/dcbfafd6-aae8-4818-b444-25a6ef7414ae)

เอา Language model มาตัวนึงที่เป็น Frozen บางทีการเทรนด์มันเปลืองเงิน ถ้าหากเราเอา layer ที่ไม่เกี่ยวกับ LLM เราทำ Projection ไปคุยแล้ว Response กับมัน
การทำ Llava มันเก่งด้านการคุยกับรูป "ผู้ชายคนนี้ถืออะไรอยู่" มันจะดีกว่า Image Captioning

![image](https://github.com/user-attachments/assets/1bea82fc-8316-4dd9-a526-088f83dde4b7)

## Diffusion Model

![image](https://github.com/user-attachments/assets/4d3ed5f4-f69a-4501-9cf9-19ddd5bffe17)

=Diffusion หมายถึงการ แพร่

Neural Network ที่เรามีฟังเผินๆ เอารูปนึงใส่ Noise ไปทีละนิด จนกลายเป็น Pure Noise แบบ Normal Distribution แล้ว

เอาให้มันTrain กลับมาให้กลายเป็นรูป

มันคือการ Predicted Gaussian White-noise เฉยๆในทุก Step มันทำให้มันโฟกัส มัน Predict Noise ไม่ใช่เกิดขึ้นระหว่างสเต็ปเดียว

ซึ่งมันไม่ได้สนใจเราแค่ Predict Epsilon คล้ายกับ U-net เราก็ Control noise ด้วย Variance มันก็จะกลายเป็น Alpha, Beta

มันคือ Reparameterization trick คูณด้วย Epsilon มันคือตัวที่อยู่ใน Diffusion เสร็จแล้ว

![image](https://github.com/user-attachments/assets/62e735ba-0b50-4ae6-83ef-473daee0fb9d)

เขาอยากให้มันเทรนด์แบบกระโดดได้ มันก็จะพิสูจน์แบบนี้คือ p-1 ก็แทน p-2 ก็คือมันจะเปลี่ยน t แล้วก็ทำไปเรื่อย ๆ จนถึง x ที่ t ที่เกี่ยวกับสเต็ปสองสเต็ป เขาก็พิสูจน์ด้วยการ probability

mean ตัวนี้เป็น Random มาจาก Normal mean ก็เป็น 0 เหมือนกัน ถ้าเช็ค mean ถ้าเรายิงไปเรื่อยๆ จนถึง t - 1 มันก็จะถึง t-1 t-2 แล้วก็ Variance เป็น 0


