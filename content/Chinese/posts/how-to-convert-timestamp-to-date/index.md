---
keywords: ['blog']
title: '时间戳转日期时间'
date: 2025-07-02T22:09:04+08:00
lastmod: 2025-07-02T22:09:04+08:00
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
let timestamp = 1624713600.0 // 示例时间戳
let date = NSDate(timeIntervalSince1970: timestamp)
```

### Go	
```go
import (
    "time"
)
timestamp := int64(1624713600) // 示例时间戳
t := time.Unix(timestamp, 0)
```

### Java	
```java
long timestamp = 1624713600; // 示例时间戳
java.util.Date date = new java.util.Date(timestamp * 1000);
```

### C	
```c
#include <time.h>
time_t timestamp = 1624713600; // 示例时间戳
struct tm *timeinfo = localtime(&timestamp);
// 或者使用 gmtime(&timestamp) 获取 UTC 时间
```

### JavaScript	
```javascript
const timestamp = 1624713600; // 示例时间戳
const date = new Date(timestamp * 1000);
```

### Objective-C	
```objective-c
NSTimeInterval timestamp = 1624713600; // 示例时间戳
NSDate *date = [NSDate dateWithTimeIntervalSince1970:timestamp];
```

### MySQL	
```sql
SELECT from_unixtime(1624713600)
```

### SQLite	
```sql
SELECT datetime(1624713600, 'unixepoch')
```

### Erlang	
```erlang
Timestamp = 1624713600, % 示例时间戳
Datetime = calendar:gregorian_seconds_to_datetime(Timestamp + 719528*24*3600).
```

### PHP	
```php
<?php
// pure php
$timestamp = 1624713600; // 示例时间戳
$date = date('Y-m-d H:i:s', $timestamp);
```

### Python	
```python
from datetime import datetime
timestamp = 1624713600  # 示例时间戳
date = datetime.fromtimestamp(timestamp)
```

### Ruby	
```ruby
timestamp = 1624713600 # 示例时间戳
time = Time.at(timestamp)
```

### Shell	
```bash
date -d @1624713600
# macOS: date -r 1624713600
```

### Groovy	
```groovy
long timestamp = 1624713600 // 示例时间戳
Date date = new Date(timestamp * 1000)
```

### Lua	
```lua
timestamp = 1624713600 -- 示例时间戳
date = os.date("*t", timestamp)
```

### .NET/C#	
```c#
long timestamp = 1624713600; // 示例时间戳
DateTimeOffset date = DateTimeOffset.FromUnixTimeSeconds(timestamp);
```

### Dart	
```dart
int timestamp = 1624713600; // 示例时间戳
DateTime date = DateTime.fromMillisecondsSinceEpoch(timestamp * 1000);
```