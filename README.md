# NotePad-master
## 基本的笔记
从github上下载源代码，贴入Android studio，稍作改动，正常运行，即可在手机端创建笔记
![](https://raw.githubusercontent.com/1047259105/Android/master/p/0.png)
## 添加笔记的时间戳
### 1.修改noteslist_item.xml
添加时间戳功能：
我们可以看出，原应用中，每个笔记条目中，只有一个TextView, 用来显示笔记的标题，而要想显示时间戳，必须再加入一个TextView, 修改后的noteslist_item.xml的代码为:
![](https://raw.githubusercontent.com/1047259105/Android/master/p/1.png)
### 2.修改时间戳类型
在新建笔记和修改笔记中，我们的时间并不是我们习惯的格式，需要我们修改一下时间戳的格式
新建笔记在NotePadProvider中的insert方法，修改笔记在NoteEditor中的updateNote方法，我们需要修改这个方法中的时间戳格式
NotePadProvider中的insert方法:
![](https://raw.githubusercontent.com/1047259105/Android/master/p/2.png)
NoteEditor中的updateNote方法:
![](https://raw.githubusercontent.com/1047259105/Android/master/p/3.png)
### 3.NoteList的修改
首先，如果查看到NotePadProvider中关于数据表的创建，我们可以发现，表中已经存在创建时间和修改时间的列
![](https://raw.githubusercontent.com/1047259105/Android/master/p/4.png)
而在NotesList中，只投影出了ID和每条笔记的标题，如果我们要加入时间戳，必须要将修改时间的列也投影出来.
所以我们将PROJECTION添加上修改时间:
![](https://raw.githubusercontent.com/1047259105/Android/master/p/5.png)
PROJECTION只是定义了需要被取出来的数据列，而之后用Cursor进行数据库查询，再之后用Adapter进行装填。
在看完源码之后，Cursor不用变化，我们需要将显示列dataColumns和他们的viewIDs加入修改时间这一属性
![](https://raw.githubusercontent.com/1047259105/Android/master/p/6.png)

## 结果：
![](https://raw.githubusercontent.com/1047259105/Android/master/p/0.png)