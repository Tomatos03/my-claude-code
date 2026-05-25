# {{SYSTEM_NAME}}-{{SIDE_NAME}}接口文档

## 公共约束

### 响应结构

所有接口响应均遵循以下统一格式：

**响应头参数**：

| 参数名 | 参数值 |
|--------|------|
| Content-Type | application/json |

**响应数据结构**：

```json
{
    "code": 200,
    "message": "success",
    "data": {}
}
```

| 字段 | 类型 | 说明 |
|------|------|------|
| code | Integer | 业务状态码，1 为成功 / 0为失败 |
| message | String | 提示信息 |
| data | Object | 存放响应数据体 |

**分页查询响应结构**：

```json
{
    "code": 200,
    "message": "success",
    "data": {
        "records": [],
        "total": 100,
        "size": 10,
        "current": 1,
        "pages": 10
    }
}
```

| 字段 | 类型 | 说明 |
|------|------|------|
| records | Array | 当前页数据列表，具体字段见各接口的「records 字段说明」 |
| total | Long | 总记录数 |
| size | Long | 每页数量 |
| current | Long | 当前页码 |
| pages | Long | 总页数 |

### 认证方式

除特别说明外，所有接口均需要在请求头参数中携带 JWT Token 进行认证:

```
Authorization: Bearer <token>
```

---

{{MODULES_SECTION}}

---

## 附录

### 枚举值定义

{{ENUM_DEFINITIONS}}
