# DS07-R1 readerfix1 启动验收

截至2026-11-02T21:52:43.581532+08:00，新Run `2026-11-02_dsainet_ds07_r1_science1-readerfix1-full-w1` 已上传、派发并获远端接受，当前 `WAIT_FOR_RESOURCES`，处于technical_reuse节点。10张GPU均因不足4096MiB容量未准入。N资格/5epoch TECH尚未开始，科学训练0/72、审计0/72，未见调度失败；不把排队或环境预检当成TECH通过或科学启动。

原环境验收已真实通过：Python路径 `[REDACTED_MACHINE]`，Python3.9.25，torch分发版 `1.13.1+cu116`。62份冻结文件逐项SHA核对通过，真实CONFIG经包内生产消费者读取eps为float 1e-8，并通过实际训练配方验证，0模型前向/0优化器更新/未读取EEG。

合同canonical SHA `d82104284d7dadd6a47831998c32727a97bca76aff0236c224fd56bfad02f243`；source manifest SHA `6971c345f0f03a7d5a7b3cf2b533b7786a484e7a397a184ec71200b77c9d93b9`。本地、注册与服务器身份一致，无最终序列化漂移。实际节点/调度进程均使用原mieeg解释器。

原起点`2026-10-23T13:28:00+00:00`及266小时累计预算保留。此次人工等待从2026-11-02T13:22:18.396823+00:00至明确确认2026-11-02T13:44:23.354+00:00，1324.957177秒；确认后恢复计时。四段已批准人工暂停共1758.542708秒，历史资源等待（含旧science1封闭355.134565秒）共53320.488382秒，未重复计入。当前新Run已核验纯排队171.195秒、有效执行4.975秒；按最新快照保守核算余额约40.935小时。SCI33、TECH2、收尾4、Transaction39小时上限不变。其他工程处理均计费，无额外预算或等待退款。

自动后续已绑定：复用C/S/R资格，资源满足后仅补N的8batch+5epoch；通过全流程遥测、TECH、用新N画像核算的串行成本及原起点预算门，才进入72项全新科学训练；全部72训练成功封存后才进入72审计。任一硬门失败即停止，零自动重试，不增加PE/头部拟合阶段。无需再次提交同Run。

旧science1保留为工程INVALID（0 N GPU worker/0科学训练/0审计），旧原冻结包、R1–R3、本次全部TECH与C/S/R成功结果均保留，旧N不完整遥测未改为PASS，P0-CUE仍关闭。

只读监控命令（精确共享入口返回值）：

```powershell
& '[REDACTED_MACHINE]' './scripts\ai4s\monitor.py' '--host' '[REDACTED_MACHINE]' '--remote-python' '[REDACTED_MACHINE]' '--output' '[REDACTED_MACHINE]' '--run-id' '2026-11-02_dsainet_ds07_r1_science1-readerfix1-full-w1'
```

同目录 `monitor_readerfix1.ps1` 包含这条原样命令。
