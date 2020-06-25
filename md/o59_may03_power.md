อัลกอริธึมที่เราจะใช้ในการแก้โจทย์ข้อนี้คือ [MO's Algorithm](https://www.geeksforgeeks.org/mos-algorithm-query-square-root-decomposition-set-1-introduction/) ซึ่งจะสามารถตอบ query รูปแบบเฉพาะแบบ offline ได้ในเวลา $\mathcal{O}((n+q)\sqrt n)$ เมื่อ $n$ คือขนาดของอาร์เรย์และ $q$ คือจำนวนคำถาม

หลังจากที่เราได้เรียงลำดับคำถามตามเงื่อนไขของ MO's Algorithm เรียบร้อยแล้ว เราจะต้องหาวิธีอัพเดทคำตอบเมื่อเราทำการเปลี่ยนแปลงอาร์เรย์ของเราโดยการเพิ่มสมาชิกเข้าหรือตัดสมาชิกออกได้เร็ว ๆ

สมมติว่าเรามีคำตอบอยู่สำหรับอาร์เรย์หนึ่ง แล้วเราต้องการจะเพิ่มตัวเลข $x$ เข้าไปในอาร์เรย์นี้ ให้ $f(x)$ เป็นจำนวนครั้งที่ $x$ ปรากฏขึ้นในอาร์เรย์ก่อนเพิ่ม เราจะได้ว่า หลังจากเพิ่ม $x$ เข้ามาในอาร์เรย์ คำตอบของเราจะเปลี่ยนไปเท่ากับ $(f(x)+1)\cdot x^{f(x)+1} - f(x)\cdot x^{f(x)}$ ซึ่งสามารถคำนวณได้โดยตรงถ้าเรารู้ค่า $f(x)$ และ $x$

ในทำนองเดียวกัน ถ้าเราต้องการจะลบตัวเลข $x$ ออกจากอาร์เรย์ คำตอบของเราจะเปลี่ยนไปเท่ากับ $(f(x)-1)\cdot x^{f(x)-1} - f(x)\cdot x^{f(x)}$ ซึ่งสามารถคำนวณได้โดยตรงเช่นกัน

หลังจากเราเปลี่ยนคำตอบแล้ว เราจะต้องอัพเดทค่าของ $f(x)$ ไปด้วย ซึ่งในข้อนี้สามารถใช้อาร์เรย์ได้ เนื่องจากค่าในอาร์เรย์จะไม่เกิน $10^6$

การอัพเดทแต่ละครั้งจึงใช้เวลา $\mathcal{O}(1)$

การยกกำลังในการคำนวณนิพจน์ทางคณิตศาสตร์ข้างต้นสามารถทำได้เร็ว ๆ โดยการใช้ [Exponentiation by Squaring](https://en.wikipedia.org/wiki/Exponentiation_by_squaring) ซึ่งจะทำงานใน $\mathcal{O}(\log k)$ เมื่อ $k$ คือเลขชี้กำลัง

ทั้งนี้ สูตรการคำนวณทั้งหมดไม่มีการหารเลย จึงสามารถคำนวณใน modulo ของตัวเลขที่ไม่ใช่จำนวนเฉพาะก็ได้ เพราะใน modulo ของตัวเลขที่ไม่ใช่จำนวนเฉพาะเรา[อาจจะหา inverse การคูณไม่ได้](https://en.wikipedia.org/wiki/Modular_multiplicative_inverse)

เราจึงสามารถแก้โจทย์ข้อนี้ได้ในเวลา $\mathcal{O}((n+q)\sqrt n)$