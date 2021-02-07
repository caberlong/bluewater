package(                                                                                            
  default_visibility = ["//:docker"]                                                                   
)

load("@io_bazel_rules_docker//cc:image.bzl", "cc_image")

cc_image(
    name = "helloworld",
    srcs = ["helloworld.cc"],
)
