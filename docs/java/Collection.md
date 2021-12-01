# 集合  
1.[Set集合详解](#Set集合详解)   

## Set集合详解  
1.Set用于存入无序元素，值不能重复。   
2.HashSet会通过元素的hashcode（）和equals方法进行判断元素师否重复。HashSet集合在判断元素是否相同先判断hashCode方法，
如果相同才会判断equals。如果不相同，是不会调用equals方法的。  