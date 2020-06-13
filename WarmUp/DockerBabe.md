# DockerBabe

- Ta tải docker image về bằng lệnh

```
docker pull pakkunandy/docker-babe
```

- Tiếp đấy ta chạy lệnh ls để xem id của image vừa tải

```
docker image ls
```

Ta tìm REPOSITORY pakkunandy/docker-babe có IMAGE ID tương ứng là gì, vd: 123456789ab


- Sau đó ta chạy docker và mở Shell trong đấy bằng lệnh
```
docker run -it 123456789ab bash
```

- Khi có shell rồi ta thử lệnh `ls` thì ta thấy có file là flag.txt chạy

```
cat flag.txt
```

Flag: HCMUS-CTF{Docker_Is_an_essential_tool_You_have_to_learn_FORRRRSURRREEEE}
