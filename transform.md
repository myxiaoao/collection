# 转换类
可以说是 Collection 用途最广泛的类别，有着非常丰富的生态系可以对 Collection 处理成你想要的样子。

## 维度与顺序
### 1. collapse() , flatten()
两者都是将维度从多维降为一维，collapse 比较适用于纯数值类型形式的数据，flatten 更适合键值对形式的数据，两个函数的用途都是将例如：`[[1,2,3], [4,5,6]]` 转换成 `[1,2,3,4,5,6]`。

### 2. flip() , keyBy()
flip 可以将 key 与 value 的关系做翻转，本来 `'name' => 'John'` 变成 `'John' => 'name'`;  
keyBy 则是可以指定特定的 key 中的 value，提取出来变成新的 key。

### 3. groupBy() , split() , splitIn()
groupBy 跟之前的 mapToGroup 很类似，直接使用特定 key 下的 value 做分组，很适合二维的多组键值对数据；  
split 和 splitIn 都可以按指定顺序去分割数据，不会形成一个新的 Collection。

### 4. implode() , join()
implode 跟大家所熟悉的 php implode 语法雷同；  
join 跟 implode 很像，但使用上更灵活，可以做到像下面这样。  
```php
collect(['a', 'b', 'c'])->join(', ', ', and '); // 'a, b, and c'
```

### 5. sort() , sortBy() , sortKeys() , reverse() 
排序相信大家都很熟悉，Collection 支持对 value ( sort )、key-value 结构的 key 对应 value (sortBy)，按照 key 的顺序 (sortKeys) 排序，而且每个 sort 都有一个对应的降序排列的函数，例如 sortByDesc()
值得一提的是，sort 是可以使用 closure 闭包，例如:

```php
$user->sort(function($a, $b){
    // return -1, 0 or 1 here
});
```

## 组合
### 1. combine() , zip() , crossJoin()
combine 可以将 `['name', 'age']` 和 `['George', 29]` 变成 `['name' => 'George', 'age' => 29]` ，zip 功能一样，只是会改变原本的 Collection。  
crossJoin 很酷，有点像找出所有的排列组合，例如把 `[1, 2]` 和 `['a', 'b']` 变成 `[[1, 'a'], [1, 'b'], [2, 'a'], [2, 'b']]`。

### 2. merge() , mergeRecursive() , replace() , replaceRecursive() , union()
merge 很常用，用来合并两个 Collection，后者有 key 重复的，将会覆盖前者，但是 merge 只会覆盖 key 是 string 的组合，replace 则会连 index 对应到也会一起覆盖；   
两者都有 Recursive 去做多维数据的合并；  
union 跟 merge 很像，只是 key 重复不会覆盖。

### 3. concat() , pad() 
concat 就是实现 『 + 』的 Collection 计算，将两者直接加在一起；   
pad 可以产生类似 padding 『 0 』 的值。

### 4. mapInto()
可以对数据做批量初始化操作。

### 5. prepend() , push() , put()
常用的函数，在最前面和最后面追加数据，put 则是更优雅的用参数方式追加。

## 获取
### 1. except() , only() , get() , forget() , pull()
except 获取 「除了 a, b 以外的」，only 则相反，是获取 「只有 a, b」，get 则是取得特定 key 的值，forget 则可以直接删除指定 key 对应数据，pull 跟 get 一样，只是会修改源 Collection 数据。

### 2. pluck()
非常好用的函数，可以对二维键值对数据结构，获取特定 key 下的所有 value。例如：
```php
$collection = collect([
    ['product_id' => 'prod-100', 'name' => 'Desk'],
    ['product_id' => 'prod-200', 'name' => 'Chair'],
]);

$plucked = $collection->pluck('name');

$plucked->all();

// ['Desk', 'Chair']
```

### 3. forPage() , nth() , pop() , shift()
forPage 可以按照分页的方式去获取；   
nth 可以指定从 x 开始，第 n 条数据；   
pop 和 shift 就是很常见的最开始和最后的位置获得数据。

### 4. intersect() , intersectByKeys() , sole()
intersect 可以用在获取两个 Collection 交集，intersectByKeys 则是比较 key 是否存在交集；   
sole 则是常用在循环处理时，匹配到对应条件的值是，则返回值，同时跳出循环。

### 5. keys() , values()
取出 Collection 所有的 key 和 value，非常常用很好理解。

### 6. skip() , take() , *Until() , *While()
skip 是從特定 x 點以後的才取，take 是相反，從特定 x 點以前的才取。
兩者都有如 skipUntil() 這類的函式，通常會跑閉包迭代，可以判斷是否符合某條件，until 和 while 則只是相反的判斷方式。

### 7. unique() , uniqueStrict()
将 Collection 去重数据，strict 严格模式。

## 转换类型
### 1. toArray() , toJson()
提供转换成 Array, Json 等常用格式
