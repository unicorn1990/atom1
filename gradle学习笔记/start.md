##### 官网学习
* 学习 Groovy http://docs.groovy-lang.org/
* 学习 Gradle DSL https://docs.gradle.org/current/javadoc/org/gradle/api/Project.html
* 学习 Android DSL和Task http://google.github.io/android-gradle-dsl/current/index.html

##### 任玉刚gradle学习：
1. Groovy基础 http://blog.csdn.net/singwhatiwanna/article/details/76084580
2. 执行时序 http://blog.csdn.net/singwhatiwanna/article/details/78797506
3. 定义Task http://blog.csdn.net/singwhatiwanna/article/details/78898113


##### Gradle脚本的执行时序:
1. 初始化：分析哪些module将被构建，为每个module创建对应的Project实例。根目录的settings.gradle文件将被解析
2. 配置：处理所有模块的build脚本，处理依赖，属性等。这时候每个模块的build.gradle将被解析并配置，这个时候会配置整个task的链表
3. 执行：根据task链表来执行某一特定task，这个task所依赖的其他task都将被提前执行
