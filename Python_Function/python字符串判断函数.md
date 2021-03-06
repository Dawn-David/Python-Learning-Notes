python判断字符串，str函数isdigit、isdecimal、isnumeric的区别
====
转载：https://www.cnblogs.com/guigujun/p/6133057.html

s为字符串<br>
`s.isalnum()` 所有字符都是数字或者字母<br>
`s.isalpha()` 所有字符都是字母<br>
`s.isdigit()` 所有字符都是数字<br>
`s.islower()` 所有字符都是小写<br>
`s.isupper()` 所有字符都是大写<br>
`s.istitle()` 所有单词都是首字母大写，像标题<br>
`s.isspace()` 所有字符都是空白字符、\t、\n、\r<br>

      isi  
-- -- -----
           
           

    >>>isinstance(a,int)
    True
    >>>isinstance(b,float)
    True
    >>>isinstance(b,int)
    False

python中str函数isdigit、isdecimal、isnumeric的区别
---

    num = "1"  #unicode
    num.isdigit()   # True
    num.isdecimal() # True
    num.isnumeric() # True

    num = "1" # 全角
    num.isdigit()   # True
    num.isdecimal() # True
    num.isnumeric() # True

    num = b"1" # byte
    num.isdigit()   # True
    num.isdecimal() # AttributeError 'bytes' object has no attribute 'isdecimal'
    num.isnumeric() # AttributeError 'bytes' object has no attribute 'isnumeric'

    num = "IV" # 罗马数字
    num.isdigit()   # True
    num.isdecimal() # False
    num.isnumeric() # True

    num = "四" # 汉字
    num.isdigit()   # False
    num.isdecimal() # False
    num.isnumeric() # True

isdigit()
---
True: Unicode数字，byte数字（单字节），全角数字（双字节），罗马数字<br>
False: 汉字数字<br>
Error: 无<br>

isdecimal()
---
True: Unicode数字，，全角数字（双字节）<br>
False: 罗马数字，汉字数字<br>
Error: byte数字（单字节）<br>

isnumeric()
---
True: Unicode数字，全角数字（双字节），罗马数字，汉字数字<br>
False: 无<br>
Error: byte数字（单字节）<br>


附录  
----
    

    unicodedata.digit("2")   # 2
    unicodedata.decimal("2") # 2
    unicodedata.numeric("2") # 2.0

    unicodedata.digit("2")   # 2
    unicodedata.decimal("2") # 2
    unicodedata.numeric("2") # 2.0

    unicodedata.digit(b"3")   # TypeError: must be str, not bytes
    unicodedata.decimal(b"3") # TypeError: must be str, not bytes
    unicodedata.numeric(b"3") # TypeError: must be str, not bytes

    unicodedata.digit("Ⅷ")   # ValueError: not a digit
    unicodedata.decimal("Ⅷ") # ValueError: not a decimal
    unicodedata.numeric("Ⅷ") # 8.0

    unicodedata.digit("四")   # ValueError: not a digit
    unicodedata.decimal("四") # ValueError: not a decimal
    unicodedata.numeric("四") # 4.0
    #"〇","零","一","壱","二","弐","三","参","四","五","六","七","八","九","十","廿","卅","卌","百","千","万","万","亿"
