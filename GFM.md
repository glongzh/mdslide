# Gitlab Flavored Markdown(GFM)说明文档
---
## Markdown是什么
----
> 一种可以使用普通文本编辑器编写的轻量级标记语言

作者：
* John Gruber
* Aaron Swartz
---
## 为啥要用Markdown
----
* 易读
* 易写
* 各种平台支持
* 便于交流
---

Gitlab Flavored Markdown受[GitHub Flavored Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)的影响，并在[CommonMark][https://github.com/gjtorikian/commonmarker]的基础上扩展了一些很实用的功能。

Gitlab可以在以下这些地方使用GFM：

* comments
* issues
* merge requests
* milestones
* snippets 
* wiki
* 仓库内的md文档

---

## 基本语法

---

### 标题

```no-highlight
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

---

### 列表

```no-highlight
1. 有序列表的item
2. 这是另一个item
   * 无序子列表
1. 具体数字并不关心，只要数字就行
   1. 有序子列表
4. 这是另一个item

* 无序列表可以用星号
- 或减号
+ 或加号
```

----
结果：

1. 有序列表的item
2. 这是另一个item
   * 无序子列表
3. 具体数字并不关心，只要数字就行
   1. 有序子列表
4. 这是另一个item

* 无序列表可以用星号
- 或减号

+ 或加号

---

### 链接

链接分两种：内联链接、引用链接
```no-highligth
内联：
[这是内联链接](https://www.baidu.com)

引用：
[这是引用链接][this is a link]
[可以用数字定义链接][1]
甚至可以省略，用[链接文字本身][]

[可以引用同仓库的其他文件的相对路径](README.md)
[也可以引用同仓库下的绝对路径](/doc/user/markdown.md)
[也可以链接到Milestones页面](/../milestones)

[this is a link]: http://www.dragonsoft.com.cn
[1]: http://www.google.com
[链接文字本身]: http://www.qq.com
```
----
结果：
内联：
[这是内联链接](https://www.baidu.com)

引用：
[这是引用链接][this is a link]

[可以用数字定义链接][1]

甚至可以省略，用[链接文字本身][]

[可以引用同仓库的其他文件的相对路径](README.md)

[也可以引用同仓库下的绝对路径](/doc/user/markdown.md)

[也可以链接到Milestones页面](/../milestones)

[this is a link]: http://www.dragonsoft.com.cn
[1]: http://www.google.com
[链接文字本身]: http://www.qq.com

> **注意:**
>
> Gitlab不能引用wiki的内容，wiki和仓库是互相独立的。

---

### 图片

内联：
```no-highlight
![alt text](img/Koala.jpg)
```
引用：
```no-highlight
![alt text][koala]

[koala]: img/Koala.jpg
```
结果：
![alt text](img/Koala.jpg)
![alt text][koala]

[koala]: img/Koala.jpg

---

### 引用

```no-highlight
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.
```

结果：

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.

---

### 表格

```
| header 1 | header 2 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |
```

结果：

| header 1 | header 2 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |

> **注意:**
>
> 表头的虚线至少得三个---
----
Cell可以设置对齐方式：

```
| Left Aligned | Centered | Right Aligned |
| :----------- | :------: | ------------: |
| Cell 1       | Cell 2   | Cell 3        |
| Cell 7       | Cell 8   | Cell 9        |
```

| Left Aligned | Centered | Right Aligned |
| :----------- | :------: | ------------: |
| Cell 1       | Cell 2   | Cell 3        |
| Cell 7       | Cell 8   | Cell 9        |

---

### 内嵌HTML

允许的HTML tag请参照此链接[http://www.rubydoc.info/gems/html-pipeline/1.11.0/HTML/Pipeline/SanitizationFilter#WHITELIST-constant][]

```no-highlight
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```
----
结果：

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

---

### 样式

```no-highlight
*斜体* 或 _斜体_

**加粗** or __加粗__

**加粗 且 _斜体_**.

~~删除此内容~~
```

结果：

*斜体* 或 _斜体_

**加粗** or __加粗__

**加粗 且 _斜体_**.

~~删除此内容~~

---

### 脚注

```no-highlight
你可以这样添加脚注.[^2]
[^2]: 这是脚注！
```

你可以这样添加脚注.[^2]

[^2]: 这是脚注！

---

## 扩展语法

---

### 语法高亮

```no-highlight
​```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
def function():
    #indenting works just fine in the fenced code block
    s = "Python syntax highlighting"
    print s
```

```
未指定语言，无语法高亮
s = "There is no highlighting for this."
But let's throw in a <b>tag</b>.
```

```

----

结果：
​```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
def function():
    #indenting works just fine in the fenced code block
    s = "Python syntax highlighting"
    print s
```

```
未指定语言，无语法高亮
s = "There is no highlighting for this."
But let's throw in a <b>tag</b>.
```

---

### 任务列表

```no-highlight
- [x] 已完成任务
- [ ] 未完成任务
    - [ ] 子任务 1
    - [x] 子任务 2
    - [ ] 子任务 3
```
----
结果：

- [x] 已完成任务
- [ ] 未完成任务
    - [ ] 子任务 1
    - [x] 子任务 2
    - [ ] 子任务 3

----
也支持有序列表：

```no-highlight
1. [x] 已完成任务
1. [ ] 未完成任务
    1. [ ] 子任务 1
    1. [x] 子任务 2
```
----
结果：

1. [x] 已完成任务
2. [ ] 未完成任务
     1. [ ] 子任务 1
     2. [x] 子任务 2

---

### 视频

支持的视频格式： `.mp4`, `.m4v`, `.mov`, `.webm`, and `.ogv`

```no-highlight
![示例视频](img/video.mp4)
```

![示例视频](img/video.mp4)

---

### Diff
```no-highlight
{+ 这是添加的内容 +}
[+ 这也是添加的内容 +]
{- 这是删除的内容 -}
[- 这是删除的内容 -]
```
结果：

{+ 这是添加的内容 +}

[+ 这也是添加的内容 +]

{- 这是删除的内容 -}

[- 这是删除的内容 -]

---

### Emoji
```no-highlight
树上骑只 :monkey: 
点个赞:thumbsup:
```
结果：

树上骑只 :monkey: 
点个赞:thumbsup:

---
## 编辑器推荐
* 你喜欢的编辑器+插件
* Typora