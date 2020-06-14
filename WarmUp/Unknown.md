# Forensics - unknown

Source file `resources/unknown`

- Thử `file` thì chỉ ra data

- Chạy `xxd unknown` để kiểm tra header

```
00000000: 8950 4e47 0d0a da0a 0000 000d 4948 4452  .PNG........IHDR
```

- Trông có vẻ là png header bị malform rồi, đây là header của một file png

```
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452  .PNG........IHDR
```

- Sửa lại header cho chuẩn rồi đọc flag thôi

Flag `HCMUS-CTF{l0l_CMU_da_b3s}`