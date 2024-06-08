# Collection Framework – Collection Interface Methods

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/CollectionInterface.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

Collection interface contains total 15 abstract methods. 14 of it’s own and one is inherited from Iterable interface. Here is the list and descriptions of those methods.

| SL No.        | Method      |  Method      |
| ------------- |-------------|--------------|
| 1. |int size()|Returns the number of elements in this collection|
| 2. |boolean isEmpty()|Checks whether this collection is empty or not. If collection is empty, it returns true otherwise it returns false|
| 3. |boolean contains(Object o)|Checks whether this collection has specified element.|
| 4. |Iterator<E> iterator()|Returns an iterator over the collection.|
| 5. |Object[] toArray()|It returns an array containing all elements of this collection.|
| 6. |<T> T[] toArray(T[] a)|	It returns an array of specified type containing all elements of this collection.|
| 7. |boolean add(E e)|	This method adds specified element to this collection. It returns true if element is added successfully to the collection otherwise it returns false.|
| 8. |boolean remove(Object o)|	Removes the specified element from this collection.|
| 9. |boolean containsAll(Collection<?> c)|	It checks whether this collection contains all elements of passed collection.|
| 10. |boolean addAll(Collection<? extends E> c)|	Adds all elements of the passed collection to this collection.|
| 11. |boolean removeAll(Collection<?> c)|	Removes all elements of this collection which are also elements of passed collection.|
| 12. |boolean retainAll(Collection<?> c)|	Retains only those elements in this collection which are also elements of passed collection.|
| 13. |void clear()|	Removes all elements in this collection.|
| 14. |boolean equals(Object o)|	Compares the specified object with this collection for equality.|
| 15. |int hashCode()|	Returns the hash code value of this collection.|

**Note :**

equals() and hashcode() methods in the Collection interface are not the methods of java.lang.Object class. Because, interfaces does not inherit from Object class. Only classes in java are inherited from Object class. Any classes implementing Collection interface must provide their own version of equals() and hashcode() methods or they can retain default version inherited from Object class.

# Collection Framework – List Interface Methods

List interface extends Collection interface. So, All 15 methods of Collection interface are inherited to List interface. Along with these methods, another 9 methods are included in the List interface to support the properties of lists. Here is the class diagram of List interface.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/ListInterface.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

| SL No.        | Method      |  Method      |
| ------------- |-------------|--------------|
| 1. |E get(int index)|Returns element at the specified position.|
| 2. |E set(int index, E element)|Replaces an element at the specified position with the passed element.|
| 3. |void add(int index, E element)|C	Inserts passed element at a specified index|
| 4. |E remove(int index)|Removes an element at specified index.|
| 5. |int indexOf(Object o)|It returns an index of first occurrence of passed object.|
| 6. |int lastIndexOf(Object o)|	It returns an index of last occurrence of passed object.|
| 7. |ListIterator<E> listIterator()|	It returns a list iterator over the elements of this list.|
| 8. |ListIterator<E> listIterator(int index)|	Returns a list iterator over the elements of this list starting from the specified index.|
| 9. |List<E> subList(int fromIndex, int toIndex)|	Returns sub list of this list starting from ‘fromIndex’ to ‘toIndex’.|

# Collection Framework – The Queue Interface Methods
Here are the methods of Queue interface. Some of the methods throw an exception if operation is not possible and some methods return a value (null or false) if operation is not possible.

| Operation      | Throws An Exception If operation is not possible    |  Returns null or false if operation is not possible     |
| -------------|-------------|--------------|
| Add an element to the queue.|add()|offer()|
| Retrieve an element from the head of the queue.|element()|peek()|
| Retrieve And Remove an element from the head of the queue.|remove()|poll()|

# Collection Framework – The Deque Interface Methods

