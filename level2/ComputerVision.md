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

## โจทย์ Image ทั้งหมด

* Image classification
* Object detection ทำ tracking เราจับทั้งหมดมาก่อน YOLO สุดท้ายจะมีฟังก์ชันเรื่อง Tracking อยู่ มันเคยชื่อ Brief Sort แต่ก็ยังมีคน Detect ก่อนแล้วก็ Track ต่อ คือมันอาจจะเร็ว แต่ก็มีโอกาสพลาด แต่ก็สามารถ Track และ Detect พร้อมๆกัน สมัยนี้ก็ยังใช้ YOLO แล้ว Work

* Image classification
* Object detection - Class ของ object และ ตำแหน่งของ Object แล้วเราค่อย Detect Object ณ ตำแหน่งนั้น ๆ พวก Faster RCNN มันพยายามทายตำแหน่งก่อน แล้วก็เลือกบางตำแหน่งมาทายคลาส
ส่วนโมเดล YOLO ก็คือทำ Step เดียวคือถ่ายและทายพร้อมๆกัน วิธีแแต่ก่อนมัน Huristics มาก ๆ ถ้าเป็น กทม. เราจะสร้าง Background Model ภาพโล่งๆ แล้วเอาภาพที่เก็บใหม่ไปลบอย่างเดิม

## โมเดล SAN - Segment Anything แต่มันกินทรัพยากรเยอะมาก

โจทย์ Image segmentation - Semantic Instance , Panoptic

อย่างเช่น เราอยากจะทำ Labeling Object Detection ถ้าเราตีกรอบเองก็จะทำนาย แต่ถ้าเราใช้ Panoptic segmentation ก่อนแล้วค่อยให้คนใส่ Label เอง

* Depth estimation -> ตัวกล้องสองอันที่เห็น Object เห็นต่างกันเท่าไหร่

การประเมินกล้องเดียว เขาจะใช้ Sensor LiDAR เก็บมา แล้วก็เป็นภาพระยะห่าง มันจะประเมินระยะห่างแบบนี้ได้ มันก็จะสะดวกดี อย่างเช่น ถ้าเราอยากจะทำขึ้นห้อง 3 มิติ หรือหุ่นยนต์กู้ภัย สตง.

โจทย์ที่น่าจะ Mass แต่ Volume เรารู้แค่ข้อมูล Relative 

คนส่วนใหญ่อยากถ่ายรูปอาหาร แต่ของที่เขาจะถ่ายเป็น รูปปริมาณของอาหาร คุณจะต้องหาวิธีเพิ่มเช่น หา Relative เทียบกับอะไรสักอย่าง เวลาถ่ายรูปอาหารให้ได้ติดนิ้ว Structure from motion
รูปภาพกลายเป็น Point Cloud

Coordinate Point Cloud ต้องขึ้น 3 มิติ เช่น เราไปตั้งกล้องถ่ายเอง เรา Register กล้องถ่ายเอง และขึ้นเอง แต่เป็นงาน Photosynth (Microsoft) แทนที่จะถ่ายเอง เขาไปรวมในภาพที่ชาวบ้านถ่ายมา

หรือจะสามารถใช้ได้ว่าเป็น Navigate ได้ว่าภาพที่คนอื่นถ่ายยมองจากมุมไหน ปีแรกทำ โมเดล point Cloud การทางพิเศษ เขาก็จะจ้าง Sensor บนเลเซอร์ เราไม่ได้ต้องทำ register รูปภาพเลย มันจะคล้าย Google street view เก็บรูปและ Point cloud แต่มัน Register กันไม่สำเร็จ ไม่แน่ใจว่าเขาทำอะไรต่อ พวก สสน. (สถาบันสารสนเทศ ทรัพยากรน้ำ) เกี่ยวกับเรื่องน้ำ เขาก็ทำระบบเก็บ Point Cloud เขาอยากดูสภาพภูมิประเทศ แต่เราไม่ได้รถคันเดียวบนถนน
มันมี เขามีเรือที่เก็บ Point Cloud ในน้ำ มันมีซากรถจมอยู่ในน้ำ มันมีขยะ ฟูกที่นอน เขาอยากเอาข้อมูลพวกนี้ออก เขาอยากรู้ดินที่ท้องน้ำมีระยะเท่าไหร่

