load("@rules_cc//cc:defs.bzl", "cc_test")

constraint_setting(name = "test_constraint")

constraint_value(
    name = "test_constraint_value",
    constraint_setting = ":test_constraint",
)

platform(
    name = "test_platform_no_constraint",
    exec_properties = {
        "exec_property": "no_constraint",
    },
    parents = ["@local_config_platform//:host"],
)

platform(
    name = "test_platform_with_constraint",
    constraint_values = [
        ":test_constraint_value",
    ],
    exec_properties = {
        "exec_property": "requires_test_constraint",
    },
    parents = ["@local_config_platform//:host"],
)

cc_test(
   name = "test_requiring_test_constraint_value",
   srcs = ["main.cc"],
   exec_compatible_with = [":test_constraint_value"]
)
