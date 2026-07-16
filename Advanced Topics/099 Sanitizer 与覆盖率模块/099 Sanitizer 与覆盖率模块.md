## 099 Sanitizer 与覆盖率模块

编写可复用 CMake 模块 ProjectAnalysis.cmake，为项目目标按选项启用 AddressSanitizer、UndefinedBehaviorSanitizer 或覆盖率。

这些能力只用于支持的编译器和配置，不传播给已安装消费者，也不能同时启用互不兼容的分析模式。

#### 输入格式：

配置选项 ENABLE_ASAN、ENABLE_UBSAN、ENABLE_COVERAGE，目标列表由调用方传入。

#### 输出格式：

编译与链接选项成对设置；非法组合在配置阶段给出清晰错误；普通 Release 构建不含分析参数。

#### 示例 1：

> 输入：cmake --preset asan
>
> 输出：测试目标带地址与未定义行为检测，ctest 可正常运行

#### 示例 2：

> 输入：同时启用 ENABLE_COVERAGE 和 ENABLE_ASAN
>
> 输出：配置失败并说明选项冲突

#### 提示：

- 优先把分析配置封装为 INTERFACE 目标，再按需链接到本项目目标。
- 使用 CheckCCompilerFlag 验证能力，并用生成表达式限制配置。
- 覆盖率报告命令应是显式目标，不应在每次普通构建时自动执行。

