+++
title= "Vegeta负载测试工具"
date= "2019-01-29T14:28:42+08:00"
tags = []
featured_image = ""
description = ""
+++

```
$ vegeta --help
Usage: vegeta [global flags] <command> [command flags]

global flags:
  -cpus int
    使用 CPU 的数量 (默认为 4 个)
  -profile string
    指定在执行期间启用哪个分析器，支持 cpu 和 heap。
  -version
    打印版本并退出。

attack command:
  -body string
    指定请求主体文件里的内容。
  -cert string
    指定用于 HTTPS 请求的 PEM 格式的客户端证书文件。如果 -key 未指定，它会被设置为这个标志的值。
  -connections int
    指定每个目标主机打开的空闲连接的最大数目，默认值为 10000。
  -duration duration
    指定发送请求到目标主机的时长，用 0 表示永久。
  -header value
    指定目标的请求头，可以重复指定多个请求头。
  -http2
    指定是否向支持的服务器发送 HTTP/2 请求，默认为：true。
  -insecure
    指定是否忽略无效的服务器 TLS 证书。
  -keepalive
    指定是否使用持久链接，默认值为：true。
  -key string
    指定 HTTPS 请求中使用的 PEM 编码的 SSL 客户端证书私钥文件。
  -laddr value
    指定要使用的本地 I P地址，默认值为：0.0.0.0。
  -lazy
    指定是否使用延迟模式读取目标。
  -output string
    指定输出文件的位置，默认为标准输出。
  -rate uint
    指定每秒钟对目标发送的请求数，默认值为：50。
  -redirects int
    指定每个请求的重定向的最大次数，默认为 10 次。当值为 -1, 不会遵循重定向但响应标记为成功。
  -root-certs value
    指定可信的 TLS 根证书文件，多个的情况下使用逗号分隔。如果未指定，使用系统默认的 CA 证书。
  -targets string
    指定目标文件，默认为标准输入。
  -timeout duration
    指定每个请求的超时时间，默认值为 30s。
  -workers uint
    指定初始化进程数量，默认值为 10。

report command:
  -inputs string
    指定报告输入文件，默认为标准输入。
  -output string
    指定报告输出文件，默认为标准输出。
  -reporter string
    指定要生成的报告的格式，支持 text，json, plot, hist[buckets]。默认为文本。

dump command:
  -dumper string
    指定转存文件，支持 json, csv 格式。默认为 json 格式。
  -inputs string
    指定要转存的输入文件，默认为标准输入，指定多个用逗号分隔。
  -output string
    指定要转存的输出文件，默认为标准输出。
```