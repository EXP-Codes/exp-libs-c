# exp-libs-c
经验构件库（C/C++版）

------

1. 拷贝 x64/Release 目录下的 exp-libs.dll 与 exp-libs.lib 文件到其他项目工程目录


2. 拷贝 exp-libs 目录下需要用到的 *.h 头文件到其他项目工程目录


3. 修改其他项目工程的stdafx.h文件，在其末尾添加：

```
#ifdef DLL_IMPLEMENT  
	#define DLL_API __declspec(dllexport) 
#else  
	#define DLL_API __declspec(dllimport) 
#endif
```


4. 在其他项目工程中把步骤1和步骤2的文件添加到解决方案，即可通过 `*.h` 头文件定义的API进行调用


5. 若其他项目工程在引用这个 exp-libs.dll 模块后，编译时出现以下错误：

> `error LNK2019: 无法解析的外部符号 __declspec(dllimport)`

则很可能是 exp-libs.dll 与该工程的编译平台位数不对（exp-libs.dll默认是64位的）