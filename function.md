python判断字符串，str函数isdigit、isdecimal、isnumeric的区别
转载：https://www.cnblogs.com/guigujun/p/6133057.html

s为字符串
s.isalnum() 所有字符都是数字或者字母
s.isalpha() 所有字符都是字母
s.isdigit() 所有字符都是数字
s.islower() 所有字符都是小写
s.isupper() 所有字符都是大写
s.istitle() 所有单词都是首字母大写，像标题
s.isspace() 所有字符都是空白字符、\t、\n、\r

判断是整数还是浮点数
a=123
b=123.123

>>>isinstance(a,int)
True
>>>isinstance(b,float)
True
>>>isinstance(b,int)
False

python中str函数isdigit、isdecimal、isnumeric的区别

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

===================
isdigit()
True: Unicode数字，byte数字（单字节），全角数字（双字节），罗马数字
False: 汉字数字
Error: 无

isdecimal()
True: Unicode数字，，全角数字（双字节）
False: 罗马数字，汉字数字
Error: byte数字（单字节）

isnumeric()
True: Unicode数字，全角数字（双字节），罗马数字，汉字数字
False: 无
Error: byte数字（单字节）

================
import unicodedata

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
