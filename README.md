# Available Tools

Below is a list of available tools that can be used with `cli.tools` and
`term.tools` domains. All domains support both http and https unless otherwise
specified.

## ip.{cli,term}.tools

Returns the public ip as seen by our servers, followed by a
new line. You can remove the new line by appending `/r` for raw.

```
# curl ip.cli.tools
136.32.123.123
#
# curl ip.cli.tools/r
136.32.123.123# 
```