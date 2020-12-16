# vue-right-click-menu · [![npm](https://img.shields.io/badge/npm-v1.0.0-2081C1)](https://www.npmjs.com/package/vue-right-click-menu) [![yarn](https://img.shields.io/badge/yarn-v1.0.0-F37E42)](https://yarnpkg.com/package/vue-right-click-menu) [![github](https://img.shields.io/badge/GitHub-depositary-9A9A9A)](https://github.com/likaia/vue-right-click-menu) [![](https://img.shields.io/github/issues/likaia/vue-right-click-menu)](https://github.com/likaia/vue-right-click-menu/issues) [![](	https://img.shields.io/github/forks/likaia/vue-right-click-menu)](https://github.com/likaia/vue-right-click-menu/network/members) [![](	https://img.shields.io/github/stars/likaia/vue-right-click-menu)](https://github.com/likaia/vue-right-click-menu/stargazers)
支持vue的浏览器右键菜单插件，效果图如下：

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0261ae22733144a6ac67ec16008355d2~tplv-k3u1fbpfcp-watermark.image)

## 插件安装
```bash
yarn add vue-right-click-menu

# or

npm install vue-right-click-menu --save
```
## 插件使用

* 在项目的入口文件`main.ts/main.js`中加入下述代码
```javascript
import rightMenu from "vue-right-click-menu";

Vue.use(rightMenu);
```
* 在你的业务代码中，在元素上绑定`v-right-click`，然后传对应的参数即可.
```vue
<template>
  <li
    class="row-panel"
    v-right-click="rightMenuObj"
  >
</template>
<script>
export default {
  computed: {
    rightMenuObj() {
      // 右键菜单对象，菜单内容和处理事件
      const obj = {
        this: this,
        text: [
          "查看资料",
          { content: "复制用户id", status: true },
          "移除该会话",
          "在联系人中查看",
          "在单聊窗口中打开",
          "会话置顶"
        ],
        handler: {
          checkingData() {
            console.log(obj.this.$store.state.token);
            console.log("查看资料点击事件");
          },
          copyId() {
            console.log("复制用户id点击事件");
          },
          removeItem() {
            console.log("移除会话点击事件");
          },
          showContact() {
            console.log("在联系人中查看");
          },
          showSingleChat() {
            console.log("在单聊窗口中打开");
          },
          topConversation() {
            console.log("会话置顶");
          }
        }
      };
      return obj;
    }
  }
}
</script>
```
### 参数说明
如示例代码所示，在元素上绑定指令，在computed中定义一个对象，传菜单内容和与之对应的事件处理函数就可以了。

接下来就跟大家讲下对象里每个属性的意义：
* this 即当前vue实例，便于在处理函数中能访问到当前vue实例中的内容
* text 类型为数组，即右键菜单要显示的内容
  * 数组内的内容分为字符串或对象，如果为字符串这一项默认是可以点击的
  * 如果你想让某个选项无法点击，则传一个对象
    * content 要显示的文字内容，字符串类型
    * status 是否禁用，boolean类型
* handler 事件处理函数，函数的顺序要与text数组内的文本顺序相对应

## 写在最后
至此，插件的所有使用方法就介绍完了。

该插件仅支持Vue2.x的项目，Vue3.x项目请移步: [vue-right-click-menu](https://github.com/likaia/vue-right-click-menu)

想进一步了解插件源码的请移步插件的GitHub仓库：[vue-right-click-menu](https://github.com/likaia/vue-right-click-menu)
