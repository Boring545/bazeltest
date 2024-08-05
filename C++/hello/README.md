bazel --batch build //:hello 执行构建
bazel-bin/hello为可执行文件
cc_library 函数将c文件制作为依赖，这里默认生成一个静态库，然后供给cc_binary构建为二进制文件
