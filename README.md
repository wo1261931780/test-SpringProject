# 🎓 test-SpringProject - Spring项目测试

![Java](https://img.shields.io/badge/Java-17+-orange?logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?logo=springboot)
![License](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)

## 📖 项目简介

test-SpringProject是Spring框架的综合性测试项目,演示Spring核心功能,包括IoC容器、AOP、事务管理、数据访问、Web开发等模块。

## 🏗️ 系统架构

```mermaid
graph TB
    subgraph "Spring核心"
        IoC[IoC容器]
        AOP[AOP模块]
        Context[上下文]
        Beans[Bean管理]
    end
    
    subgraph "数据访问"
        JDBC[JdbcTemplate]
        ORM[ORM框架]
        TX[事务管理]
        DAO[DAO模式]
    end
    
    subgraph "Web层"
        MVC[Spring MVC]
        REST[RESTful API]
        Security[安全框架]
        WebSocket[WebSocket]
    end
    
    subgraph "测试"
        UnitTest[单元测试]
        IntegrationTest[集成测试]
        MockTest[Mock测试]
    end
    
    IoC --> Beans
    Beans --> Context
    Context --> AOP
    
    JDBC --> TX
    ORM --> TX
    TX --> DAO
    
    MVC --> REST
    REST --> Security
    Security --> WebSocket
    
    Context --> UnitTest
    AOP --> IntegrationTest
    DAO --> MockTest
```

## 🚀 快速开始

```bash
# 克隆项目
git clone https://github.com/yourusername/test-SpringProject.git

# 运行项目
mvn spring-boot:run

# 运行测试
mvn test
```

## 💡 核心示例

### IoC容器

```java
@Configuration
@ComponentScan
public class AppConfig {
    
    @Bean
    public DataSource dataSource() {
        return DataSourceBuilder.create()
            .url("jdbc:mysql://localhost:3306/test")
            .username("root")
            .password("password")
            .build();
    }
    
    @Bean
    public JdbcTemplate jdbcTemplate(DataSource dataSource) {
        return new JdbcTemplate(dataSource);
    }
}
```

### AOP切面

```java
@Aspect
@Component
public class LoggingAspect {
    
    @Around("execution(* com.example.service.*.*(..))")
    public Object logMethod(ProceedingJoinPoint joinPoint) throws Throwable {
        String methodName = joinPoint.getSignature().getName();
        
        System.out.println("Before: " + methodName);
        Object result = joinPoint.proceed();
        System.out.println("After: " + methodName);
        
        return result;
    }
}
```

## 📝 更新日志

### v1.0.0 (2024-01-01)
- ✨ 初始版本发布
- ✨ 完成IoC容器测试
- ✨ 完成AOP切面测试
- ✨ 完成事务管理测试

---

⭐ 如果这个项目对你有帮助,欢迎Star支持!
