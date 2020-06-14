# Cryptography - Xor

-   Đoán là bài này dùng **XOR Cipher**, cần tìm key.

-   Mã được viết ở **base16**, nhưng số lượng các ký tự là lẻ, nên ta thêm 0 ở đầu

```
0e0a19131a79051d123d113b14166535163519023d280d0b290f0b053b2d363d3b3b
```

-   `Flag` luôn có dạng `HCMUS-CTF{...}`, nên ta sẽ thử xor 18 ký tự đầu của mã với `HCMUS-CTF` (2 ký tự base16 tương đương 1 ký tự ASCII):

```
0e0a19131a79051d12 xor HCMUS-CTF = FITFITFIT
```

-   Suy ra key là `FIT`. Đem **xor** đoạn mã với `FIT` viết lặp lại đến khi bằng chiều dài đoạn mã, ta được **Flag**:

```
HCMUS-CTF{XoR_1s_a_KinD_oF_Crypto}
```

**Flag**: `HCMUS-CTF{XoR_1s_a_KinD_oF_Crypto}`
