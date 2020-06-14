# Web Exploitation - Secret Directory

Các web challenges khác có số port `1337` (`leet`), `1339`, `1340`, `1341`, có vẻ bỏ qua `1338` nhỉ?

Link http://159.65.13.76:1339/

-  Mở ra không có gì cả, chỉ có hint là video `Mr Robot Main Theme`. Hmm... Robot à, vào ngay `/robots.txt` kiểm tra xem

```
robots.txt
User-agent: *
Disallow: /flagflagflagflag
Disallow: /flagpassword
```

- Thử vào `/flagflagflagflag` thì yêu cầu đăng nhập

- Vào `flagpassword` thì có hint `To get password, you must come from /flagflagflagflag`

- Sửa `Referer` header thành `http://159.65.13.76:1338/flagflagflagflag`, lấy được username và password

```
hcmus_society
youhavedonewellyoungone
```

- Login vào `/flagflagflagflag` để lấy flag thôi

Flag `HCMUS-CTF{1t_1zzzz_Crucial_t0_kn0W_Headers_and_R0b0tz}`