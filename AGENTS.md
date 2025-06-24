## 质量检查

前端代码遵循以下检查步骤：

1. 运行 `pnpm install` 安装依赖。
2. 执行 `pnpm run lint` 进行代码风格检查，确保没有错误和警告。
3. 执行 `pnpm run build` 确保前端代码能够正确构建。

> 前端补丁必须通过以上 3 步。

## README更新

质量检查完成后，根据现在重构的程度完善项目根目录的README.md文件，需要加上本次说明的时间(北京时间)节点 yyyy-MM-dd HH:mm:ss 。README.md文件里记录程序的结构情况和基本的功能。

## 前端开发说明

1. **开发环境使用 Mock 数据和与服务端进行交互，涉及到的技术有：**

- [Nitro](https://nitro.unjs.io/) 轻量级后端服务器，可部署在任何地方，项目用作于 Mock 服务器。
- [axios](https://axios-http.com/docs/intro) 用于发送 HTTP 请求与服务端进行交互。

2. **所有前端代码尽可能使用vuetify的组件重构，支持多主题切换**
4. **公共组件放在src\components文件夹；页面放在src\pages文件夹**
5. **编程时注意组件化,不要一个页面写非常多的代码**

## 说明

- 本项目是一个小说阅读网站，需要兼容多端阅读体验
- 使用vue+vuetify