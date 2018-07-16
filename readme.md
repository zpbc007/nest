# nestjs学习

## 创建工程

```shell
$ npm i -g @nestjs/cli
$ nest new project
```

核心文件
```
src
|-- app.controller.ts
|-- app.module.ts
|-- main.ts
```

|文件|描述|
|---|---|
|main.ts|应用程序入口文件。使用 __NestFactory__用来创建Nest实例|
|app.module.ts|定义AppModule应用程序的根模块|
|app.controllers.ts|带有单个路由的基本控制器示例|

## 注解

- @Controller(prefix?: stirng)

标注一个class为controller，接收一个参数作为路由前缀

```typescript
import { Controller, Get } from '@nestjs/common'

@Controller('cats')
export class CatsController {
    @Get()
    findAll() {
        return []
    }
}
```

- @Request()

http请求对象

- @Response()

http响应对象

- @Next()

next

- @Session()

req.session

- @Param(param?: string)

req.params / req.params[param]

- @Body(param?: string)

req.body / req.body[param]

- @Query(param?: string)

req.query / req.query[param]

- @Headers(param?: string)

req.headers / req.headers[param]

- @Get()

http get 请求

- @Post()

http post 请求

- @Put()

http put 请求

- @Delete()

http delete 请求

- @Patch()

http patch 请求

- @Options()

- @Head()

- @All()

- @HttpCode()

更改res返回code

## 处理响应的方法

 - 直接返回对象或数组会自动转为JSON。返回字符串时，Nest将返回一个字符串。默认返回状态码200，post为201。可以通过@HttpCode()改变返回的状态码
 - 可以注入@Res响应对象并改变它

## 路由参数

```typescript
@Get(:id)
findOne(@Param() params) {
    console.log(params.id)
    return {}
}
```

## 模块

|名称|描述|
|---|---|
|providers|有Nest注入器实例化的提供者，并且可以至少在整个模块中共享|
|controllers|必须创建的一组控制器|
|impots|导入模块所需的导入模块列表|
|exports|此模块提供的提供者的子集，并应在其他模块中使用|