## MLOps

Machine Learning Projects - พี่บอยด์ กรรมการ EXP

![image](https://github.com/user-attachments/assets/59fa85c1-2a1c-41ce-8423-9ff8c39f5ae2)

Data Scientist -> ทำ Explore Data, Preprocessing แล้วก็ทำ Modeling

![image](https://github.com/user-attachments/assets/25b521c3-22c7-46d2-9d16-fdbe9e0516f0)

Maintain ไม่ไหว ทำ Automate ไม่ได้ ต้องมานั่ง Predict ทุกวัน เช่น Data Scientist เขามักจะทำ Jupyter Notebook ไม่ได้มี Design Patterns, Structure มีหลายชีท โฟลเดอร์ไม่จัด รันบน Environments

โดยปกติเรามักจะมีแค่ Data Scientist ส่งไฟล์ Excel เพื่อบอก Top 10% ส่งต่อให้กับ BU

![image](https://github.com/user-attachments/assets/c5bfc6bd-3d44-4821-8773-f471c9c4239c)

รับงานเพิ่มหรือ Scalability เราก็ต้องรับงานต่อ

![image](https://github.com/user-attachments/assets/ce79acc4-2588-48dd-af30-e0168d3b2161)

เราทำให้มันเป็น Collaboration, Monitoring

![image](https://github.com/user-attachments/assets/369d7094-ba51-4421-9ce5-4a73d1ddbadd)

บางที่รับ AI Engineer รับแต่ Data Scientist บางทีก็ต้องทำ DE, PM ด้วย มันตอบไม่ได้ขึ้นอยู่กับบริษัท

![image](https://github.com/user-attachments/assets/91c5151f-ad68-49e4-81ef-888017a16a42)

## MLOps Principles

![image](https://github.com/user-attachments/assets/33ecd61f-f522-42ef-b6d5-e60c0cb4c6c8)

1. Iterative-Incremental MLOp Life-cycle
 
![image](https://github.com/user-attachments/assets/1a1191a8-07f0-4025-8294-6e9142112082)

มันไม่มีวันจบเพราะว่า Data มีการเปลี่ยนอยู่เรื่อย ๆ พฤติกรรมของ Customer บางทีอาจเปลี่ยนได้เร็ว เปลี่ยนได้ช้า

2. Automation

![image](https://github.com/user-attachments/assets/8d793d54-8776-473f-8add-79c51fb4cfa9)

![image](https://github.com/user-attachments/assets/4ff183fa-4245-473f-9b3d-5a149fab5f73)

* Push code ขึ้น Repository แล้วก็ทำ CI/CD กับ ML systems

![image](https://github.com/user-attachments/assets/771497bd-23ce-4237-91a5-a0986b61de6f)

---

พอเรามีงานเยอะขึ้น ML Pipeline ทำ Automate

![image](https://github.com/user-attachments/assets/9f14cde7-6977-48dc-9822-4d9bede66144)

3. Continuous X

![image](https://github.com/user-attachments/assets/e005d5a9-2499-4dc9-80f5-b0a14af15266)

CI -> Push แล้วเช็คโค้ด, Conflicts, Libraries, unit test
CD -> Deploy Server


![image](https://github.com/user-attachments/assets/552ddd0d-da13-4be3-827a-62f554dec034)

ก่อนขึ้น Production จะต้องมี Criteria การเช็คว่ามันโอเคหรือยัง

![image](https://github.com/user-attachments/assets/f4ce7314-aaf9-432b-bd9d-b382f50012e8)

Staging ของ UAT ก็คือทำ Production Environments มันจะต่อไปอีกโลกนึง

พอเป็น Machine Learning ก็เลยเป็น Continuous Training เราไม่รู้ว่าจะ Trigger Train Model เมื่อไหร่ อาจมีการเปลี่ยนเมทริกซ์
พฤติกรรมลูกค้าเปลี่ยน เราก็จะทำ mlflow (ทำ Tracking, Versioning ของการทำ Machine Learning Projects)
ปัจจุบันเพิ่ม LLM Flexibility ถ้าเรามีโปรเจ็ค Multi-agents เอา LLM มาคุยกัน แล้วมันต้องมีการส่งต่อกัน เราสามารถเช็ค
Messages ที่มีการส่งต่อ Agent แล้วเราทำ Debugging ได้ดี

![image](https://github.com/user-attachments/assets/9bb56b23-50c0-44b0-a68e-2a51231ecd7c)

![image](https://github.com/user-attachments/assets/f61a6ab6-5086-42db-8330-c1db6a076aeb)

เราอยากรู้ว่ามันผิดปกติรึเปล่า แล้วเราจะได้แก้ไขได้ทัน ถ้าหากมี Dashboard แล้วมันไม่ Alert ก็ไม่มีประโยชน์
Feature เปลี่ยน Accuracy Drop แล้ว พฤติกรรมลูกค้าเปลี่ยน จะทำการ Training ใหม่เมื่อไหร่

4. Versioning







