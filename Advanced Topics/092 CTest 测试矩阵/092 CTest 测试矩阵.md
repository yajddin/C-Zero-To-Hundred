## 092 CTest 测试矩阵

为 calc 库建立 CTest 测试。一个 test_calc 可执行程序接收操作与参数；注册加、减、边界值和预期失败用例，并为测试添加标签。

#### 输入格式：

通过 BUILD_TESTING 控制是否构建测试，默认行为遵循 CTest 模块约定。

#### 输出格式：

ctest 能发现所有测试；正确实现时全部通过，错误实现时给出明确失败用例。

#### 示例 1：

> 输入：ctest --test-dir build -L unit --output-on-failure
>
> 输出：所有 unit 测试通过

#### 示例 2：

> 输入：ctest --test-dir build -R overflow
>
> 输出：只运行名称匹配 overflow 的测试

#### 提示：

- 使用 include(CTest)、add_test、PASS_REGULAR_EXPRESSION 等功能。
- 测试目标和注册逻辑仅在 BUILD_TESTING 开启时生效。

