# Mybatis  
1.[#{}和\${}的区别是什么](#井号和\${}的区别是什么)  

## 1. #{}和\${}的区别是什么 <span id='井号和\${}的区别是什么'></span>  
 `${}`是 Properties 文件中的变量占位符，它可以用于标签属性值和 sql 内部，属于静态文本替换，比如order by 后的排序字段可以通过`${}`进行传入。  
 `#{}`是 sql 的参数占位符，MyBatis 会将 sql 中的`#{}`替换为?号，在 sql 执行前会使用 PreparedStatement 的参数设置方法，按序给 sql 的?号占位符设置参数值，比如 ps.setInt(0, parameterValue)，`#{item.name}` 的取值方式为使用反射从参数对象中获取 item 对象的 name 属性值，相当于 `param.getItem().getName()`。