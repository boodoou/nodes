# JAVA 



## 1 创建对象

### 1.1如何通过反射机制获取类的私有构造器？怎么规避？

### 1.2什么是过程化的编程？静态工具类是不是过程化的？

### 1.3子类实例化时会调用父类的构造器，这个动作发生在子类中还是父类中？

子类在实例化时，会在子类的构造器中调用父类的构造器，而且必须是子类构造器中的第一个语句；

这个语句在没有声明时是默认存在的，它默认会调用父类的默认构造器，即父类的无参构造器；

如果父类没有无参构造器时，需要在子类的构造器中通过supper(...)调用相应的构造器，否组编译会报错，如：

```java
    // BigCar extends Car
	public BigCar() {
        super("car");
        // ...
    }
```

当子类的构造器中无法调用父类的任何构造器时，这个类是无效的，也无法通过编译。

### 1.4只有私有构造器的类能不能被继承？如果能，它的子类能不能被实例化？

如果一个类只存在私有的构造器，那么这些构造器是无法被除了自身以外的类调用的，当然也包括其它类的构造器中，即子类无法在构造器中实现父类构造器的调用，这个子类是无效的，亦即只包含私有构造器的类是无法被继承的。

### 1.5子类可以调用父类的静态方法吗？

可以。

### 1.6 Map的KeySet是否可以直接修改？如果可以，会不会影响原Map的KeySet？

以常用的HashMap为例（Map的不同实现类存在差异），首先，可以通过keySet()方法获取Map的KeySet，它是Map的一个内部类，在HashMap中是这样声明的：

```java
 final class KeySet extends AbstractSet<K> {...}
```

而AbstractSet又继承了AbstractCollection：

```java
public abstract class AbstractSet<E> extends AbstractCollection<E> implements Set<E> {...}
```

KeySet和AbstractSet中都没有重写add方法，KeySet的add方法来自于父类的父类AbstractCollection：

```java
public boolean add(E e) {
    throw new UnsupportedOperationException();
}
```

如果直接调用keySet的add()方法，它会抛异常；

但是，KeySet重写了remove()方法，它直接操作Map的数据，与Map的remove()是等价的：

```java
public final boolean remove(Object key) {
    return removeNode(hash(key), key, null, false, true) != null;
}
```

可见，HashMap的KeySet不允许添加新值（新Key）,但是可以删除Key，而且同时可以删除该Key对应的数据。

### 1.7 怎样有效地使用接口的默认方法？



