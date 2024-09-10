# Go Rules 教程

首先，在 `WORKSPACE` 文件中找到加载 Go 规则的部分，然后替换为修改后的 Go 规则。

接着，找到 `go_register_toolchains` 函数，并将参数修改为 `version = "host"`，即使用本地安装的 Go 编译器。当然，这要求本地已经安装了 RISC-V 可用的 Go 编译器。

以下是修改后的 `WORKSPACE` 配置：

```python
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "3ea7ab202cd1805abf7aec405658ef90f216098325795ea6b6f23b41a998c949",
    urls = [
        "https://github.com/Boring545/rules_go/releases/download/v0.50.1/rules_go-v0.50.1.zip",
    ],
)

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

go_rules_dependencies()

go_register_toolchains(version = "host")
```

## 构建步骤

在当前目录下，可以执行以下命令来构建所有内容：

```bash
bazelisk build //...
```

接着，运行以下命令来运行项目：

```bash
bazelisk run //:basic-gazelle
```

更多详细信息，请参考 [Bazel Go Rules 教程](https://bazel-contrib.github.io/SIG-rules-authors/go-tutorial.html)。
