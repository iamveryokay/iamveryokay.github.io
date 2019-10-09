Title: 使用python给文献排序
Date: 2019-10-09
Category: Misc
Modified: 2019-10-09 21:14
Tags: Python

# 直接上代码
```python
import os
from xpinyin import Pinyin


def my_function(lis):             #输入一个名字的列表
    pin=Pinyin()
    result=[]
    for item in lis:
        result.append((pin.get_pinyin(item),item))
    result.sort()
    for i in range(len(result)):
        result[i]=result[i][1]
    result=' '.join(result)       #将排好序的结果使用空格连接，方便输出
    print(result)


file_path = '/Users/xxx/Documents/References.txt'

with open(file_path, 'r', encoding='utf-8') as f:
    tmp_read = f.readlines()

my_function(tmp_read)
```

# 改进版本
原来的版本只能排序字符，不能保证原来docx的字体样式，下面的代码保留了字体样式，但是需要多加一个库
```python
from xpinyin import Pinyin
import docx
from docx.oxml.ns import qn
from  docx.shared import  Pt


def isAllZh(s):
    '包含汉字的返回TRUE'
    for c in s:
        if '\u4e00' <= c <= '\u9fa5':
            return True
    return False


def my_function(lis):             #输入一个名字的列表
    pin=Pinyin()
    result=[]
    cnt = 0
    for item in lis:
        result.append((pin.get_pinyin(item), item, cnt))
        cnt += 1
    result.sort()
    for i in range(len(result)):
        result[i]=result[i][2]
    # result=' '.join(result)       #将排好序的结果使用空格连接，方便输出
    return result


file_path = '/Users/xxx/Documents/References.docx'
save_path = '/Users/xxx/Documents/test.docx'
file = docx.Document(file_path)

text_list = list(map(lambda x: x.text, file.paragraphs))
# sort_index = [i[0] for i in sorted(enumerate(text_list), key=lambda x:x[1])]
sort_index = my_function(text_list)

file_new = docx.Document()
file_paragraphs = file.paragraphs

for i in sort_index:
    paragraph = file_new.add_paragraph()
    runs = file_paragraphs[i].runs
    for j in runs:
        run = paragraph.add_run(j.text)
        run.italic = j.italic
        run.font.size = Pt(10.5)
        if not isAllZh(j.text):
            run.font.name = 'Calibri'
        else:
            run.font.name = u'SimSun (中文正文)'
            r = run._element
            r.rPr.rFonts.set(qn('w:eastAsia'), u'SimSun (中文正文)')


file_new.save(save_path)
```


