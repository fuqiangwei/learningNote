# Angular4




## 搭建开发环境
  Angular-CLI、webpack
## 组件与指令
### 数据绑定
- 事件绑定:

```Html
<input (input)="onInputEvent($event)">

```
### HTML属性绑定
#### 基本HTML属性绑定
```html
<td [attr.colspan]="tablecolspan">something</td>

```

#### css类绑定
```html
<!-- someExpression表达式会替换掉aaa bbb  -->
<div class="aaa bbb" [class]="someExpression"></div>
<!-- 如果isSpecial为true, 会添加ccc -->
<div class="aaa bbb" [class.ccc]="isSpecial">something</div>

<div [ngClass]="{aaa:isAAA, bbb: isBBB}">something</div>
```
#### 样式绑定

```html
<button [style.color]="isTrue ?'red' :'green'">red</button>
<span [ngStyle]="{'font-style':this.canSave ? 'italic':'normal'}">something</span>
```

组件与指令、模板、数据绑定与事件绑定、组件间通讯、生命周期、动效、服务、管道
## 模块与共享模块
## 路由与动态加载
### Route 导航
  - Routes: 路由配置, 保存着哪个URL对应展示哪个组件,以及在哪个`RouterOutlet`中展示组件
  - RouterOutlet: 在Html中标记路由内容呈现位置的占位符指令
  - Router: 负责在运行时执行路由的对象, 可以通过调用其`navigate()`和`navigateByUrl()`方法来导航到一个指定的路由
  - RouterLink: 在HTML中声明路由导航用的指令,参数是数组
  - ActivateRoute: 当前激活的路由对角,保存着当前路由的信息,如路由地址,
### 路由传递数据
  - 查询参数: `/product?id=1&name=2`   => `ActivatedRoute.queryParams[id]`
  - 路由路径: `{path/product/:id}` => `ActivateddRoute.queryParams[id]`
  - 路由配置: `{path:/product, component:ProductComponent, data:[{isProd:true}]}` => `ActivatedRoute.data[0][isProd]`
### 路由重定向和子路由和辅助路由
#### 辅助路由

```html
<router-outlet></router-outlet>
<router-outlet name="aux"></router-outlet>

{path:'xxx',component:XxxComponent, outlet:"aux"}
{path:'yyy',component:YyyComponent, outlet:"aux"}

<a [routerLink] = "['/home', {outlets: {aux: 'xxx'}}]">xxx</a>
<a [routerLink] = "['/product', {outlets: {aux: 'yyy'}}]">yyy</a>

```
#### 路由守卫

> 只有用户已经登录并拥有某些权限时才能进入某些路由.
> 一个由表单组成的向导,例如注册流程,用户只有在当前路由的组件中填写了满足要求的信息才可以导航到下一个路由.
> 当用户未执行保存操作而试图离开当前导航时提醒用户.

- CanActivate: 处理导航到某路由的情况
- CanDeactivate: 处理从当前路由离开的情况
- Resolve: 在路由激活之前获取路由数据

 基本用法、多层嵌套、动态加载模块、

## 依赖注入

> 依赖注入: DI `Dependency Injection`
> 控制反转: IOC `Inversion Of Control`
> 注入器: `constructor(private productService: ProductService){}`
> 提供器: `providers: [ProductService]` 或`[{providers: ProductService, useClass: ProductService}]`

## 表单与数据校验
### 模板式表单
> 表单的数据模型是通过组件模板中的相关指令来定义的,因此使用这种方式定义表单的数据模型时,我们会受限于HTML语法,所以模板驱动的方式只适合用于一些简单的场景

### 响应式表单
> 通过编写`TypeScript`代码而不是Html代码来创建一个底层的数据模型,在这个模型定义好后,使用一些特定的指令,将模板上的HTML元素与底层的数据模型连接在一起.

### 区别
- 不管是哪种表单,都有一个对应的数据模型来存储表单的数据. 在模板式表单中,数据模型是由`angular`基于组件模板中的指令隐式创建的. 而在响应表单中,是通过编码明确的创建数据模型然后将模板上的`html`与底层的数据模型转接在一起
- 数据模型并不是一个任意的对象, 它是一个由`angular/forms`模块中的一些特定的类, 如`FormControl`,`FormGroup`,`FormArray`等组成的. 在模板式表单中是能能直接访问到这些类的.
- 响应式表单并不会替你生成`HTML`,模板仍然需要自己来编写

## 与服务端通讯
Observable与RxJS
## i18n
## 前端自动化测试
## 高阶内容
WebWorker、ServiceWorker、SEO与Universal、ionic、PWA
