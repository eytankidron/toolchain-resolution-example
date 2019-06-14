cc_library(
    name = "hello-world-lib",
    srcs = ["hello-world-lib.cc"],
    hdrs = ["hello-world-lib.h"],
)

genrule(
    name = "echo",
    outs = ["echo.txt"],
    cmd = "echo $(locations :hello-world-lib) > $@",
    tools = [
        ":hello-world-lib",
    ],
)

platform(
    name = "plain_platform",
    remote_execution_properties = """
        properties: {
          name: "container-image"
          value:"docker://gcr.io/gcp-runtimes/ubuntu_16_0_4@sha256:096632d8fb3e78fbd58ae6a2b25ed46020dc70e65d89bca774af6f7b2de6898c"
        }
        properties {
           name: "OSFamily"
           value:  "Linux"
        }
        """,
)
