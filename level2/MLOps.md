## MLOps

Machine Learning Projects - พี่บอยด์ (BigData RPG) กรรมการ EXP

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

![image](https://github.com/user-attachments/assets/9d5ffabc-4fda-4f1e-b521-ceda76e5b683)

ลองดู Jupyter Notebook ว่ามันงอกรึเปล่า แน่นอนทำหลาย Preprocessing

ถ้าเป็นเรื่องของ Software Engineer เราก็จะเก็บ Code Versioning

Size limit มันมีขนาดของโมเดลและ Data ซึ่งมันเก็บใน Large File System ที่อาจจะช่วยในการเก็บแต่มันไม่โอเคใน Code

ฉะนั้นการเก็บ Data ควรจะเก็บแบบ Artifact มันเป็นไฟล์ที่เอาไว้ Point เช่นมันเก็บอยู่ที่ Bucket GCP ซึ่ง Data เราเก็บไว้วันที่เท่าไหร่ Version อะไร
มันก็จะเรียกว่า Artifacts ไฟล์ธรรมดาไว้ในโค้ดได้ หรือ GitHub GitLab ได้ 

Data Version Control - Track Data เช่น Data ไว้ทำ Embedding

Ml flow - เราจะใช้ RandomForest แบบไหน Parameters ยังไง

![image](https://github.com/user-attachments/assets/494fe98e-44fc-4f12-9e25-f98cb65edc33)

เวลาเรา Build Images เป็น Snapshot ไป

5. Experiments Tracking

You can't improve what you don't measure

![image](https://github.com/user-attachments/assets/862fdb19-eb5e-47ca-b1cc-24304b57ea39)

เราใช้ Environments ตัวไหนบ้าง เช่น ใช้ Conda, uv, poetry, pip install

Conda ยังไม่ค่อยดีใน Production graded แต่ปัจจุบันเราจะใช้เป็น Poetry เป็น Package Manager เวลาที่เราจะ Install package อะไรก็ตามที

มันก็จะ Track หมดเลยว่า ใช้ Lib เวอร์ชั่นอะไร python version, lib แล้วเพื่อนโหลดไป มันจะรู้เลยว่าจะต้องใช้ Artifacts และ version project เป็นยังไงบ้าง

Metrics -> Business Unit, เช่น ถ้าเราทำนายหุ้น เราจะใช้ Metrics วัดว่าโมเดลอะไรเป็นตัวดีไม่ดี

Business Unit เขาจะส่งแค่เขาลงเงินเข้าไปได้แค่ไหน เขาไม่สนใจ Error เราก็จะลด Cost การสูญเสียลูกค้า เดือนหน้ายังมี Subscribe แต่ถ้าเราทำนายไม่ถูก เราก็จะเกิด Cost สูญเสียลูกค้าไปหาอีกฝั่งได้

เราจะต้องทำ Cross function คิด Profit ให้มองโลกหลายๆฝั่ง

6. Testing

![image](https://github.com/user-attachments/assets/b336926a-99be-4fe7-802a-a7adf6b878f0)

สมัยก่อนไม่มีโมเดลก็จะทำ Integration Test

![image](https://github.com/user-attachments/assets/b71424e7-5622-4379-ab5b-b01e4ac89376)

![image](https://github.com/user-attachments/assets/bfbebdbf-fede-4b47-a501-23dc481b06a7)

เราไม่สามารถใช้โมเดลเดียวในการ Predict Behaviour ได้ เช่น บอยซื้อทุกวัน แต่ถ้าใช้โมเดลทุกวัน แต่เขาใช้งานทุกสัปดาห์ ก็จะถูก Track ว่า Churn การใช้งานมันไม่เหมือนกัน

เห็นไหมว่าฝ่าย Marketing  Marketing Lanuch Campaign แต่ถึงแม้เขาไม่บอก เราจะต้องทราบว่าพฤติกรรมเขาเปลี่ยน

![image](https://github.com/user-attachments/assets/2859cc5e-b651-4c34-95b4-ab1513f2900e)

โมเดลพัง เพราะไม่ทำ Unit tests ว่า Schema มันเปลี่ยนไป Key มันผิด Deploy model ก็ไม่ได้

![image](https://github.com/user-attachments/assets/9f8a4a21-16b9-48ad-ab18-be5ec0a1e109)

A/B Testing เวลาที่เขาเครดิตก็ให้กู้ แต่ดัน Fault Rate มันเยอะ คือ ให้กู้แต่ไม่ได้คืน อาจจะมาจากโมเดล ไม่ได้ทำ Backtesting หรือตอน Train model Offline มันไม่ได้เจอ Edge cases

Edge cases - เราไม่เจอบ่อยแล้วเราจะ Handle กับมันยังไง ฉะนั้นเราไม่ได้ใช้โมเดลเดียวเพื่อตอบทุกเคสก็ได้

ในแบงค์ ปกติทำ Risk Model เขาไม่ได้ใช้โมเดลสวยหรู Deep Learning ไม่ได้ใช้ เขาใช้พวก Random Forest, Decision Tree เพราะเขาอยากรู้ว่า เขาปล่อยกู้ได้ ยังไง

![image](https://github.com/user-attachments/assets/43bf71f9-e510-4213-8ec7-ac6dde485768)

![image](https://github.com/user-attachments/assets/4cd69a1c-1dbf-4fa9-b99b-bc751e40bb69)

Business Matrix

8. Reproducibility

ทำซ้ำได้ แล้วยังเป็นเวอร์ชั่นเดิม ถ้าใครทำ Feature Versioning ก็จะใช้ Feast คนที่ใช้เริ่มต้นคือ Gojek หรือ Grab Food Delivery แล้วพอ Data Scientists ใหญ่
หลายๆ โปรเจ็คก็จะทำ Feature ที่ซ้ำกันได้ ฉะนั้นเราก็ทำ Feature Store เพื่อแชร์ Features กัน เห็นที่ไทยแล้วมี LINEMAN

![image](https://github.com/user-attachments/assets/8e69d836-dc38-4ba0-b864-466ec7cb033d)

![image](https://github.com/user-attachments/assets/b518d3a2-f745-4abf-8f33-00ee1bc57a80)

LLM - เป็น Non-deterministics แต่โมเดลทั่วไปเป็น Deterministics หาค่าได้อยู่แล้ว

![image](https://github.com/user-attachments/assets/7b2de2e2-359d-4a22-90f5-f928bfcaa334)

![image](https://github.com/user-attachments/assets/72d5536f-e864-40b3-bbd1-daeb0f4b1103)

Delivers BU 

![image](https://github.com/user-attachments/assets/0068a7cd-dfa9-4acb-bd5d-cbcef2a71df1)

Streamlit จะเจอช่องโหว่ก็จะโจมตีตลอดเวลา มันจะแก้ไขให้เลย แต่ถ้า Gradio มี Risk Vulnerability สูง
แต่ถ้า Deploy gradio ก็จะโดนดึงคีย์ไปใช้ HuggingFace จริงๆการ Deploy







