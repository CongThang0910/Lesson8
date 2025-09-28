# STM32F103 – Đọc ADC và hiển thị giá trị qua UART

## 📌 Mô tả
Chương trình sử dụng **STM32F103C8T6** để đọc tín hiệu từ kênh ADC (PA0).  
- Nếu nối **biến trở**: giá trị đọc được sẽ đổi sang điện áp (mV).  
- Nếu nối **cảm biến nhiệt độ LM35**: giá trị đổi ra điện áp và suy ra nhiệt độ (°C).  
- Kết quả sẽ gửi qua UART1 và hiển thị trên terminal.

---

## 🛠️ Yêu cầu phần cứng
- **Board**: STM32F103C8T6 (Blue Pill).  
- **Cảm biến/nguồn tín hiệu**:  
  - Biến trở 10kΩ nối vào PA0, hoặc  
  - Cảm biến nhiệt độ LM35 nối ra PA0.  
- **USB-TTL** để kết nối UART với máy tính.  

**Kết nối chân**:  
- PA0 → tín hiệu analog (biến trở/LM35).  
- PA9 (TX) → RX USB-TTL.  
- PA10 (RX) → TX USB-TTL.  
- GND ↔ GND.  

---

## ⚙️ Cấu hình

### 1. ADC1
- Pin: PA0 = ADC Channel 0.  
- Độ phân giải: 12-bit (0–4095).  
- Chế độ: Independent, continuous conversion.  
- Sample time: 55.5 cycles.  
- Điện áp tham chiếu: 3.3V.  

Công thức chuyển đổi:  
- Điện áp (mV) = (ADC_Value / 4095) × 3300.  
- Nhiệt độ LM35 (°C) = Điện áp (mV) / 10.  

### 2. UART1
- Baudrate: 9600.  
- Word length: 8 bit.  
- Stop bit: 1.  
- Parity: None.  
- Mode: TX, RX.  

---

## 🖥️ Terminal
Mở phần mềm terminal (PuTTY, TeraTerm, RealTerm, …) với cấu hình:  
- Baudrate: 9600  
- Data bits: 8  
- Stop bits: 1  
- Parity: None  

**Kết quả mong đợi** (ví dụ khi dùng LM35):  
