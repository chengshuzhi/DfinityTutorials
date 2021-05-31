# 查看默认的前端

如果开发环境安装了 node.js，那么项目中会包含一个简单的前端示例，示例中的JavaScript模板脚本index.js会在浏览器中对接explore\_hello程序。

前端模板部署步骤

1. 打开命令行，进入项目目录
2. 打开src/explore\_hello\_assets/src/index.js文件，查看代码  


   ```text
   import { Actor, HttpAgent } from '@dfinity/agent';
   import { idlFactory as explore_hello_idl, canisterId as explore_hello_id } from 'dfx-generated/explore_hello';

   const agent = new HttpAgent();
   const explore_hello = Actor.createActor(explore_hello_idl, { agent, canisterId: explore_hello_id });

   document.getElementById("clickMeBtn").addEventListener("click", async () => {
     const name = document.getElementById("name").value.toString();
     const greeting = await explore_hello.greet(name);

     document.getElementById("greeting").innerText = greeting;
   });
   ```

   模板index.js文件使用两个import语句为dfx生成的explorer\_hello canister显式创建代理实例和actor。

   此文件与模板 index.html 文件结合使用，以显示带有图像、输入和greet方法按钮的 HTML 页面。

   示例文件倒入创建的Canister并在一个提示框中调用greet函数。

3. 关闭index.js文件继续
4. 查看自动创建的前端资源文件  
   **`ls -l .dfx/local/canisters/explore_hello_assets/`**

   命令输出示例



   ```text
   drwxr-xr-x  9 pubs  staff     288 Apr  6 14:25 assets
   -r--r--r--  1 pubs  staff    2931 Dec 31  1969 assetstorage.did
   -r--r--r--  1 pubs  staff  265823 Dec 31  1969 assetstorage.wasm
   -rw-r--r--  1 pubs  staff    3651 Apr  6 14:25 explore_hello_assets.d.ts
   -rw-rw-rw-  1 pubs  staff    2931 Dec 31  1969 explore_hello_assets.did
   -rw-r--r--  1 pubs  staff    4236 Apr  6 14:25 explore_hello_assets.did.js
   -rw-r--r--  1 pubs  staff     149 Apr  6 14:25 explore_hello_assets.js
   -rw-rw-rw-  1 pubs  staff  265823 Dec 31  1969 explore_hello_assets.wasm
   ```

   这些文件是使用node模块和index.js文件由 dfx build命令自动生成的

5. 打开浏览器，进入在dfx.json中配置的网址127.0.0.1:8000  
   按下面到格式添加canisterId 参数和explore\_hello\_assets 容器识别码到URL

   **`?canisterId=<YOUR-CANISTER-IDENTIFIER>`**

   完整路径示例

   **`http://127.0.0.1:8000/?canisterId=rrkah-fqaaa-aaaaa-aaaaq-cai`**

6. 查看HTML页面  
7. 点击Click Me来调用greet函数 

![](../../.gitbook/assets/image%20%284%29.png)

![](../../.gitbook/assets/image%20%286%29.png)

