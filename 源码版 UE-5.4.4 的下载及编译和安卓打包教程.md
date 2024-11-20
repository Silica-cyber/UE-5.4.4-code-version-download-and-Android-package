## 源码版 UE-5.4.4 的下载及编译和安卓打包教程（Windows系统）

0. **注意事项⚠：**

    **0.1 在进行下列工作之前，首先看看自身的电脑配置，笔者的笔记本配置为：**
    	· 运行内存：16 GB
    	· 存储空间：512 GB（最好还是1TB）
    	· 处理器：Intel(R) Core(TM) i5-10300H CPU @ 2.50GHz   2.50 GHz
    	· 显卡：RTX 1650
    	该配置能够勉强下载并运行源码版 UE，并进行安卓打包。

    **0.2 下一步是电脑分盘（仅供参考）：**
    	C 盘最好留有 50GB 的空闲（虽然并不是安装在C盘，但安装 Android Studio 需要默认 C 盘路径，以及打包时也要占用 C 盘），其他盘有一个应为 250 GB（留有 230 GB 的空闲也可），另一个也留有比较多的位置，用于存储 UE 的项目。

    ​	<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120102722867.png" alt="image-20241120102722867"  />

    **0.3 其他硬性条件：**
    	请在科学上网的情况下进行各种下载及安装（Android Studio 官网必须翻墙了）。当然各位也可以使用本文附上的各种安装包（UE 源码，Android Studio 2022版）：

    **通过百度网盘分享的文件：下载**
    **链接：https://pan.baidu.com/s/1HmzDFK7leln1qNi-DKiv_w** 
    **提取码：xyzh** 
    **--来自百度网盘超级会员V5的分享**

    ​	虽然可以避过下载要翻墙，但安装时也还是需要科学上网的。

    ​	其次，对官方攻略及其他攻略抱有选择性吸收的心态，不要全盘照搬照做。
    ​	最后，请在执行以下步骤的过程前，做好长期奋战的心理准备，因为你可能会遇到许多报错，让人心力交瘁，笔者从开始查询相关资料起，直到第 5 天才成功打包。总之相信自己，干就完事！

