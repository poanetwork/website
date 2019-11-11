# 升级实例到更大的类型

1. 登录到您的AWS控制台。 在服务“Services”中，选择“ EC2”，然后导航到左侧栏中的"Instances" &gt; "Instances"。 您应该看到当前区域中所有实例的列表，类似于此：选择要升级的实例。 **仔细检查IP地址，以确认您正在从正确的网络升级正确的节点** 
2. 单击操作“Actions”，从下拉列表中选择Instance State" &gt; "Stop" 确认要停止的实例。 
3. 等待直到实例状态“Instance state”变为已停止“stopped”，然后单击操作“Actions”，然后选择实例设置并更改实例类型"Instance settings" &gt; "Change instance type"。选择新的实例类型（例如`t2.xlarge`），单击“**OK**”确认。 
4. 检查实例列表上实例类型“instance type”列中的值是否已更新 
5. 单击操作“Actions”，然后单击实例状态并点开始"Instance state" &gt; "Start"。 
6. 等待实例状态“Instance state”更改为正在运行“running”。 还要在netstat仪表板（[sokol netstat](https://sokol-netstat.poa.network/) / [core netstat](https://core-netstat.poa.network/)）中检查您的节点是绿色的并且正在加载。 这可能需要一些时间才能安定下来。 
7. 返回AWS页面，重要的是，**升级后，节点的公共IP地址将更改**。 您应该记下新的IP地址并将其保存在“IPv4 Public IP”列中。 
8. 通过ssh登录到您的节点，例如

```text
ssh root@192.0.2.1
```

    9. 编辑奇偶校验配置文件以更新您的公共IP地址。 要在您喜欢的文本编辑器（例如`nano`）中执行此打开文件

```text
nano /home/validator/node.toml
```

搜索类似的行

```text
nat = "extip:192.0.2.1"
```

将该行中的IP地址更改为新的IP地址，例如

```text
nat = "extip:192.0.2.2"
```

保存并退出文本编辑器（对于`nano`，请按CTRL + X，然后按y）。

10.   重新启动奇偶校验和netstats

```text
sudo systemctl restart poa-parity
```

重新启动netstats

```text
sudo systemctl restart poa-netstats
```

11.  再次检查您的节点在netstats中是否为绿色。

