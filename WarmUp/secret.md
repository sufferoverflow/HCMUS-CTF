# Secret - Pwn

- Tải binary về mở bằng `radare2` để disassemble thì sẽ thấy chương trình so sánh input với flag bằng hàm `strncmp`  với độ dài là độ dài của input

- Nghĩa là input chỉ cần giống những kí từ đầu của flag thì sẽ qua được cái check này

- Mọi flag đều có dạng HCMUS-CTF{...} nên ta sẽ nhập `H` là input và thế là lấy được cờ

Flag: `HCMUS-CTF{strncmp_is_so_fun}`
