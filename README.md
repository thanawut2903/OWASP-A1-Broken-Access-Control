# OWASP-A1-Broken-Access-Control

# Hijack a Session

กระบวนการที่ผู้ไม่หวังดี (เช่น ผู้โจมตี) รับควบคุมของเซสชัน (session) ของผู้ใช้โดยไม่ได้รับอนุญาต ซึ่งเซสชันนั้นส่วนใหญ่จะเป็นเซสชันของเว็บไซต์หรือแอปพลิเคชัน ทำให้ผู้โจมตีสามารถเข้าถึงและทำกิจกรรมต่างๆ ในบทบาทของผู้ใช้นั้นๆ ได้ เช่น การเข้าถึงข้อมูล การทำธุรกรรม หรือการดำเนินการอื่นๆ โดยใช้เซสชันของผู้ใช้แทน

วิธีการที่ผู้โจมตีจะใช้ในการ Hijack a Session อาจมีหลายวิธี ซึ่งรวมถึง:

1. Session Hijacking: การแอบเข้าถึง session ID ของผู้ใช้และใช้ ID นั้นเพื่อรับควบคุม session โดยไม่ได้รับอนุญาต

2. Cross-Site Scripting (XSS): การฝังสคริปต์ที่ไม่ปลอดภัยในเว็บไซต์หรือแอปพลิเคชันที่ผู้ใช้เข้าชม ซึ่งสคริปต์นี้อาจทำให้ session ID ของผู้ใช้ถูกส่งไปยังผู้โจมตี

3. Man-in-the-Middle (MITM) Attack: การโจมตีโดยผู้โจมตีตั้งตรงอยู่ระหว่างผู้ใช้และเว็บไซต์หรือแอปพลิเคชัน ซึ่งทำให้ผู้โจมตีสามารถดักรับและแก้ไขข้อมูลที่ส่งผ่านกลางทางได้ เช่น session ID หรือข้อมูลอื่นๆ

4. Session Fixation: การโจมตีโดยการตั้งค่า session ID ล่วงหน้าและให้ผู้ใช้เข้าระบบด้วย session ID ที่ถูกตั้งค่าล่วงหน้า ซึ่งทำให้ผู้โจมตีสามารถใช้ session ID นั้นได้

การ Hijack a Session เป็นช่องโหว่ที่ร้ายแรง เนื่องจากผู้โจมตีสามารถทำกิจกรรมต่างๆ ในบทบาทของผู้ใช้นั้นๆ ได้ ดังนั้น การป้องกันจากการ Hijack a Session เป็นสิ่งที่สำคัญ ซึ่งอาจรวมถึงการใช้ HTTPS สำหรับการเชื่อมต่อที่ปลอดภัย

