# Twitter_comment数据爬取 🧐🧐

### 00 (先装了typora再打开这个文件...,typora常用快捷键:

##### 01 Ctrl+shift+1:展示/关闭左侧大纲

##### 02 暂时没有O(∩_∩)O哈哈~

### 01 准备好环境,==python3.8==或以上,开发环境选择pycharm

### 02 代码奉上:

- ==代码(新建一个.py后缀名的文件之后下面代码直接放进去即可O(∩_∩)O,如果运行不成功或有别的异常问题可以往下看FAQ^ _ ^)==

```python
# Description ==> TODO
# BelongsProject ==> sgg_spider
# BelongsPackage ==> 
# Version ==> 1.0
# CreateTime ==> 2022-11-14 17:33:27
# Author ==> _02雪乃赤瞳楪祈校条祭_艾米丽可锦木千束木更七草荠_制作委员会_start


import requests

from bs4 import BeautifulSoup


file = open(file='d:/twitter_comment.txt',encoding='utf-8',mode='w')
for i in range(1,101,1):
    print('====>',i)
    result01 = requests.request(method='get',
                                url='https://explorer.altmetric.com/details/82549788/twitter/page:%d'%(i))
                                # 1.0 url='https://explorer.altmetric.com/details/77676422/twitter/page:%d'%(i))
                                # 2.0 'https://explorer.altmetric.com/details/94531651/twitter/page:2?'
                                # 3.0 'https://explorer.altmetric.com/details/91957925/twitter/page:2?_pjax=.content-panel'
                                # 4.0 'https://explorer.altmetric.com/details/77699394/twitter/page:2?_pjax=.content-panel'
                                # 5.0 'https://explorer.altmetric.com/details/82549788/twitter/page:2?_pjax=.content-panel'
    result01.encoding = 'utf-8'

    result002 = BeautifulSoup(result01.text, 'html.parser')
    i = 0
    for item in result002.select('.summary'):
        i += 1
        if i >= 5:
            res = '第%d条=>%s'%(i-4,item.text)
            file.writelines(res)
            file.write('\n')
            print('第',i-4,'条','==>',item.text)
```

### 03 依赖库问题

##### Q:没有提前装好所需要的依赖库

##### A:直接打开命令行`pip install 依赖库名称`安装即可,或者直接百度找一下也有很多python下载安装依赖库的教程的...

### 04 暂时没想到别的了O(∩_∩)O哈哈~欢迎补充...