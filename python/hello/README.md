
## 项目结构

本项目展示了如何使用 Bazel 构建一个 Python 程序，并配置 `WORKSPACE` 文件来引入 `rules_python` 规则。以下是项目目录的结构：

```
.
├── BUILD
├── WORKSPACE
└── hello.py
```

- **`BUILD`**: Bazel 构建配置文件。
- **`WORKSPACE`**: Bazel 工作区配置文件。
- **`hello.py`**: Python 源文件。

## `WORKSPACE` 文件内容

### 说明

- **`http_archive`**: 用于从指定 URL 下载并解压 `rules_python` 规则的发布版本。
  - **`name`**: 规则的名称，这里是 `rules_python`。
  - **`urls`**: 规则包的下载链接。
  - **`strip_prefix`**: 解压缩时去除的前缀，用于正确的目录结构。

- **`py_repositories`**: 引入 `rules_python` 规则所需的 Python 依赖和工具链。

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

## 示例

**`hello.py`** 内容示例：

```python
def main():
    print("Hello, Bazel!")

if __name__ == "__main__":
    main()
```

构建并运行后，终端应显示：

```
Hello, Bazel!
```

## 总结

- `WORKSPACE` 文件配置了 `rules_python` 规则和其他设置。
- `BUILD` 文件定义了一个 Python 可执行文件 `hello`。
- 构建命令生成的可执行文件位于 `bazel-bin` 目录。
- 可以通过 `bazel-bin/hello` 运行生成的 Python 可执行文件。
```

这个 `README` 文件提供了 `WORKSPACE` 文件的详细配置说明、构建和运行 Python 程序的步骤，以及如何组织项目结构。如果需要进一步的帮助或修改，请告诉我！
