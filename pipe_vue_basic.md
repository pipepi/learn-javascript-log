# vue basic
## application instance 应用或全局实例
```js
const app = Vue.createApp({
    /* options*/
})
```
- 作用：注册全局（应用下的所有组件实例mount()方法返回管道）可用的各类部件
    - component registed by component(key,obj)
    - directive registed by directive(key,obj)
    - plugins registed by use(obj)
- 方法：
    - directive(key,directiveDefination)
        ```js
        app.directive('my-directive',{
            // set of lifecycle hooks
            created(){},beforMount(){},mounted(){},
            beforeUpdate(){},updated(){},beforeUnmount(){},Unmount(){}
        })
        ```
        - lifecycle hooks are passed arguments
            - el 
                - the directive bound to element
            - binding
                - instance
                    - component instance where directive is used
                - value
                    - 传递给指令的属性值
                        ```js
                        v-my-directive="1+1"
                        // the value is 2
                        ```
                - oldValue
                    - 旧值
                    - 只在beforeUpdate and updated 钩子函数中有值
                - arg 
                    - 传递给指令的参数，和value是不同的管道
                        ```js
                        v-my-directive:foo="1+2"
                        // the arg is foo,and value is 3
                        ```
                - modifiers
                    - 修饰器
                        ```js
                        v-my-directive.foo.bar
                        // the modifiers is {foo:true,bar:true}
                        ```
                - dir
                    - 指令注册到应用实例时，传入的指令定义对象参数
                        ```js
                        app.directive('focus',{
                            mounted(el){
                                el.focus()
                            }
                        })
                        // the dir is {mounted(el){el.focus();}}
                        ```
            - vnode
                - el 对应的DOM元素的blueprint蓝图
            - prevNode
                - 旧虚节点
                - 只在beforeUpdate and updated 钩子函数中有值