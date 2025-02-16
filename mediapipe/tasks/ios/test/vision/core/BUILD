load(
    "//mediapipe/framework/tool:ios.bzl",
    "MPP_TASK_MINIMUM_OS_VERSION",
)
load(
    "@build_bazel_rules_apple//apple:ios.bzl",
    "ios_unit_test",
)
load(
    "@org_tensorflow//tensorflow/lite:special_rules.bzl",
    "tflite_ios_lab_runner",
)

package(default_visibility = ["//mediapipe/tasks:internal"])

licenses(["notice"])

# Default tags for filtering iOS targets. Targets are restricted to Apple platforms.
TFL_DEFAULT_TAGS = [
    "apple",
]

# Following sanitizer tests are not supported by iOS test targets.
TFL_DISABLED_SANITIZER_TAGS = [
    "noasan",
    "nomsan",
    "notsan",
]

objc_library(
    name = "MPPImageObjcTestLibrary",
    testonly = 1,
    srcs = ["MPPImageTests.m"],
    data = [
        "//mediapipe/tasks/testdata/vision:test_images",
    ],
    deps = [
        "//mediapipe/tasks/ios/common:MPPCommon",
        "//mediapipe/tasks/ios/vision/core:MPPImage",
        "//third_party/apple_frameworks:Accelerate",
        "//third_party/apple_frameworks:CoreGraphics",
        "//third_party/apple_frameworks:CoreMedia",
        "//third_party/apple_frameworks:CoreVideo",
        "//third_party/apple_frameworks:UIKit",
    ],
)

ios_unit_test(
    name = "MPPImageObjcTest",
    minimum_os_version = MPP_TASK_MINIMUM_OS_VERSION,
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = TFL_DEFAULT_TAGS + TFL_DISABLED_SANITIZER_TAGS,
    deps = [
        ":MPPImageObjcTestLibrary",
    ],
)

objc_library(
    name = "MPPMaskObjcTestLibrary",
    testonly = 1,
    srcs = ["MPPMaskTests.m"],
    deps = ["//mediapipe/tasks/ios/vision/core:MPPMask"],
)

ios_unit_test(
    name = "MPPMaskObjcTest",
    minimum_os_version = MPP_TASK_MINIMUM_OS_VERSION,
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = TFL_DEFAULT_TAGS + TFL_DISABLED_SANITIZER_TAGS,
    deps = [
        ":MPPMaskObjcTestLibrary",
    ],
)
