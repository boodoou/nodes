# Lombok

---

## 1 常用注解

### @Data

### @Accessors

参数说明：

- fluent

  ```java
  @Data
  @Accessors(fluent = true)
  public class User {
      private Long id;
      private String name;
      
      // 生成的getter和setter方法如下，方法体略
      public Long id() {}
      public User id(Long id) {}
      public String name() {}
      public User name(String name) {}
  }
  ```

- **chain**

  ```java
  @Data
  @Accessors(chain = true)
  public class User {
      private Long id;
      private String name;
      
      // 生成的setter方法如下，方法体略
      public User setId(Long id) {}
      public User setName(String name) {}
  }
  ```

- **prefix**

  ```java
  @Data
  @Accessors(prefix = "p")
  class User {
  	private Long pId;
  	private String pName;
  	
  	// 生成的getter和setter方法如下，方法体略
  	public Long getId() {}
  	public void setId(Long id) {}
  	public String getName() {}
  	public void setName(String name) {}
  }
  ```

### @Builder

### @EqualsAndHashCode



