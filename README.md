# move-sui
sui by move. All IN MOVE

## 常用命令
要检查Sui是否已安装
```
which sui
```

将Sui客户端连接到网络
```
sui client
```

要检查当前可用的环境别名
```
sui client envs
```

切换活动网络
```
sui client switch --env <ALIAS>
```

查看当前钱包地址
```
sui client active-address
```

查看当前地址中的币
```
sui client gas
```
## 开发命令
创建新项目
```
sui move new project_name
```

构建项目
```
sui move build
```

单元测试命令
```
sui move test
```

## 发布新币
发布命令
```
sui client publish --gas-budget 5000000
```

查看当前活动对象
```
sui client objects

╭───────────────────────────────────────────────────────────────────────────────────────╮
│ ╭────────────┬──────────────────────────────────────────────────────────────────────╮ │
│ │ objectId   │  <OBJECT-ID>                                                         │ │
│ │ version    │  10                                                                  │ │
│ │ digest     │  <DIGEST-HASH>                                                       │ │
│ │ objectType │  <PACKAGE-ID>::my_module::Forge                                      │ │
│ ╰────────────┴──────────────────────────────────────────────────────────────────────╯ │
│ ╭────────────┬──────────────────────────────────────────────────────────────────────╮ │
│ │ objectId   │  <OBJECT-ID>                                                         │ │
│ │ version    │  10                                                                  │ │
│ │ digest     │  <DIGEST-HASH>                                                       │ │
│ │ objectType │  0x0000..0002::coin::Coin                                            │ │
│ ╰────────────┴──────────────────────────────────────────────────────────────────────╯ │
│ ╭────────────┬──────────────────────────────────────────────────────────────────────╮ │
│ │ objectId   │  <OBJECT-ID>                                                         │ │
│ │ version    │  10                                                                  │ │
│ │ digest     │  <DIGEST-HASH>                                                       │ │
│ │ objectType │  0x0000..0002::package::UpgradeCap                                   │ │
│ ╰────────────┴──────────────────────────────────────────────────────────────────────╯ │
╰───────────────────────────────────────────────────────────────────────────────────────╯
```
objectId 字段是每个对象的唯一标识符。

Coin 对象

Forge 对象

UpgradeCap 对象

交易命令
```
sui client call --package $PACKAGE_ID --module apt --function mint --args $APT_TREASURYCAP 1 $TO_ADDRESS --gas-budget 100000000
```
