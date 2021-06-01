# 构建并部署demo项目

部署构建linkup示例应用步骤如下：

1. 运行pwd命令检查你仍然在项目目录
2. 运行下面的命令构建linkedup canister

   ```text
   dfx buildcopy
   ```

3. 运行下面的命令在本地网络部署项目

   ```text
   dfx canister install --allcopy
   ```

   您将会看到类似下面的 `connectd`, `linkedup` 和 `linkedup_assets` 三个canisters 的标识符信息：

   ```text
   Installing code for canister connectd, with canister_id 75hes-oqbaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
   Installing code for canister linkedup, with canister_id cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
   Installing code for canister linkedup_assets, with canister_id 7kncf-oidaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
   ```

4. 复制由dfx canister install命令返回的linkedup\_assets canister识别码
5. 浏览器中打开linkedup\_assets canister

   例如：

   ```text
   http://127.0.0.1:8000/?canisterId=7kncf-oidaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
   ```



