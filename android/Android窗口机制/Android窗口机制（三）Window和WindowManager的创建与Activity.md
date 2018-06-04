https://www.jianshu.com/p/6afb0c17df43

笔记：
  一个Activity对应一个Window ，且有一个mWindow和mWindowManager成员变量。WindowManager的实现类是WindowManagerImpl。WindowManagerImpl的方法是通过WindowManagerGlobal（单例）代理实现。
  mDecor也是Activity的成员变量
