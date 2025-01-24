---
layout: post
title: "Điều khiển LED với Charlieplexing"
subtitle: "Điều khiển 240 LED chỉ với 16 chân !?"
date: 2025-01-24
author: "yusenpai"
header-img: "img/post-bg-2015.jpg"
tags: []
---

Hello mọi người, hôm nay mình sẽ chia sẻ về một kỹ thuật tên là **charlieplexing** để điều khiển LED với số lượng chân **ít nhất có thể**.

# Mở đầu

Chuyện là mình đang thiết kế một cái gadget bé bé xinh xinh như thế này:

![alt text](/assets/2025-01-24-liquid_pedant.png)
*Fluid Simulation Pendant. Nguồn: [mixela](https://www.youtube.com/watch?v=jis1MC5Tm8k&t=909s)*

---

Trên đó có 216 LED nhỏ (cỡ [0402](https://www.ultralibrarian.com/2020/06/02/0402-package-footprint-resistor-sizes-and-parameters-ulc) - siêu bé luôn 😓). Do không gian hạn chế nên mình chỉ được dùng một con vi điều khiển bé bé để điều khiển đống LED ấy. Mà con mình dùng có số lượng chân GPIO hạn chế (đâu đó 16 chân - vì nó quá bé), nên buộc mình phải mò tới nhiều kỹ thuật điều khiển LED.

# Điều khiển 1 LED đơn

**LED** (Light Emitting Diode) là một diode phát ra ánh sáng khi có dòng điện đi qua. Cách điều khiển LED rất đơn giản: Nối Anode của LED với điện thế dương, nối Cathode của LED với đất (0V). Và đó cũng là cách mình làm cháy vài con LED 😓.
![alt text](/assets/2025-01-24-led.png)
![alt text](/assets/2025-01-24-led_forward_voltage.png)
*Đồ thị điện áp so với dòng điện qua LED*

---

Nhìn vào đồ thị ở trên: khi điện áp đặt vào LED vào khoảng 1.8V - 2.0V thì dòng điện đi qua LED bắt đầu tăng nhanh. Ở điện áp 2.4V, dòng điện qua LED là 50mA. Nếu điều khiển điện áp đặt vào LED không tốt (như trường hợp của mình, mình gắn thẳng LED vào nguồn 5V luôn 🤭) thì dòng điện qua LED quá lớn -> làm LED cháy. Nên người ta thường gắn trở nối tiếp với LED để hạn dòng, giá trị khoảng 200 Ohm tới 10kOhm.

Điện áp đặt vào LED mà khiến dòng điện bắt đầu tăng nhanh gọi là **Forward Voltage - Vf**. LED màu khác nhau thì có Vf khác nhau:

- LED đỏ, cam, vàng: Vf = 1.8V - 2.3V
- LED xanh lá, xanh dương: Vf = 2.6V - 3.4V

Dòng điện qua LED từ 1mA tới 10mA là ổn. Dòng lớn hơn sẽ rất chói

## Điều khiển LED với chân GPIO của vi điều khiển

Một chân GPIO của vi điều khiển có điện áp mức cao là +3.3V hoặc +5V (tuỳ việc được cấp nguồn +3.3V hay +5V). Dòng điện (có thể đi ra hoặc đi vào) tối đa khoảng 30mA. Mạch điện như hình dưới.

![alt text](/assets/2025-01-24-led_circuit.png)

---

Nguồn vi điều khiển là +3.3V, mình thường chọn LED màu xanh (với Vf = 3.1V) thì bỏ luôn điện trở cũng được. Thay đổi trạng thái chân GPIO thành mức cao/thấp sẽ khiến LED sáng/tắt theo. Muốn điều chỉnh độ sáng có thể dùng [PWM](https://vi.wikipedia.org/wiki/Điều_chế_độ_rộng_xung). Vậy là xong, ta đã có thể điều khiển 1 LED đơn.

# Điều khiển nhiều LED với multiplexing

Chuyện bắt đầu phức tạp khi có thêm nhiều LED để điều khiển. Giả sử có n LED, theo cách ở trên thì mình cần tới n chân GPIO để điều khiển.

Vậy nên ta phải tìm cách nào đó để điều khiển nhiều LED cùng lúc với một chân GPIO. Kỹ thuật này gọi là **multiplexing**. Ta sắp xếp các LED thành một ma trận (hoặc thành hình chữ nhật cho dễ hình dung 😉). Các LED chung hàng sẽ có chân **Anode** nối chung với một chân GPIO. Các LED chung cột sẽ có chân **Cathode** nối chung với một chân GPIO khác.

![alt text](/assets/2025-01-24-led_matrix.png)
*Ma trận LED 4x4. Kí hiệu của dây theo hàng là R1..4, kí hiệu của dây theo cột là C1..4*

---

Ban đầu các chân GPIO đều ở mức thấp (0V), khiến cho tất cả đèn tắt. Cách điều khiển như sau: Muốn LED ở hàng m, cột n sáng, thì:

- Rm ở mức cao, các chân điều khiển hàng khác mức thấp.
- Cn ở mức thấp, các chân điều khiển cột khác mức cao.

Ví dụ:

Để LED(2,3) (hàng 2, cột 3) sáng: R2 nối mức cao; R1, R3, R4 nối mức thấp. C3 nối mức thấp; C1, C2, C4 nối mức cao. Chỉ có LED(2,3) sáng. Những LED khác không sáng vì:

- Điện áp ở chân Anode và Cathode **bằng nhau** (đều là mức cao hoặc đều là mức thấp), hoặc
- Điện áp ở chân Anode **thấp hơn** Cathode (Anode mức thấp, Cathode mức cao). Vì LED là diode, chỉ dẫn điện **theo một chiều từ Anode sang Cathode**.
  
![alt text](/assets/2025-01-24-led_matrix_example1.png)
*Dây màu đỏ đang ở mức cao. Dây màu xanh đang ở mức thấp.*

---

Để LED(1, 4) sáng, ta cũng làm tương tự: R1 nối mức cao; R2, R3, R4 nối mức thấp. C4 nối mức thấp; C1, C2, C2 nối mức cao.

![alt text](/assets/2025-01-24-led_matrix_example2.png)

---

Vậy nếu ta muốn LED(1,4) và LED(2,3) sáng **cùng lúc** thì sao? Giả sử nối R1, R2 nối mức cao; R3, R4 nối mức thấp. C1, C2 nối mức cao; C3, C4 nối mức thấp. Trái với mong đợi, có tới 4 đèn sáng thay vì 2:

![alt text](/assets/2025-01-24-led_matrix_example3.png)

---

Vì sao á? Cái này để bạn đọc tự suy nghĩ 🤷‍♂️. Bạn sẽ nhận ra không thể làm cho hai đèn LED sáng cùng lúc được, **trừ trường hợp hai đèn đó nằm cùng một hàng hoặc cùng một cột**.

Thay vì cố gắng điều khiển tất cả LED **cùng lúc**, ta chỉ cần các LED **trên cùng một cột**, rồi chuyển sang cột kế tiếp, và lặp lại khi đến cột cuối cùng. Nếu chuyển cột đủ nhanh, kết hợp hiện tương lưu ảnh ở mắt người (Nguồn: [Wikipedia](https://vi.wikipedia.org/wiki/Hiện_tượng_lưu_ảnh_trên_võng_mạc)) mà ta sẽ thấy tất cả các cột sáng **cùng lúc**. Và đó là cách mà ta điều khiển ma trận LED với kỹ thuật **multiplexing**.

Tóm lại:

- Số chân GPIO cần để điều khiển ma trận LED n hàng, m cột: n + m
- Kỹ thuật điều khiển: Điều khiển từng cột LED (hoặc hàng, tuỳ bạn). Chuyển sang cột khác ở tốc độ cao khiến mắt người lưu ảnh lên võng mạc.

Vậy nếu bạn muốn thay đổi độ sáng cho từng LED thì sao? Cái này bạn có thể kết hợp với PWM, nhưng khó quá nên thôi mình xin pass 🥹.

Wellll, kỹ thuật này thực sự rất tốt, nhưng chưa đủ tốt với mình. Để điều khiển ma trận LED 16x15 (240 LED), cần 16 + 15 = 31 chân GPIO. Con số đó vẫn là quá nhiều. Vậy nên mình tìm tới kỹ thuật **charlieplexing**, cũng là phần chính của bài viết này. Với charlieplexing, chỉ cần 16 chân GPIO để điều khiển 240 LED ?! Không nhìn nhầm đầu 😊.

# Điều khiển nhiều LED với charlieplexing

*Còn tiếp*