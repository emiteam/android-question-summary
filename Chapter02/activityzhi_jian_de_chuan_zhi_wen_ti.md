# Activity之间的传值问题
####1.利用Intent对象携带简单数据类型数据
利用Intent的Extra部分来存储我们想要传递的数据，可以传送int, long, char等一些基础类型,对复杂的对象就无能为力了。

1.1 设置参数

```java
Intent intent = new Intent();  
intent.setClass(MainActivity.this,NextActivity.class); 
Bundle bundle = new Bundle();  
bundle.putString("name", "zhouqingpeng"); 
bundle.putString("pwd", "123456"); 
intent.putExtras(bundle);  
startActivity(intent);  
```

1.2 接收参数

```java
Bundle bunde = this.getIntent().getExtras();  
String name = bunde.getString("name");  
String pwd = bunde.getString("pwd");  
```

####2.利用Intent对象携带如ArrayList之类复杂些的数据
这种原理是和上面一种是一样的，只是要注意下。 在传参数前，要用新增加一个List将对象包起来。

2.1 设置参数传递复杂些的参数  

```java
Map map1= new HashMap(); 
map1.put("key1", "value1");  
map1.put("key2", "value2");  
List<Map> list = new ArrayList<Map>();  
list.add(map1);  
Intent intent = new Intent();  
intent.setClass(MainActivity.this,ComplexActivity.class); 
Bundle bundle = new Bundle();  
//须定义一个list用于在budnle中传递需要传递的ArrayList
ArrayList bundlelist = new ArrayList();   
bundlelist.add(list);   
bundle.putParcelableArrayList("list",bundlelist); 
intent.putExtras(bundle);               
startActivity(intent);  
```

2.2 接收参数

```java
Bundle bundle = getIntent().getExtras();   
ArrayList list = bundle.getParcelableArrayList("list");  
List<Map> lists = (List<Map>)list.get(0);  
String sResult = "";  
   for (Map m : lists){
      for (String k : m.keySet()){
         sResult += "\r\n"+k + " : " +m.get(k);
      }            
}
```

####3.通过实现Serializable接口
3.1 设置参数
利用Java语言本身的特性，通过将数据序列化后，再将其传递出去。

//通过Serializable接口传参数的例子  

```java
HashMap map2= new HashMap();  
map2.put("key1", "value1");  
map2.put("key2", "value2");  
Bundle bundleSerializable = new Bundle();  
bundleSerializable.putSerializable("serializable",map2);  
Intent intentSerializable = new Intent();    
intentSerializable.putExtras(bundleSerializable);  
intentSerializable.setClass(MainActivity.this,SerializableActivity.class);
startActivity(intentSerializable);
```

3.2 接收参数


```java
Bundle bundle =this.getIntent().getExtras();           
HashMap map = (HashMap)bundle.getSerializable("serializable");
String sResult = "map.size() ="+map.size(); 
Iterator iter = map.entrySet().iterator();
while(iter.hasNext()){  
    Map.Entry entry = (Map.Entry)iter.next(); 
    Object key = entry.getKey();
    Object value = entry.getValue();
    sResult +="key----"+(String)key;
    sResult +="value----"+(String)value;
}
```

