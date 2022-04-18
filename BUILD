# bgfx.bazel - bgfx building in bazel
# Author: Alex Rozgo <alex.rozgo@gmail.com>

load("@rules_cc//cc:defs.bzl", "cc_library")

package(default_visibility = ["//visibility:public"])

srcs = [
    "src/**/*.cpp",
    "3rdparty/libsquish/*.cpp",
    "3rdparty/libsquish/*.h",
    "3rdparty/libsquish/*.inl",
    "3rdparty/edtaa3/*.cpp",
    "3rdparty/edtaa3/*.h",
    "3rdparty/etc1/*.cpp",
    "3rdparty/etc1/*.h",
    "3rdparty/etc2/*.cpp",
    "3rdparty/etc2/*.hpp",
    "3rdparty/nvtt/**/*.cpp",
    "3rdparty/nvtt/**/*.h",
    "3rdparty/nvtt/**/*.inl",
    "3rdparty/pvrtc/*.cpp",
    "3rdparty/pvrtc/*.h",
    "3rdparty/astc/*.cpp",
    "3rdparty/astc/*.h",
    "3rdparty/tinyexr/*.h",
]

srcs_iqa = [
    "3rdparty/iqa/include/*.h",
    "3rdparty/iqa/source/*.c",
]

# Break out iqa to applyu
cc_library(
    name = "iqa",
    srcs = glob(srcs_iqa),
    hdrs = glob([
        "**/*.h",
    ]),
    copts = [
    ],
    includes = [
        "3rdparty/iqa/include",
    ],
)

cc_library(
    name = "bimg-linux",
    srcs = glob(srcs),
    hdrs = glob([
        "**/*.h",
        "src/bimg_p.*",
        "3rdparty/lodepng/*.cpp",
    ]),
    copts = [
        "-Wno-class-memaccess",
    ],
    includes = [
        "3rdparty",
        "3rdparty/iqa/include",
        "3rdparty/nvtt",
        "include",
    ],
    deps = [
        "iqa",
        "//bimg/3rdparty/astc-codec:astc_codec",
        "//bx:bx-linux",
    ],
)

cc_library(
    name = "bimg-macos",
    srcs = glob(srcs),
    hdrs = glob([
        "**/*.h",
        "src/bimg_p.*",
        "3rdparty/lodepng/*.cpp",
    ]),
    includes = [
        "3rdparty",
        "3rdparty/iqa/include",
        "3rdparty/nvtt",
        "include",
    ],
    deps = [
        "//bimg/3rdparty/astc-codec:astc_codec",
        "//bx:bx-macos",
    ],
)
