load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

rules_python_version = "0.13.0" 

http_archive(
    name = "rules_python",
    sha256 = "090bfe913d05878db759cdab77061042ff826c3a96b8853aa695405f8c992af5",
    strip_prefix = "rules_python-{}".format(rules_python_version),
    url = "https://github.com/bazelbuild/rules_python/archive/{}.zip".format(rules_python_version),
)

load("@rules_python//python:repositories.bzl", "python_register_toolchains")

python_register_toolchains(
    name = "python3_8",
    python_version = "3.8",
)

load("@python3_8//:defs.bzl", "interpreter")

load("@rules_python//python:pip.bzl", "pip_parse")

pip_parse(
   name = "py_deps",
   requirements_lock = "//infra/python:requirements_lock.txt",
)
load("@py_deps//:requirements.bzl", "install_deps")
install_deps()