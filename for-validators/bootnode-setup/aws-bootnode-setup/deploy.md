# 部署

#### 创建实例

1. 在配置了所有选项之后，您首先需要创建一个实例：（您仍应位于： ~/deployment-playbooks中\)

   ```text
   ansible-playbook bootnode.yml
   ```

   除非您未设置密码短语或您最近输入密码，否则此脚本将询问您SSH密钥密码短语。  

2. 完成此过程后，检查脚本的输出并记下IP（例如`192.0.2.1`）地址和AWS InstanceID（例如`i-0123456789abcdef0`）以备后用。 如果选择使用弹性IP，请记下节点的最终IP地址。 
3. 使用服务器的IP地址创建`hosts`文件（例如192.0.2.1）：

   ```text
   [bootnode]
   192.0.2.1
   ```

4. 运行ansible脚本

   ```text
   ansible-playbook -i hosts site.yml
   ```

5. 在浏览器中打开`NETSTATS_SERVER`地址，然后检查名为**NODE\_FULLNAME**的节点是否出现在列表中 
6. 登录到该节点并从奇偶校验日志中获取enode：

   ```text
   ssh root@192.0.2.1
   grep enode /home/bootnode/logs/parity.log
   ```

   复制`enode` uri并将其发送给仪式主持人。 如果找不到此行，请重新启动奇偶校验

   ```text
   systemctl restart poa-parity
   ```

   然后再试一次。 如果仍然找不到`enode` uri，请使用以下命令重新启动所有服务。

{% hint style="info" %}
如果在奇偶校验重新启动后您发现在`NETSTATS_SERVER` url上您的节点开始落后于其他节点（块号小于其他节点），请尝试重新启动统计信息服务（假设您以root身份连接）：
{% endhint %}

```text
su bootnode
pm2 restart all
```

之后，刷新`NETSTATS_SERVER` URL，然后再次检查您节点的块号。 如果您的节点仍然不活动或缺少`enode`，请登录到root帐户并重新启动操作系统.

```text
su 
shutdown -r now
```

