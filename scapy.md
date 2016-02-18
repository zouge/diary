# Scapy 小结

在Mac下使用Scapy ，有不少的问题。因为对Linux兼容得比较好，所以在kali下进行学习。
Scapy的使用，`$sudo scapy` 就可以了，[官方文档](http://www.secdev.org/projects/scapy/doc/installation.html)。

Scapy的一些基本常识：

以下是一些Scapy的应用
## ARP
#### send
```
>>> send(ARP(psrc="10.211.55.55", pdst="10.211.55.2"))
.
Sent 1 packets.
>>>
```
#### arping
```
>>> arping("10.211.55.*")
Begin emission:
**Finished to send 256 packets.

Received 2 packets, got 2 answers, remaining 254 packets
  00:1c:42:00:00:18 10.211.55.1
  00:1c:42:00:00:08 10.211.55.2
(<ARPing: TCP:0 UDP:0 ICMP:0 Other:2>, <Unanswered: TCP:0 UDP:0 ICMP:0 Other:254>)
```
#### srp
```
>>> ans, unans = srp(Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(pdst="10.211.55.2"), timeout=2)
Begin emission:
Finished to send 1 packets.
.*
Received 2 packets, got 1 answers, remaining 0 packets
>>> ans.summary(lambda (s,r): r.sprintf("%Ether.src% %ARP.psrc%") )
00:1c:42:00:00:08 10.211.55.2
>>>
```

---
待续。。。
