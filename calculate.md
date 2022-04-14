# 计算类
collection 可以很方便的做数学常见的计算，或者判断是否含有特定值，也能比较两个 collection 之间的不同。

## Integer
### 1. avg() , average()
计算平均值用的函数，算是必会的函数，average() 是 avg() 的 alias 别名函数，用法单一。

### 2. count() , sum()
非常常见的函数，前者可以做计数统计；后者可以做相加统计，并且能使用 Closure 闭包函数做更弹性的应用。

### 3. median() , mode()
主要是统计学常用的中位数( median ) 和众数 ( mode )。 
> 中位数：按顺序排列的一组数据中居于中间位置的数。  
> 众数:一组数据中出现次数最多的数值。

### 4. min() , max()
可以查询最小与最大值，比较常用的函数。

### 5. reduce()
reduce 是常见但不是很直观的迭代型计算函数，可以先参考官方例子：

```php
$collection = collect([1, 2, 3]);

$total = $collection->reduce(function ($carry, $item) {
    return $carry + $item;
});

// 6
```

其中 $carry 是一个贯穿每一次循环的变量，每一次的结果会赋值给 $carry ，而 $item 就是每一次 collection 里面 item

### 6. search()
可以找出对应值在 collection 中位置的 index ，对于键值对型 collection 很适用。

## Boolean
### 1. contains() , containsStrict()
经常搭配闭包一起使用，可以很方便的查询 Collection 中包含指定值，并且提供 Strict 模式做严格比对。

### 2. every() , has() , some()
这三个函数比较像是 contains 的延伸，every 是要确认每一个 item 都符合条件，has 是判断 key 值，some 则是 contains 的 alias 别名函数。

### 3. isEmpty() , isNotEmpty()
其实底层使用的就是 empty() 这个 PHP 函数，但是更加统一，语义化。

### Array
### 1. diff() , diffassoc() , diffKeys()
比较两个 collection 的不同，diff 主要是比对 value 的不同，diffKeys 是比对 key， diffassoc 则会比较 key-value 的层级。

### 2. duplicates() , duplicatesstrict()
可以找出两个 collection 中有哪些 value 重复，并提供 strict 模式。
