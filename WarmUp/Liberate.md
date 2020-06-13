# Forensics - Liberate

Source image: `/resources/30_4.jpg`

Chạy thử `file 30_4.jpg`

Tìm được comment

`I think it should be flag 84-*O;_:@97XK8VARo.6;aX,J3&P&SDI[TqATE2`

Hmm, trông có vẻ là flag được encode rồi

Tiếp tục mở image dưới dạng text để tìm manh mối, có dòng `<rdf:li xml:lang='x-default'>Base85</rdf:li>`

Decode với Base85 sẽ ra flag

Flag `HCMUS-CTF{uSed_ASCII85_encoder}`