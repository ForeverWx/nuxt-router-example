# nuxt-router-example
ssr-nuxt-lrouter-example
<br>

# Vue ssr Nuxt 框架 嵌套 动态 路由 详解

<br>

## 动态路由

**Nuxt 默认 自动生成 pages 下文件 作为路由结构**
<br/>

**目录结构**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510162533416.png)
### 效果
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510165520626.gif)
```
<template>
  <nuxt-link to="/example/home">首页</nuxt-link>
  <nuxt-link to="/example/login">登录</nuxt-link>
</template>
```

<br>

## 嵌套路由

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510161000233.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0ZvcmV2ZXJCYW5h,size_16,color_FFFFFF,t_70)
<br>

**项目结构**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510171019215.png)
<hr>

**解析：home.vue 组件 为父组件 默认入口  子组件存放在 home 文件下  
index.vue 为父组件必选组件 （命名为_index.vue）为可选组件**

<br>

#### **可选组件 必选组件 深入理解:**

**必选组件：访问 /example/home/默认展示index.vue 内容**

**可选组件：访问 /example/home/默认展示 home.vue组件内容 （实现子组件路由）**

<br/>


### 实例
**设置 非必选组件 通过 home.vue 实现组件路由**
<br/>

**目录结构**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510173630278.png)

**home.vue**
```
<template>
  <div>
    <div>
      <nuxt-link to="/example/home/index">index</nuxt-link>
      <nuxt-link to="/example/home/blog">blog</nuxt-link>
      <nuxt-link to="/example/home/college">colleage</nuxt-link>
    </div>
    <div>
      <nuxt-child/>
    </div>
  </div>
</template>

<script>
  export default {
    name: "home.vue"
  }
</script>

<style scoped>

</style>

```
<hr>

**解析： 通过 此种目录结构 方式定义路由 可以直接操控子组件显示 布局，样式等 更直观体现组件效果**

**nuxt-child  路由展示子组件** 

**注意：定义 必要组件(index.vue) 将无法体现 home.vue 父子路由效果**
<br/>

### 效果
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510174804592.gif)

<br/>


## 动态嵌套路由 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510175854513.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0ZvcmV2ZXJCYW5h,size_16,color_FFFFFF,t_70)
<hr>

**解析：Router 1=>控制 View1 
View1 =>包含 Route 2 View2
Router 2 =>控制 View 2**

**目录结构**

![在这<hr里插入图片描述](https://img-blog.csdnimg.cn/20200510180706888.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0ZvcmV2ZXJCYW5h,size_16,color_FFFFFF,t_70)
<hr>

**解析：目录结构和方式 嵌套路由 相似**
<br/>


### 实例

<br>

**home.vue**
```
<template>
  <div>
    <h1>首页</h1>
    <div>
      <nuxt-link to="/example/home/index">index</nuxt-link>
      <nuxt-link to="/example/home/blog">blog</nuxt-link>
      <nuxt-link to="/example/home/college">colleage</nuxt-link>
      <nuxt-link to="/example/home/home_menu">menu</nuxt-link>
    </div>
    <div>
      <nuxt-child/>
    </div>
  </div>
</template>

<script>
  export default {
    name: "home.vue"
  }
</script>

<style scoped>

</style>

```
**解析： 增加 menu 组件 home_menu 路由
home_menu  为 home 子组件 => menu 入口
menu入口 =>路由 menu 子组件**

**menu.vue**
```
<template>
  <div>
    <h1>菜单</h1>
    <el-row>
      <el-col :span="12">
        <ul>
          <li>
            <nuxt-link to="/example/home/home_menu/index">index</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/example/home/home_menu/blog">blog</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/example/home/home_menu/college">colleage</nuxt-link>
          </li>
        </ul>
      </el-col>
      <el-col :span="12">
        <nuxt-child/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: "home_vue"
  }
</script>

<style scoped>

</style>

```
<br>

### 效果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200510181833783.gif)
<br>

## 总结：
<hr>

**新手入门 比较容易出错的几个地方：**

**嵌套路由显示内容和结构不否： 是否命名为必选组件**

**嵌套路由直接展示子组件页面：子组件是否定义规范，是否在父组件目录下**

**路由访问提示地址不存在：:to=‘{name:''}’ 配置name 属性 还是 path 属性**

<hr>


<br>


## 使用方式


将 pages 文件 拷贝到 nuxt 项目 主目录 替换掉原有 pages


