# 验证Cycles钱包

将 ICP 代币转换为Cycles后，您可以验证Cycles钱包Canister并检查您当前的Cycles余额。

1. 运行以下命令验证您部署的Cycles钱包的Canister标识符：﻿ ﻿`dfx identity --network ic get-wallet`﻿ ﻿输出 类似如下：﻿ ﻿`gastn-uqaaa-aaaae-aaafq-cai`
2. 运行类似于以下的命令，检查您的Cycles钱包Canister是否已正确配置并有余额：﻿ ﻿`dfx wallet --network ic balance`﻿ ﻿该命令返回余额，例如：﻿ ﻿`15430122328028812 cycles.`﻿ ﻿您还可以使用类似于以下内容的 URL 在 Web 浏览器中访问您的默认Cycles钱包：﻿ ﻿`https://<WALLET-CANISTER-ID>.raw.ic0.app`﻿ ﻿首次访问该应用程序时，您会看到一条通知，提示您正在使用匿名设备，并提示您验证您的身份、授权访问钱包并注册您的设备。
3. 单击“Authenticate”以继续使用 Internet 身份服务。
4. 输入用户号﻿ ﻿有关 Internet 身份服务以及如何注册多个身份验证设备和方法的详细信息，请参阅如何使用 Internet 身份服务。
5. 使用您的用户号和您注册的身份验证方法（例如，安全密钥或指纹）进行身份验证。
6. 单击Proceed以访问默认周期钱包应用程序。
7. 通过复制“注册设备”页面中显示的命令并在终端中运行它来注册您用于此会话的设备。﻿ ﻿例如，使用类似于以下的命令调用Cycles钱包Canister的授权方法：﻿ ﻿`dfx canister --no-wallet --network ic call "gastn-uqaaa-aaaae-aaafq-cai" authorize '(principal "ejta3-neil3-qek6c-i7rdw-sxreh-lypfe-v6hjg-6so7x-5ugze-3iohr-2qe")'`﻿ ﻿确保您复制的命令具有 --no-wallet 选项和正确的网络 \(ic\) 别名。 您应该将Canister标识符（在本例中为 gastn-uqaaa-aaaae-aaafq-cai）指定为与您的身份相关联的Cycles钱包。 但是，如果这是您在网络上的第一个钱包，您可能无法识别被授权的委托人。 在这种情况下，使用不同的账户是预期的行为。﻿ ﻿当运行授权命令后浏览器刷新时，将显示您的主账户的Cycles钱包。
8. 在浏览器中查看您的Cycles余额和活动。

![](../../.gitbook/assets/image%20%2832%29.png)

