# 在浏览器中测试函数



Canister接口描述语言-通常指Candid或更通用的说法IDL-提供一个常用的语言来描述Canister签名服务。这个语言提供了一个统一的方法以在多种语言和工具中与Canister交互，例如dfx命令行，JavaScript和Motoko。

基于actor的签名类型，Candid也提供一个web接口允许你调用Canister函数来测试和排除bug。

在本地使用dfx deploy 或 dfx canister install部署完项目后，就可以在浏览器中访问Candid Web接口。访问Candid Web接口可以查看并测试Canister函数，而无需编写前端代码。

使用Candid Web接口测试Canister函数步骤如下

1. 复制关联应用的Candid UI的Canister 识别码
2. 打开浏览器，导航到dfx.json配置文件中定义的地址和端口本地网络会默认绑定到127.0.0.1:8000
3. 添加canisterId参数来访问Candid Web接口  


   例如，完整的URL应该和下面的示例类似

   ```text
   http://127.0.0.1:8000/?canisterId=<YOUR-UI-CANISTER-IDENTIFIER>
   ```

4. 将&lt;应用程序&gt;\_assets Canister标识符粘贴到“Provide a canister ID”字段中，然后单击“Go”。
5. 查看程序中定义的函数调用和类型
6. 在函数后面输入合适的类型值或点击Random生成一个值，然后点击Call或Query查看结果。 注意根据数据类型，Candid接口回现实额外的配置来测试函数。例如，如果函数需要一个数组，则需要额外输入数组的元素数量

![](../../.gitbook/assets/image%20%281%29.png)

