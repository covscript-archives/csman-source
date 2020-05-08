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
    - 平台(`Generic 或 OS_Compiler_Architecture`, 如`Win32_MSVC_AMD64`).json
        - 注意：
            - 除运行时包本身，所有的包必须依赖运行时包
            - `cs.runtime`为运行时包，`cs.develop`为开发包，这两个包名独占
            - CovScript Package 依赖标准版本号，CovScript Extension 依赖二进制版本号
        - 通用(`Generic`) 或 标准版本(`STD_XXXXXX`，如`STD_200302`) 或 二进制版本(`ABI_XXXXXX`，如`ABI_200203`)
            - {(包名(字符串):描述对象)...}
            - 描述对象格式:
                - Description: 字符串，包的描述
                - Author: 字符串，作者
                - Verizon: {("版本号":版本对象)...}
                - Stable: [Version]
                - Unstable: [Version]
            - 版本对象格式:
                - STD: 字符串，标示该运行时遵循的标准版本(仅`cs.runtime`和`cs.develop`可用)
                - ABI: 字符串，标示该运行时的二进制版本(仅`cs.runtime`和`cs.develop`可用)
                - Dependencies: {("包名":"Stable 或 Unstable 或 版本号")...}
                - ContentUrl: 字符串，指定压缩包的存放地址

## CSMAN 包格式
- csman.json
    - State: (Stable 或 Unstable 或 Preview) 字符串，指示版本状态
    - Contents: {("文件名 或 目录名":"类型(BIN(可执行文件) 或 DEV(源代码头文件) 或 LIB(库文件) 或 CSP(CovScript包) 或 CSE(CovScript扩展) 或 DOC(文档))")...}
- 内容: 需符合csman.json的描述
