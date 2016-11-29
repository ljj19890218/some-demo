# vue-router 类似app的页面你切换

> 额，为什么要这样切换呢？

## 切换方式

* 单页之间的切换 `slide-fade`
* 父级切换到子级 `slide-right`
* 子集返回父级   `slide-left`

## 切换条件判断

在根路由上绑定了一个 `transition`，name值是动态数据 `$router.app.pageTransition`，在路有前切换，还是路由后切换呢？

初步 `router.afterEach` 中，做了一个延迟，判断当前页面是返回还是前进，效果一般，页面切换就只有前进、后退，没有了单页之间的切换。需要在路由信息中做一个返回的标识。

然后再 `router.beforeEach` 中通过路由的长度来判断是单页还是子级，哈希和History模式不同，长度也不同，兼容不好，没有返回的切换，路由兼容也不好，路由中无需做标识。