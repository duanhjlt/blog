---
keywords: ['blog', 'timestamp', 'devutils']
title: '获取当前时间戳'
date: 2025-07-01T22:51:08+08:00
lastmod: 2025-07-01T22:51:08+08:00
draft: false
description: 
author: 'duanhongjin'
tags: ['devutils']
categories: []
tocLevels: ["h2", "h3", "h4"]
comments: true # 本页面是否显示评论
reward: true # 打赏
showToc: true # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: true # 底部不显示分享栏
showbreadcrumbs: true #顶部显示路径
---

### Swift

```swift
NSDate().timeIntervalSince1970
```

### Go

```go
import (
  "time"
)
int64(time.Now().Unix())
```

### Java

```java
System.currentTimeMillis() / 1000
```

### C

```c
#include <sys/time.h>

// ...
struct timeval tv;
gettimeofday(&tv, NULL);
// 秒： tv.tv_sec
// 毫秒： tv.tv_sec * 1000LL + tv.tv_usec / 1000
```

### JavaScript

```javascript
Math.round(new Date() / 1000)
```

### Objective-C

```objective-C
[[NSDate date] timeIntervalSince1970]
```

### MySQL

```mysql
SELECT unix_timestamp(now())
SQLite	
SELECT strftime('%s', 'now')
```

### Erlang	

```erlang
calendar:datetime_to_gregorian_seconds(calendar:universal_time())-719528*24*3600.
```

### PHP	

```php
<?php
// pure php
time();
```

### Python	

```python
import time
time.time()
```

### Ruby

```ruby	
Time.now.to_i
```

### Shell	

```shell
date +%s
```

### Groovy	

```groovy
(new Date().time / 1000).longValue()
```

### Lua	

```lua
os.time()
```

### .NET/C#	
```.net
DateTimeOffset.UtcNow.ToUnixTimeSeconds();
```

### Dart	

```dart
(new DateTime.now().millisecondsSinceEpoch / 1000).truncate()
```