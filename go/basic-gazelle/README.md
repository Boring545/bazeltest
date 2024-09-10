# Go Rules Tutorial
首先一般在WORKSPACE里找到加载go规则的地方，替换我修改的go规则
然后找到go_register_toolchains这个函数，修改参数为version = "host"，即使用本地的go，当然，这需要在本地提前安装好riscv可用的go
```
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "3ea7ab202cd1805abf7aec405658ef90f216098325795ea6b6f23b41a998c949",
    urls = [
        "https://github.com/Boring545/rules_go/releases/download/v0.50.1/rules_go-v0.50.1.zip",
    ],
)

#load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

#go_rules_dependencies()

go_register_toolchains(version = "host")
```
