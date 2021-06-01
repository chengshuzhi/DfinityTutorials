# 查看新前端

现在可以通过输入资源canister识别码访问默认程序的新的前端。

查看自定义前端步骤：

1. 打开浏览器，导航到dfx.json配置文件中定义的地址和端口

   例如，如果你使用的是默认的网络配置，可以导航到127.0.0.1:8000。.

   T要指定想查看的canister，用下面的格式添加canisterId参数和custom\_greeting\_assets canister识别码到URL：

   ```text
   ?canisterId=<YOUR-ASSET-CANISTER-IDENTIFIER>
   ```

   完整的URL示例如下：

   ```text
   http://127.0.0.1:8000/?canisterId=cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
   ```

2. 验证你可以触发一个greet

   例如：

   ![Sample front-end](https://sdk.dfinity.org/docs/developers-guide/_images/react-greeting.png)  

3. 替换输入框中你想要展示的Name，然后点击Get Greeting查看结果

   例如：

   ![Greeting result](https://sdk.dfinity.org/docs/developers-guide/_images/greeting-response.png)  

![](../../.gitbook/assets/greeting-response.png)

![](../../.gitbook/assets/image%20%2825%29.png)

###  <a id="_revise_the_front_end_and_test_your_changes"></a>

