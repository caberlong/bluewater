package(                                                                                            
  default_visibility = ["//:docker"]                                                                   
)

load("@io_bazel_rules_docker//cc:image.bzl", "cc_image")

cc_binary(
    name = "helloworld_cc_binary",
    srcs = ["helloworld.cc"],
)

cc_image(
    name = "helloworld",
    deps = [":helloworld_cc_binary"]
)
