# idshwk7

## 信息隐藏方法
使用`LSB-Steganography`进行信息隐藏，隐藏的文件是png格式的图片，带有个人信息

## 如何提取信息
使用`LSB-Steganography`的修改版进行信息提取：修改`decode_binary`如下
```python
def decode_binary(self):
        l = int(self.read_bits(64), 2)
        output = b""
        for i in range(l):
            output += chr(int(self.read_byte(),2))#.encode("utf-8"), 修改的地方，把encode去掉
        return output
```
然后
```python
python LSBSteg.py decode -i test.png -o info.png
```
即可得到包含个人信息的PNG格式图片
