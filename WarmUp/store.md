# Pwn - store

- Tải file store về và disassemble bằng radare2

- Ta thấy giá của các món hàng là một con số lấy từ `rand()` rồi biến đổi

- Dịch ngược quá trình biến đổi của kết quả hàm `rand()` ta được

```c++
int get_price()
{
	int a, b, c, d;
	a = rand();
	c = a;
	d = 0x87e5753;
	a = c;
	d = ((int64_t)a * (int64_t)d) >> 32;
	d = d >> 12;
	a = c;
	a = a >> 31;
	d = d - a;
	a = d;
	a = a * 123456;
	c = c - a;
	return c;
}
```

- Chạy hàm trên vài lần trước khi kết nối tới server

- So sánh giá hiển thị trên server với kết quả trả về từ hàm, nhập số thứ 4 từ hàm vào ta sẽ được flag

Flag: `HCMUS-CTF{N3v3r_Us3_srand_time_0}`
