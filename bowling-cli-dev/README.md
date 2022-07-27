# 初始化
- lerna init
- add .gitignore
# 创建package
- lerna create xxx 创建package
- lerna add  xxx 对全部的package安装依赖xxx
    - lerna add xxx packages/core 对单独的包进行安装
- learna link 形成软接依赖
- lerna clean 删除node_modules
# 发布
- lerna version 增加version
- lerna diff 
- lerna changed 
- lerna publish 发布