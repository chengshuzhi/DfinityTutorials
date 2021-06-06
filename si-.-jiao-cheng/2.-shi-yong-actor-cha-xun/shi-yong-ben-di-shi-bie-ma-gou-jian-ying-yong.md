# 使用本地识别码构建应用

如果你只需要对这个简单程序做本地测试，那么，就不需要再ICP网络为这个程序的编译输出保留一个单独的Canister识别码。

在本节中，可以无需连接ICP网络来编译程序。dfx build命令可以创建一个本地硬编码的canister识别码。

测试程序时，在无需本地启动或连接ICP网络的情况下，你都可以使用这个本地识别码。

构建程序执行文件步骤：

1. 进入项目目录
2. 使用本地识别码构建程序命令

   ```text
   dfx build --check
   ```

   --check 选项使您能够在本地构建项目以验证它是否编译并检查生成的文件。 因为dfx build --check命令仅生成一个临时标识符，所以您应该看到类似于以下内容的输出：

   ```text
   Building canisters to check they build ok. Canister IDs might be hard coded.
   Building canisters...
   ```

   如果程序成功编译，可以

   在`.dfx/local/canisters` 和 `.dfx/local/canisters/actor_hello/` 查看输出的文件。  


   比如，使用tree命令查看创建的文件

   ```text
   tree .dfx/local/canisters
   ```

   命令输出

   ```text
   .dfx/local/canisters
   ├── actor_hello
   │   ├── actor_hello.d.ts
   │   ├── actor_hello.did
   │   ├── actor_hello.did.js
   │   ├── actor_hello.js
   │   └── actor_hello.wasm
   └── idl

   2 directories, 5 files
   ```



