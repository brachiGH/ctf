````python
enc = '灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸弰㑣〷㘰摽'

flag = ''
for c in enc:
	a = chr(ord(c) >> 8)
	b = chr(ord(c) - (ord(a) << 8))
	flag = flag + a + b
	print(flag)


enc2 = ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
print(enc)
print(enc2)