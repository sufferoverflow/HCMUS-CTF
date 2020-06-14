# Web Exploitation - Secret Agency

Link: (http://159.65.13.76:1337/)

- Xem source code sẽ thấy có comment 
```
secret agent = eevee
```

- Tên đề bài gợi ý mình sửa User-Agent header của request. Có thể sử dụng Firefox để sửa request rồi gửi luôn cho tiện

```
User-Agent: eevee
```

Flag `HCMUS-CTF{+he_4g3nt_Izzz_eevoolution0123456}`