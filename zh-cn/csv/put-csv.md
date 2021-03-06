# 导出CSV

## 应用场景

1. 较多的 xlsx 文件碎片，合并为单一CSV文件，统一处理；
2. xlsx文件新增的速度大于任务处理速度，可异步将文件转为CSV后，使用更高效的工具处理（例如：数据库工具直接导入CSV）；

更多的应用场景等待你去发现...........

## **函数原型**

```php
putCSV(resource $handler): bool
```

### **resource $handler**

> 文件指针必须是有效的，必须指向由 fopen() 或 fsockopen() 成功打开的文件(并还未由 fclose() 关闭)。

## 示例

```php
$config = ['path' => './tests'];
$excel  = new \Vtiful\Kernel\Excel($config);

$filePath = $excel->fileName('tutorial.xlsx', 'TestSheet1')
    ->header(['Item', 'Cost'])
    ->data([
        ['Item_1', 'Cost_1', 10, 10.9999995],
    ])
    ->output();

// 写入方式打开，将文件指针指向文件末尾。
$fp = fopen('./tests/file.csv', 'a');

$csvResult = $excel->openFile('tutorial.xlsx')
    ->openSheet()
    ->putCSV($fp);
```
