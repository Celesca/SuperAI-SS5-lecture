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





