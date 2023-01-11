1.标题
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
2.段落格式字体：
*斜体文本*
_斜体文本_
**粗体文本** 
__粗体文本__
***粗斜体文本*** 
___粗斜体文本 ___


分割线：
***
* * *
*********** 
--- 
- - -
------------- 

删除线：(文字上添加删除线）~~HelloWorld~~
下划线：<u>带下划线文本</u>脚注：（对文本的补充说明）有些类似论文里的引用[^Reference][^Reference]: 这是引用13.列表无序列表使用* - +作为列表标记
 * 第一项
 * 第二项

有序列表使用数字加上 . 号
 1. 第一项
 2. 第二项

列表嵌套：在子列表前面加四个空格
1. 第一项
- 第一项嵌套1    
- 第一项嵌套2
2. 第二项    
- 第二项嵌套1    
- 第二项嵌套2
4.区块：
> 最外层
>> 第一层嵌套
>>> 第二层嵌套

5.markdown代码：
段落上一个函数活片段的代码可以用反引号包起来 
``printf()`函数代码区块
使用4个空格或tab键
    <?php
    echo 'RUNOOB';
    function test(){
        echo 'test';
    )
也可以用```报过一段代码，并指定一种语言（也可以不指定）
```javascript
$(document).ready(function() {
    alert('RUNOOB');
});
```
在markdown中使用mermaid画不同类型的图

'''mermaid

sequenceDiagram
    Actor Alice
    Actor Bob
    Alice->>Bob: Hi, Bob
    Bob->>Alice: Hi, Alice
'''
文档地址：https://mermaid-js.github.io/mermaid/#/flowchart
6.markdown链接
[连接名称](链接地址)
或者
<链接地址>
例如 这是一个链接 [百度](https://www.baidu.com) 
或 直接使用链接地址 <https://www.baidu.com>
7.markdown图片
markdown图片语法格式如下：
![alt属性文本](图片地址)
![alt属性文本](图片地址 "可选标题")
![凉快照片](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fhbimg.b0.upaiyun.com%2Fd07e1d34c18f5a943587bd2c8868ef6595fa85ab16950-JTMSBQ_fw658&refer=http%3A%2F%2Fhbimg.b0.upaiyun.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1651991659&t=caba614436ddb58dbd0a7bdaac009b3f)

markdown无法指定图片的高度和宽度，如果需要的话，可以使用普通的<img>标签
< img src="http://static.runoob.com/images/runoob-logo.png" width="50%">
8.markdown表格
制作表格用 | 来分隔不同的单元格，使用 - 来分隔表头和其他行
|  表头   | 表头  |
|  ----  |  ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |
9.markdown高级技巧
1）在markdown涵盖范围之内的标签，都可以直接站在文档里面用html撰写
目前支持的html元素有：<kbd><b><i><em><sup><sub><br>等
使用<kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>delete</kbd>完成关机
2）markdown使用很多特殊符号表示特定的意义，如果需要显示特定的符号需要使用转义字符，
markdown使用反斜杠转义特殊字符
**文本加粗**
\*\*正常显示星号\*\*
markdown支持以下这些符号前面加反斜杠来转义：
\ 反斜线
` 反引号
* 星号
_ 下划线
{} 花括号
[] 方括号
() 小括号
# 井字号
+ 加号
- 减号
. 英文句点
! 感叹号