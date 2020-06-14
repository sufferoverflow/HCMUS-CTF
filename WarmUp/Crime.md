# Forensics - Crime

-   Mount ra thư mục, ta được 3 file: language.png, Wanted.jpg, Secret.zip.

-   File jpg không mở được. Gõ lệnh `file Wanted.jpg`, tìm ra được file format là webp. Đổi sang png, ta được:
    ![zodiac killer](./resouces/zodiac_killer.png)

-   File Secret.zip cần mật khẩu để giải nén, đoán file language.png chính là mật khẩu đã được mã hóa. Từ ảnh trên, suy ra công cụ mã hóa là Zodiac Killer Cipher. Decode đoạn mã trong language.png, ta được `FITPASS`

-   Giải nén file Secret.zip bằng mật khẫu trên, ta được 1 file pdf và 1 file txt. Trong file txt có chứa Flag.

Flag `HCMUS-CTF{social_distancing_for_this_pandamic}`
