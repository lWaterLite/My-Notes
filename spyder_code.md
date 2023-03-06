## Xpath解析

```python
pip install lxml  # 安装环境
from lxml improt etree  # 导包
tree = etree.parse('file_path')  # 将本地html文件加载到etree对象中
tree = etree.HTML('page_text')  # 将网络获取的html源码加载到etree对象中
tree.xpath('xpath_expression')  # xpath方法
'''
xpath语法:
/表示一个层级，//表示多个层级
属性定位:tag[@attrName="attrValue"]
索引定位:tag[1],索引号从1开始
返回标签的文本数据:tag/text(),注意返回的是一个list,同理可分直系获取/和多层获取//
返回属性值:tag/@arrtName,返回的仍然是列表
'''
```

## Session对象

```python
import requsets
session = request.session() # 创建session对象
page_text = session.get(url, headers).text
# 采用session获取或者发送请求，可以获取并保存cookie
```

