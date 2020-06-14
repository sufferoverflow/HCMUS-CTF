# Forensics - InsideMe

Source file `resources/yoda_super.jpg`

- Thử `binwalk yoda_super.jpg`

```
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
193302        0x2F316         RAR archive data, version 5.x
```

- Đổi thành file rar nào

`mv yoda_super.jpg yoda_super.rar`

- Unrar ra được 2 file `secret` và `light.pdf`. `secret` chả có gì cả

- Thử `file light.pdf`

```
light.pdf: JPEG image data, JFIF standard 1.01
```

- Rename thành `light.jpg`, mở ảnh ra đọc flag thôi

Flag `HCMUS-CTF{1t_is_a_s1mpl3_BinWalk}`