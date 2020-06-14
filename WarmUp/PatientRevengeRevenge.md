# Reverse Engineering - Patient Revenge Revenge 

- Dùng IDA để disassemble chương trình

- Tìm lệnh sleep, ở đây là gồm 2 lệnh để gọi system call:
```
push 0x539 # 0x68 0x39 0x05
call Sleep # 0xff 0x15 0x48 0x10 0x41
```

- Mở Hex Editor lên và tìm vùng có đoạn hex như trên thay thế vùng lệnh sleep bằng NOP (0x90)

- Lưu lại thay đổi trên và chạy chương trình

- Dùng auto click để click vào nút.

- Sau khi click đủ số lần flag sẽ hiện lên

Flag: `HCMUS-CTF{d0_y0u_kn0w_ARc_fourrrrrrrrrrrr}`