| Operation            || Throws An Exception If operation fails.    |  Returns null or false if operation fails.     |
| -------------|-------------|-------------|--------------|
| Insertion |Front End|addFirst()|offerFirst()|
|      ^    |Rear End |addLast() |offerLast() |
| Retrieval |Front End|getFirst()|peekFirst() |
| ^         |Rear End |getLast() |peekLast()  |
| Retrieval And Removal |Front End|removeFirst()|pollFirst()|
| ^         |Rear End |removeLast() |pollLast()|

# Deque As Queue :
As Deque interface extends Queue interface, it inherits all methods of Queue interface. So, you can use all those inherited methods to perform Queue operations. Along with them, methods defined in the Deque interface can also be used for Queue operations. Below is the list of Queue methods and their equivalent Deque methods.

| Queue Methods            |Equivalent Deque Methods| 
| -------------|-------------|
| add()|addLast()|
| offer()|OfferLast()|
| element()|getFirst()|
| peek()|peekFirst()|
| remove()|removeFirst()|
| poll()|pollFirst()|

# Deque As Stack :
Deque interface has two more methods – pop() and push(). These two methods make Deque to function as a stack (Last-In-First-Out). Along with these two methods, you can also use addFirst(), peekFirst() and removeFirst() for stack operations. Below is the list of Stack methods and their equivalent methods of Deque.

| Stack Methods            |Equivalent Deque Methods| 
| -------------|-------------|
| push()|addFirst()|
| pop()|removeFirst()|
| peek()|peekFirst()|

# Collection Framework – The Set Interface Methods
Here is the list of Set interface methods. All methods are inherited from Collection interface.

| Method | Description | 
| -------------|-------------|
| int size()|Returns the number of elements in the set.|
| boolean isEmpty()|Checks whether the set is empty or not.|
| boolean contains(Object o)|Checks whether this set has specified element.|
| Iterator<E> iterator()|Returns an iterator over the set.|
| Object[] toArray()|	It returns an array containing all elements of the set.|
| <T> T[] toArray(T[] a)|It returns an array of specified type containing all elements of this set.|
| boolean add(E e)|This method adds specified element to this set only if that element doesn’t present already. It returns true if element is added successfully otherwise returns false.|
| boolean remove(Object o)|Removes the specified element from this set.|
| boolean containsAll(Collection<?> c)|It checks whether this set contains all elements of passed collection.|
| 	boolean addAll(Collection<? extends E> c)|Adds all elements of the passed collection to this set if they are not already present.|
| boolean removeAll(Collection<?> c)|Removes all elements of this set which are also elements of passed collection.|
| boolean retainAll(Collection<?> c)|Retains only those elements in this set which are also elements of passed collection.|
| void clear()|Removes all elements in this set.|
| boolean equals(Object o)|Compares the specified object with this set for equality.|
| int hashCode()|Returns the hash code value of this set.|

# Collection Framework – The SortedSet Interface Methods
SortedSet interface defines 6 more methods along with the inherited methods from Set interface. These methods make the processing of SortedSet elements more easy. Here is the list of SortedSet interface methods.

| SortedSet Interface Methods | Description | 
| -------------|-------------|
| Comparator<? super E> comparator()|Returns Comparator used to order the elements. If no comparator is supplied, it returns null.|
| SortedSet<E> subSet(E fromElement, E toElement)|Returns a portion of this set whose elements range from ‘fromElement’ (Inclusive) and ‘toElement’ (Exclusive).|
| SortedSet<E> headSet(E toElement)|Returns a SortedSet whose elements are in the range from first element of the set (Inclusive) to ‘toElement’ (exclusive).|
| SortedSet<E> tailSet(E fromElement)|Returns a SortedSet whose elements are in the range from ‘fromElement’ (Inclusive) to last element of the set (exclusive).|
| E first()|Returns first element of the SortedSet.|
| E last()|Returns last element of the SortedSet.|

# Collection Framework – The NavigableSet Interface Methods

