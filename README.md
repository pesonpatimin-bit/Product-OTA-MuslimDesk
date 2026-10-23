# Product-OTA-MuslimDesk
ทำโปรเจกต์ Muslim Desk Companion V1.0.0 เสร็จแล้วครับ อยู่ในไฟล์ muslim-desk-companion.zip เป็นโปรเจกต์ใหม่ทั้งชุด เหมาะกับการสร้าง repository ใหม่ ผมยังไม่ได้ Build ด้วย PlatformIO จริง แต่เช็กส่วนสำคัญบนเครื่องผมแล้ว ตามรายละเอียดด้านล่าง

สิ่งที่ได้

หน้า Main

แถบสถานะแสดงชื่อ “Muslim Desk Companion” ไอคอน Wi-Fi และปุ่มตั้งค่า
อายะห์อัลกุรอาน ตัวอาหรับขนาดใหญ่ มีคำแปลอังกฤษตัวเล็กและชื่อซูเราะห์กำกับด้านล่าง สุ่มใหม่ทุกวัน (รีสตาร์ตแล้วยังเป็นอายะห์เดิมของวันนั้น) และแตะที่อายะห์เพื่อสุ่มอันใหม่ได้
นาฬิกา พร้อมวันที่ เมือง และข้อความนับถอยหลังถึงเวลาละหมาดถัดไป เช่น Isha in 31m
เวลาละหมาดทั้ง 5 เวลา (Fajr, Dhuhr, Asr, Maghrib, Isha) ตามพิกัดของเครื่อง ช่องของเวลาถัดไปเป็นสีเขียว ส่วนเวลาที่ผ่านไปแล้วเป็นสีเทา

หน้า Settings ยังเหมือนเดิมทั้งหมด (Wi-Fi, OTA, Device spec, Developer mode, Error history, Factory reset) ส่วนสภาพอากาศและคุณภาพอากาศจากเวอร์ชัน 1.0.3 ถูกเอาออก

ที่เช็กไปแล้ว
ภาพหน้าจอ ผมคอมไพล์ LVGL บนเครื่องผมแล้วเรนเดอร์หน้า Main ขนาด 320×240 ออกมาดู ปรับขนาดแถวจนทุกอย่างพอดีจอ ทั้งอายะห์ที่ยาวและสูงสุดกับอายะห์สั้น
อักษรอาหรับ LVGL วางสระ (ฮะรอกะห์) และเครื่องหมายหยุดอ่านในอัลกุรอานได้ไม่ถูกต้อง ผมจึงวาดตัวอักษรเป็นภาพด้วยฟอนต์ Amiri Quran ตอนสร้างโปรเจกต์ แล้วฝังเป็นรูปในเฟิร์มแวร์ ผลที่ได้คือสระและเครื่องหมายอยู่ตำแหน่งถูกต้อง สร้างอายะห์ครบ 36 อายะห์ ใช้พื้นที่ราว 285 KB ถ้าเฟิร์มแวร์ใหญ่เกินที่ OTA รองรับ จะแจ้งตอน Build
เวลาละหมาด คำนวณบนเครื่อง ไม่ต้องใช้อินเทอร์เน็ต ผมเทียบกับไลบรารีดาราศาสตร์อิสระ 7 กรณี (กรุงเทพ, ยะลา, มักกะห์, ลอนดอน, ซิดนีย์, นิวยอร์ก) ตรงกันภายในไม่ถึง 1 นาที ตัวอย่างกรุงเทพวันนี้ได้ Fajr 04:57, Dhuhr 12:01, Asr 15:22, Maghrib 17:54, Isha 19:01
สิ่งที่ต้องทำก่อนใช้
include/config.h แก้ YOUR_NEW_REPO ใน FW_MANIFEST_URLS เป็นชื่อ repo ใหม่ของคุณ
ตำแหน่ง ค่าตั้งต้นหาเมืองจาก IP ซึ่งหยาบและอาจคลาดเคลื่อน ถ้าอยากได้เวลาละหมาดตรงจริง ให้ตั้ง LOC_AUTO 0 แล้วใส่พิกัดของคุณเองใน LOC_LAT, LOC_LON, LOC_NAME และ TZ_OFFSET_SEC
วิธีคำนวณ ค่าตั้งต้นคือ Muslim World League (Fajr 18°, Isha 17°) และ Asr แบบ Shafi’i ให้เทียบกับตารางเวลาของมัสยิดใกล้บ้าน แล้วปรับ PRAYER_FAJR_ANGLE, PRAYER_ISHA_ANGLE, PRAYER_ASR_FACTOR หรือ PRAYER_ADJUST_MIN (ปรับเป็นนาที) จนตรงกัน ผมไม่ทราบว่ามัสยิดของคุณใช้วิธีไหน
Build แล้ว Upload ผ่านสายครั้งแรก จากนั้นอัปเดตผ่าน OTA ตามขั้นตอนเดิมได้ (README ในโปรเจกต์สรุปไว้)
เรื่องที่ควรตัดสินใจก่อนปล่อยเป็นสินค้า
ลิขสิทธิ์คำแปล คำแปลภาษาอังกฤษเป็นของ Saheeh International ซึ่งมีลิขสิทธิ์ ถ้าจะขายต้องขออนุญาตเจ้าของ หรือเปลี่ยนไปใช้คำแปลที่ใช้ได้ เช่น ฉบับที่เป็นสาธารณสมบัติ (สคริปต์เปลี่ยนแหล่งข้อมูลได้) ส่วนข้อความอาหรับมาจากแพ็กเกจ quran-json ซึ่งระบุไลเซนส์ไม่ตรงกันเองสองที่ (CC-BY-4.0 กับ CC-BY-SA 4.0) ควรอ่านเงื่อนไขให้แน่ใจ รายละเอียดอยู่ใน CREDITS.md
ตรวจความถูกต้องของอัลกุรอาน ผมเลือกเฉพาะอายะห์ที่สมบูรณ์ (ไม่ตัดครึ่งอายะห์) และข้ามอายะห์ที่ฟอนต์วาดไม่ครบ 3 อายะห์ ได้แก่ 49:10, 36:58 และ 93:4 ก่อนปล่อย ควรให้ผู้รู้หรือครูสอนอัลกุรอานเปิดดูภาพทุกอายะห์เทียบกับมุศหัฟฉบับพิมพ์ ผมสร้างไฟล์ภาพตัวอย่างให้ดูได้ด้วยสคริปต์ tools/gen_quran.py
เวลาละหมาดเป็นค่าคำนวณ ไม่ใช่ตารางทางการ ควรบอกผู้ใช้ให้เทียบกับมัสยิดในพื้นที่
ความเป็นส่วนตัว ถ้าเปิด LOC_AUTO 1 อุปกรณ์จะเรียก ipwho.is ซึ่งเห็น IP สาธารณะของเครือข่ายนั้น ตั้ง LOC_AUTO 0 เพื่อไม่ให้เรียกบริการนี้เลย
ข้อจำกัดตอนนี้

