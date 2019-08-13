workspace(name = "prometheus")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "io_bazel_rules_go",
    remote = "https://github.com/bazelbuild/rules_go.git",
    tag = "0.19.1",
)

git_repository(
    name = "bazel_gazelle",
    remote = "https://github.com/bazelbuild/bazel-gazelle.git",
    tag = "v0.18.1",
)

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

go_rules_dependencies()

go_register_toolchains()

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies", "go_repository")

gazelle_dependencies()

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

go_repository(
    name = "com_github_prometheus_prometheus",
    build_extra_args = ["--exclude=vendor"],
    build_file_proto_mode = "disable",
    importpath = "github.com/prometheus/prometheus",
    patches = ["//:BUILD.bazel.patch"],
    tag = "v2.8.1",
)
