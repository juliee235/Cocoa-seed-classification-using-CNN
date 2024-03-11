# Cocoa-seed-classification-using-CNN (Ongoing)
Cocoa seed quality grading algorithm using convolutional neural network\
โครงงานนี้เป็น Senior project มีจุดประสงค์เพื่อคัดเเยกคุณภาพเมล็ดโกโก้ ลดความผิดพลาดจากมนุษย์ ลดระยะเวลาในการคัดเเยก เเละมีความเเม่นยำมากขึ้น\
โดยได้รับความร่วมมือในการจัดหาชุดข้อมูล(dataset) จากสำนักวิชาทรัพยากรการเกษตร จุฬาลงกรณ์มหาวิทยาลัย 

![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/257ebf93-706f-48e1-b7be-95626e63c045)

## เกณฑ์การคัดเเยกเมล็ดโกโก้
1. ตามสี\
   สีม่วง(เมล็ดที่ไม่ดี)\
   สีน้ำตาล(เมล็ดที่ดี)
   ![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/82954a4c-a780-4d36-83d8-b6dd404a082a)

3. ตามลักษณะผิดปกติ \
   เมล็ดที่มีสีเทาหินชนวน (Slaty)\
   เมล็ดที่ขึ้นรา(Moldy) \
   เมล็ดงอก (Germinated) \
   เมล็ดเสียหายจากแมลง (insect damaged)
   

## ชุดข้อมูล (Dataset)
ชุดข้อมูลโกโก้ที่ผ่ากลาง (Cut-test) โดยสำนักวิชาทรัพยากรการเกษตร จุฬาลงกรณ์มหาวิทยาลัย อย่างน้อย 5200 เมล็ด โดยอยู่ใน [images]() เเละ Labels โดยใช้ Labelme.com เป็นเครื่องมือในการช่วย โดยอยู่ใน [labels]() 
โดยมีรูปตัวอย่างดังต่อไปนี้
![Chiangmai 6 รอบ 1 (ปรับแสง)](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/b2f40b6f-56e4-4fd0-bf8d-0261311a031b)

## เเผนการดำเนินงาน
![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/4e1d9086-c0af-4c01-b001-a0194d57a838)

## One stage detector : YOLOv8(state of art method)
![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/a854d46e-808c-460f-8c1f-2bf2de1254a7)
โดยกำหนด Parameter ดังต่อไปนี้\
	- initial learning rate = 0.1\
 	- epochs = 300\
  	- batch size = 1\
   	- degrees(หมุนรูป) : 20\
	- fliplr(ความน่าจะเป็นที่จะ Flip ซ้าย-ขวา): 0.5\
	- flipud(ความน่าจะเป็นที่จะ Flip ขึ้น-ลง): 0.5

 ## ผลลัพธ์การดำเนินการ
 ตัวอย่างผลลัพธ์ที่โมเดลทำนายได้
 ![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/6d46e329-b0fc-463d-b754-65d0e1824471)

 1. ประสิทธิภาพในการนับเมล็ด
โดยเมล็ดที่ Detect ผิดเกิดจาก model ไปตรวจจับพื้นหลัง(background) เเละสร้าง Bounding boxs ซ้ำเมล็ดเดิม
 ![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/558e69b0-6019-458d-a1e2-e07de80cd0dc)
 2. ประสิทธิภาพในการคัดเเยกสี
โดยคลาสสีม่วงมีข้อมูลที่น้อยกว่าสีน้ำตาลอย่างมากทำให้ ผลการคัดเเยกเมล็ดสีม่วงออกมาไม่ดี
![ภาพ](https://github.com/juliee235/Cocoa-seed-classification-using-CNN/assets/138569824/fd00905b-2e60-44b6-8f46-cd983b183eec)

 3. ประสิทธิภาพในการคัดเเยกสิ่งผิดปกติ (Ongoing)


## สรุปผล
การใช้โมเดล One stage detector(YOLO v8) ได้ประสิทธิภาพในช่วง 70-80% เเละประสบปัญหา Imbalanced dataset จึงสามารถเเก้ได้จากใช้ Generative adversarial network(GAN) ในการ upsampling minor class(Ongoing) เเละใช้โมเดลที่มีประสิทธิภาพสูงกว่า(two stage detector)(Ongoing)

   	




