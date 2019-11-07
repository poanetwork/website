# Upgrade Instance to a Larger Instance Type

1. Login to your AWS console. In "Services" select "EC2" and navigate to "Instances" &gt; "Instances" in the left sidebar. You should see a list of all your instances in the current region, similar to this:  Select the instance you want to upgrade. **Double check IP address to verify that you're upgrading correct node from correct network** 
2. Click "Actions", from dropdown select "Instance State" &gt; "Stop"   Confirm the instance you want to stop. 
3. Wait until "Instance state" changes to "stopped", then click "Actions" and select "Instance settings" &gt; "Change instance type"  Select the new instance type \(e.g. `t2.xlarge`\)  Click **OK** to confirm. 
4. Check that value in "Instance type" column on the instances list was updated\| 
5. Click "Actions", then "Instance state" &gt; "Start"  
6. Wait until "Instance state" changes to "running". Also check in netstat dashboard \([sokol netstat](https://sokol-netstat.poa.network/)/[core netstat](https://core-netstat.poa.network/)\) that your node is green and catching up. This may take some time to settle down. 
7. Back to AWS page, it is important that **After upgrade your node's public IP address will change**. You should note and save the new IP address in "IPv4 Public IP" column. 
8. Login to your node via ssh, e.g.

```text
ssh root@192.0.2.1
```

    9. Edit parity configuration file to update your public ip address. To do this open file in your favourite text editor \(e.g. `nano`\)

```text
nano /home/validator/node.toml
```

Search for a row similar to

```text
nat = "extip:192.0.2.1"
```

change IP address in this line to a new one, e.g.

```text
nat = "extip:192.0.2.2"
```

Save and exit text editor \(for `nano`, press CTRL+X then y\).

10.   Restart parity and netstats

```text
sudo systemctl restart poa-parity
```

Restart netstats

```text
sudo systemctl restart poa-netstats
```

11.  Check again that your node is green in netstats.

