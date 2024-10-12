# NestJS 笔记

## 命名规范

- 方法名 小驼峰命名
- 参数名 小驼峰命名

## 路由接口遵循 RESTfulAPI 设计风格

- 业务关联数据查询，只查询 Id，Name 字段，接口命名以 /r 开头。

## 不同请求参数接收方式

```js
// Swagger UI 接口说明
@ApiOperation({
    summary: '获取数据接口', // 简介描述
})

// URL传参
@ApiParam({ name: 'id', description: '评估 主键 ID' })

// GET请求传参数
@ApiQuery({ name: 'pageSize', description: '页数', example: 10 })
@ApiQuery({ name: 'pageNum', description: '页码', example: 1 })

// POST请求参数
@ApiBody({ type: Dto })
```

## 校验实体 常用数据类型

```js
@ApiProperty({
  description: '日期类型',
})
@IsNotEmpty({ message: '日期 不能为空' })
@IsDate({ message: '日期 类型错误' })
@Type(() => Date)
date: string;

@ApiProperty({
  description: '数字类型',
})
@IsNotEmpty({ message: '数量 不能为空' })
@IsNumber({}, { message: '数量 类型错误' })
quantity: number;

@ApiPropertyOptional({
  description: '字符类型',
})
@IsOptional()
@MaxLength(500, { message: '备注信息 最多500个字符' })
remark: string;
```
