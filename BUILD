licenses(["notice"])  # Apache 2

package(default_visibility = ["//visibility:public"])

exports_files(["LICENSE"])

cc_library(
    name = "ssl",
    hdrs = glob([
        "thirdparty_build/include/boringssl/**/*.h",
    ]),
    copts = ["-I/usr/include/boringssl"],
    linkopts = ["-lboringssl_crypto", "-lboringssl_decrepit", "-lboringssl_ssl"],
)

cc_library(
    name = "abseil_strings",
    hdrs = glob(["thirdparty_build/include/absl/**/*.h"]),
    copts = ["-I/usr/include/absl"],
    linkopts = [
        "-labsl_base_libbase",
        "-labsl_base_libthrow_delegate",
        "-labsl_strings_libinternal",
        "-labsl_strings_libstr_format_internal",
        "-labsl_strings_libstrings",
    ],
)

cc_library(
    name = "abseil_time",
    hdrs = glob(["thirdparty_build/include/absl/**/*.h"]),
    copts = ["-I/usr/include/absl"],
    linkopts = [
        "-labsl_base_libbase",
        "-labsl_base_libspinlock_wait",
        "-labsl_numeric_libint128",
        "-labsl_time_internal_cctz_libcivil_time",
        "-labsl_time_internal_cctz_libtime_zone",
        "-labsl_time_libtest_util",
        "-labsl_time_libtime",
    ],
)

cc_library(
    name = "rapidjson",
    hdrs = glob(["thirdparty_build/include/rapidjson/**/*.h"]),
    copts = ["-I/usr/include/rapidjson"],
    linkopts = [],
)

cc_library(
    name = "googletest_main",
    hdrs = glob(["thirdparty_build/include/gtest/**/*.h"]),
    copts = ["-I/usr/include/gtest"],
    linkopts = ["-lgtest", "-lgtest_main"],
)

cc_library(
    name = "jwt_verify_lib",
    srcs = [
        "src/check_audience.cc",
        "src/jwks.cc",
        "src/jwt.cc",
        "src/status.cc",
        "src/verify.cc",
    ],
    hdrs = [
        "jwt_verify_lib/check_audience.h",
        "jwt_verify_lib/jwks.h",
        "jwt_verify_lib/jwt.h",
        "jwt_verify_lib/status.h",
        "jwt_verify_lib/verify.h",
    ],
    deps = [
        "abseil_strings",
        "abseil_time",
        "rapidjson",
        "ssl",
    ],
)

cc_test(
    name = "check_audience_test",
    srcs = [
        "src/check_audience_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "jwt_test",
    srcs = [
        "src/jwt_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "jwks_test",
    srcs = [
        "src/jwks_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "verify_pem_test",
    srcs = [
        "src/test_common.h",
        "src/verify_pem_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "verify_audiences_test",
    srcs = [
        "src/test_common.h",
        "src/verify_audiences_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "verify_time_test",
    srcs = [
        "src/test_common.h",
        "src/verify_time_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "verify_jwk_rsa_test",
    srcs = [
        "src/test_common.h",
        "src/verify_jwk_rsa_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)

cc_test(
    name = "verify_jwk_ec_test",
    srcs = [
        "src/test_common.h",
        "src/verify_jwk_ec_test.cc",
    ],
    linkopts = [
        "-lm",
        "-lpthread",
    ],
    linkstatic = 1,
    deps = [
        ":jwt_verify_lib",
        "googletest_main",
    ],
)