The NavigableSet is a SortedSet with navigation facilities. The NavigableSet interface provides many methods through them you can easily find closest matches of any given element. It has the methods to find out less than, less than or equal to, greater than and greater than or equal of any element in a SortedSet.

The NavigableSet interface extends SortedSet interface. 

| NavigableSet Interface Methods | Description | 
| -------------|-------------|
| E lower(E e)|Returns greatest element in this set which is strictly less than the given element.|
| E floor(E e)|Returns greatest element in this set which is less than or equal to the given element.|
| E ceiling(E e)|Returns the least element in this set which is greater than or equal to the given element.|
| E higher(E e)|Returns the least element in this set which is strictly greater than the given element.|
| E pollFirst()|Retrieves and removes the first element in this set.|
| E pollLast()|Retrieves and removes last element in this set.|
| NavigableSet<E> descendingSet()|Returns reverse order view of this set.|
| Iterator<E> descendingIterator()|Returns an iterator over the elements of this set in descending order.|
| NavigableSet<E> subSet(E fromElement, boolean fromInclusive,E toElement, boolean toInclusive)|Returns a view of this set whose elements are in the range from ‘fromElement’ to ‘toElement’.|
| NavigableSet<E> headSet(E toElement, boolean inclusive)|Returns a view of this set whose elements are in the range from first element of this set to ‘toElement’.|
| NavigableSet<E> tailSet(E fromElement, boolean inclusive)|Returns a view of this element whose elements are in the range from ‘fromElement’ to last element of this set.|

# Java Collection Framework – The Map Interface Methods

|       SL NO.      | Methods     | Descriptions |
|-------------|-------------|-------------|
|1      |int size()|Returns number of key-value pairs in this map.|
|2      |boolean isEmpty()|Checks whether this map is empty or not.|
|3      |boolean containsKey(Object key)|Returns true if this map contains a mapping for the specified key.|
|4      |boolean containsValue(Object value)	|	Returns true if this map contains one or more keys associated with the specified value.|
|5      |V get(Object key)|Returns value associated with the specified key.|
|6      |V put(K key, V value)|Adds the specified key-value pair to this map. If the specified key already exist in the map, old value will be replaced by the specified value.|
|7      |V remove(Object key)|Removes the specified key along with it’s value from this map.|
|8      |void putAll(Map<? extends K, ? extends V> m)|Copies all key-value pairs from the specified map to this map.|
|9      |void clear()|Removes all mappings from this map.|
|10     |Set<K> keySet()|Returns a set containing all keys of this map. The returned set is backed by actual map. So, changes made to the map are reflected in the set and vice-versa.|
|11     |Collection<V> values()|Returns a collection of values of this map. The returned collection is backed by actual map. So, any changes made to the map is reflected in collection and vice-versa.|
|12     |Set<Map.Entry<K, V>> entrySet()|Returns set view of the mappings contained in this map.|
|13     |boolean equals(Object o)|Compares the specified object with this map.|
|14     |int hashCode()|Returns hashcode value of this map.|

# Important Methods Of HashMap In Java :
1) public V put(K key, V value)

This method inserts specified key-value mapping in the map. If map already has a mapping for the specified key, then it rewrites that value with new value.

2) public void putAll(Map m)

This method copies all of the mappings of the map m to this map.

3) public V get(Object key)

This method returns the value associated with a specified key.

4) public int size()

This method returns the number of key-value pairs in this map.

5) public boolean isEmpty()

This method checks whether this map is empty or not.

6) public boolean containsKey(Object key)

This method checks whether this map contains the mapping for the specified key.

7) public boolean containsValue(Object value)

This method checks whether this map has one or more keys mapping to the specified value.

8) public V remove(Object key)

This method removes the mapping for the specified key.

9) public void clear()

This method removes all the mappings from this map.

10) public Set<K> keySet()

This method returns the Set view of the keys in the map.

11) public Collection<V> values()

This method returns Collection view of the values in the map.

12) public Set<Map.Entry<K, V>> entrySet()

