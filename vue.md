- 模版语法
    - 文本,js表达式 {{xxx}}
    - 指令 
        是带有 v- 前缀的特殊特性。指令特性的值预期是单个 JavaScript 表达式
        - v-bind, :  指定参数的值
        - v-on, @  绑定事件
    - 动态参数， [参数名]
- 计算属性和侦听器
    - 方法：不会缓存，
    - 计算属性：响应式依赖进行缓存
    - 侦听属性：数据变化时执行异步或开销较大的操作