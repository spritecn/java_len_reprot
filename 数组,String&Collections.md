# Array数组
- 数组和Collection的区别是，数组可以存基础类型和对象，Colection只能存对像，不能存基础类型
- 数组创建：
  - 先声明后初始化
    ```java
    int siz = 3;
    int[] intArray;
    intArray = new int[size]  //数字的大小是不可变的，也不是不能add
    ```
  -    声明并初始化
    ```
    int[] intAarray = new int[3]
    ```
  - 初始化并赋值
    ```java
    int[] intAarray = {3，4，5}
    ```
- 元素值更改
    ```java
    intArray[0] = 3;
    ```
- 遍历数组
    ```java
    for(int item:intArray){
        System.out.println(itm);
    }
    ```
    ```java
    for(int i;i<intArray.size();i++){
        System.out.println(item);
    }
    ```
- Arrays工具类,常用方法
  - Arrays.toSting(array),打印
  - Arrays.asList(array),将array转为列表，这个列表不能add，如果是原始类型，会将整个list转为一个元素
  - Arrays.sort(array)，对array进行自然排序,注原地排序不是排序后返回
  - Arrays.fill(array,arrayType value),将value值分配给所有的元素
  - Arrays.copyOf(array,int index),复制从0到inex的元素到新数组，不包括index,如果不写index是全部复制
  - Arrays.copyOfRange(array, int from, int to),复制从from到to的元素到新数组，不包括to
  - Arrays.equals(array1,array2),比较两个array的所有值是否相同
  - Arrays.deepEquals,Arrays.deepToSting,深度遍历比较/打印
  - Arrays.stream(array),生成java8的stream,用于函数式并行操作，类同Stream.of(array)，对于原生对像，Arrays.stream(array)会自动做包装类操作，而Stream.of(array)，是将整个list放入stream.

# String
- String 字符串类,核心是一个char数组


# Collection

## List
### ArrayList

### LinkedList

## Map
### HashMap
### LinkedHashMap
### TreeMap

## Set