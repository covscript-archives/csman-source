The man behind Covariant Script who maintains all versions, packages and lots of trivial stuffs for programmers.

**We call him `csman`.**

## 平台
- [ ] Windows
    - [ ] MSVC [Experimental]
        - [ ] AMD64
        - [ ] i386
        - [ ] ARM64
        - [ ] ARM
    - [ ] MinGW-w64
        - [ ] AMD64 [Mainstream]
        - [ ] i386
- [ ] Linux
    - [ ] GCC
        - [ ] AMD64 [Mainstream]
        - [ ] i386
        - [ ] ARM
        - [ ] MIPS
- [ ] macOS
    - [ ] clang
        - [ ] AMD64 [Mainstream]

## CSMAN 源定义
- 根目录
    - csman.json
        - Version: 字符串，标示CSMAN标准版本
        - BaseUrl: 字符串，标示当前源基础地址
        - Platform: ["平台"...]
    - 平台(`Generic 或 OS_Compiler_Architecture`, 如`Win32_MSVC_AMD64`)
        - 注意：CovScript Package依赖标准版本号，CovScript Extension依赖二进制版本号，但这两者在书写依赖时也可以依赖特定版本的CovScript Runtime
        - csman.json
            - Version: {("VER":"运行时版本号" 或 "STD":"标准版本号" 或 "ABI":"二进制版本号")...}
            - Latest: [Version]
            - Nightly: [Version]
        - 运行时版本号(`VER_Master.Major.Minor.Revise`, 如`VER_2.3.3.3`)
            - csman.json
                - STD: 字符串，标示该运行时遵循的标准版本
                - ABI: 字符串，标示该运行时的二进制版本
                - RTM: 字符串，标示运行时环境的包名，一般为`cs.runtime`
                - DEV: 字符串，标示开发环境的包名，一般为`cs.develop`
                - ContentUrl: 字符串，可选，指定压缩包的存放地址
            - 发行包
                - CSMAN 包格式，打包成相应的ZIP压缩包
            - 开发包
                - CSMAN 包格式，打包成相应的ZIP压缩包
        - 标准版本号(`STD_XXXXXX`，如`STD_200201`) 或 二进制版本号(`ABI_XXXXXX`，如`ABI_200201`)
            - 注意：所有的包必须依赖一个运行时版本
            - csman.json
                - {(包名(字符串):描述对象)...}
                - 描述对象格式:
                    - Description: 字符串，包的描述
                    - Author: 字符串，作者
                    - Verizon: ["版本号"...]
                    - Latest: [Version]
                    - Nightly: [Version]
                    - ContentUrl: 字符串，可选，指定压缩包的存放地址
            - 扩展包(`包名_版本号.zip`，如`cics.darwin_1.0.zip`)
                - CSMAN 包格式，打包成相应的ZIP压缩包

## CSMAN 包格式
- csman.json
    - State: (Stable 或 Unstable 或 Preview) 字符串，指示版本状态
    - Dependencies: {("包名":"latest 或 nightly 或 版本号")...}
    - Contents: {("类型(BIN(可执行文件) 或 DEV(源代码头文件) 或 LIB(库文件) 或 CSP(CovScript包) 或 CSE(CovScript扩展) 或 DOC(文档))":"文件名 或 目录名")...}
- 内容: 需符合csman.json的描述
