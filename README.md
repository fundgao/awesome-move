# [move-sui](https://docs.sui.io/guides/developer/getting-started/sui-install)
sui by move. All IN MOVE

## [Sui Move导论](https://intro-zh.sui-book.com)

## 常用命令
要检查Sui是否已安装
```
which sui
```

Sui客户端 [初始化教程](Install/01.cli_start.md)
```
sui client
```

要检查当前可用的环境别名
```
sui client envs
```

新增testnet和mainnet节点
```
sui client new-env --alias testnet --rpc https://fullnode.testnet.sui.io:443
sui client new-env --alias mainnet --rpc https://fullnode.mainnet.sui.io:443
```

切换活动网络
```
sui client switch --env <ALIAS>
```

查看当前钱包地址
```
sui client addresses

sui client active-address
```

创建新钱包
```
sui client new-address <KEY_SCHEME> <ALIAS>

KEY_SCHEME 加密类型
0 for ed25519, 1 for secp256k1, 2: for secp256r1
```

切换钱包
```
#通过地址切换
sui client switch --address 0x69ed35387475725ac0a6932ffcc9bf8a628c161abf815c82432222b98e0eaa01
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

领取开发币、测试币
```
#testnet
curl --location --request POST 'https://faucet.testnet.sui.io/v1/gas' --header 'Content-Type: application/json' --data-raw '{ "FixedAmountRequest": { "recipient": "<ADDRESS>" } }'

#devnet
curl --location --request POST 'https://faucet.devnet.sui.io/gas' --header 'Content-Type: application/json' --data-raw '{ "FixedAmountRequest": { "recipient": "<ADDRESS>" } }'
```

发送代币
```
sui client transfer --to <接收方地址> --object-id <gasCoinId> --gas-budget 10000000

注意：--gas-budget为本次交易所需的手续费，尽量写大一些，交互中会自动计算，并不是填写的数值。
```

合并代币
多个不同余额的代币进行合并：
```
sui client merge-coin --primary-coin <保留代币地址> --coin-to-merge <被合并代币地址> --gas-budget 10000000
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
更新 sui 环境
```
cargo install --locked --git https://github.com/MystenLabs/sui.git --branch testnet sui
```

更新 Rust 环境
```
rustup update stable
```
