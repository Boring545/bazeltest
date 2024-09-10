## 项目结构

本项目展示了如何使用 Bazel 构建一个 Python 程序，并配置 `WORKSPACE` 文件来引入 `rules_python` 规则，并且使用本地安装的 Python 解释器。

- **`BUILD`**: Bazel 构建配置文件。
- **`WORKSPACE`**: Bazel 工作区配置文件。
- **`hello.py`**: Python 源文件。

## `BUILD` 文件内容

以下是 `BUILD` 文件的内容，用于定义 Python 可执行文件：

```python
py_binary(
    name = "hello",
    srcs = ["hello.py"],
    deps = [],
)
```

- **`py_binary`**: 用于定义 Python 可执行文件。
  - **`name`**: 目标名称，这里是 `hello`。
  - **`srcs`**: 源文件列表，这里包含 `hello.py`。
  - **`deps`**: 依赖项列表，这里为空，表示没有额外的依赖。

## 注意要点
1. 在 `WORKSPACE` 中，将类似 `python_interpreter_target = "@python39_host//:python"` 的内容替换为 `python_interpreter = "/usr/bin/python3"`。
2. 删除类似 `load("@python3_10//:defs.bzl", "interpreter")` 的内容。

## 执行构建

通过以下命令执行构建：

```bash
bazel --batch build //:hello
```

## 构建输出

在构建完成后，生成的可执行文件将位于 `bazel-bin` 目录下，文件名为 `hello`。你可以通过以下命令运行它：

```bash
bazel-bin/hello
```

构建并运行后，终端应显示：

```
Hello, Bazel!
```
