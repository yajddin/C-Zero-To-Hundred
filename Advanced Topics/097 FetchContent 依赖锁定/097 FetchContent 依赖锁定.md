## 097 FetchContent 依赖锁定

项目依赖外部 tinylog。优先使用系统已安装包；找不到时才通过 FetchContent 获取，并锁定到确定提交。还要允许离线用户传入本地源码目录。

#### 输入格式：

用户可设置 USE_SYSTEM_TINYLOG、FETCHCONTENT_SOURCE_DIR_TINYLOG 或完全使用默认配置。

#### 输出格式：

三种来源最终都提供统一目标 tinylog::tinylog，主项目其余部分无需判断来源。

#### 示例 1：

> 输入：系统已安装兼容 tinylog，USE_SYSTEM_TINYLOG=ON
>
> 输出：使用系统包，不发起下载

#### 示例 2：

> 输入：指定 FETCHCONTENT_SOURCE_DIR_TINYLOG=/src/tinylog
>
> 输出：使用本地源码，可完全离线配置

#### 提示：

- 使用 FetchContent，固定 GIT_TAG 到提交哈希而非浮动分支。
- 不在库项目中无条件下载依赖，避免劫持上层工程选择。

