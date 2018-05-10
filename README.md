# Caller Hook for [Logrus](https://github.com/sirupsen/logrus) <img src="http://i.imgur.com/hTeVwmJ.png" width="40" height="40" alt=":walrus:" class="emoji" title=":walrus:" />

使用hook的方式让Logrus拥有输出日志时输出源代码所在文件和行号功能

## 示例

### 默认

```go
package main

import (
    log "github.com/sirupsen/logrus"
    caller "github.com/xdxiaodong/logrus-hook-caller"
)

func main() {
    log.SetFormatter(new(log.JSONFormatter))
    hook_caller := caller.NewHook(&caller.CallerHookOptions{
	//DisabledField: true,
	//EnableFile: true,
	//EnableLine: true,
	//Flags:      caller.Llongfile,
	})
    log.AddHook(hook_caller)
    log.Info("hello world")
}
```

### 源文件完整路径

```go
package main

import (
    log "github.com/sirupsen/logrus"
    caller "github.com/xdxiaodong/logrus-hook-caller"
)

func main() {
    log.SetFormatter(new(log.JSONFormatter))
    hook_caller := caller.NewHook(&caller.CallerHookOptions{
	Flags:      caller.Llongfile,
	})
    log.AddHook(hook_caller)
    log.Info("hello world")
}
```