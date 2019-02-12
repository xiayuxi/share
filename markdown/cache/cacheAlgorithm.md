## Cache Algorithm

### LFU(Least Frequently Used)
根据数据的历史访问频率来淘汰数据，其核心思想是“如果数据过去被访问多次，那么将来被访问的频率也更高”

LFU的每个数据块都有一个引用计数，所有数据块按照引用计数排序，具有相同引用计数的数据块则按照时间排序
### LRU（LeastRecently User）
根据数据的历史访问记录来进行淘汰数据，其核心思想是“如果数据最近被访问过，那么将来被访问的几率也更高”
### LRU-K(LeastRecently Used K)
相比LRU，LRU-K需要多维护一个队列，用于记录所有缓存数据被访问的历史。只有当数据的访问次数达到K次的时候，才将数据放入缓存。当需要淘汰数据时，LRU-K会淘汰第K次访问时间距当前时间最大的数据
### FIFO(First inFirst out)
最先进入的数据，最先被淘汰。一个很简单的算法。只要使用队列数据结构即可实现。那么FIFO淘汰算法基于的思想是”最近刚访问的，将来访问的可能性比较大”
### 2Q(Two Queues)
同样也是为了解决LRU算法的缓存污染问题。类似于LRU-2，不同点在于2Q将LRU-2算法中的访问历史队列改为一个FIFO缓存队列，即：2Q算法有两个缓存队列，一个是FIFO队列，一个是LRU队列。
当数据第一次访问时，2Q算法将数据缓存在FIFO队列里面，当数据第二次被访问时，则将数据从FIFO队列移到LRU队列里面，两个队列各自按照自己的方法淘汰数据
