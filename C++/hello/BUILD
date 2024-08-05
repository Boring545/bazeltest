# BUILD

cc_library(
    name = "lhello",
    srcs = ["hello.cpp"],
    hdrs = ["hello.h"],
)

cc_binary(
    name = "hello",
    srcs = ["main.cpp"],
    deps = [":lhello"],
)

