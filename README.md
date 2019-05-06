## final.md分工
尽快完成final.md中各个功能的分工吧
初步要求：尽快完成对各个文件的说明，尤其是对各个接口的说明
然后大家整合一下，按照功能把前端后端响应部分整合到一起即可完整最终版
*一切文件以master上面的文件为准，记得每次修改之前先fetch！！！*
在写报告的时候记得对各个功能进行测试，并把结果用图片的方式记录下来。

## 更新 18.12.23 by zyk
- [ ] 后端：禁止禁言用户发言
- [ ] 管理员前端：按钮更好看
- [ ] 管理员前端：调节表头的位置
- [ ] 管理员前端：首页制作
- [ ] 后端：代码更代码==>zyk admin.py+auth.py;wrh blog.py+user.py
- [ ] db.py ==> 使用peeweee
- [ ] 用户前端：文件下载

管理员处搜索功能实现
## 更新 18.12.19 by zyk
完善了管理员相关界面
完善了对所有用户、帖子的管理，包括禁言、是否置顶、删除等操作
需要解决的问题：
- [ ] 搜索不会写QAQ等wrh把搜索写出来了我改一下
- [ ] new_member.html中第八行那个.css文件路径错误
- [ ] 管理员界面该放什么东西待定(很那去记，最近删除过的东西这个集合，不如简单点放几张可爱的图片？)
## 更新 18.12.17 by zyk
1. 修改auth/temp_index.html 第75行使用了nickname
2. 修改了auth.py 中的login函数，默认第一个注册是管理员
3. 增加了admin.py文件，在这里定义管理员相关的函数，具体等前端出来改
4. 修改了blog.py，保证是按照时间顺序排序
待改进的：
- [ ] 在auth/temp_index.html中能否想办法展示文件
- [ ] 等待admin.py前端
- [ ] 要不要把post里面的created改成，last_modified？
- [ ] 个人主页部分的后端待改进
## 更新 18.12.12 by wrh

### schema.sql
**需要重新运行schema.sql，会把之前的数据全部drop掉**

新增的字段有注释表示

新增：

user is_block

user created

user nickname

user email

post is_top

取消：

reply title


### blog.py
回复取消了title

### user.py
增加了查看修改个人信息的功能

### auth.py blog.py home.py
为修改的字段提供支持 为user.py提供支持

easy_set.html是一个简易的设置网页


# 更新
更改了login和register的界面，然后register里有一些东西需要后端重写一下，具体可以看Web-flaskr2/flaskr/flaskr/templates/auth/temp_reg.html里的注释，我大概写了要如何修改auth.py里跟注册有关的内容。

以及这个文件夹为什么会这么多层。。。有一些是不是冗余的啊。。。



## 更新 18.12.9

大体布局已经全部写完了，剩下还有一些细节还要慢慢再改。

html文件中带temp_前缀的是有用的文件，其余的跟最终成品没有直接关系。

需要后端对接的地方：

- [ ] 对于每个用户，需要新增一些变量。需要记录每个用户收藏的帖子，以及回复总数，回复总数我暂时命名成replynum。另外需要存用户的头像。刚注册的时候应该为空，我这边会自动给未设置头像一个头像，然后通过个人设置里面上传改变头像。头像我这边暂时命名的是avatar
- [ ] 对于每一个帖子，希望同时存储发帖者的nickname，这样nickname用来显示在屏幕上，username用来登录。
- [ ] 每个帖子需要记录被收藏的次数以及被回复的次数。我暂时命名成了marknum（收藏次数）和replynum（回复次数）。
- [ ] 每个帖子需要储存发帖者的头像。头像也命名成avatar
- [ ] 每个帖子需要记录是否是置顶和精帖。我暂时命名的是top和goodpost
- [ ] 回复取消title，只用body就行了，以及也是一样的问题，需要记录nickname
- [ ] 回复的回复不用管。。。应该我这边能怎么弄一下让它在回复的文字框里@那个人才对= =
- [ ] 需要写一个删除回复的函数，我不是很清楚后端需要怎么实现？我参考删除帖子的前端胡写了一个不知道能不能接上。。。
- [ ] 用户个人设置和个人主页那一块需要新写py文件【或者写在auth里也可以？那这样我就把重定向改成auth.xxx就行了，以及因为这里没py文件前端能不能正常运行就玄学了= =后端写得差不多了互相报错吧【可能就单方面指教前端了
- [ ] 用户需加邮箱（email）属性，注册的时候设成空就行了，之后可以在设置里改。
- [ ] 用户需加创建（created）属性，记录什么时候注册的账号。
- [ ] 用户需加markposts属性，记录收藏的帖子

**如果想要正常运作，应该只要在temp_index.html找到那个users.home的url_for，把那个url_for删掉，编程href=“”应该就可以正常打开网站了。**

## 关于文件上传的一个问题 18.12.11

现在文件上传跟帖子是不绑定的关系是吗？我看这个只存了name和file的位置。如果想做文件在对应的帖子中展现那么就需要在帖子的属性里面也记录，如果只是想在一个页面里把所有的文件下载连接弄出来的话那就前端再写一个网页。

哦告辞好像没事了。。。我再看看。。。