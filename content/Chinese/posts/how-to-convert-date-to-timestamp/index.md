---
keywords: ['blog']
title: '日期时间转时间戳'
date: 2025-07-02T22:04:40+08:00
lastmod: 2025-07-02T22:04:40+08:00
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
let date = NSDate() // 任意时间对象
let timestamp = date.timeIntervalSince1970
```

### Go	
```go
import (
    "time"
)
t := time.Now() // 任意时间对象
timestamp := t.Unix()
```

### Java	
```java
java.util.Date date = new java.util.Date(); // 任意时间对象
long timestamp = date.getTime() / 1000;
```

### C	
```c
#include <time.h>
time_t t = time(NULL); // 任意时间对象
long timestamp = (long)t;
```

### JavaScript	
```javascript
const date = new Date(); // 任意时间对象
const timestamp = Math.round(date.getTime() / 1000);
```

### Objective-C	
```objective-c
NSDate *date = [NSDate date]; // 任意时间对象
NSTimeInterval timestamp = [date timeIntervalSince1970];
```

### MySQL	
```sql
SELECT unix_timestamp('2021-06-26 12:00:00') // 任意时间
```

### SQLite	
```sql
SELECT strftime('%s', '2021-06-26 12:00:00') // 任意时间
```

### Erlang	
```erlang
Datetime = calendar:universal_time(), % 任意时间
Timestamp = calendar:datetime_to_gregorian_seconds(Datetime) - 719528*24*3600.
```

### PHP	
```php
<?php
// pure php
$date = new DateTime(); // 任意时间对象
$timestamp = $date->getTimestamp();
```

### Python	
```python
import time
from datetime import datetime
date = datetime.now()  # 任意时间对象
timestamp = int(date.timestamp())
```

### Ruby	
```ruby
time = Time.now # 任意时间对象
timestamp = time.to_i
```

### Shell	
```bash
date -d "2021-06-26 12:00:00" +%s
```

### Groovy	
```groovy
Date date = new Date() // 任意时间对象
long timestamp = (date.time / 1000).longValue()
```

### Lua	
```lua
date = os.time({year=2021, month=6, day=26, hour=12, min=0, sec=0}) -- 任意时间
timestamp = date
```

### .NET/C#	
```c
DateTimeOffset date = DateTimeOffset.Now; // 任意时间对象
long timestamp = date.ToUnixTimeSeconds();
```

### Dart	
```dart
DateTime date = DateTime.now(); // 任意时间对象
int timestamp = (date.millisecondsSinceEpoch / 1000).truncate();
```