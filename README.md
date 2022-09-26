这是经过改造的wkhtmltopdf的可执行程序

原始代码在https://github.com/wkhtmltopdf/wkhtmltopdf

我改造后的代码在：https://github.com/yulei88/wkhtmltopdf

以下内容做了改造（见outline.cc文件）

# 为插图和地图制作目录而增加的大纲的内容

原先wkhtmltopdf中只能从<h?>标签获取title,page,link和backLink四个内容

我增加了以下属性：id,tag,class,subtitle,source.sourceurl

可以取得<h? id="xxxx" tag="xxxx" ,,,>的值，供对应处理目录的xlst文件使用

# 页眉和页脚的增加了section2

原先wkhtmltopdf的[section]指代章节的名称，放于页眉或页脚上

但是当章节名称太长时，页眉页脚显示不下，造成文字重叠

我增加了[section2]，如果章节名超过20个字符，则截取17个然后加"..."于尾部

# 页眉和页脚的增加了topage1

原先wkhtmltopdf的[topage]指代总页数，但可能程序有问题，总页数有时候会少一页

所以临时增加[topage1]比[topage]大1，算是以上问题的临时解决方案



wkhtmltopdf and wkhtmltoimage
-----------------------------

wkhtmltopdf and wkhtmltoimage are command line tools to render HTML into PDF
and various image formats using the QT Webkit rendering engine. These run
entirely "headless" and do not require a display or display service.

See https://wkhtmltopdf.org for updated documentation.

## Building
wkhtmltopdf has its own dedicated repository for building and packaging.

See https://github.com/wkhtmltopdf/packaging
