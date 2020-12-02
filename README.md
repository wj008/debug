# debug
安装

composer require wj008/debug

需要配合 调试服务器使用,php socket 端口需要打开

使用：

```php

use debug\Logger;

Logger::log("test", "xxxx", 3);
Logger::info("xxxxdsd", ["xxxx"], ["cccc" => "xxx"]);
Logger::log(false);

function a()
{
    throw new \Exception("这个是一个测试错误信息");
}

function b()
{
    a();
}

try {
    b();
} catch (\Exception $e) {
    Logger::error($e->getMessage(), PHP_EOL. $e->getTraceAsString());
}

$time1 = microtime(true);
//执行sql 耗时
usleep(50000);
$time2 = microtime(true);

Logger::sql('select * from table where pid=1 and name="xxxx"', $time2 - $time1);
```

