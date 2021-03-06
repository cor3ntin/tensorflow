load("//tensorflow:tensorflow.bzl", "tf_py_test")

package(
    licenses = ["notice"],  # Apache 2.0
)

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)

py_library(
    name = "impl",
    srcs = [
        "api.py",
        "conversion.py",
    ],
    srcs_version = "PY2AND3",
    visibility = ["//tensorflow:__subpackages__"],
    deps = [
        "//tensorflow/python:platform",
        "//tensorflow/python:util",
        "//tensorflow/python/autograph/converters",
        "//tensorflow/python/autograph/core",
        "//tensorflow/python/autograph/operators",
        "//tensorflow/python/autograph/pyct",
        "//tensorflow/python/autograph/pyct/static_analysis",
        "//tensorflow/python/autograph/utils",
        "@gast_archive//:gast",
    ],
)

tf_py_test(
    name = "api_test",
    srcs = ["api_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    tfrt_enabled = True,
    deps = [
        ":impl",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python/autograph/core:test_lib",
        "//tensorflow/python/autograph/utils",
        "//third_party/py/numpy",
    ],
)

tf_py_test(
    name = "conversion_test",
    srcs = ["conversion_test.py"],
    tfrt_enabled = True,
    deps = [
        ":impl",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python/autograph/impl/testing:pybind_for_testing",
        "@gast_archive//:gast",
    ],
)
