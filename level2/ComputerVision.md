## Computer Vision

Tasks (low level) Intensity transformation - ทำ Histogram equalization, Contrast stretching

Histogram - เป็น Non-parametric อธิบายการแจกแจงข้อมูล โดยไม่ได้อ้างอิงตามสถิติข้อมูลได้ โดยเราตัดแต่งเป็น Bin ว่าเป็นเท่าไหร่
ว่าเราไม่ได้ตั้งสมมติฐานเพิ่ม 

สมมติว่าเราให้ภาพเราเป็น Gaussian, Laplacian

แต่แค่เป็น Parametric model อันนี้เป็นตัวอย่างโจทย์ Computer Vision ไม่ได้เข้าใจรูปภาพเท่าไหร่ หรือโจทย์ Banarization เช่นเรามี Gray Scale
เราอยากตัดให้เป็นแค่สองกลุ่ม ระหว่าง 0,1 เลย มันจะมีประโยชน์ประเภท OCR เราอยากแปลงรูปภาพให้เป็น Text ปกติจะเป็นตัวหนังสือสีดำที่เป็นแค่สีขาว
แต่ทั้งนี้ขึ้นกับว่าเราเก็บรูปนั้นยังไง มันก็จะเหลือแค่สองค่า ค่าจะอยู่ระหว่าง 0-255 เราก็จะทำ Banarization หรือ Thresholding เพื่อตัดค่าก่อน

มันคือทำกันมา 30-40 ปีแล้ว ตัวหนังสือเป็นสีดำ ปริมาณพิกเซลสีขาวจะเยอะกว่าสีดำ เราสามารถตั้งสมมติฐานเพิ่มได้ว่า Distribution ของสีขาว แล้วสีดำถือว่าเป็น Noise
แล้วเราก็ตั้งค่า Mean Threshold 2 variance เป็นวิธีการตั้ง Threshold ให้กลายเป็น Binarization

พวกแอบถ่ายรูปก็ทำ Image Filtering เราควรจะออกแบบฟิลเตอร์แบบไหนดี เช่น Smoothing, Edge detection, Sharpening เช่นภาพ Ultrasound ถ้าเราทำ Smooth ให้รูปเรียบไปเลย
แต่ Details บางอย่างก็จะหายไป มันอาจจะไม่ได้เหมาะกับทุกงาน ต้องทำให้เหมาะกับสิ่งที่ตัวเองสนใจ

* Morphological operations
  - Erosion and Dilation สนใจสีขาว ทำ Thresholding จะเป็นจุดเล็กๆ นั้นมา มันมักจะเป็น preprocessing ในหลายๆงาน
 

![image](https://github.com/user-attachments/assets/91d59843-13e9-4e57-a2d6-97bd824025aa)

ML - KNN ตอบตามเพื่อน หรือ Linear regression ทำตามเส้น โมเดลยุคใหม่ก็ SVM
เวลาคนมาเคลมว่าใช้ SVM เขาจะถามว่าใช้ Kernel อะไร ถ้าตอบไม่ได้จะตก ถ้าเราไม่ใช้ Kernel functions ถ้าไม่ใช้ มันก็จะเป็น Linear Classifier ธรรมดา
คุณเป็น 1 บรรทัดเขียนว่า Support Vector Machine ถ้าจะมีคือคุณใส่เกณฑ์ในการเทรนหลายแบบ ฉะนั้นจะต้องดูเรื่อง Kernel ในโลกไม่ได้มีแค่เฉพาะเรื่อง Neural Network



