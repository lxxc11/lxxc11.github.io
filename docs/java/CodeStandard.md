# 编码规范  
1.[避免内嵌多个if](#避免内嵌多个if)  
2.[直接return精简返回对象](#直接return精简返回对象)  
3.[多异常合并](#多异常合并)  
4.[Integer.valueOf与Integer.parseInt的使用](#区别valueof与parseint使用)  
5.[创建空对象优化](#创建空对象优化)  
6.[拒绝魔法值](#拒绝魔法值)

## 避免内嵌多个if  
错误示例代码  
```java
        if (CollectionUtils.isNotEmpty(roleInfos)) {
            for (RoleInfo roleinfo : roleInfos) {
                if (GLOBAL_ADMIN_ROLE.equals(roleinfo.getRole())) {
                    return true;
                }
            }
        }
```  
正确示例代码  
```java
        if (CollectionUtils.isEmpty(roleInfos)) {
            return false;
        }
        for (RoleInfo roleinfo : roleInfos) {
            if (GLOBAL_ADMIN_ROLE.equals(roleinfo.getRole())) {
                return true;
            }
        }
```  

## 直接return精简返回对象  
错误示例代码  
```java
            Response response = client.request(request, timeoutMills);
            return response;
```  
正确示例代码  
```java
            return client.request(request, timeoutMills);
```

## 多异常合并  
错误示例代码  
```java
        try {
            //TODO
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
```  
正确示例代码  
```java
        try {
            //TODO
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        } 
```
## Integer.valueOf与Integer.parseInt的使用<span id="区别valueof与parseint使用"></span>    
错误示例代码  
```java
        int avg = Integer.valueOf(avgString.toString());
```  
正确示例代码  
```java
        int avg = Integer.parseInt(avgString.toString());
```

## 创建空对象优化  
错误示例代码  
```java
Response response = null;
```  
正确示例代码  
```java
Response response;
```  

## 拒绝魔法值  
错误示例代码  
```java
String value = System.getProperty("project.name");
```  
正确示例代码  
```java
String value = System.getProperty(IdentifyConstants.PROJECT_NAME_PROPERTY);
```