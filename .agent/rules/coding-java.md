---
trigger: glob
globs: ["**/*.java"]
---

# Java 编码规范 (ms-java-yaml2code-sdk)

## 基础规范（遵循全局 Java DDD 规范）

### 命名约定
- 类名 `PascalCase`，方法/变量 `camelCase`，常量 `UPPER_SNAKE_CASE`

### 单一职责
- 每个类/方法只做一件事，函数不超过 50 行，文件不超过 300 行

### 错误处理
- **禁止**空的 `try-catch` 块，必须精准捕获并记录日志
- 对外部 YAML 输入进行合法性校验（防御性编程）

### SDK 设计规范
- SDK 公共 API 必须有 Javadoc 注释（描述功能、参数、返回值、异常）
- 使用 Builder 模式封装复杂对象构建
- 解析异常必须包装为业务语义明确的自定义异常（如 `YamlParseException`）

### OpenAPI 解析
- 使用 Jackson 的 `ObjectMapper` 或 SnakeYAML 解析，禁止手写字符串处理
- 解析后的模型必须是类型明确的 POJO，禁止使用 `Map<String, Object>` 传递解析结果
