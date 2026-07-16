## 098 工具链与 Presets 工作流

为桌面调试、Ninja 发布和 ARM 交叉编译建立 CMakePresets.json；ARM 配置使用独立工具链文件，不在项目脚本中修改编译器。

#### 输入格式：

提供本机编译器以及 arm-none-eabi 工具链路径；开发者可通过环境或用户预设补充本机路径。

#### 输出格式：

cmake --list-presets 展示清晰预设；三个预设使用独立构建目录和正确缓存变量。

#### 示例 1：

> 输入：cmake --preset dev
>
> 输出：配置到 build/dev，启用测试与调试信息

#### 示例 2：

> 输入：cmake --preset arm-release
>
> 输出：使用 ARM 工具链配置到 build/arm-release，不执行目标平台程序

#### 提示：

- 区分 configurePresets、buildPresets 和 testPresets，并合理继承。
- 工具链文件设置 CMAKE_SYSTEM_NAME、编译器及查找根路径策略。
- 不把个人绝对路径提交到共享预设。

