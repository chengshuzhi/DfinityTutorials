# 查看前端

现在可以通过输入资源canister识别码访问默认程序的新的前端。

查看前端步骤

1. 打开浏览器，导航到dfx.json配置文件中定义的地址和端口

   例如，如果你使用的是默认的网络配置，可以导航到127.0.0.1:8000。.

   用下面的语法增加 `canisterId` 参数和 `contacts_assets` canister 标识符到URL：

   ```text
   ?canisterId=<YOUR-CANISTER-IDENTIFIER>
   ```

   完整的URL示例如下：

   ```text
   http://127.0.0.1:8000/?canisterId=cxeji-wacaa-aaaaa-aaaaa-aaaaa-aaaaa-aaaaa-q
   ```

2. 验证你可以看到一个**My Contacts**表单

   例如：

   ![Sample front-end](https://sdk.dfinity.org/docs/developers-guide/_images/mycontacts-form.png)  

3. 通过输入名称，地址和邮箱文本以及电话数字创建一个或多个记录，然后点击 **Add Contact**.
4. 清除表单内容并在查询名称中输入联系名称，然后点击Lookup查看保存的联系信息

   记住你输入的Lookup名称必须完全匹配你输入的名称

![](../../.gitbook/assets/image%20%2824%29.png)