* โจทย์ Image Search (ในยุคเริ่มต้นของ Internet) เวลาเสิร์จคุณพิมพ์ Query ก็จะหา Web Page แล้วก็ Return มา ซึ่งมันผลไม่ค่อยดี ก็เลยเกิดเป็นเทรนด์ใหม่คือ

- Content-based image retrieval เราจะใช้ Content รูปภาพในการเสิร์จ เราต้องมีภาพตัวอย่าง และสกัดพวกสี Texture ความหมาย แล้วก็มีฐานข้อมูลรูปภาพ เราก็สกัดเด่นแล้วก็ดู match แล้วก็ return
มันเรียกว่า CBIR โจทย์ต่อยอด Relevant Feedback เวลาเสิร์จ น้อยที่เราจะเจอของที่เราจะหาเป๊ะๆ เช่น Search Engine 50 ภาพ เขาก็จะให้เขาคลิก และภาพที่เหลือจะไม่ใช่ แล้วมันก็จะรัน Search Engine แล้วก็รัน Feedback มันก็จะหาไปเรื่อยๆ มันก็จะเจอภาพกลุ่มที่เราชอบ (คนทำเรื่องนี้มีเยอะมาก) ปัญหาคือ User ที่จะหามันภาระที่จะหาเป็น Query User ต้องมีภาพตั้งต้น
- Object Search (20 กว่าปี) เอา YOLO มา index รูปภาพ จังหวะที่เอา model มา index มันคือการเลือกคีย์เวิร์ดที่เราเสิร์จ ก็จะไม่เกินข้อมูลที่เรารู้จัก เช่น มากกว่า 80 คำ เราต้องเทรนด์กับ object detection ตัวอื่น
- งานยุคใหม่ Image Search from text query (Model CLIP) เป็นโมเดลย่อยสองอันคือ Text, รูปภาพ และเขาเทรนให้มันทำ Embedding เอา รูปภาพมา Embedded แล้วก็เอาคำบรรยาย Embedded 1 อัน

ถ้ามันสอดคล้องกันก็จะได้ Vector Embedding ที่ใกล้ๆ เคียงกัน เราก็จะเอารูปภาพมา Embedding แล้วก็ Text แล้ว Vector มาเทียบกัน
คู่ภาพ คำบรรยาย 400 ล้านรูป

ผมอยาก Detect รูปภาพโฆษณา ก็คือเอารูปมาแล้วก็ใส่

นี่คือภาพโฆษณา
นี่คือภาพถ่าย
นี่คือภาพการ์ตูน

แล้วก็เอาคำบรรยายพวกนี้มาเทียบกับภาพ ถ้า Vector Embeddings ถ้ามันใกล้เคียงโฆษณา เราก็จะตี Label นั้นเลย

หรือถ้าจะ Detect ความรุนแรง โป๊เปลือย ก็ใช้โมเดล CLIP ก็ดีเลย ก็จะมี BLIP, LLavA

เราก็จะมีงานกลุ่มพวก Multi-Modal
* Image captioning

* งานด้านกลุ่ม Medical ใส่รูปปอด แล้วก็จะได้ Report ปกติในห้องหมอจะทำงาน Technician และดูผล Radiologist นักรังสี พอเราดูแล้ว มันอาจจะเป็นปอดคุณดูไม่สวยหรือปอดเบี้ยว
หรือ X-Ray มาแล้ว อาจจะมี Pacemaker ในหัวใจ โดยอาจจะไม่ได้เกี่ยวกับความผิดปกติในโรคจริง ๆ แล้วหมอก็จะวินิจฉัยว่าเป็นโรคอะไร

อย่างเหตุผลที่แล็ปทำอะไร กรมควบคุมโรค ปกติจะเป็นรูปภาพ พร้อมเฉลย TB, มันเป็นรูปภาพพร้อม Report ของนักรังสีแพทย์ ซึ่งมันดีกว่า มันมีเยอะกว่าชื่อโรค แต่แค่มันไม่ได้พร้อมใช้ในงาน Classification โดยตรง
ดังนั้นเราก็จะทำเป็น Image Captioning เลยดีกว่าไหม

