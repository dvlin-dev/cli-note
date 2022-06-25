# cli-note

# 1.0.1

## 注册命令

通过在 `package.json` 中加入下列代码注册脚手架命令。
```

"bin": {
    "bowling-cli-test": "bin/index.js"
  },
```
此时通过 `npm` 安装该库后，就会自动注册 `bowling-cli-test` 命令，本质是一个软链接。
## #!/usr/bin/env node

通过在文件首行假如 `#!/usr/bin/env node` 让该文件变成可执行文件，他会自动去找node环境。

相当于原本原本通过 `node index.js` 才能执行文件，现在通过 `./index.js` 就可以执行了。
```
node index.js ->>> index.js
```  

## pushlish 时链接本地仓库

如果你在 `npm pushlish` 的时候，当前的目录下有 `bowling-cli-test` ，`npm i bowling-cli-test -g` 的时候，就会创建本地软链，本地修改文件，会即时改变 `bowling-cli-test` 运行结果。
若像连接远程仓库，则需满足当前当面不存在同名目录。

## 脚手架本地 link

链接本地库文件：
```
cd your-lib-dir
npm link
cd your-cli-dir
npm link your-lib
```
> tips：
在link后，需要在`dependencies` 中加入your-lib,否则在上线之后没办法正确的引用

取消链接本地库文件：
```
cd your-lib-dir
npm unlink
cd your-cli-dir
# link 存在
npm unlink your-lib
# link 不存在
rm -rf node_modules
npm install -S your-lib
```

理解 npm link :
`npm link your-lib: ` 将当前项目中node modules 下指定的库文件链接到 node 全局 node modules 的库文件
`npm link:` 将当前项目链接到`node` 全局`node_modules`中作为一个库文件，并解析`bin`配置，创建可执行文件。

`npm unlink`：
`npm unlink:` 将当前项目从`node`全局`node_modules`中移除。
`npm unlink you-lib`： 将当前项目中的库文件依赖移除

