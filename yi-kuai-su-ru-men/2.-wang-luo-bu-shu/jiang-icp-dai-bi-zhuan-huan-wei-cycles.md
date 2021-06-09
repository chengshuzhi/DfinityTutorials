# 将 ICP 代币转换为Cycles

现在您已经确认了您的账户信息和当前的 ICP 代币余额，您可以将其中一些 ICP 代币转换为Cycles并将它们移动到Cycles钱包中。

转移 ICP 代币以创建Cycles钱包：

1. 运行类似于以下的命令，从您的帐户转移 ICP 代币来创建一个带有Cycles的新Canister：﻿ ﻿`dfx ledger --network ic create-canister <controller-principal-identifier> --amount <icp-tokens>`﻿ ﻿此命令将您为 --amount 参数指定的 ICP 令牌数量转换为Cycles，并将Cycles与由您指定的控制账户标识符相关联。﻿ ﻿例如，以下命令将 .25 个 ICP 令牌转换为Cycles，并将默认身份的账户标识符指定为新Canister的控制器：﻿ ﻿`dfx ledger --network ic create-canister tsqwz-udeik-5migd-ehrev-pvoqv-szx2g-akh5s-fkyqc-zy6q7-snav6-uqe --amount .25`﻿ ﻿如果交易成功，Ledger会记录该事件，您应该会看到类似于以下内容的输出：﻿ ﻿`Transfer sent at BlockHeight: 20﻿ ﻿Canister created with id: "gastn-uqaaa-aaaae-aaafq-cai"`
2. 运行类似于以下的命令，在新创建的Canister中安装Cycles钱包代码：﻿ ﻿`dfx identity --network ic deploy-wallet <canister-identifer>`﻿ ﻿例如：﻿ ﻿`dfx identity --network ic deploy-wallet gastn-uqaaa-aaaae-aaafq-cai`﻿ ﻿命令输出如下：﻿ ﻿`Creating a wallet canister on the ic network.﻿ ﻿The wallet canister on the "ic" network for user "default" is "gastn-uqaaa-aaaae-aaafq-cai"`

