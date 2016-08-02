#1.构造继承
利用call()或apply()在子类型构造函数中运行父类型构造函数以达到继承目的<br>
缺陷:无法继承原型属性和方法，没有原型无法复用

#2.原型继承
利用原型链原理将子类型原型指向父类型实例实现继承<br>
缺陷:<br>
1.创建子类型实例时无法向父类型传递参数<br>
2.重写子类的原型等于父类的一个实例，如果父类包含引用类型的属性，那么子类所有实例都会共享该属性(这句话来自http://blog.csdn.net/xuqinggangsls/article/details/51490390)

#3.组合继承
利用原型继承和构造继承组合创造的组合继承，使子类型既能继承父类型的原型方法和属性，也能使子类型实例时能够向父类型传递参数
缺陷:<br>
在创建子类型原型和子类型构造函数时都分别调用了父类型构造函数

#4.寄生组合继承
原型链继承时不用实例化父类型，而只用实例化一个临时副本(子类原型不是直接指向父类父类实例化对象，而是指向父类副本的实例化对象)，从而改进了组合继承两次调用父类型构造函数的缺点

#\#tips
###typeof                  
例:<br>
typeof(1)==number  //true<br>
判断变量是否为空或者是什么类型的<br>
ps:用if(typeof(a)===undefind)比if(!a)好，因为当a未声明时前者并不会抛出异常<br>

###instanceof              
例:<br> 
var child = new parent()     
child instanceof parent //true  
判断child是否是parent的实例 

###isPrototypeOf           
例:<br> 
var child = new parent()    
parent.prototype.isPrototypeOf(child) //true  
判断parent.prototype是否出现在child的原型链中

###getPrototypeOf        
例:<br> 
function parent(){}<br> 
parent.prototype.name="chen";<br> 
var child = new parent();<br> 
console.log(Object.getPrototypeOf(child).name)  //"chen"<br> 
返回child的原型

###hasOwnProperty
例:<br> 
function parent(){<br> 
  this.age=13;<br> 
}<br> 
parent.prototype.name="chen";<br> 
var child = new parent();<br> 
console.log(child.hasOwnProperty("age"))    //true   该属性是child继承父类型构造函数的属性<br> 
console.log(child.hasOwnPrototype("name"))  //false  该属性是从父类型原型对象继承来的<br> 
child.name="tan";                           //通过重写屏蔽了原来的属性name，此时这个name就成了实例真正的属性<br> 
console.log(child.hasOwnPrototype("name"))  //true  是child实例真正有的属性 <br> 
<br>
判断实例中的某个属性是否是来自本地属性还是继承自其父类型的原型对象的属性

###in
例:<br> 
console.log("age" in child)    //true  该属性是child的属性<br> 
console.log("name" in child)   //true  该属性是child的属性<br> 
<br>
判断某个属性是否是属于实例对象，无论是来自本地属性还是继承自其父类型的原型对象的属性

###值类型
数字、字符串、布尔值、null、undefined<br>
值类型a传递给另一个变量b时，实际上是分配了一个新的内存空间给b，b的任何修改都不会影响a的值

###引用类型
数组、对象、函数<br>
引用类型a传递给另一个变量b时，实际上是将a的地址指针复制给了b，a、b的修改都会对引用类型的值造成影响


