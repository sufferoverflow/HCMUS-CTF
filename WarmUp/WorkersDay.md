# Forensics - Workers' Day

Source file `resources/iwd_e.jpg`

- Thử `file` và `binwalk` đều trông khá bình thường, có khả năng là steghide

```
steghide extract -sf iwd_e.jpg

wrote extracted data to "flag.txt".

cat flag.txt
```

Flag `HCMUS-CTF{simply_use_steghide_to_hiding_something}`