# GitHubAction



**简介：** Qt 5.12.11 + MSVC 2019 + Win10 21H1 + CMake 3.21.1 仅使用命令行生成一个 Qt 程序

<br>

```bash
// cmd 编译 Qt 64 位项目 
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\VC\Auxiliary\Build\vcvarsall.bat" x64
cmake -G "Visual Studio 16 20179" -A x64 ..
devenv GitHubAction.sln /Build "Release|x64"

// cmd 编译 Qt x86 位项目 
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\VC\Auxiliary\Build\vcvarsall.bat" x86
cmake -G "Visual Studio 16 2019" -A Win32 ..
devenv GitHubAction.sln /Build "Release|Win32"


// PS
添加 "C:\Qt\Qt5.12.11\5.12.11\msvc2017\bin" 到 path 后，cmd 执行 echo %PATH% 使其立即生效
添加 "C:\Qt\Qt5.12.11\5.12.11\msvc2017_64\bin" 到 path 后，cmd 执行 echo %PATH% 使其立即生效
```

<br>

---

msvc 交叉编译：使用 `vcvarsall.bat` 设置命令行编译环境（[参考](https://blog.csdn.net/10km/article/details/51722353)）
`%VS140COMNTOOLS%/VC` 下就有 `vcvarsall.bat`，用于生成命令行编译环境。
如果要在命令行生成 32 位代码，就执行 v`cvarsall x86`
如果要在 32 位系统下生成 64 位代码，就执行 `vcvarsall x86_amd64`
如果要在 64 位系统下生成 32 位代码，就执行 `vcvarsall x86` 或 `vcvarsall amd64_x86`
到了 VS2015，已经支持 arm 平台了，所以如果要生成 arm 平台的代码，就执行 `vcvarsall x86_arm` ；如果你的操作系统是 64 位的也可以 `vcvarsall amd64_arm`

<br>

<br>

> **微软 MSVC**
>
> devenv："C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE\devenv.com"  编译项目实例
> vcvarsall.bat "C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\VC\Auxiliary\Build\vcvarsall.bat" 初始化 msvc 交叉编译的环境（x86/x64）

