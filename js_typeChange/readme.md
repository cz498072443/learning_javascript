观点来源 http://justjavac.com/javascript/2012/12/20/object-plus-object.html

#原始值转原始值
(1)转数字参考观点来源中的ToNumber()<br>
(ps:补充一点当string不能成功转数字时则返回NaN),转字符串参考观点来源中的ToString()<br>
(2)转boolean:'',+-0,NaN转换为false<br>

#原始值转对象
这个目前还很迷

#对象转原始值
###ToPrimitive()转换为原始类型
(1)如果待转换的变量本身为对象则先执行valueOf(),若执行后返回值为原始类型则返回这个原始值<br>
(2)如果不是原始类型则执行toString(),若执行后返回值为原始类型则返回这个原始值<br>
(3)如果还不是原始类型则报错(TypeError)<br>
ps:Date类型对象会先执行toString(),其他类型的值都是先执行valueOf()<br>

###ToNumber()转换为数字
(1)如果待转换的变量为对象,则先调用ToPrimitive()将其转换成原始类型<br>
(2)将返回的原始类型通过调用ToNumber()转换为数字<br>

###ToString()转换为字符串
(1)如果待转换的变量为对象,则先调用ToPrimitive()将其转换成原始类型<br>
(2)将返回的原始类型通过调用ToString()转换为数字<br>