* Visual Question Answering - ใส่รูป แล้วถามตอบเกี่ยวกับรูป เช่น รูปนี้เป็นชายหรือหญิง ปกติยังไม่ติด

* Image Generation From text prompt - แล้ว generate prompt ออกมา ปรับพารามิเตอร์ให้สวย หรือปรับสกิล AI Engineer สู้พวกเรียนศิลปะไม่ได้

## โจทย์ (More advanced)

ImageNet เป็น Reference ชุดเทสจะมีหมื่นกว่ารูป และมี Paper with codes

มีคนพยายามใช้ Spiking Neural Networks พยายามเอาเข้ามาทำ NN แต่มันก็ยังไม่ค่อยน่าสน เพราะว่ามันเหมือนเป็น Activation function นึง

* Basic NN
เราใช้ข้อมูลจาก Gradient ฟังก์ชัน Partial derivatives สมมติผมดูก้อนนี้ พวก Weights ใน Connection ทั้งหลายตาม Direction of changes that increases the value of the function

* Loss function และ Gradient Descent (มันเป็นข้อมูลที่ Noise เยอะ มันเชื่ออะไรไม่ได้ครั้งเดียว)

* Gradient Vanishing Problem - ใช้ Feature Map เราก็จะสร้าง custom filter แล้วก็ทำ Feature Map เวลามันสไลด์ เราจะได้ค่า Gradient 100 ชุด โดยการอยู่บนพารามิเตอร์ชุดเดียวกัน เราสามารถเอามาบวกกันได้เลย Amplitude ก็จะใหญ่พอที่จะเทรน โดยการทำ Slide Filter มองในมุมนึงเป็น Share weight เลยทำให้ได้ผลดี อีกอันนึงที่ Convolution Filter อีกอันที่เทรนด์ได้ มันคล้ายกับ Glabo Filter
* เวลาดูที่ฟีลเตอร์ มันจะเอาฟีลเตอร์ล่างมาผสมกัน ตอนแรกได้เส้น โค้ง Shape แล้วก็ได้เป็นหน้าตา มันเป็น Hierarchial representation มันคล้ายกับสมองของเรา
มันก็เป็น Representation ด้าน Computer Vision เราต้องการ Build

![image](https://github.com/user-attachments/assets/df134716-dde8-4f49-8e0a-3e5434903f59)

GIST + Bag of Forwarding เห็นว่าจะมา CNN หมดเลยเพราะดีกว่า

* Gradient Vanishing Solution 2 : ResNet / skip connection

เขามีความเชื่อว่า Convolution มัน Share weight ก็จะแก้ Gradient หายได้ดี แต่ถ้ามีคนที่ต่อ Convolution 7-8 ชั้น และปี 2015 ลองต่อไป 20 ชั้น / 50 ชั้น ผลเริ่มห่วย ไอตัว Weight Gradient มันไม่ได้แก้ปัญหา แต่มัน Delay ปัญหาออกไปต่างหาก

ฉะนั้นเราจะเติมชื่อ Skip-connection มันจะเป็น FX แล้วไปบวก ต่อ Layer ยาวๆ โดยไม่หายไปได้ บางทีอาจจะ Skip ข้ามบล็อคจากข้ามท้ายก็มี มันก็จะมี ResNet ที่ Skip ทีละ 2 และก็ DenseNet
กลายเป็นโครงสร้างมาตรฐาน พวก GPT แต่ไม่ได้เจาะจงด้านงาน Image มันเป็นโครงสร้างงานมาตรฐาน VGG ไม่มี Skip connection แต่จบอยู่ที่ 20 layers ถ้าเราไม่มี เราจะการตีความ Layer มันจะ Complex เรื่อยๆ เราตีความได้ แต่การตีความมันจะไม่ถูก เพราะมัน Skip ได้ Layer ล่างง่ายกว่า Feature บน เสมอ มันตีความไม่ถูกแน่นอน

* Feature for Facial Verification
Fault Accept Rate / Fault Reject กี่ % / ตัวจริงโดนเตะออกกี่เปอร์เซ็นต์