This method returns the Set view of all the mappings in this map.

13) public V putIfAbsent(K key, V value)

This method maps the given value with specified key if this key is currently not associated with a value or mapped to a null.

13) public boolean remove(Object key, Object value)

This method removes the entry for the specified key if this key is currently mapped to a specified value.

14) public boolean replace(K key, V oldValue, V newValue)

This method replaces the oldValue of the specified key with newValue if the key is currently mapped to oldValue.

15) public V replace(K key, V value)

This method replaces the current value of the specified key with new value.

# List Methods:

* get(int index)
* set(int index, E element)
* add(int index, E element)
* remove(int index)
* indexOf(Object o)
* lastIndexOf(Object o)
* listIterator()
* listIterator(int index)
* subList(int fromIndex, int toIndex)

# Queue Methods :

* **PriorityQueue** : 
    * add(), 
    * offer(), 
    * remove(), 
    * poll(), 
    * element(), 
    * peek(), 
    * clear(), 
    * comparator(), 
    * iterator(), 
    * forEach(), 
    * contains(), 
    * spliterator()


* **ArrayDeque** : 
    * add(), 
    * addAll(), 
    * addFirst(), 
    * addLast(), 
    * getFirst(),
    * getLast(), 
    * offer(), 
    * offerFirst(), 
    * offerLast(), 
    * peek(), 
    * poll(), 
    * pop(), 
    * push(), 
    * contains(), 
    * remove(), 
    * removeAll(), 
    * removeFirst(), 
    * removeFirstOccurrence(), 
    * removeLast(), 
    * removeLastOccurrence(), 
    * removeIf(), 
    * size(), 
    * clear(), 
    * isEmpty(), 
    * iterator(), 
    * spliterator()

# Set Methods :

* add(), 
* addAll(), 
* remove(), 
* removeAll(), 
* contains(), 
* containsAll(), 
* retainAll(), 
* size(), 
* clear(), 
* isEmpty(), 
* iterator(), 
* spliterator(), 
* toArray(), 
* copyOf(), 
* of()

# Map Methods :

* put(), 
* putAll(), 
* putIfAbsent(), 
* get(), 
* getOrDefault(), 
* remove(), 
* containsKey(), 
* containsValue(), 
* keySet(), 
* values(), 
* entrySet(),
* size(), 
* isEmpty(), 
* clear(), 
* compute(), 
* computeIfAbsent(), 
* computeIfPresent(), 
* forEach(), 
* merge(), 
* replace(), 
* replaceAll()

# Some Useful Methods Of java.Util.Collections :

| Method      |  Description      |
|-------------|--------------|
| Collections.copy()      |  This method is used to copy all elements from one list to another list.      |
| Collections.frequency()      |  This method checks the number of occurrences of a specified element in the given Collection.      |
| Collections.max()      |  It returns the maximum element in the given Collection.      |
|Collections.min()|It returns the minimum element in the given Collection.|
| Collections.replaceAll()      |  It replaces all occurrences of old value with new value in the given list.      |
|Collections.sort()|This method sorts the specified list in the ascending order.|
|Collections.synchronizedCollection()|This method returns the synchronized version of the specified Collection.|
|Collections.synchronizedList()|This method returns the synchronized i.e thread safe list backed by the specified list.|
|Collections.synchronizedMap()|This method returns the synchronized map backed by the specified map.|
|Collections.synchronizedSet()|This method returns the synchronized Set backed by the specified Set.|

# Iterator Methods :
<b>boolean hasNext()</b> –> Checks whether collection has more elements.

<b>E next()</b>  –> Returns the next element in the collection.

<b>void remove()</b>  –> Removes the current element in the collection i.e element returned by next().

# ListIterator Methods :
<b>boolean hasNext()</b> –> Checks whether the list has more elements when traversing the list in forward direction.

<b>boolean hasPrevious()</b> –> Checks whether list has more elements when traversing the list in backward direction.

