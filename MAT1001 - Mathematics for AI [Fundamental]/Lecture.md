## What is Machine Learning?

-> ให้คอมพิวเตอร์เรียนแบบการทำงาน โดยดูจาก Pattern และกระบวนการ Inference เช่น การเห็นคุณลักษณะ ว่าคุณจะทำอะไรต่อ

![image](https://github.com/user-attachments/assets/6ddbcc13-36cf-4df5-a3e9-4adc7b51e79e)

ML มีทั้งหมด 6 แบบ

Supervised Learning : หรือ Classification

Regression : การหาเทรนด์เชิงเส้น / Non-linear หาแบบไม่ใช่เส้น

Unsupervised Learning : แบบไม่มีผู้สอน ระบบจะสังเกตฟีเจอร์แล้วจัดกลุ่มเอง โดยเรียนรู้ความเหมือนแตกต่างของกลุ่ม (โครงสร้างที่ซ่อนเร้นในข้อมูล)

Dimensionality Reduction : การลดมิติข้อมูล (มันไม่ใช่ Feature Extraction - ที่สกัดฟีเจอร์ออกมา)

Reinforcement Learning : ลองผิดลองถูกตามสิ่งแวดล้อม มันจะปรับจนได้คะแนนสูงสุด

Imitation learning : เรียนรู้ที่จะเลียนแบบ เช่น การขับรถของ Tesla เช่น เอาหุ่นมาดูมนุษย์แล้วมันจดจำ การตอบโต้ของมนุษย์

ซึ่งคณิตศาสตร์ที่เราจะพูดถึง เป็น 4 เรื่อง :

![image](https://github.com/user-attachments/assets/536ad87a-f759-4696-81b1-aac700e61a22)

## 2. Linear Algebra

Vector -> จุดๆหนึ่งที่อยู่ใน Space (ปริภูมิ) แต่ Space มีขนาด m มิติ 

องค์ประกอบของเวกเตอร์ มีจำนวนตามขนาดของ Space เช่น มีสามมิติจะเป็น 3 Components

ถ้าเราทาบเงาออกมา เราจะบอกเงาที่ทาบออกมา (จุดสีแดง) ว่า Components มีตามมิติ แล้วก็ Vector x เป็นจุดๆ หนึ่งบน Space ทาบแกนออกมาได้ Vector 3 มิติ

![image](https://github.com/user-attachments/assets/8094ccdf-27f7-4b9c-9acc-5b177376906c)

Object นึงสกัด Feature ออกมาเป็น Vector ซึ่งมันก็คือ Data point นึง 
หรือเรียกได้ว่า Vector คือสิ่งที่เราสามารถ Represent Data point เป็นจุดๆนึงบน Space ได้
(สามารถสร้าง vector ได้จากการสกัด feature จาก object)

Matrix -> Series ของจุด n จุดที่อยู่บน Space ( Matrix จะเขียนบนตัวหนา ) / Set of data points หรือ Datasets เราก็จะเอามาทำเป็น Column Vector

Note : Cambridge ขีดเส้นใต้ / Oxford เอา ลูกศรด้านบน

![image](https://github.com/user-attachments/assets/75575c45-20da-4d64-b961-7eb82c8c8459)

* Matrix Operations

![image](https://github.com/user-attachments/assets/d424d8a7-91fa-48b9-b89e-d5d81b73a453)

Norm L1, Norm L2 Regulization เป็นหนึ่งใน Norm ด้วยนะ

![image](https://github.com/user-attachments/assets/3d998b10-572a-4389-bfa7-c37f7af14f29)

* Linear Transformation

![image](https://github.com/user-attachments/assets/950532b9-ebae-4edc-9c00-b11d94ab3542)

การคูณ Matrix ก็คือการแปลงเชิงเส้นใน ML เรามีจุดสามจุดใน Matrix ไปวางบน Space ใหม่

โดยมีแกนอยู่ในตัว Matrix ตัวแรก ก็คือแกน (2,1) กับ (1,2) เมื่อเอาสามจุดนี้ไปวางลงบน Space ใหม่ปุ๊บ มันจะหน้าตาใหม่ แล้วเราจะถอด Space A ออก
แล้วก็ดูว่าจุดแต่ละจุดบนกราฟเดิมจะเป็นเท่าไหร่

มันคือการเปลี่ยน Perspective ให้เป็นตำแหน่งใหม่บน Space เดิม มันคือการคูณ Matrix (Linear Transformation)










