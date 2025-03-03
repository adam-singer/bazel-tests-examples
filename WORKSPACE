load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "b8a1527901774180afc798aeb28c4634bdccf19c4d98e7bdd1ce79d1fe9aaad7",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.4.1/bazel-skylib-1.4.1.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.4.1/bazel-skylib-1.4.1.tar.gz",
    ],
)

http_archive(
    name = "io_bazel_rules_scala",
    # sha256 = "141a3919b37c80a846796f792dcf6ea7cd6e7b7ca4297603ca961cd22750c951",
    strip_prefix = "rules_scala-6.6.0",
    url = "https://github.com/bazelbuild/rules_scala/archive/refs/tags/v6.6.0.tar.gz",
)

# https://github.com/bazel-contrib/rules_jvm_external?tab=readme-ov-file#with-workspace-file-legacy
# maven_install(
#     artifacts =  ["com.github.ghostdogpr:caliban_2.13:2.0.1"],
#     maven_install_json = "@//:maven_install.json",
#     repositories = [
#         "https://maven.google.com",
#         "https://repo1.maven.org/maven2",
#     ],
#     version_conflict_policy = "pinned",
#     fetch_sources = True,
# )

load("@io_bazel_rules_scala//:scala_config.bzl", "scala_config")
scala_config(scala_version = "2.13.12")

load("@io_bazel_rules_scala//scala:scala.bzl", "rules_scala_setup", "rules_scala_toolchain_deps_repositories")

rules_scala_setup()

rules_scala_toolchain_deps_repositories(fetch_sources = True)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")
rules_proto_dependencies()
rules_proto_toolchains()

load("@io_bazel_rules_scala//scala:toolchains.bzl", "scala_register_toolchains")
scala_register_toolchains()

register_toolchains(
    "//:semanticdb_toolchain",
)

load("@io_bazel_rules_scala//testing:scalatest.bzl", "scalatest_repositories", "scalatest_toolchain")
scalatest_repositories()
scalatest_toolchain()

