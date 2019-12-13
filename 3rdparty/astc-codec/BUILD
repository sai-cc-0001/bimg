# Copyright 2018 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("@rules_cc//cc:defs.bzl", "cc_library", "cc_test")

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "api",
    hdrs = ["include/astc-codec/astc-codec.h"],
)

cc_library(
    name = "base",
    hdrs = [
        "src/base/bit_stream.h",
        "src/base/bottom_n.h",
        "src/base/math_utils.h",
        "src/base/optional.h",
        "src/base/string_utils.h",
        "src/base/type_traits.h",
        "src/base/uint128.h",
        "src/base/utils.h",
    ],
    includes = ["."],
    features = ["-parse_headers"],
)

cc_test(
    name = "base_test",
    srcs = [
        "src/test/bit_stream_test.cpp",
        "src/test/bottom_n_test.cpp",
        "src/test/math_utils_test.cpp",
        "src/test/optional_test.cpp",
        "src/test/string_utils_test.cpp",
        "src/test/type_traits_test.cpp",
        "src/test/uint128_test.cpp",
    ],
    includes = ["bimg/3rdparty/astc-codec"],
    deps = [
        ":base",
        "@gtest//:gtest_main",
    ],
)


cc_library(
    name = "astc_codec",
    hdrs = ["include/astc-codec/astc-codec.h"],
    includes = ["include"],
    visibility = ["//visibility:public"],
    deps = ["//bimg/3rdparty/astc-codec/src/decoder:codec"],
)
