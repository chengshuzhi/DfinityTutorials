# 本地项目部署



部署程序到 ICP 网络需要 WebAssembly 模块和 canister\_manifest.json 文件

部署步骤：

1. 进入项目目录
2. 运行命令  
   **`dfx canister install --all`**

   命令输出



   ```text
   Installing code for canister explore_hello, with canister_id rrkah-fqaaa-aaaaa-aaaaq-cai
   Installing code for canister explore_hello_assets, with canister_id ryjl3-tyaaa-aaaaa-aaaba-cai
   Authorizing our identity (pubs-id) to the asset canister...
   Uploading assets to asset canister...
     /index.html 1/1 (480 bytes)
     /index.js 1/1 (296836 bytes)
     /main.css 1/1 (484 bytes)
     /sample-asset.txt 1/1 (24 bytes)
     /logo.png 1/1 (25397 bytes)
     /index.js.map 1/1 (964679 bytes)
     /index.js.LICENSE.txt 1/1 (499 bytes)
   ```

3. 运行下面的命令调用程序相关函数  


   **`dfx canister call explore_hello greet everyone`**

   命令参数

   * explore\_hello 调用的 Canister 名称或应用服务
   * greet 调用的方法
   * everyone 传给 greet 函数的参数

4. 验证输出 **`("Hello, everyone!")`**

