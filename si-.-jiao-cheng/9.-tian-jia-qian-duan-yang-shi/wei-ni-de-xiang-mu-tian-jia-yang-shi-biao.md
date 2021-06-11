# 为你的项目添加样式表

你现在可以创建一个新的CSS文件并添加到你的项目

添加步骤：

1. 切换到 `src/contacts_assets/assets` 目录

   ```text
   cd src/contacts_assets/assets/
   ```

2. 将 `main.css` 文件重命名为 `mycontacts.css`.

   ```text
   mv main.css mycontacts.csscopy
   ```

3. 在编辑器中打开 `mycontacts.css` 文件并删除内容
4. 定义一些样式属性

   例如，拷贝贴贴下面的代码：

   ```text
   html {
       background-color: bisque;
   }

   body {
       font-family: Arial, Helvetica, sans-serif;
       display: block;
       margin: 10px;
   }

   h1 {
       color: darkblue;
       font-size: 32px;
   }

   div.new-entry {
       margin: 30px 20px 30px 20px;
   }

   .new-entry > div {
       margin-bottom: 15px;
   }

   table {
       margin-top: 12px;
       border-top: 1px solid darkblue;
       border-bottom: 1px solid darkblue;
   }

   #form {
       margin: 30px 0 30px 20px;
   }

   button {
       line-height: 20px;
   }

   #lookupName {
       margin-right: 12px;
   }
   ```

5. 保存并关闭 `mycontacts.css` 文件
6. 切换到 `src/contacts_assets/src` 目录

   ```text
   cd ../srccopy
   ```

7. 在编辑器中打开 `index.js` 文件并删除内容
8. 拷贝贴贴下面的代码到 `index.js` 文件

   ```text
   import { Actor, HttpAgent } from '@dfinity/agent';
   import { idlFactory as contacts_idl, canisterId as contacts_id } from 'dfx-generated/contacts';

   import * as React from 'react';
   import { render } from 'react-dom';
   import '../assets/mycontacts.css'; // Import custom styles

   const agent = new HttpAgent();
   const contacts = Actor.createActor(contacts_idl, { agent, canisterId: contacts_id });

   class Contact extends React.Component {
     constructor(props) {
       super(props);
       this.state = {
       };
     }

     async doInsert() {
       let name = document.getElementById("newEntryName").value;
       let add1 = document.getElementById("newEntryAddress1").value;
       let add2 = document.getElementById("newEntryAddress2").value;
       let email = document.getElementById("newEntryEmail").value;
       let phone = document.getElementById("newEntryPhone").value;

       contacts.insert(name, add1, add2, email, parseInt(phone, 10));
     }

     async lookup() {
       let name = document.getElementById("lookupName").value;
       contacts.lookup(name).then(opt_entry => {
         let entry;

         if (opt_entry.length == 0) {
           entry = { name: "", description: "", phone: ""};
         } else {
           entry = opt_entry[0]
         }

         document.getElementById("newEntryName").value = entry.name;
         document.getElementById("newEntryAddress1").value = entry.address1;
         document.getElementById("newEntryAddress2").value = entry.address2;
         document.getElementById("newEntryEmail").value = entry.email;
         document.getElementById("newEntryPhone").value = entry.phone.toString();
       });
     }

     render() {
       return (
         <div class="new-entry">
           <h1>My Contacts</h1>
           <div>
             Add or update contact information:
   	      <form id="contact">
             <table>
               <tr><td>Name:</td><td><input id="newEntryName"></input></td></tr>
               <tr><td>Address 1 (street):</td><td><input id="newEntryAddress1"></input></td></tr>
               <tr><td>Address 2 (city and state):</td><td><input id="newEntryAddress2"></input></td></tr>
               <tr><td>Email:</td><td><input id="newEntryEmail"></input></td></tr>
               <tr><td>Phone:</td><td><input id="newEntryPhone" type="number"></input></td></tr>
             </table>
           </form>
           </div>
           <div>
             <button onClick={() => this.doInsert()}>Add Contact</button>
           </div>
           <div>
             Lookup name: <input id="lookupName" style={{ "line-height": "20px" }}></input>
             <button onClick={() => this.lookup()}>Lookup</button>
           </div>
         </div>
       );
     }
   }

   document.title = "DFINITY CONTACT EXAMPLE";

   render(<Contact />, document.getElementById('contacts'));
   ```

9. 将 `index.js` 文件重命名为 `index.jsx` 

   ```text
   mv index.js index.jsx
   ```

10. 在编辑器中打开 `src/contacts_assets/src/index.html` 文件， 将 `main.css` 替换为 `mycontacts.css` 并且更新 `body` 包含 `<div id="contacts"></div>`.

    例如：

    ```text
    <!doctype html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width">
        <title>contacts</title>
        <base href="/">

        <link type="text/css" rel="stylesheet" href="mycontacts.css" />
    </head>
    <body>
        <div id="contacts"></div>
    </body>
    </html>
    ```

11. 退回到项目根目录

    例如：

    ```text
    cd ../../..
    ```



