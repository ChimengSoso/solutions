ในข้อนี้ เราต้องการทราบขนาดของกล่องที่มากที่สุด ที่ยังสามารถเคลื่อนที่ไปยังมุมขวาบนได้

สำหรับกล่องที่มีขนาด $h \times w$ เราจะสามารถตรวจสอบว่าสามารถเคลื่อนที่ไปยังมุมขวาบนได้หรือไม่ด้วยการใช้ Breadth First Search โดยเราจะยึดตำแหน่งมุมซ้ายล่างของกล่องเป็นหลัก

สมมติว่ากล่อง ณ ปัจจุบันอยู่ที่ตำแหน่ง $(r, c)$ เราจะสามารถตรวจสอบได้ว่ากล่องสามารถเคลื่อนที่ไปยัง $(r + d_r, c + d_c)$ โดย

- กำหนดให้ $A$ เป็นอาร์เรย์สองมิติ และ $A_{i, j}$ มีค่าเป็น $1$ เมื่อพิกัด $(i, j)$ เป็นช่องที่มีกับระเบิด มิฉะนั้นจะมีค่าเป็น $0$

เราจะเคลื่อนที่ไปยัง $(r + d_r, c + d_c)$ ได้ก็ต่อเมื่อ $\sum \limits_{i=r+d_r}^{r+d_r+h-1} [\sum \limits_{j=c+d_c}^{c+d_c+1-1} A_{i, j}] = 0$ เพราะหากค่าดังกล่าวมีค่ามากกว่า $0$ แสดงว่ามีอย่างน้อย 1 ช่องภายในบริเวณของกล่องที่มีกับระเบิดอยู่ ทำให้เราไม่สามารถเคลื่อนที่ไปยังช่อง $(r + d_r, c + d_c)$

สำหรับค่าผลรวมที่ได้กล่าวไว้ด้านบนนี้ เราสามารถหาได้ภายใน $\mathcal{O}(1)$ ด้วยการทำ Prefix Sum สองมิติ ทำให้เวลาการทำงานเป็น $\mathcal{O}(RC)$ สำหรับการตรวจสอบกล่องหนึ่งครั้ง

หากเราตรวจสอบทุกขนาดกล่องที่เป็นไปได้ จะทำให้เวลาการทำงานรวมเป็น $\mathcal{O}(R^2C^2)$ แต่สังเกตว่าหากกล่องที่มีขนาด $h \times w$ สามารถเคลื่อนที่ไปยังมุมขวาบนได้ จะได้ว่า กล่องที่มีขนาด $h \times 1, h \times 2, \dots, h \times (w - 1)$ และ $1 \times w, 2 \times w, \dots, (h - 1) \times w$ ก็จะสามารถเคลื่อนที่ไปยังมุมขวาบนได้เช่นกัน

จากคุณสมบัติดังกล่าว เราจึงสามารถล็อกความกว้างของกล่องแล้ว Binary Search ความสูงของกล่อง หรือล็อกความสูงของกล่องแล้ว Binary Search ความกว้างของกล่อง (เลือกแบบใดก็ได้) ทำให้เวลาการทำงานลดลงเหลือเพียง $\mathcal{O}(R^2C \log C)$ หรือ $\mathcal{O}(RC^2 \log R)$

Time Complexity: $\mathcal{O}(R^2C \log C)$ หรือ $\mathcal{O}(RC^2 \log R)$