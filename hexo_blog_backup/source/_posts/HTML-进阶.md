---
title: HTML 进阶
date: 2018-06-25 17:48:06
tags: HTML
---
# 概念
1. HTML 发展史：
![HTML 发展史](图1.PNG)

2. HTML 文档：
分为文档声明，<html> 根标签（根标签中分为文档头部，文档主体）。

- 文档声明（HTML5）为 `<!DOCTYPE html>` 。
- 文档头部内容：
![文档头部内容](图2.PNG)

# 标签
## 语法
常用属性：
- id：`<div id="nav"></html>div>`
- class: `<span class="time"></span>`
- style: `<div style="display:none;"></div>`
- title：`<a title="收藏"></a>` 

## 章节
1. 标签概况：
![标签集合](图3.PNG)

2. 章节标签：
之前用 div 进行分割，HTML5 新增的标签，可以更好的语义化。
![章节标签](图4.PNG)

## 文本
- 超链接： `<a href="" target=""></a>` //链接还可以是锚点（#eg），也可以是一个 name 值。

其余标签参考博文《HTML 基础》。

## 组标签
- div
- p
- ul，ol，dl（自定义列表的 type 属性表示用什么作为序号，如 `type="a"`）。

## 资源
- img：`<img src="" alt="">`

- iframe：`<iframe src=""></iframe>`

- object，embed：嵌入外部资源。
![嵌入外部资源](图5.PNG)

- video：（自动播放可加入 autoplay 属性，循环播放用 loop 属性）。
![video](图6.PNG)

- audio：
![audio](图7.PNG)

- canvas，svg：用来嵌入图像。

- map，area：可以用来定义热点。
![map，area](图8.PNG)

## 表格
标题，行，表头&列组成。
```
<table border="1">
	<caption>这是一个表格</caption>
	<thead>
	<tr>
		<th>OS</th>
		<th>Chinese?</th>
		<th>French</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>iOS 10</td>
		<td>YES</td>
		<td>YES</td>
	</tr>
	</tbody>
	<tfoot>
	<tr>
		<td colspan="3">列延展3个格子</td> <!--rowspan 为行延展，行合并-->
	</tr>
	</tfoot>
</table>
```
```
<thead>用来包裹表格表头行</thead>
<tbody>用来包裹表格 body 部分行</tbody>
<tfoot>用来包裹表格 foot 行</tfoot>
```

## 表单
用来将数据传送给后台。

1. form:
action 属性为提交到哪个接口。
表单内用 `<fieldset></fieldset>` 来分区，其标题用 `<legend></legend>` 。
```
<form action="/login" method="post">
	<fieldset>
		<legend></legend>
		...
	</fieldset>
	...
</form>
```

2. input:
表单中常用的标签。
name 属性为传到后台的名称，value 属性为传到后台的名称对应的值。
下拉选择中，可以用 optgroup 标签对 option 进行分组，`<optgroup label="group"></optgroup>`
![input](图9.PNG)
![input2](图10.PNG)
![input3](图11.PNG)
![input4](图12.PNG)
![input5](图13.PNG)

## 语义化
用正确的标签来描述页面。
语义化用来 SEO，提高代码可读性等。

# 实体字符
类似于转义字符。

1. 两种表示方法：
- &entity_name; `&nbsp;`
- &#entity_number; `&#160;`

2. 常用实体字符：
![常用实体字符](图14.PNG)