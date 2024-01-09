# VMWARE ESXi 安装吃120G空间解决办法

> 在安装ESXi的时候，引导后，按Shift+O键。

runweasel cdromBoot后输入：
autoPartitionOSDataSize=8192

（适用于esxi7.0）

systemMediaSize=min

（对于8.0，min占用约32G）
注意大小写，回车安装便可。