<b>E next()</b>  –> Returns the next element in the list and moves the cursor forward.

<b>E previous()</b>  –> Returns the previous element in the list and moves the cursor backward.

<b>int nextIndex()</b> –> Returns index of the next element in the list.

<b>int previousIndex()</b> –> Returns index of the previous element in the list.

<b>void remove()</b>  –> Removes the current element in the collection i.e element returned by next() or previous().

<b>void set(E e)</b> –> Replaces the current element i.e element returned by next() or previous() with the specified element.

<b>void add(E e)</b> –> Inserts the specified element in the list.

# Properties Of LinkedList Class In Java:

* You can insert the elements at both the ends and also in the middle of the LinkedList. Below is the list of methods for insertion operations.

| Insertion At Head        | Insertion In The Middle      |  Insertion At Tail      |
| ------------- |-------------|--------------|
| addFirst(E e) |add(int index, E e)|add(E e)|
| offerFirst(E e) |addAll(int index, Collection c)|addAll(Collection c)|
|               |               |offer(E e)  |
|               |               |offerLast(E e)|

* You can remove the elements from the head, from the tail and also from the middle of the LinkedList.

| Removing from head        | Removing from the middle      |  Removing from the tail      |
| -------------|-------------|--------------|
| poll()       |Remove(int index)|pollLast()|
| pollFirst()  |           | removeLast()   |
| remove()     |           |                |
| removeFirst()|           |                |

* You can retrieve the elements form the head, from the middle and from the tail of the LinkedList. Below is the list of retrieval methods.

| Retrieving from the head        | Retrieving from the middle      |  Retrieving from the tail     |
| -------------|-------------|--------------|
| element()       |get(int index)|getLast()|
| getFirst() |           | peekLast() |
| peek()     |           |                |
| peekFirst()|           |                |

# How do you manipulate ArrayList elements?

ArrayList provides methods like get(), isEmpty(), contains(), indexOf(), replaceAll() to manipulate its elements. Where as array doesn’t provide such methods.

# ArrayList To Array In Java :

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2016/07/ArrayToArrayList.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

# How To Sort An ArrayList In Java?
To sort an ArrayList, we use sort() method of Collections class. Collections class is an utility class in java.util package consisting of many useful methods. (Collections and Collection are two different entities. Check this for more info). Collections.sort() method has two overloaded forms. They are,

1) sort(List<T> list)  :  This method sorts the specified list according to natural ordering of its elements.

2) sort(List<T> list, Comparator<? super T> c)  : This method sorts the specified list according to supplied Comparator.

These two methods are used not only just to sort the ArrayList, but also other list types like LinkedList and Vector. Let’s see how to sort an ArrayList with some simple examples.

# Elementary Modification Operations On ArrayList :
The following methods are used to perform elementary modification operations on ArrayList.

<b>boolean add(E e) :</b>

This method appends an element at the end of this List. If the ArrayList is empty then there will be exactly one element after this operation.

<b>void add(int index, E element) :</b>

This method inserts an element at the specified position.

<b>boolean remove(Object o) :</b>

It removes first occurrence of specified element from the list.

<b>E remove(int index) :</b>

This method removes an element from the specified position.

<b>E set(int index, E element) :</b>

This method replaces an element at the specified position with the passed element.

# Bulk Modification Operations On ArrayList :
The following methods are used to perform bulk modifications on ArrayList.

<b>boolean addAll(Collection<? extends E> c) :</b>

This method appends all elements of the passed collection at the end of this list.

<b>boolean addAll(int index, Collection<? extends E> c) :</b>

This method inserts all elements of the passed collection at the specified position in this list.

<b>boolean removeAll(Collection<?> c) :</b>

This method removes all elements of this list which are also elements of the passed collection.

<b>boolean retainAll(Collection<?> c) :</b>

This method retains only those elements in this list which are also elements of the passed collection.

<b>void clear() :</b>

This method removes all elements of the list.