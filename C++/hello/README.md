### 构建命令

执行以下命令来构建目标：

```bash
bazel --batch build //:hello
```

### 构建结果

在构建完成后，你会在 `bazel-bin` 目录中找到生成的文件：

- **`bazel-bin/hello`**: 这是构建出的可执行文件。
- **`bazel-bin/libhello.a`**: 这是 `cc_library` 规则生成的静态库文件。

### 规则说明

- **`cc_library`**:
  - 用于将 C++ 源文件编译成库。默认情况下，`cc_library` 规则生成一个静态库（`.a` 文件），该库包含了指定源文件的编译结果。
  - 示例定义如下：

    ```python
    cc_library(
        name = "hello",
        srcs = ["hello.cpp"],  # 库的源文件
        hdrs = ["hello.h"],    # 库的头文件
    )
    ```

- **`cc_binary`**:
  - 用于创建一个可执行文件，依赖于指定的库。
  - 示例定义如下：

    ```python
    cc_binary(
        name = "hello_program",
        srcs = ["main.cpp"],   # 主程序的源文件
        deps = [":hello"],    # 依赖于 `hello` 库
    )
    ```

### 总结

- `cc_library` 规则将源文件编译成静态库，并生成 `.a` 文件。
- `cc_binary` 规则将静态库与主程序文件链接，生成可执行文件。
- `bazel-bin` 目录包含了构建出的结果文件，包括静态库和可执行文件。

