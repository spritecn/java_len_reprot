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
- 字符串是不可变的，也就是说如果对字符串变量重新赋值，会重新生成一个对象
- String 创建方式有：
    - 字面量直接创建 Sting str = "abc";
    - new: String str = new String("abc")
- String 连接的方式有：
    - 直接用+号连接： Sting str = "aaa" + "bbb"
    - 用concat: Sting str = "aaa".concat("bbb")
    - 用 StringBuilder:
        ```java
            //参数 6用来指定初始容量，如果容量基本确认，设定初始容量可以提升性能
            StringBuilder stringBuilder = new StringBuilder(6); 
            stringBUilder.append("aaa");
            stringBuilder.append("bbb");
            String str = stringBuilder.toString();
        ```
    - 用StringBuffer,用法和StringBuilder一样，区多是，StringBuffer是多线程同步的，多线程安全
- String类常用方法有：
    - int String.length() 获取字符串长度
    - boolen String.equals(Str) 相同判断
    - byte[] String.getBytes(String charsetName):获取指定编码字符串码byte序列,如果不加charsetName会根据平台输出，一般建议一定要写上 "UTF8"
    - int String.indexOf(str),lastIndexOf(str):返回字符串或字符第一次或最后一次出现的位置
    - boolen String.matches(String regex):判断字符串是否和正则匹配
    - String String.replace("oldStr","newStr"):返回用newStr替换所有oldStr后的字符串
    - String String.replaceAll("regexStr","newStr")/replaceFirst:返回用newStr替换了所有与正则表达式匹配子串后的字符串/replaceFirst只替换第一个匹配到的子串
    - String[] String.split(String regex,int limit):根据正则分割字符串，可以直接定字符串，("acount=? and uu =? or n=?").split("and|or"),可以实现多条分割;如果加了limit参数，大于limit-1的内容会合并成一个，适用于只需要前几个分割串的时候
    - boolen String.startsWith("prefix")/endsWith:判断字符串是否以prefix开始/结束
    - String String.subString(int beginIndex,int endIndex):返回从beginIndex到endIdex的子字符串
    - String String.trim()/:去除前后所有空白字符，包含 ('/t', '/n', '/v', '/f', '/r', ' ', '/x0085', '/x00a0', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', '?', '/u2028', '/u2029', ' ', '?')
    - toLowCase,toUpCase:转换大小写
- StringUtils，是Apache common工具包提供的String工具类：
    - 使用时需要导入org.apache.commons.lang3.StringUtils
    - 常用方法有：
        - 判空类：StringUtils.isEmpty("str"),isNotEmpty,isBlank,isNotBlank
        - 去空白除类：StringUtils.trim("str")只去除控制字符，strip("str")/stripStart,stripEnd只去除两端空白字符,stripAll去除所有空白字符
            - trimToNull,stripToNull,trimToEmpty,stripToEmpty,去除后如果是空串，返回null，stripToNull("") = null
        - 判断相同类 StringUtils.equals(str1,str2), 忽略大小写：StringUtils.equalsIgnoreCase(str1, str2)
        - 拼接：StringUtils.join/StringUtils.joinWith:
            ```java
                String[] strs={"I","love","chinese","family"};
                System.out.println(StringUtils.join(strs));//Ilovechinesefamily
                System.out.println(StringUtils.join(strs,","));//I,love,chinese,family
                System.out.println(StringUtils.joinWith(",","I","love","chinese","family"));//I,love,chinese,family
            ```
        - 字符串位置类：indexOf,startsWith/endsWith 和String类一致
        - 是否包含： StringUtils.contains("str1","str2")
        - 类型判断类：
            - StringUtils.isAlpha 是否只包含字符
            - StringUtils.isisAlphanumeric 只包含字符和数字
            - StringUtils.isNumeric 只包含数值 小数也算
            - 以上三个可以后面加Space加入包含空格 isAlphaSpace,isNumerSpace
            - StringUtils.isWhitespace 只包含空格
        - 截取类：
            - StringUtils.substring 和String.subString一样
            - StringUtils.left("str",1)/right 取左边/右边
            - StringUtils.mid("str",1,2) 从第1个开始取两个
            - StringUtils.substringBetween(testString,fromString,toString ):取得两字符之间的字符串
            - StringUtils.substringAfter( ):取得指定字符串后的字符串
            - StringUtils.substringBefore( )：取得指定字符串之前的字符串
            - StringUtils.substringBeforeLast( )：取得最后一个指定字符串之前的字符串
            - StringUtils.substringAfterLast( )：取得最后一个指定字符串之后的字符串
        - 字符串翻转：StringUtils.reverse("abcdef")//fedba
        - 数组转字符串StringUtil.convString(String []/List,","),第二个参数为分隔符,默认是,


# Collection
1. Collection 是层次结构 中的根接口
1. Collection 继承自Iterable,即可迭代，可forearch
1. Collection 具体有子接口Set 和 List 
1. Set 和 List 的区别主要是 List内元素可重复，Set内元素不可重复
## List
1. 主要包含 ArrayList,LinkedList，CopyOnWriteArrayList,Vector 实现
1. ArrayList 是基于数组实现的
1. LinkedList 是基于链表实现的
1. Vector 和 ArrayList 也是基于数组实现的，但是他是线程安全的
1. CopyOnWriteArrayList 是ArrayList的线程安全封装，用写时copy方式同步
1. ArrayList,LinkedList的主要区别在于 ArrayList实现了随机访问get set较快，而LinkedList add和remove较快
1. 一般使用ArrayList,当add数据量大时使用LinkedList
## Set
1. Set的主要实现有HashSet,LinkedHashSet,TreeSet,EmnuSet
2. HashSet 基于HashMap实现,LinkedHashSet 基于LinkedHashMap实现
3. TreeSet 是基于TreeMap实现的，并且实现了SortSet接口，使用元素的自然顺序对元素进行排序，或者根据创建 set 时提供的 Comparator 进行排序
4. EmnuSet 是专门给枚举类的set类，Emnu类值少于16时 保存的值是Emnu位，比较少用
4. 上述实现都是线程不安全的，可以通过 Set s = Collections.synchronizedSortedSet(new TreeSet(...));包装来实现线程同步

# Map
1. Map<K,V>是一种将键映射到值的对象
2. 主要包含 HashMap,Hashtable,LinkedHashMap,TreeMap,Hashtable实现，还有枚举的EmnuMap
3. 实现类初始化时，可以传入初始容量，如果容量固定，建议传入，可优化性能
4. HashMap基于Hash实现,无序,允许使用单个null 键，Hashtable与 HashMap类似，它继承自Dictionary类。不同的是：它不允许记录的键或者值为空；它支持线程的同步
5. LinkedHashMap,是HashMap的子类，保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的
6. TreeMap 根据键的自然顺序排序，基于红黑树实现
7. EmnuMap 的键必须是枚举值,
4. 非同步类实现，可通过 Map m = Collections.synchronizedMap(new HashMap(...));包装实现同步
