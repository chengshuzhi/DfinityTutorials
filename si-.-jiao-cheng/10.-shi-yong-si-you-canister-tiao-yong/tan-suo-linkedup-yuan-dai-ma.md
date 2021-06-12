# 探索Linkedup源代码

工作经历和教育背景的用户信息源码文件由下面文件构成

* main.mo文件包含actor和LinkedUp示例程序的关键函数
* types.mo文件定义自定义类型，描述用户身份和信息，在linkedup canister的main程序中被导入使用
* utils.mo文件提供帮助函数



#### 查询和更新操作 <a id="_query_and_update_operations"></a>

在使用 LinkedUp 示例应用程序时，您可能会注意到某些操作（例如查看资料或执行搜索）几乎立即返回结果。 其他操作（例如创建资料或添加连接）需要更长的时间。

这些性能差异说明了在 `linkedup` canister 中使用查询和更新调用之间的差异。

例如, 在 `src/linkedup/main.mo` 文件中,  `create` 和 `update` 函数是改变canister状态的更新调用, 但为查看和搜索资料的函数 `get` 和 `search` 函数是查询调用:

```text
  // Profiles

  public shared(msg) func create(profile: NewProfile): async () {
    directory.createOne(msg.caller, profile);
  };

  public shared(msg) func update(profile: Profile): async () {
    if(Utils.hasAccess(msg.caller, profile)) {
      directory.updateOne(profile.id, profile);
    };
  };

  public query func get(userId: UserId): async Profile {
    Utils.getProfile(directory, userId)
  };

  public query func search(term: Text): async [Profile] {
    directory.findBy(term)
  };
```

#### canisters之间的相互作用 <a id="_interaction_between_the_canisters"></a>

在此示例中,  `linkedup` canister 利用定义在 `connectd` canister中的函数. 这种分离简化了每个canister中的代码，并说明了如何通过从一个或多个canister调用另一个canister中定义的通用函数来扩展项目。

要使一个canister中定义的公共函数在另一个canister中可用：

1. 在调用canister中增加 `import` 语句

   在此示例中, 公共函数定义在 `connectd` canister 并且被 `linkedup` canister调用.

   因此, `src/linkedup/main.mo` 文件包含以下代码:

   ```text
   // Make the Connectd app's public methods available locally
   import Connectd "canister:connectd";
   ```

2. 在导入canister中使用 `canister.function` 语法调用公共方法

   在此示例中, `linkedup` canister 调用`connectd` canister的 `connect` 和 `getConnections` 函数

您可以看到 `linkedup` canister 和 `connectd` canister 在 `main.mo` 源文件中交互的代码.

例如, `src/connectd/main.mo` 定了下面的函数:

```text
actor Connectd {
  flexible var graph: Digraph.Digraph = Digraph.Digraph();

  public func healthcheck(): async Bool { true };

  public func connect(userA: Vertex, userB: Vertex): async () {
    graph.addEdge(userA, userB);
  };

  public func getConnections(user: Vertex): async [Vertex] {
    graph.getAdjacent(user)
  };

};
```

因为 `Import` 语句, `connectd` 函数对于 `linkedup` canister 是可用的， `src/linkedup/main.mo` 包含下列代码:

```text
  // Connections

  public shared(msg) func connect(userId: UserId): async () {
    // Call Connectd's public methods without an API
    await Connectd.connect(msg.caller, userId);
  };

  public func getConnections(userId: UserId): async [Profile] {
    let userIds = await Connectd.getConnections(userId);
    directory.findMany(userIds)
  };

  public shared(msg) func isConnected(userId: UserId): async Bool {
    let userIds = await Connectd.getConnections(msg.caller);
    Utils.includes(userId, userIds)
  };

  // User Auth

  public shared query(msg) func getOwnId(): async UserId { msg.caller }

};
```

