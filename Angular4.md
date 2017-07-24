# Angular4




## 搭建开发环境
  Angular-CLI、webpack
## 组件与指令
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


## 表单与数据校验
## 与服务端通讯
Observable与RxJS
## i18n
## 前端自动化测试
## 高阶内容
WebWorker、ServiceWorker、SEO与Universal、ionic、PWA
