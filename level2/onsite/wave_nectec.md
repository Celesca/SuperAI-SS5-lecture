## โจทย์ : ปัญหาการกัดเซาะในชายฝั่ง

เกี่ยวกับ Estimate ความสูงของคลื่นก่อนและหลังของโครงสร้าง เพื่อบอกว่าโครงสร้างนั้นดีหรือไม่ดี

Dominant Wave Height Estimation Based on Spectral Analysis for Coastal Erosion Monitoring System in Real Time

นอกจากการติดตั้งเซ็นเซอร์ในทะเล มากกว่า Global และ Local อย่างเช่นเราอยากรู้ความเข้มแสงและก็ CCTV คือจริงๆ เราสามารถใช้กล้อง CCTV เพื่อตรวจจับ Shore Coastline ไดเพื่อดูการเปลี่ยนแปลง

Wave Height 

Data from Sensor -> Mean subtraction -> Fourier Transform -> Peak detection -> Dominant wave parameter  estimation -> Wave height

Sampling rate ของข้อมูล

ปกติคลื่นในทางทะเล มันจะเป็น monotonic sine wave แต่พอใกล้ฝั่งจะซับซ้อนมาก มาจากคลื่นที่จะมาแทรกซ้อน หรือสะท้อนจากชายฝั่ง หรือการได้มาแล้วเราจะต้องหาความสูงที่สำคัญให้ได้

ข้อมูล Time Series พื้นฐานที่จะใช้มันคือ Fourer transform / Fourier Analysis


