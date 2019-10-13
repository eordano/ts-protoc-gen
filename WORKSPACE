workspace(
    name = "ts_protoc_gen",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "ad4be2c6f40f5af70c7edf294955f9d9a0222c8e2756109731b25f79ea2ccea0",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/0.38.3/rules_nodejs-0.38.3.tar.gz"],
)

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories")

node_repositories(package_json = ["//:package.json"])

load("@build_bazel_rules_nodejs//:defs.bzl", "yarn_install")

yarn_install(
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
)

load("@npm//:install_bazel_dependencies.bzl", "install_bazel_dependencies")

install_bazel_dependencies()

load("@npm_bazel_karma//:package.bzl", "npm_bazel_karma_dependencies")

npm_bazel_karma_dependencies()

load("@io_bazel_rules_webtesting//web:repositories.bzl", "web_test_repositories")
web_test_repositories()

load("@io_bazel_rules_webtesting//web/versioned:browsers-0.3.2.bzl", "browser_repositories")
browser_repositories(
    chromium = True,
)

load("@npm_bazel_typescript//:index.bzl", "ts_setup_workspace")

ts_setup_workspace()

load("@ts_protoc_gen//:defs.bzl", "typescript_proto_dependencies")

typescript_proto_dependencies()
