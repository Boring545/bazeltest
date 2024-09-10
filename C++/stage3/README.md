# Stage 3
注意：文件.bashrc，其存储了一些执行时的参数，其中build:linux --action_env=BAZEL_DO_NOT_DETECT_CPP_TOOLCHAIN=1 或类似的描述可能导致C项目构建失败，原因大致为C规则的问题，需要使其适配RISCV     

In this stage we step it up and showcase how to integrate multiple ```cc_library``` targets from different packages.

Below, we see a similar configuration from Stage 2, except that this BUILD file is in a subdirectory called lib. In Bazel, subdirectories containing BUILD files are known as packages. The new property ```visibility``` will tell Bazel which package(s) can reference this target, in this case the ```//main``` package can use ```hello-time``` library. 

```
cc_library(
    name = "hello-time",
    srcs = ["hello-time.cc"],
    hdrs = ["hello-time.h"],
    visibility = ["//main:__pkg__"],
)
```

To use our ```hello-time``` library, an extra dependency is added in the form of //path/to/package:target_name, in this case, it's ```//lib:hello-time```

```
cc_binary(
    name = "hello-world",
    srcs = ["hello-world.cc"],
    deps = [
        ":hello-greet",
        "//lib:hello-time",
    ],
)
```

To build this example, use
```
bazel build //main:hello-world
```
