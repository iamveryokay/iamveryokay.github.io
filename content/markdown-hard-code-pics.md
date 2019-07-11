Title: Markdown 使用base64 编码嵌入图片
Date: 2019-04-28
Category: Misc
Modified: 2019-04-28 23:04
Tags: Colab, Youtube-dl

# 加入markdown代码段
```markdown
![](data:image/png;base64,xxx)
```
xxx为生成的base64编码

# python转换脚本
```python
from base64 import b64encode

fig_path = 'path/xxx.jpg'

with open(fig_path, 'rb') as f:
    tmp_read = f.read()

ret = b64encode(tmp_read)
print(ret.decode('utf-8'))
```