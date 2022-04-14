# 分组类
这里会介绍 Collection 针对同样的数据做分组会用到的函数。

## 1. chunk() , chunkWhile()
chunk 是很推荐使用的函数，可以按照指定的数量，选择数据中的部分来计算并迭代，chunkWhile 可以指定 chunk 到特定的条件是停止。

## 2. partition() , splice() , sliding()
partition 可以将一个 collection 按照某种条件语句，切割成 2 个 collection，splice 跟 partition 用法相似，只是会从原来的 collection 切割，所以会影响原有的 collection。
sliding 可以将 `[1,2,3]` 切割成 `[[1,2],[2,3],[2,3]]`

### 3. countBy
可以将 `[1, 2, 2, 2, 3]` 变成 `[1 => 1, 2 => 3, 3 => 1]`，变成一个统计结果的数据。
