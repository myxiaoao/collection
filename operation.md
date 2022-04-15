# 操作类

这个分类比较特别一点，不太像是为了数据本身，而是为了程序处理的需求

## 1. collect() , make() , times()

collect 是复制一个新的 Collection ，make 则会新增一个 Collection，times 则可以按照次数产生 Collection 内的值，后两者都可以作为静态方法使用。

## 2. dd() , dump()

非常常用，debug 用的函数，打印出详细的内容， 区别在于前者会中断输出，后者不会。

## 3. marco()

可以制作拓展函数（宏）使用。

## 4. pipe() , pipeInto() , tap()

pipe 和 tap 都可以将 Collection 设计成一个工作流使用，前者是对 Collection 本身发起，tap 则可以在调用函数操作后再处理，可以参考源码，一个返回 Collection 本身：

```php
$collection = collect([1, 2, 3]);

$piped = $collection->pipe(function ($collection) {
    return $collection->sum();
});

// 6

collect([2, 4, 3, 1, 5])
    ->sort()
    ->tap(function ($collection) {
        Log::debug('Values after sorting', $collection->values()->all());
    })
    ->shift();

// 1
```

pipeInto 类似 mapInto，可以 Collection 本身传入指定 class construct 中。

## 5. random() , shuffle()

random 可以随机获取 Collection 数据，shuffle 用来随机打乱 Collection。

## 6. wrap() , unwrap()

可以将传入的值转换为 Collection

## 7. unless() , when() , empty() , notEmpty()

unless 和 when  都是用来判断符合某些条件才执行闭包操作，例如：

```php
$collection = collect([1, 2, 3]);

$collection->when(true, function ($collection) {
    return $collection->push(4);
});

$collection->when(false, function ($collection) {
    return $collection->push(5);
});

$collection->all();

// [1, 2, 3, 4]
```

而两者是相反的逻辑判断；

empty 和 notEmpty 则是两者就有的拓展函数，判断当 Collection 是否为空时的行为，用法如 whenEmpty()。

---

到此为止，Laravel 的 Collection 函数说明完毕，希望可以帮助到你更有概念，写出更优雅的代码来处理数据。
