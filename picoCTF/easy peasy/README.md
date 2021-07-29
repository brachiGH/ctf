```python
start = key_location
stop = key_location + len(ui)

kf = open(KEY_FILE, "rb").read()
#repeat key if (stop == KEY_LEN)
if stop >= KEY_LEN:
    stop = stop % KEY_LEN
    key = kf[start:] + kf[:stop]
else:
    key = kf[start:stop]
```

[https://www.youtube.com/watch?v=VodIW2TT_ag](https://www.youtube.com/watch?v=VodIW2TT_ag)
```bash
python3 -c "print('a'*49968);print('a'*32)" | nc mercury.picoctf.net 64260
```

returns:
---
```
This is the encrypted flag!
51466d4e5f575538195551416e4f5300413f1b5008684d5504384157046e4959

What data would you like to encrypt? Here ya go!
...2593d1959523d1900563d1907523d1959543a3d1902553d190704573d1905580f023d190051513d1907523d190407553d1959071b133d1905523d19

What data would you like to encrypt? Here ya go!
50156e4a5451536e4a0357406e4a5005106e4a51036e4a03056e4a53026e4a0a





enF = 0x51466d4e5f575538195551416e4f5300413f1b5008684d5504384157046e4959
enA = 0x50156e4a5451536e4a0357406e4a5005106e4a51036e4a03056e4a53026e4a0a
A = 'a'*32 = "{:02x}".format(ord('a'))*32 = 0x6161616161616161616161616161616161616161616161616161616161616161

enF = key ^ Flag
enA = key ^ A

enF^enA = key^Flag ^ key^A = Flag ^ A   <==>   Flag^A = enF ^ enA

==>  Flag^A^A = enF^enA^A    <==>    Flag = enF^enA^A


Flag = "{:02x}".format(0x51466d4e5f575538195551416e4f5300413f1b5008684d5504384157046e4959 ^ 0x50156e4a5451536e4a0357406e4a5005106e4a51036e4a03056e4a53026e4a0a ^ 0x6161616161616161616161616161616161616161616161616161616161616161) = 0x3361313639343464616434333237313763636333393435643364393634323161

```

Hex to ASCII Text Converter: `3361313639343464616434333237313763636333393435643364393634323161` <=> `3a16944dad432717ccc3945d3d96421a`