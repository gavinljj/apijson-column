# apijson-column  [![](https://jitpack.io/v/APIJSON/apijson-column.svg)](https://jitpack.io/#APIJSON/apijson-column)
腾讯 [APIJSON](https://github.com/Tencent/APIJSON) 4.6.6+ 的字段插件，支持 字段名映射 和 !key 反选字段，可通过 Maven, Gradle 等远程依赖。<br />
A column plugin for Tencent [APIJSON](https://github.com/Tencent/APIJSON) 4.6.6+ , support Column Inverse and Column Mapping.

## 添加依赖
## Add Dependency

### Maven
#### 1. 在 pom.xml 中添加 JitPack 仓库
#### 1. Add the JitPack repository to pom.xml
```xml
	<repositories>
		<repository>
		    <id>jitpack.io</id>
		    <url>https://jitpack.io</url>
		</repository>
	</repositories>
```
<br />

#### 2. 在 pom.xml 中添加 apijson-column 依赖
#### 2. Add the apijson-column dependency to pom.xml
```xml
	<dependency>
	    <groupId>com.github.APIJSON</groupId>
	    <artifactId>apijson-column</artifactId>
	    <version>LATEST</version>
	</dependency>
```

<br />
<br />

### Gradle
#### 1. 在项目根目录 build.gradle 中最后添加 JitPack 仓库
#### 1. Add the JitPack repository in your root build.gradle at the end of repositories
```gradle
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```
<br />

#### 2. 在项目某个 module 目录(例如 `app`) build.gradle 中添加 apijson-column 依赖
#### 2. Add the apijson-column dependency in one of your modules(such as `app`)
```gradle
	dependencies {
	        implementation 'com.github.APIJSON:apijson-column:latest'
	}
```

<br />
<br />
<br />

## 初始化
## Initialization
见 [ColumnUtil](/src/main/java/apijson/column/ColumnUtil.java) 的注释及 [APIJSONBoot](https://github.com/APIJSON/APIJSON-Demo/blob/master/APIJSON-Java-Server/APIJSONBoot) 的 [DemoSQLConfig](https://github.com/APIJSON/APIJSON-Demo/blob/master/APIJSON-Java-Server/APIJSONBoot/src/main/java/apijson/demo/DemoSQLConfig.java) 和 [DemoSQLExecutor](https://github.com/APIJSON/APIJSON-Demo/blob/master/APIJSON-Java-Server/APIJSONBoot/src/main/java/apijson/demo/DemoSQLExecutor.java) <br />

See document in [ColumnUtil](/src/main/java/apijson/column/ColumnUtil.java) and [DemoSQLConfig](https://github.com/APIJSON/APIJSON-Demo/blob/master/APIJSON-Java-Server/APIJSONBoot/src/main/java/apijson/demo/DemoSQLConfig.java), [DemoSQLExecutor](https://github.com/APIJSON/APIJSON-Demo/blob/master/APIJSON-Java-Server/APIJSONBoot/src/main/java/apijson/demo/DemoSQLExecutor.java) in [APIJSONBoot](https://github.com/APIJSON/APIJSON-Demo/blob/master/APIJSON-Java-Server/APIJSONBoot)

<br />
<br />
<br />

## 使用
## Usage

### 1.反选字段
### 1.Column Inverse
"@column": "!columnKey"  // 返回排除 columnKey 后的全部其它字段 <br />
"@column": "!columnKey"  // return all columns except for columnKey
```js
{
    "User": {  // id,sex,name,tag,head,contactIdList,pictureList,date
        "id": 82001,
        "@column": "!contactIdList"  // -> id,sex,name,tag,head,pictureList,date
    }
}
```

![image](https://user-images.githubusercontent.com/5738175/113572899-ab903380-964b-11eb-9f3c-69f3437d8a54.png)


### 2.字段名映射
### 2.Column Mapping
"@column": "showKey"  // 隐藏了数据库的对应真实字段名 <br />
"@column": "showKey"  // the real column name is hidden
```js
{
    "User": {  // id,sex,name,tag,head,contactIdList,pictureList,date
        "id": 82001,
        "@column": "gender"  // -> sex 
    }
}
```

![image](https://user-images.githubusercontent.com/5738175/113572926-b77bf580-964b-11eb-8a17-10917669c2aa.png)

注意：[APIAuto](https://github.com/TommyLemon/APIAuto) 不能自动获取并展示对应映射字段 showKey 的类型、长度、注释等文档，只能通过手写注释来实现 <br />
Note: [APIAuto](https://github.com/TommyLemon/APIAuto) cannot automatically get and show the document for the showKey, you can add comment manually. 

<br /><br />

#### 对你有用的话点右上角 ⭐Star 支持一下，谢谢 ^_^
#### Please ⭐Star this project ^_^
https://github.com/APIJSON/apijson-column
