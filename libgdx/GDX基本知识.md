### 基本概念
1. Texture 纹理
1. SpriteBatch 纹理画布

### 6大系统交互接口
* `Gdx.app`        Application： 代表一个游戏应用的实例，通常在平台的启动器中被实例化并启动API客户端（core 子项目可以看做是 API 客户端）。该接口实例会将应用程序层面的事件通知API客户端，比如窗口大小的改变。Application 还提供了日志输出系统和各种查询方法，例如内存的使用情况，操作系统版本信息，获取系统剪贴板等。
* `Gdx.files`      Files： 暴露平台底层的文件系统，提供统一的对文件操作的抽象接口。
* `Gdx.input`      Input： 通知 API 客户端用户的输入，例如鼠标点击，键盘按键按下，触摸屏幕和传感器事件。同时还支持轮询和事件驱动处理。
* `Gdx.net`        Net： 提供一个跨平台的通过 HTTP/HTTPS 访问资源的方法，还可以创建 TCP 服务和客户端 sockets。
* `Gdx.audio`      Audio： 可用于创建音效和音乐实例，提供重放音效和音乐的方法，同时可以直接访问 PCM 音频的输入输出设备。
* `Gdx.graphics`   Graphics： 暴露 OpenGL ES 2.0 接口。还提供查询帧率，渲染时间步，获取屏幕宽高等方法。

### 生命周期事件方法
* `create()`： 当应用被创建时调用一次。
* `resize(int width, int height)`： 游戏屏幕尺寸改变并且不处于暂停状态将被调用，在 create() 方法之后也会被调用一次。
* `render()`： ApplicationListener 中的游戏循环渲染方法，每时每刻都在被调用。游戏逻辑的更新通常也是在这个方法中被执行。
* `pause()`： 当游戏界面被新的一个界面覆盖时（例如按下 Home 键回到主界面时被主界面覆盖，来电时被来电界面覆盖），该方法将被调用。通常在这里保存暂停时的游戏状态。
* `resume()`： 被其他界面覆盖后（pause 状态后），重新回到游戏界面时，该方法被调用。
* `dispose()`： 当应用被销毁时调用。
![](http://img.blog.csdn.net/20151205160048806)

### 基础概念
1. `纹理类（Texture）` 负责解码一个图片文件并加载到 GPU 内存，可以看做代表的是一张图片,一个图片文件被加载为 Texture 实例后，如果不再需要使用到这个 texture，需要手动调用释放资源的方法 texture.dispose() 进行资源释放
2. `纹理画布（SpriteBatch）`英文直译则为“精灵批处理”，它主要用于将纹理绘制到屏幕上，类似于 Android 和 HTML5 中的 Canvas （画布），因此这里我姑且把它称为“纹理画布”。SpriteBatch 将对所有绘制的纹理进行批处理并经过优化后发送到 GPU
在绘制前后必须调用 batch.begin() 和 batch.end() 方法， 在不需要这个 SpriteBatch 对象时，需要手动调用 batch.dispose() 方法释放资源。
3. `TextureRegion（纹理区域）` 表示 Texture（纹理）的一部分矩形区域（当然也可以表示整个 Texture 区域），可以用来绘制纹理中的一部分显示在屏幕上
4. `Sprite`（精灵）继承自 TextureRegion（纹理区域），本质上可以看作是一个 TextureRegion，但它比 TextureRegion 要强大的多，封装得更完善，
   除了表示一张图片外，还附加拥有许多属性，例如 在屏幕中的位置/坐标（绘制起点），缩放比，旋转角度，透明度/颜色 等。Sprite 更加具体地描述了游戏中的一个元素（游戏人物，道具，背景图片等），可以看做是一张图片加上绘制这张图片时附加的各种变换属性的封装。
   Sprite 可以看做是如下构成：
   ```
   Sprite = Texture/TextrueRegion + 属性（坐标，缩放比，旋转角度，是否X / Y轴方向取镜像，透明度/颜色 等）
   ```



GDX <------> Android
Game         Activity
Screen       Fragment
Stage        Layout
group        ViewGroup
Actor        View

![](http://img.blog.csdn.net/20151205170644774)
