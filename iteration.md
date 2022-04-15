# 迭代类
在数据操作中，时常会有针对 Collection 做循环处理，迭代每一个数据项，而针对迭代是不同的情况，可以有不同的函数可以操作使用。

## 1. filter() , reject()
filter 可以说是使用率最高的函数，可以在循环结束以后只保留符合条件的数据项；   
reject 则相反，符合条件的数据会被忽略掉。

## 2. each() , eachSpread()
each 可以当做 foreach 来使用；   
eachSpread 则是可以运用在二维数据结构下，就如同 Spread 字面意思一样，把二维数据的值一一赋值给参数，在其他相关函数也有对应的功能。
```php
$collection = collect([['John Doe', 35], ['Jane Doe', 33]]);

$collection->eachSpread(function ($name, $age) {
    // $name = John Doe...
    // $age = 35...
});
```

## 3. map() , mapSpread() , mapWithKeys() , mapToGroup()
map 也是很常用的函数，在迭代后生成一个新的符合条件的 Collection；   
mapSpread 则不再说明；  
mapWithKeys 则是迭代时，需要返回 index 键值；   
mapToGroup 比较特别，可以做归类，将 Collection 按 value 分组。
```php
$collection = collect([
    [
        'name' => 'John Doe',
        'department' => 'Sales',
    ],
    [
        'name' => 'Jane Doe',
        'department' => 'Sales',
    ],
    [
        'name' => 'Johnny Doe',
        'department' => 'Marketing',
    ]
]);

$grouped = $collection->mapToGroups(function ($item, $key) {
    return [$item['department'] => $item['name']];
});

$grouped->all();

/*
    [
        'Sales' => ['John Doe', 'Jane Doe'],
        'Marketing' => ['Johnny Doe'],
    ]
*/

$grouped->get('Sales')->all();

// ['John Doe', 'Jane Doe']
```

## 4. transform() , flatmap()
transform 其实就是 map，只是改变原来的 Collection，而不是新建一个 Collection；   
flatmap 则可以将二维 Collection 转换为一维。


