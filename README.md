# 4-Bit ALU Circuit Design 🧮

> **Báo cáo Bài tập lớn môn Điện tử số** > **Trường Điện - Điện tử | Đại học Bách Khoa Hà Nội (HUST)**
> 
> **GVHD: PGS.TS.Hoàng Mạnh Thắng**

Dự án thiết kế mạch **ALU (Arithmetic Logic Unit) 4-bit**, có khả năng thực hiện các phép toán số học (Cộng, Trừ, Nhân) và các phép toán logic (AND, OR, XOR, NOT) trên hai toán hạng 4-bit.
---

### 1. Mô phỏng trên Proteus
Mạch được thiết kế và kiểm chứng logic trên phần mềm Proteus 8.17.

![Proteus Simulation](https://github.com/ducsuibot/4-bit-ALU-circuit-design/blob/main/proteus%208.17/proteus.png?raw=true)

### 2. Mạch thực tế (Breadboard)
Lắp ráp trên board mạch trắng sử dụng các IC số cơ bản.

![Real Board Hardware](https://github.com/ducsuibot/4-bit-ALU-circuit-design/blob/main/alu4bit.png)

---

## 🚀 Chức năng & Nguyên lý hoạt động

Mạch sử dụng bộ giải mã **3-bit Select** để lựa chọn chức năng tính toán.

### Bảng trạng thái (Truth Table)

| Select (3-bit) | Chế độ (Mode) | Mô tả | Chi tiết |
| :---: | :---: | :--- | :--- |
| **000** | **ADD / SUB** | Cộng / Trừ | Điều khiển bởi 1 bit phụ (0: ADD, 1: SUB) |
| **001** | **MUL** | Nhân | Phép nhân 2 số 4-bit (Output 8-bit) |
| **010** | **AND** | Logic AND | A & B |
| **011** | **OR** | Logic OR | A \| B |
| **100** | **XOR** | Logic XOR | A ^ B |
| **101** | **NOT** | Logic NOT | Đảo bit A |

### nguyên lý hoạt động
* **Input:** Hai số A và B (4-bit mỗi số).
* **ADD/SUB:** 2 mạch này dùng chung 1 mạch và dùng 1 tín hiệu 1 bit để điều chọn add hoặc sub. add(0): Cộng 2 số không dấu (output 5-bit để hiện tràn số), sub(1): trừ 2 số có dấu (Bù 2).
* **MUL:** Nhân 2 số không dấu (Output tối đa 225), mạch sử dụng cổng AND để nhân và các bộ Adder để cộng dồn các kết quả trung gian sau khi đã dịch bit.
* **AND,OR,XOR,NOT:** thực hiện các phép toán này vào A, B.
---

## 🛠 Linh kiện sử dụng (Components)

| Loại linh kiện | Mã IC / Tên | Chức năng chính |
| :--- | :--- | :--- |
| **Decoder** | 74HC138 | Giải mã tín hiệu Select để chọn khối chức năng |
| **Adder** | 74LS83 | Bộ cộng toàn phần (Full Adder) |
| **Logic Gates** | 74LS86 (XOR) | Dùng cho mạch cộng/trừ và chức năng XOR |
| **Logic Gates** | 74HC08 (AND) | Dùng cho mạch nhân và chức năng AND |
| **Logic Gates** | 74HC32 (OR) | Dùng cho chức năng OR |
| **Logic Gates** | 74HC04 (NOT) | Dùng cho chức năng NOT |
| **Hiển thị** | LED Đơn | Hiển thị kết quả output nhị phân |
| **Input** | Dip Switch | Nhập dữ liệu đầu vào |

---

## 📂 Cấu trúc thư mục

```text
4-bit-ALU-circuit-design/
├── proteus 8.17/       # File mô phỏng .pdsprj
├── board.jpg           # Ảnh chụp mạch thật
├── README.md           # Tài liệu hướng dẫn
└── ...