1. **获得源码版 UE-5.4.4（以下整合自官方攻略）**

   提示：笔者提供的下载链接里，可以直接下载源码版 UE 5.4.4 的压缩包（这是从官网上下的，如果你不想通过 Git 克隆库的方法进行源码版 UE 的下载，就可以下这个）并解压在 250G 的大盘里，并不清楚后续步骤是否需要用到该步骤做到的账号关联，建议还是要关联账号。

   总结：你需要注册 GitHub 账号，并注册 Epic 账号，然后在 Epic 中选择关联你的 GitHub 账号，邮件通过后就能访问 GitHub 上 UE 的源代码了，注意首页一定是 5.5 的，要下载 5.4.4 就要看右边的release 里。

   ![image-20241120104150703](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120104150703.png)

   [下载虚幻引擎源代码 | 虚幻引擎 5.4 文档 | Epic Developer Community | Epic Developer Community](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/downloading-unreal-engine-source-code?application_version=5.4)

   该文字描述的图文版：

   [GitHub上的虚幻引擎 - Unreal Engine](https://www.unrealengine.com/zh-CN/ue-on-github)

2. **编译源码版 UE-5.4.4（对应下载源代码那一块）**

   大体需要根据官方网站给出的方法进行编译。但里面的几个小步骤需要注意

   下图是官方网站给出的方法，但第二步请安装 Visual Studio Community 2022（[为虚幻引擎C++项目设置Visual Studio开发环境 | 虚幻引擎 5.5 文档 | Epic Developer Community | Epic Developer Community](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine)），并勾选安装右边的几个拓展和一个 SDK.

   第三步，则要在运行 setup.bat（批处理文件）之前先右键点击“编辑”，将：
   set PROMPT_ARGUMENT=--prompt 语句后面加上“ --threads=64”，注意 -- 号前有个空格，不然运行时无法识别。
   这部分参考了[让虚幻4源码Setup.bat下载速度飞起 - 哔哩哔哩](https://www.bilibili.com/opus/481312434835748133#:~:text=很多人喜欢从github下载虚幻源码来编译“完整版”的虚幻4，但全程就一个字来形容，慢。。。)。我们要做的就是增加线程，提高速度（笔者的笔记本用64已经跑满了，不加的话是很慢的小水管），不要试图减少其他部分以降低占用空间，后面可能会报错，让你又要重新运行 setup.bat（而且你并不确定重新运行 setup.bat 是否能够让之前下载的覆盖掉，所以我在成功之前都是删除整个 UnrealEngine-5.4.4-release 文件然后重新解压）。
   第五步，参考[visual studio2022编译unreal engine5.4.4源码_vs2022编译ue5-CSDN博客](https://blog.csdn.net/aoxuestudy/article/details/141717221)。点开 UE5.sln 之后，先对 UE 进行右键，设为启动项目，选择 development editor，如果有提示需要安装额外的组件就安装，提示该解决方案含有漏洞的包可以不管，点击 UE5 之后出现的检查界面也可以不管。官方给出的编译时间仅供参考，像笔者的笔记本就用了 7 个小时左右的时间才完成。。。

   ![image-20241120154747969](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120154747969.png)

   ![image-20241120154804711](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120154804711.png)

   ![image-20241120154816045](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120154816045.png)

   检查后会有一堆报错，但实际是能够完成打包的，所以不用管

   ![image-20241120161017196](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120161017196.png)

   ![image-20241120104948007](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120104948007.png)

   官方给出的方法

   ![image-20241120120534735](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120120534735.png)

   下载并安装 VS2022 时需要勾选的东西

   ![image-20241120154240108](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120154240108.png)

   ![image-20241120155045819](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120155045819.png)

   编译成功

3. **安卓打包（将制作好的项目打包成手机应用安装包.apk）**

   编译成功后，每次想要打开 UE5 就可以通过 VS 来打开虚幻引擎，按 F5 运行，就能看到虚幻编辑器弹出来了，操作界面也打开了。要进行打包，就要先创建一个项目，建议先创建一个 c++ 的空项目，目标平台为移动平台（即手机等产品），质量预设选择可缩放（笔者这里选最大会生成失败）。

   ![image-20241120160458767](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120160458767.png)

   建好之后，后续可以从 VS 中打开新建的项目，不需要通过引擎去打开项目（笔者运行内存不够支撑引擎和项目一起打开）。同样是点开后 F5 生成运行项目。

   ![image-20241120160909221](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120160909221.png)

   打开项目可以后可以对当前视图进行一些场景编辑等操作，保存之后，既要对其进行安卓打包了。首先建议尝试点击编辑器里的选项，使用 Turnkey 安装 Android Studio。参考这个[【UE5.4】猫猫都能看懂的Android打包新版攻略_ue5.4安卓打包-CSDN博客](https://blog.csdn.net/qq_35587645/article/details/139207695)。

   如果像我一样安装报错了，可以先参考我的做法（链接到惨痛的教训），然后走官方给出的路线：[如何为你的虚幻引擎开发环境设置Android SDK和NDK | 虚幻引擎 5.5 文档 | Epic Developer Community | Epic Developer Community](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/advanced-setup-and-troubleshooting-guide-for-using-android-sdk)，做完后再回到上一个参考链接中查看打包操作。

   Turnkey 安装报错![image-20241120162057972](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120162057972.png)

   一般按照上述步骤下来，打包就能够成功了（注意 C 盘容量）。其实随着打包次数增多，打包时间也会有所下降。

   最后打包成功![image-20241120162923581](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120162923581.png)

   第一次打包失败![image-20241120162831862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120162831862.png)

   

   4. 惨烈的教训——网上攻略与版本不对应
      写在前排：如果你想要查找一个从0开始，即电脑上完全没有安装过 UE ，的安装源码版 UE 的攻略，那么请务必注意网上各种攻略书写的时间，以及这份攻略对应的 UE 版本！如果使用了旧版本（5.3 对比 5.4 就已经算旧版本了）的攻略，那么最后打包的时候就会失败，出现 Unknown Error！

> ![](C:\Users\Administrator\Pictures\Screenshots\屏幕截图(145).png)
>
> 笔者一开始使用了[UE5.2源码版获取安装，编译，新建项目，Android打包全流程（详解）_ue源码版-CSDN博客](https://blog.csdn.net/m0_63673681/article/details/132857358)，该攻略不适合 5.4.4 的安装
>
> 如果已经不小心使用了该攻略（前面的源码版安装与官方差不多，后面Android Studio部分则完全不适用），那么要做的就是完全卸载旧版本的Android Studio，[完全卸载Android studio教程_android studio如何彻底卸载重装-CSDN博客](https://blog.csdn.net/qq_46941656/article/details/119918496)，最后在搜索栏中搜索“编辑系统环境变量”检查，点击环境变量，如果没有删除则一个个对着路径删除 ANDROID_HOME、JAVA_HOME、NDK_ROOT、NDKROOT 这四个变量。
>
> ![image-20241120100024315](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120100024315.png)
>
> ![image-20241120100130625](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20241120100130625.png)
>
> 如果删除后再安装新的Android Studio版本（UE官方推荐 Android Studio Version: Flamingo 2022.2.1 Patch 2 May 24, 2023）时出现无法勾选下载的情况参照该攻略：[Android Studio SDK无法勾选安装的解决方案_sdk components setup无法勾选 sdk-CSDN博客](https://blog.csdn.net/qq_42257666/article/details/129781420)，修改Hosts文件即可（直接复制粘贴，不行再查找IP）。

最后：本攻略在《Persona3》经典天鹅绒房间BGM **全ての人の魂の詩** 的优美乐声下完成，该BGM有助于帮助为源码版UE下载和UE项目安卓打包焦头烂额的人们平复心情，笔者倾情推荐。