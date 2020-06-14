# Reverse Engineering - StackString

Source file `resources/stackstring`

- Disassemble main với `gdb`, thấy có rất nhiều `movb`, khả năng cao là assign từng kí tự vào array flag

- Bỏ file vào `edb`, step qua hết đoạn `movb` rồi đọc flag trong memory thôi

Flag `HCMUS-CTF{St4cK_Str1ng_G00D_old_techn1qu3}`