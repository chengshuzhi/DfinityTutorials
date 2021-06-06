# 注册构建并部署应用

在开发环境中连接到本地ICP网络后，就可以在本地注册构建部署应用了。

部署应用步骤：

1. 检查是否在项目根目录
2. 注册构建并部署应用命令

   ```text
   dfx deploycopy
   ```

   `dfx deploy` 命令会输出执行的操作信息

   请注意 `dfx deploy` 命令显示的标识符仅在本地网络环境下有效

   要在外部 Internet Computer 网络上部署, 您必须使用 `--network` 命令行选项和特定网络名称或地址 来注册标识符. 例如, 运行下列命令，以使用别名 `ic` 在 Internet Computer 上部署：

   ```text
   dfx deploy --network=ic
   ```

3. 复制 `contacts_assets` canister 标识符到剪贴板

   如果你没有记录标识符，可以运行下面的命令获取

   ```text
   dfx canister id contacts_assets
   ```



