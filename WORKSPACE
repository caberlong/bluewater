workspace(name = "bluewater")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# **********************************
# Python
# **********************************
rules_python_version = "c8c79aae9aa1b61d199ad03d5fe06338febd0774" # Latest @ 2020-10-15
http_archive(
    name = "rules_python",
    sha256 = "5be9610a959772697f57ec66bb58c8132970686ed7fb0f1cf81b22ddf12f5368",
    strip_prefix = "rules_python-{}".format(rules_python_version),
    url = "https://github.com/bazelbuild/rules_python/archive/{}.zip".format(rules_python_version),
)
load("@rules_python//python:repositories.bzl", "py_repositories")
py_repositories()

load("@rules_python//python:pip.bzl", "pip_install")

# Create a central repo that knows about the dependencies needed for
# requirements.txt.
# pip_install(
#   name = "my_deps",
#   requirements = "//configs:requirements.txt",
# )

# **********************************
# Docker
# **********************************
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "1698624e878b0607052ae6131aa216d45ebb63871ec497f26c67455b34119c80",
    strip_prefix = "rules_docker-0.15.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.15.0/rules_docker-v0.15.0.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load(
    "@io_bazel_rules_docker//cc:image.bzl",
    _cc_image_repos = "repositories",
)

_cc_image_repos()

#container_pull(
#  name = "java_base",
#  registry = "gcr.io",
#  repository = "distroless/java",
#  # 'tag' is also supported, but digest is encouraged for reproducibility.
#  digest = "sha256:deadbeef",
#)
