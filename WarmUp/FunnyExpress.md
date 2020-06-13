# Funny Express - Web Exploitation

- Trong express `request.query` có thể được parse value ra dạng Number, String, Object, Array

- Check 1, 2, 3 thì ta có thể thấy được là nếu query.length === undefined thì sẽ qua cả 3 check này vì:

```js
q1.length == q.length
0 == undefined
false

q2.length != q1.length
0 != 0
false

q1.length + q2.length == q.length
0 + 0 == undefined
false
```

- Vậy query hiện tải của ta sẽ là: `?query[length]=undefined`

- Lúc này ta thử nối chuỗi

```
const lastCheck = 'Hello ' + q + ' World';
```

- Thì nếu q không phải kiểu Primitive (Number, String, ...) thì hàm `toString(): String` sẽ được gọi trên q, nên ta có thể viết đè hàm toString để nó trở thành một thứ khác như là property thay vì method. Như vậy phép nối chuỗi sẽ throw.

- Query sẽ thành: `?query[length]=undefined&query[toString]=0`

- Dùng query này ta sẽ lấy được cờ, nhưng như ta đã biết nếu ta thử lấy một property không tồn tại trong object nó cũng sẽ trả về undefined. Vậy ta có thể đơn giản hóa query còn `?query[toString]=0`

Flag: `HCMUS-CTF{DidntKn0wN0d3JSW0uld_be_sooo00z_Funny}`
