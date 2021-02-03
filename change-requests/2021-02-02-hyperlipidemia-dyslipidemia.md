# Hyperlipidemia => Dyslipidemia

## คำขอเปลี่ยนแปลงระบบ
* เปลี่ยนหัวข้อ Hyperlipidemia ใน comorbid เป็น Dyslipidemia
* นำ Hyperlipidemia เป็นเป็นตัวเลือกของ specification

## สิ่งที่ต้องทำในการเปลี่ยนนี้
- [x] แก้ไข admission form config [Hyperlipidemia => Dyslipidemia]
- [x] แก้ไข admission from โดยเปลี่ยน label [Hyperlipidemia => Dyslipidemia]
- [x] เพิ่ม Hyperlipidemia  ให้เป็นตัวเลือก specification ของ Dyslipidemia รวมกับของเดิมเป็น [Hyperlipidemia, Hypercholesterolemia, Hypertriglyceridemia, Mixed-hyperlipidemia] ตามลำดับ
- [x] แก้ไขให้ admission form ต้องรู้จักทั้ง Hyperlipidemia ของเดิมและ Dyslipidemia ใหม่ เมื่อคนเขียน note เข้ามาเขียนต่อ โปรแกรมจะ check แล้วแจ้งว่ายังไม่ได้ลง comorbid dyslipidemia ไม่ว่าเดิม note นั้นจะเคยลงข้อมูล hyperlipidemia มาแล้วหรือไม่ก็ตาม
- [x] แก้ไข admission form manager เพื่อให้ทำการบันทึก Dyslipidemia field ใหม่ สามารถทำได้และยกเลิกความสามารถในการบันทึก Hyperlipidemia field เก่า
- [x] หน้า preview ต้องรู้จักทั้งข้อมูล Hyperlipidemia และ Dyslipidemia เนื่องจากไม่ได้ปิดระบบเพื่อทำการ change ดังนั้นจะมีสถานการณ์ที่เกิดขึ้นในหน้า preview หลังการ change เกิดขึ้นดังนี้
    * ผู้เขียนอยู่ในหน้า preview และตอนเขียนยังเป็น Hyperlipidemia แบบเดิม แล้วกด publish กรณีนี้จะได้ report ออกมาเป็น Hyperlipidemia
    * ผู้เขียนอยู่ในหน้า preview และตอนเขียนยังเป็น Hyperlipidemia แบบเดิม แต่ไม่ publish กลับมาเขียน note ต่อ กรณีนี้เมื่อกลับไปเขียนต่อจะพบว่าข้อมูล Dyslipidemia ยังไม่ได้ลงต้องลงจึงจะ publish ได้

## ประเด็นปรึกษา
* หากอยู่ระหว่างการเขียน note แล้วทำการ change เห็นว่า คนเขียนควรได้ตรวจด้วยตัวเองว่า เมื่อมีการเปลี่ยนหัวข้อแล้วเขียนตนต้องการเขียนอย่างไร สำหรับการให้โปรแกรมแปลงข้อมูล hyperlipidemia(no data|no|yes + specification) มาเป็น dyslipidemia (เฉพาะ ที่ยังไม่ published) เลยก็ทำได้ ฝากกรรมการตัดสินใจ
* การเพิ่ม hyperlipidemia ให้เป็น specification ของ dyslipidemia ต้องทำการทำความเข้าใจกับผู้เขียนหรือไม่ว่า หากต้องการเลือก dyslipidemia specification hyperlipidemia จะต้องมีข้อมูล lab สนับสนุนว่าเป็น hyperlipidemia ตามเกณฑ์ของสิทธิ์ เพราะไม่เช่นนั้นแล้ว change นี้ก็จะไม่ได้แก้ปัญหาตั้งแต่ต้นที่วางไว้ เพราะในรายงานจะพิมพ์ตัว specification ออกมา
