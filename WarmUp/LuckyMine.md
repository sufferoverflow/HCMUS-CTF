# LuckyMine - Reverse Engineering

- Tải file LuckyMine.exe về và disassemble bằng JetBrain dotPeek

- Xem qua ta có thể thấy mine được sinh ra qua hàm `Raw_Check_Safe` và hàm này gọi một hàm khác là `Scramble`

- Ta copy cả 2 hàm ra một chương trình mới

```c#
public static void Main()
{
    for (int i = 0; i < 50; i++)
        for (int j = 0; j < 50; j++)
            if (Raw_Check_Safe(i, j))
                Console.WriteLine(i + " " + j);
}
```

- Từ đó ta có được tọa độ của những ô không có mine

```
25 9
30 1
36 42
38 17
42 17
```

- Mở chương trình lên, click vào những ô đó và Flag sẽ hiện ra

Flag: `HCMUS-CTF{C_SHARPez}`
