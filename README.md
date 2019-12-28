# learn-HashMap
The key note for HashMap of Java

**This class makes no guarantees as to the order of the map; in particular, it does not guarantee that the order will remain constant over time**

HashMap不保证元素顺序

**Iteration over collection views requires time proportional to the "capacity" of the HashMap instance (the number of buckets) plus its size (the number of key-value mappings). Thus, it's very important not to set the initial capacity too high (or the load factor too low) if iteration performance is important.**

如果看重迭代性能，则不应将HashMap的容量设置的过大（或负载因子过底），因为迭代所需要的时间和HasmMap的容量（桶数组大小）和其中的元素数量成正比

**When the number of entries in the hash table exceeds the product of the load factor and the current capacity, the hash table is rehashed (that is, internal data structures are rebuilt) so that the hash table has approximately twice the number of buckets.**

当HashMap的元素数量大于其桶数组大小与负载因子的乘积时，HashMap将被rehash

**The expected number of entries in the map and its load factor should be taken into account when setting its initial capacity, so as to minimize the number of rehash operations. If the initial capacity is greater than the maximum number of entries divided by the load factor, no rehash operations will ever occur.**

为尽量减少rehash的次数，应考虑HashMap的初始容量与负载因子。若初始大小（桶数组）大于最大元素个数除以负载因子，则rehash永不会发生.

**Note that this implementation is not synchronized.**

HashMap不是线程安全的