![image](https://github.com/thanawut2903/OWASP-A1-Broken-Access-Control/assets/159118913/2fd3e522-76d8-403c-b84a-8fc14b5ce8fd)

Video การทำ Hijack a Session : https://www.youtube.com/watch?v=YO8rsCMVUyY&t=51s

การป้องกันการ Hijacking a Session

1.  การใช้ HTTPS: การใช้การเชื่อมต่อที่ปลอดภัยด้วย HTTPS ช่วยป้องกันการดักรับข้อมูลและการโจมตี MITM (Man-in-the-Middle)

2.  การใช้งาน Cookies ที่มีความปลอดภัย: ใช้ Secure Cookies เพื่อป้องกันการดักรับข้อมูลและการโจมตีการแอบอ้างอิง (Session Hijacking)

3.  การใช้งานโทเค็น (Tokens) สำหรับการตรวจสอบตัวตน (Authentication): โทเค็น (Tokens) ที่มีอายุการใช้งาน (Expiration Time) และมีการล็อคอินเป็นช่วงเวลาสั้นๆ ช่วยลดความเสี่ยงจากการโจมตีและการขโมยโทเค็น

4.  การใช้งานการตรวจสอบระดับของผู้ใช้ (User Level Checks): ตรวจสอบสิทธิ์และระดับของผู้ใช้ก่อนทำการเข้าถึงข้อมูลหรือดำเนินการต่างๆ

5.  การใช้งาน IP Whitelisting: กำหนด Whitelist สำหรับ IP Address ที่มีสิทธิ์เข้าถึงระบบ เพื่อป้องกันการเข้าถึงไม่จาก IP ที่ไม่มีอยู่ใน Whitelist

6.  การใช้งาน CAPTCHA: การใช้งาน CAPTCHA เพื่อระงับการโจมตีแบบอัตโนมัติ (Automated Attacks) ที่มีจำนวนมาก

7.  การใช้งาน Multi-Factor Authentication (MFA): การใช้งาน MFA เพื่อเพิ่มระดับความปลอดภัยในการตรวจสอบตัวตนของผู้ใช้

8.  การตรวจสอบและปรับปรุงเว็บแอปพลิเคชัน (Web Application Security): ตรวจสอบและปรับปรุงระบบเว็บแอปพลิเคชันเพื่อป้องกันช่องโหว่ที่เปิดโอกาสให้เกิดการโจมตี

9.  การตรวจสอบและล็อกอินอัตโนมัติ: จัดการระบบการตรวจสอบและล็อกอินโดยอัตโนมัติเมื่อมีกิจกรรมที่เป็นประการประการที่ผิดปกติ

10.  การฝึกอบรมและการสร้างความตระหนัก: ฝึกอบรมผู้ใช้งานเพื่อเพิ่มความตระหนักในเรื่องการรักษาความปลอดภัยและการใช้งานที่ปลอดภัยของระบบ

# Insecure Direct Object References (IDOR)

เป็นช่องโหว่ที่พบในระบบเว็บแอปพลิเคชันที่มีความไม่ปลอดภัย เป็นหนึ่งในช่องโหว่ที่ OWASP (Open Web Application Security Project) ได้จัดอยู่ในอันดับต้นๆ


IDOR เกิดจากการอ้างอิงอ็อบเจ็กต์ (object) โดยตรงที่ไม่มีการควบคุมหรือการตรวจสอบสิทธิ์ให้เพียงพอ ทำให้ผู้ไม่ประสงค์ดีสามารถเข้าถึงหรือแก้ไขข้อมูลของอ็อบเจ็กต์นั้นได้ ซึ่งอาจเป็นข้อมูลที่เป็นความลับ ส่วนตัว หรือที่สำคัญ โดยที่ไม่ได้รับอนุญาต

การป้องกัน Insecure Direct Object References (IDOR)

1.  การใช้ระบบสิทธิ์การเข้าถึง (Access Control): สร้างระบบสิทธิ์การเข้าถึงที่เข้มงวดและมีการตรวจสอบในการอนุญาตการเข้าถึงข้อมูล เช่น ให้สิทธิ์เฉพาะตามหลัก Least Privilege และตรวจสอบสิทธิ์ก่อนให้เข้าถึงข้อมูล

2.  การใช้รหัสอ้างอิง (Reference Codes) แทนตัวเลขหรือชื่อ: การใช้รหัสอ้างอิงที่สุ่มและไม่คาดเดาได้ใน URL เพื่อลดความเสี่ยงจากการทำแบบ Brute Force หรือการเดารหัส

3.  การใช้งานส่วนกลางในการจัดการข้อมูล: ใช้งานส่วนกลางที่มีการควบคุมเข้มงวดในการจัดการข้อมูล เพื่อป้องกันการเข้าถึงข้อมูลโดยตรง

4.  การตรวจสอบสิทธิ์และการอนุญาตก่อนที่จะดำเนินการ: ตรวจสอบสิทธิ์และการอนุญาตก่อนที่จะทำการอ้างอิงหรือดำเนินการต่อข้อมูล และปฏิเสธการเข้าถึงหรือการดำเนินการที่ไม่ได้รับอนุญาต

5.  การใช้ HTTPS: การใช้การเชื่อมต่อที่ปลอดภัยด้วย HTTPS จะช่วยป้องกันการดักรับข้อมูลและการโจมตี MITM (Man-in-the-Middle)

6.  การเข้ารหัสข้อมูล: การใช้การเข้ารหัสข้อมูลที่ส่งผ่านเครือข่าย เช่น การเข้ารหัสข้อมูลที่อ้างอิงเพื่อป้องกันการแอบแก้ไขข้อมูล

7.  การทดสอบและตรวจสอบ: ทำการทดสอบเจาะระบบ (penetration testing) และการตรวจสอบระบบเพื่อค้นหาช่องโหว่ IDOR และปรับปรุงระบบเพื่อป้องกัน

8.  การสร้างการเข้ารหัสเพื่อความปลอดภัย (Security Token): การสร้างและใช้งาน Security Token เพื่อป้องกันการโจมตี CSRF (Cross-Site Request Forgery) และการป้องกันการอ้างอิง ID โดยไม่มีอนุญาต

# Missing Function Level Access Control

เป็นช่องโหว่ทางความปลอดภัยที่พบในแอปพลิเคชันเว็บหรือระบบอื่นๆ ที่ไม่มีการตรวจสอบระดับการเข้าถึง (Access Control) ให้เพียงพอ ทำให้ผู้ไม่ประสงค์ดีสามารถเข้าถึงหรือใช้งานฟังก์ชันหรือแอคชันที่ไม่ได้รับอนุญาต หรือทำฟังก์ชันนั้นๆ ในบทบาทที่ไม่ถูกต้อง

การป้องกัน Missing Function Level Access Control 

1.  การใช้งานสิทธิ์การเข้าถึง (Access Control): สร้างระบบสิทธิ์การเข้าถึงที่เข้มงวดและมีการตรวจสอบในการอนุญาตการเข้าถึงฟังก์ชันหรือแอคชัน เช่น ให้สิทธิ์เฉพาะตามหลัก Least Privilege และตรวจสอบสิทธิ์ก่อนที่จะเรียกใช้งาน

2.  การตรวจสอบและตรวจสอบสิทธิ์อย่างเข้มงวด: ตรวจสอบสิทธิ์และการอนุญาตอย่างเข้มงวดก่อนที่จะดำเนินการใดๆ ที่เกี่ยวข้องกับการเข้าถึงและใช้งานฟังก์ชันหรือแอคชันต่างๆ ในระบบ

3.  การใช้งานโทเค็น (Tokens): ใช้โทเค็น (Tokens) ที่มีอายุการใช้งาน (Expiration Time) เพื่อควบคุมการเข้าถึงฟังก์ชันหรือแอคชัน และสร้างโทเค็นใหม่เมื่อต้องการทำงานเฉพาะ

4.  การใช้งานการตรวจสอบและการบันทึกกิจกรรม (Auditing): บันทึกกิจกรรมการเข้าถึงและการใช้งานฟังก์ชันหรือแอคชัน เพื่อตรวจสอบและตรวจจับการใช้งานที่ผิดปกติหรือไม่ได้รับอนุญาต

5.  การประยุกต์ใช้งานฟังก์ชันที่มีให้บนอินเทอร์เฟซ: จัดการฟังก์ชันที่มีให้ในอินเทอร์เฟซเท่านั้น และไม่มีการเปิดเผยหรือเข้าถึงฟังก์ชันที่ไม่ได้รับอนุญาต

6.  การฝึกอบรมและการสร้างความตระหนัก: ฝึกอบรมผู้ใช้งานเพื่อเพิ่มความตระหนักในเรื่องการรักษาความปลอดภัยและการใช้งานที่ปลอดภัยของระบบ

7.  การตรวจสอบและปรับปรุงเว็บแอปพลิเคชัน (Web Application Security): ตรวจสอบและปรับปรุงระบบเว็บแอปพลิเคชันเพื่อป้องกันช่องโหว่ที่เปิดโอกาสให้เกิดการโจมตีที่เกี่ยวข้องกับการเข้าถึงและใช้งานฟังก์ชันหรือแอคชันที่ไม่ได้รับอนุญาต

# Spoofing an Authentication Cookie

การโจมตีโดยที่ผู้ไม่ประสงค์ดีเขียนข้อมูลเท็จในคุกกี้การอนุมัติเพื่อทำให้ระบบเชื่อมต่อคิดว่าผู้ใช้นั้นมีสิทธิ์และเข้าถึงข้อมูลต่างๆ โดยไม่ได้รับอนุญาตจริงๆ นั่นคือผู้ไม่ประสงค์ดีสามารถเข้าถึงข้อมูลส่วนตัวหรือดำเนินการใดๆ ในบทบาทของผู้ใช้นั้นๆ

การป้องกัน Spoofing an Authentication Cookie

1.  การใช้ HTTPS: การใช้การเชื่อมต่อที่ปลอดภัยด้วย HTTPS ช่วยป้องกันการดักรับข้อมูลและการโจมตี MITM (Man-in-the-Middle) ที่อาจนำไปสู่การ Spoofing ข้อมูล

2.  การใช้งาน Secure Cookies: ใช้คุกกี้ที่ถูกเข้ารหัสและมีการตรวจสอบความถูกต้อง เช่น การตรวจสอบลายเอก (Signature) ของคุกกี้ เพื่อป้องกันการเปลี่ยนแปลงของคุกกี้

3.  การใช้งานโทเค็น (Tokens) สำหรับการตรวจสอบตัวตน (Authentication): การใช้โทเค็น (Tokens) ที่มีอายุการใช้งาน (Expiration Time) เพื่อควบคุมการเข้าถึงและป้องกันการ Spoofing ข้อมูล

4.  การใช้งาน HTTP Only Cookies: การใช้คุกกี้ที่เฉพาะในการสื่อสารผ่าน HTTP และไม่สามารถเข้าถึงได้ผ่านภาษาสคริปต์ของเบราว์เซอร์ เพื่อลดความเสี่ยงจากการโจมตี Cross-Site Scripting (XSS) ที่อาจเป็นประเภทหนึ่งของการ Spoofing

5.  การตรวจสอบและบันทึกกิจกรรม (Auditing): ตรวจสอบและบันทึกกิจกรรมการใช้งานที่เกี่ยวข้องกับคุกกี้และการตรวจสอบสิทธิ์ เพื่อตรวจจับและป้องกันการโจมตีที่เกี่ยวข้องกับการ Spoofing

6.  การใช้งาน Multi-Factor Authentication (MFA): การใช้งาน MFA เพื่อเพิ่มระดับความปลอดภัยในการตรวจสอบตัวตนของผู้ใช้ และลดความเสี่ยงจากการโจมตีที่เกี่ยวข้องกับการ Spoofing

7.  การทำความเข้าใจและการฝึกอบรม: ฝึกอบรมผู้ใช้งานเพื่อเพิ่มความตระหนักในเรื่องการรักษาความปลอดภัยและการป้องกันการโจมตี Spoofing และการใช้งานที่ปลอดภัยของระบบ


