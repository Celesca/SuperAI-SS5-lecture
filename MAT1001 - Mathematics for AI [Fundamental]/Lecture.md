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

Bitmap เป็นค่าสี Gray-scale เอาแค่หนึ่งจุด ที่ตำแหน่ง x,y มีค่า bitmap เราอยากจะเลื่อนจุด ในทาง Computer Vision ใช้ Translation ในการเลื่อนจุด เอามาคูณกับ Bitmap

นี่คือประโยชน์ในการคูณ Matrix 

![image](https://github.com/user-attachments/assets/d313c86d-6771-463a-a2ee-e8332b446f6a)

* Determinant คือขนาดของ Space A (ที่เป็น Space ใหม่ที่เราทำ) เป็น Scaling factor ของการ Transformation ตัว Space A 

- ถ้า Determinant มากกว่า 1 นั่นหมายความว่า Vector จะถูกขยายขนาด ถูกยืดตาม Space A
- Determinant น้อยกว่า 0 Vector จะวิ่งสวนทางเหมือนเดิม

## Eigenvectors

![image](https://github.com/user-attachments/assets/1b2944b2-74c1-4b7f-8b6a-40f269022164)

Matrix 1 ก้อนคือ Set ของจุด โดยเรา Represent มือแทน Matrix แล้วเราอยากรู้ว่ามือมีคุณสมบัติอะไรบ้าง เราต้องมองให้รอบทุกทิศ เพื่อให้รู้จักคุณสมบัติของมัน

การมองรอบทุกทิศ รายละเอียดมากเกินไป มันไม่สามารถคำนวณไหว ทำยังไงดีให้มันง่ายกว่า Information น้อยลง แต่ Represent ข้อมูลได้

เราใช้วิธีการ Projection (การทาบเงา) เอาไฟส่องมือ แล้วเอาฉากมารับ เพื่อดูว่าเงาที่อยู่บนฉากหน้าตาเป็นยังไง ถ้าเงามันหน้าตาคล้ายๆมือ เราสามารถศึกษาเงา แทนพฤติกรรมของมือทั้งก้อนได้

ถ้าเราฉายแบบ ง่าวๆ รูปแรก มันไม่ค่อยเหมือนมือ เราต้องปรับมุมแสงกับฉากไปเรื่อย ๆ ปรากฎว่าเงาเริ่มใกล้ความเป็นมือ มันได้เงาที่หน้าตาเหมือนมือ

ทิศทางในการฉายแสงที่ตั้งฉาก แล้วเห็นเงาแล้วเงายังสามารถ Represent ความเป็นมือได้อยู่ เราเรียกว่า "Eigenvector"

Eigenvalue คือความชัดของรูปภาพบนมือ ซึ่งอันนี้เราเรียกว่าการลดมิติข้อมูล 

ทิศทางที่ลดมิติแล้วยังเก็บ Information ได้มากสุดเรียกว่า "Eigenvector" เวกเตอร์ -> Characteristic direction ทิศทางที่ฉายแสง

Information Recovery -> ความสามารถในการสืบย้อนและคืนกับ Information กลับมาได้ Eigenvalues เป็นค่าคงที่ บอกว่าเงานั้นชัดแค่ไหน

Note : ในรูปสามมิติบางรูปก็ไม่มี Eigenvector เพราะว่าเงาเบลอหมดทุกทาง

PCA ใช้หลักการนี้เลย โปรเจกต์เงายังไงให้ลักษณะยังเกาะกลุ่มอยู่ได้

Threshold ว่าภาพนั้นมันเบลอหรือไม่เบลอ มันเป็นคำพูดที่ไม่ถูกต้องทางทฤษฏี การจะหา Eigenvectors จะต้องหาร Matrix แล้วเราจะพบว่ามี Matrix บางตัวเป็น Determinant เป็น 0 มันจะหารไม่ได้ ทำให้บางตัวไม่มี Eigenvectors = 0

มันมีทิศทางการฉายแสงมากกว่า 1 เช่น กระป๋องหรือเจล มันได้วงกลม หรือเห็นเป็นรูปหลอด วัตถุแต่ละอันอาจมี Eigenvectors ได้มากกว่า 1 ตัว แต่ละทิศทางจะมี Eigenvalues เป็นของตัวเอง

เช่น ถ้าเงาใหญ่ ก็จะมี Eigenvalues เยอะที่สุด เราจะเรียกทิศทางการฉายเงานั้นว่า Dominant Eigenvectors -> เพราะ Represent ได้มากสุด

* การหา Eigenvectors -> ต้องทำ Cramer จับแถวลบแถว จนได้เมทริกซ์แนวทแยง แก้สมการเชิงเส้น

![image](https://github.com/user-attachments/assets/af67b057-bc10-409d-bfec-c68f72a69688)

Power Method ->

เรามี Eigenvectors ของ Matrix A (จัตุรัส) เราจะมีเวกเตอร์ตัวนึงเป็น Column vector สุ่มขึ้นมา (แต่ห้ามเป็น 0)

เอาไปคูณกับ Matrix A แล้วหารด้วย Norm เราจะได้ เรายิ่งคูณ Matrix A มากเข้า แล้วเมทริกซ์ v ค่ามันจะค่อยๆลู่เข้า
v น้อยลงเรื่อยๆ สรุปแล้ว v ที่ลู่เข้ามันจะกลายเป็น Eigenvectors มันมีวิธีการที่คูณเข้าไปเรื่อยๆแล้ว Column vector v มันลู่เข้าเฉย

แล้วถ้า Vector - 1 ถ้า Eigenvectors มันคืออันเดียวกันเลย - 1 
ในตัว Power Method สามารถคำนวณ Eigenvectors เราสามารถคำนวณค่า norm ก่อนสุดท้าย เราเอา Eigenvectors แล้วก็จับมันมาคูณทแยง แล้วลบกับ Matrix A ตัวเดิม
จากนั้นคำนวณ Power method ก็จะออกมาเป็น Eigen-pair นั้นก็เข้าใจเรื่อย ๆ แล้วก็คำนวณ Eigenvectors คำนวณออกมาเรื่อย ๆ

![image](https://github.com/user-attachments/assets/e1d7c792-4b43-4f9f-9167-f1f77fb79da9)

