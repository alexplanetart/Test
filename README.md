# 照片选择功能文档
目前结构的主要弊端如下：
1. 基类SelectPhotoFragment 及 PhotoAlbumRecycleViewAdapter 定义的共有行为过多 优点：方便增加新的图片选择页面  缺点：页面功能扩展困难（比如增加分页或者修改图片显示方式）
2. 数据请求都是用AsyncTask实现
3. 无分页功能


## 功能需求
1.  选择一张/多张图片
2.  账号登陆
3.  滤镜功能
4.  多级目录展示图片
5.  分页加载功能

为了更好的满足 选择一张或者多张图片 以及 半屏显示图片选择页面 的需求， 保持自定义View包含Fragment这种方式 不变
整体结构请见 https://www.processon.com/view/link/618486d25653bb14c261c093
![image](https://user-images.githubusercontent.com/93108740/140440511-a50098ea-e025-49bd-8a0c-25308022f94c.png)


## 自定义View SelectPhotoBottomView
### 功能需求
1. 全屏显示/半屏显示/隐藏
2. 选择图片


具体请见 https://www.processon.com/view/link/6184867a1efad40ab183de0c

![image](https://user-images.githubusercontent.com/93108740/140442688-a0e30994-591b-47ca-b49a-67acb3812f24.png)


## 图片选择页面
图片选择页面大致分为以下几类
1. Local
2. Facebook
3. Instagram
4. Google Photos
5. Dropbox
6. Drive

所有页面共同的行为如下:https://www.processon.com/view/link/61848b3d7d9c0828a1533c7f
![image](https://user-images.githubusercontent.com/93108740/140443818-93775506-5267-47bd-8347-e74be49fc538.png)


## GooglePhoto
1. GooglePhoto页面除了实现基类 BasePhotoFragment定义的行为之外，其他所有行为都在内部实现（比如数据展示，多级目录展示，选中图片时链接过期问题处理，加载更多逻辑，更新图片选中状态 等）
2. GooglePhoto中的图片数据有对应的数据类型 GooglePhotoBean， 使用时通过扩展方法 转成UI层需要的Photo类型
3. 页面整体结构 UI(Activity/Fragment)--->ViewModel--->Repository
4. GooglePhoto页面图片列表 使用对应的适配器GooglePhotoAdapter

请见 https://www.processon.com/view/link/61849c800e3e744a77ca5c81

![image](https://user-images.githubusercontent.com/93108740/140450502-b42e8cf9-a6b4-4201-b431-41a6d3f04447.png)

