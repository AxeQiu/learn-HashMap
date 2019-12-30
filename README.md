# learn-HashMap
The key note for HashMap of Java

* **This class makes no guarantees as to the order of the map; in particular, it does not guarantee that the order will remain constant over time**

HashMap不保证元素顺序

* **Iteration over collection views requires time proportional to the "capacity" of the HashMap instance (the number of buckets) plus its size (the number of key-value mappings). Thus, it's very important not to set the initial capacity too high (or the load factor too low) if iteration performance is important.**

如果看重迭代性能，则不应将HashMap的容量设置的过大（或负载因子过底），因为迭代所需要的时间和HasmMap的容量（桶数组大小）和其中的元素数量成正比

* **When the number of entries in the hash table exceeds the product of the load factor and the current capacity, the hash table is rehashed (that is, internal data structures are rebuilt) so that the hash table has approximately twice the number of buckets.**

当HashMap的元素数量大于其桶数组大小与负载因子的乘积时，HashMap将被rehash

* **The expected number of entries in the map and its load factor should be taken into account when setting its initial capacity, so as to minimize the number of rehash operations. If the initial capacity is greater than the maximum number of entries divided by the load factor, no rehash operations will ever occur.**

为尽量减少rehash的次数，应考虑HashMap的初始容量与负载因子。若初始大小（桶数组）大于最大元素个数除以负载因子，则rehash永不会发生.

* **Note that this implementation is not synchronized.**

HashMap不是线程安全的

* **MIN_TREEIFY_THRESHOLD:　The smallest table capacity for which bins may be treeified.(Otherwise the table is resized if too many nodes in a bin.) Should be at least 4 * TREEIFY_THRESHOLD to avoid conflicts between resizing and treeification thresholds.**

桶数组大小至少为 TREEIFY_THRESHOLD 的4倍(TREEIFY_THRESHOLD=8，MIN_TREEIFY_THRESHOLD实际取值为64），才有可能红黑树化，否则以resize()操作代替treeify()

因此，初始化HashMap时最好指定初始容量
```java
Map<String, Object> map = new HashMap<>(64, 0.75f);
```

* **containsValue(Object value)**

containsValue十分消耗性能（扫描所有元素，导致O(n)的复杂度），任何情况下应避免使用
```java
for (int i = 0; i < tab.length; ++i) {
  for (Node<K,V> e = tab[i]; e != null; e = e.next) {
    ...
  }
}
```

* **Node<K, V>的对象成员hash和hashCode()方法**

Node<K, V>的对象成员hash存储的是key的hash(使用key的hashCode高低位异或) ; 自身的hashCode()方法是key的hashCode异或value的hashCode. Node<K, V>的hashCode()方法不参与get, put过程.
