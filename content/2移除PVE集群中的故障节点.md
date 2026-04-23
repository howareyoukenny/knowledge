# 移除PVE集群中的故障节点

## 1 迁移故障节点pve9上的虚拟机到其它节点

## 2 备份pve9数据

## 3 在pve9上执行

```
systemctl stop pve-cluster.service
systemctl stop corosync.service
pmxcfs -l
rm /etc/pve/corosync.conf
rm -rf /etc/corosync
killall pmxcfs
systemctl start pve-cluster.service
```

## 4 在其它节点执行

```
pvecm delnode pve9
rm -rf /etc/pve/nodes/pve9
```