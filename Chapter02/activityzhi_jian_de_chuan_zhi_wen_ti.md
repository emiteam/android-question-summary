# Activity之间的传值问题
####1.利用Intent对象携带简单数据类型数据
利用Intent的Extra部分来存储我们想要传递的数据，可以传送int, long, char等一些基础类型,对复杂的对象就无能为力了。

1.1 设置参数

```Intent intent = new Intent();  
intent.setClass(MainActivity.this,NextActivity.class); 
Bundle bundle = new Bundle();  
bundle.putString("name", "zhouqingpeng"); 
bundle.putString("pwd", "123456"); 
intent.putExtras(bundle);  
startActivity(intent);  ```

1.2 接收参数

```Bundle bunde = this.getIntent().getExtras();  
String name = bunde.getString("name");  
String pwd = bunde.getString("pwd");  ```


