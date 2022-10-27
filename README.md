# Example Maven multi-module project by modules

本项目为 Java 模块测试项目

## 模块化方式：

在父模块中使用<modules>标签指定子模块，在子模块中使用<parent>标签指定父模块

### 父模块 pom.xml

```xml
  <groupId>seal.io</groupId>
  <artifactId>example-root</artifactId>
  <version>2.0-SNAPSHOT</version>
  <name>example-root</name>
  <!-- pom 打包方式代表父工程 -->
  <packaging>pom</packaging>

  <!-- 父模块包含子模块 -->
  <modules>
    <module>module1</module>
    <module>module2</module>
  </modules>

   <!-- 父模块包含依赖，其中log4j包含漏洞，这些依赖将会被子模块继承 -->
  <dependencies>
    <dependency>
      <groupId>org.apache.logging.log4j</groupId>
      <artifactId>log4j-core</artifactId>
      <version>2.12.0</version>
    </dependency>
  </dependencies>
```

### 子模块 pom.xml

Module 1:

```xml
  <!-- 父模块的GAV -->
  <parent>
    <groupId>seal.io</groupId>
    <artifactId>example-root</artifactId>
    <version>2.0-SNAPSHOT</version>
  </parent>

  <!-- 子模块pom，groupID和version使用父模块的 -->
  <artifactId>module1</artifactId>
  <name>module1</name>
```

Module 2:

```xml
  <!-- 父模块的GAV -->
  <parent>
    <groupId>seal.io</groupId>
    <artifactId>example-root</artifactId>
    <version>2.0-SNAPSHOT</version>
  </parent>

  <!-- 子模块pom，groupID和version使用父模块的 -->
  <artifactId>module2</artifactId>
  <name>module2</name>
```
