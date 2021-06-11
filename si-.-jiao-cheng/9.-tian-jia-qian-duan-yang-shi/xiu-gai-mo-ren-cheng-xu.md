# 修改默认程序



本章节中，你将会修改主程序，以便你可以保存和查询联系信息。

修改源码步骤如下。

1. 打开src/contacts/main.mo文件并删除已有内容
2. 复制粘贴下面的代码  


   ```text
   import List "mo:base/List";
   import AssocList "mo:base/AssocList";

   actor Contact {

     var contacts : ContactsMap = List.nil();

     type Name = Text;
     type Phone = Nat;

     type Entry = {
       name : Name;
       address1 : Text;
       address2 : Text;
       email : Text;
       phone : Phone;
     };

     type ContactsMap = AssocList.AssocList<Name, Entry>;

     func nameEq(lhs : Name, rhs : Name) : Bool {
       return lhs == rhs;
     };

     public func insert(name : Name, address1 : Text, address2 : Text, email : Text, phone : Phone) : async () {
        let newEntry : Entry = {
          name;
          address1;
          address2;
          email;
          phone;
        };

        let (newContacts, _) = AssocList.replace(
          contacts,
          name,
          func(n: Name, m: Name) : Bool { n == m },
          ?newEntry
        );
        contacts := newContacts;
     };

     public query func lookup(name : Name) : async ?Entry {
       return AssocList.find(contacts, name, nameEq);
     };
   };
   ```

3. 保存修改并关闭main.mo文件继续。

