# 修改默认配置

在探索默认项目章节，已经介绍了创建新项目会添加一个`dfx.json`配置文件到项目目录。在本章节中，需要修改一些默认配置。

dfx.json配置修改步骤

1. 在编辑器中，打开 `dfx.json` 配置文件，将默认的main设置从`main.mo`更改为`increment_counter.mo`。

   ```text
   "main": "src/my_counter/increment_counter.mo",
   ```

   对于本教程，将源文件的名称从main.mo更改为increment\_counter.mo仅说明了dfx.json配置文件中的设置如何确定要编译的源文件。

   在更复杂的应用中，dfx.json配置文件中可能会有多个你要包含依赖的源文件需要管理。这种情况下-dfx.json文件中定义了多个canister和程序-有多个被命名为main.mo的文件可能会导致混乱。

   文件的其他部分无需修改。

2. 保存并关闭dfx.json继续。
3. 修改源代码目录中主程序的文件名来匹配dfx.json中的配置。

   ```text
   mv src/my_counter/main.mo src/my_counter/increment_counter.mo
   ```

