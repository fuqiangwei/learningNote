# Angular4

## 搭建开发环境

Angular-CLI、webpack

### Angular-CLI 常用命令

```bash
ng new projectname -si --style=scss
```

## 组件与指令

### 组件必备三要素

* 装饰器:`@component`-- 装饰器里面的属性就是元数据
* 模板:`Template`
* 控制器:`Control` 一个标准的 typescript 类,

### 模块/MODULE

```javascript
import { BrowserModule } from '@angular/platform-browser';

@NgModule({
  declarations: [AppComponent], // 只能声名组件,指令,管道
  imports: [BrowserModule], // 启动该模块依赖的其它模块
  providers: [], // 只能声名服务
  bootstrap: [] // 声名模块的主组件
})
export class AppModule {}
```

### 引入第三方模块

1. 安装第三方模块 `npm install jquery --save`
2. 在`.angular-cli.json`引入 styles 属性中引入 css, scripts 属性中引入 js
3. 安装类型类型描述文件 `npm install @types@jquery --save-dev`

### 数据绑定

* 事件绑定:

```Html
<input (input)="onInputEvent($event)">
```

### HTML 属性绑定

#### 基本 HTML 属性绑定

```html
<td [attr.colspan]="tablecolspan">something</td>
<button (click)="saved = true"></button>

<!-- 属性绑定和插值表达式是一个东西 -->
<img [src]="imgUrl">
<img src="{{imgUrl}}">  
```

#### html 属性和 DOM 属性

1. 少量 html 属性和 DOM 属性之间有 1:1 的关系, 比如 ID
2. 有些 html 属性没有对应的 DOM 属性,如 colspan
3. 有些 DOM 属性没能对应的 HMTL 属性, 比如 textContent
4. 就算名字相同, HTML 属性和 DOM 属性也不是同一样东西
5. HTML 属性的值指定了初始值,DOM 属性的值表示当前值. DOM 属性的值可以改变,HTML 属性的值不能改变
6. 模板绑定是通过 DOM 属性和事件绑定来工作的, 而不是 HMTL 属性

#### css 类绑定

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

* Routes: 路由配置, 保存着哪个 URL 对应展示哪个组件,以及在哪个`RouterOutlet`中展示组件
* RouterOutlet: 在 Html 中标记路由内容呈现位置的占位符指令
* Router: 负责在运行时执行路由的对象, 可以通过调用其`navigate()`和`navigateByUrl()`方法来导航到一个指定的路由
* RouterLink: 在 HTML 中声明路由导航用的指令,参数是数组
* ActivateRoute: 当前激活的路由对角,保存着当前路由的信息,如路由地址,

### 路由传递数据

* 查询参数: `/product?id=1&name=2` => `ActivatedRoute.queryParams[id]`
* 路由路径: `{path/product/:id}` => `ActivateddRoute.queryParams[id]`
* 路由配置: `{path:/product, component:ProductComponent, data:[{isProd:true}]}` => `ActivatedRoute.data[0][isProd]`
  ### 路由重定向和子路由和辅助路由

`{path:'',component:XxxComponent,redirectTo: 'xxx',pathMatch: 'full'}`

### 辅助路由

```html
<router-outlet></router-outlet>
<router-outlet name="aux"></router-outlet>



<a [routerLink] = "['/home', {outlets: {primary:'home', aux: 'xxx'}}]">xxx</a>
<a [routerLink] = "['/product', {outlets: {aux: 'yyy'}}]">yyy</a>
```

```javascript
const route: Routes = [
  {
    path: 'xxx',
    component: XxxComponent,
    outlet: 'aux',
    canActivate: [路由守卫],
    canDeactivate: [路由守卫],
    Resolve: { data: dataResolve }
  },
  { path: 'yyy', component: YyyComponent, outlet: 'aux' }
];
```

#### 路由守卫

> 只有用户已经登录并拥有某些权限时才能进入某些路由.
> 一个由表单组成的向导,例如注册流程,用户只有在当前路由的组件中填写了满足要求的信息才可以导航到下一个路由.
> 当用户未执行保存操作而试图离开当前导航时提醒用户.

* CanActivate: 处理导航到某路由的情况
* CanDeactivate: 处理从当前路由离开的情况
* Resolve: 在路由激活之前获取路由数据

基本用法、多层嵌套、动态加载模块、

## 依赖注入

> 依赖注入: DI `Dependency Injection`
> 控制反转: IOC `Inversion Of Control`
> 注入器: `constructor(private productService: ProductService){}`
> 提供器: `providers: [ProductService]` 或`[{providers: ProductService, useClass: ProductService}]`

## 表单与数据校验

### 模板式表单

> 表单的数据模型是通过组件模板中的相关指令来定义的,因此使用这种方式定义表单的数据模型时,我们会受限于 HTML 语法,所以模板驱动的方式只适合用于一些简单的场景

### 响应式表单

> 通过编写`TypeScript`代码而不是 Html 代码来创建一个底层的数据模型,在这个模型定义好后,使用一些特定的指令,将模板上的 HTML 元素与底层的数据模型连接在一起.

### 区别

* 不管是哪种表单,都有一个对应的数据模型来存储表单的数据. 在模板式表单中,数据模型是由`angular`基于组件模板中的指令隐式创建的. 而在响应表单中,是通过编码明确的创建数据模型然后将模板上的`html`与底层的数据模型转接在一起
* 数据模型并不是一个任意的对象, 它是一个由`angular/forms`模块中的一些特定的类, 如`FormControl`,`FormGroup`,`FormArray`等组成的. 在模板式表单中是能能直接访问到这些类的.
* 响应式表单并不会替你生成`HTML`,模板仍然需要自己来编写

## 与服务端通讯

Observable 与 RxJS

## i18n

## 前端自动化测试

## 高阶内容

WebWorker、ServiceWorker、SEO 与 Universal、ionic、PWA

## 常用工具

1. [组件树生成器][53f65de5]
2. «»

[53f65de5]: https://github.com/compodoc/ngd/ '组件树生成器'