ข้อความเป็นภาษาอังกฤษทั้งหมด (ตัวอาหรับเป็นภาพ) ถ้าอยากเพิ่มวันที่ฮิจเราะห์ ผมทำได้ แต่การคำนวณวันที่ฮิจเราะห์อาจต่างจากการเห็นดวงจันทร์จริงได้ 1 วัน จึงอยากให้คุณตัดสินใจก่อน ส่วนอายะห์เพิ่มเติมแก้ในไฟล์ tools/verses.txt แล้วรันสคริปต์ใหม่ได้เลย

พอสร้าง repository ใหม่แล้ว บอกชื่อมาได้ครับ ผมจะใส่ลิงก์ใน config.h ให้ และเตรียมไฟล์ manifest.json สำหรับเวอร์ชัน 1.0.0 ให้พร้อมใช้
________________________________________________________________________
Credits and licences

Check these before you ship or sell the device. This file is information, not legal advice.

Part	Source	Licence / note
Arabic text (Uthmani)	The Noble Quran Encyclopedia (quranenc.com), packaged by the npm module quran-json (risan/quran-json)	The package lists CC-BY-4.0 in package.json but CC-BY-SA 4.0 in its README. Read the licence and keep the attribution.
English translation	Saheeh International (Umm Muhammad), via Tanzil.net	Copyrighted translation. Free redistribution inside a product is not automatically allowed. Ask the rights holder for permission for a commercial product, or switch to a translation you may use.
Arabic font used to draw the verses	Amiri Quran (Khaled Hosny)	SIL Open Font License 1.1. The pictures are drawn from this font.
UI library	LVGL 8.3	MIT
Display / touch libraries	TFT_eSPI, XPT2046_Touchscreen	see each repository
City / time zone lookup	ipwho.is	Called over HTTPS from the device. It sees the public IP of the network the device is on. Set LOC_AUTO 0 to turn it off.
Prayer times	calculated on the device	Same solar formulas as PrayTimes.org. Approximate.
Religious accuracy
Before release, have a qualified person (a hafiz / Quran teacher) check every verse picture in src/quran_data.cpp against a printed mushaf. A wrong mark in the Quran is a serious problem.
Prayer times are calculated, not official. Always tell users to compare with their local mosque timetable.

