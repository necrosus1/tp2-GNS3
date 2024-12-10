# tp2-GNS3
## etape1
sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE=eth0
NAME=nat
BOOTPROTO=dhcp
ONBOOT=yes

sudo nmcli connection reload
sudo nmcli connection up nat
 ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=113 time=23.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=113 time=36.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=113 time=25.3 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=113 time=29.2 ms

sudo vi /etc/sysconfig/network-scripts/ifcfg-eth1

DEVICE=eth1
NAME=lan

BOOTPROTO=static
ONBOOT=yes

IPADDR=10.2.1.254
NETMASK=255.255.255.0

sudo nmcli connection reload
sudo nmcli connection up lan

ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group defau0
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP gro0
    link/ether 0c:07:55:a4:00:00 brd ff:ff:ff:ff:ff:ff
    altname enp0s3
    altname ens3
    inet 192.168.122.218/24 brd 192.168.122.255 scope global dynamic noprefixro0
       valid_lft 3082sec preferred_lft 3082sec
    inet6 fe80::e07:55ff:fea4:0/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP gro0
    link/ether 0c:07:55:a4:00:01 brd ff:ff:ff:ff:ff:ff
    altname enp0s4
    altname ens4
    inet 10.2.1.254/24 brd 10.2.1.255 scope global noprefixroute eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::e07:55ff:fea4:1/64 scope link
       valid_lft forever preferred_lft forever

##Configuration de node1.tp2.efrei
##Ping de node1.tp2.efrei vers router.tp2.efrei
 ping 10.2.1.254

84 bytes from 10.2.1.254 icmp_seq=1 ttl=64 time=3.093 ms
84 bytes from 10.2.1.254 icmp_seq=2 ttl=64 time=3.395 ms
84 bytes from 10.2.1.254 icmp_seq=3 ttl=64 time=2.212 ms
84 bytes from 10.2.1.254 icmp_seq=4 ttl=64 time=2.400 ms
84 bytes from 10.2.1.254 icmp_seq=5 ttl=64 time=1.684 ms

##Ping de node1.tp2.efrei vers 8.8.8.8
 ping 8.8.8.8

84 bytes from 8.8.8.8 icmp_seq=1 ttl=108 time=61.994 ms
84 bytes from 8.8.8.8 icmp_seq=2 ttl=108 time=86.531 ms
84 bytes from 8.8.8.8 icmp_seq=3 ttl=108 time=45.078 ms
84 bytes from 8.8.8.8 icmp_seq=4 ttl=108 time=60.953 ms
84 bytes from 8.8.8.8 icmp_seq=5 ttl=108 time=70.305 ms

trace  8.8.8.8
trace to 8.8.8.8, 8 hops max, press Ctrl+C to stop
 1   10.2.1.254   6.385 ms  2.220 ms  0.811 ms
 2   192.168.122.1   3.353 ms  1.950 ms  1.917 ms
 3   10.0.3.2   3.015 ms  1.565 ms  1.540 ms
 4   *10.0.3.2   48.571 ms (ICMP type:3, code:3, Destination port unreachable)


##Afficher la CAM Table du switch

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0050.7966.6800    DYNAMIC     Et0/0
   1    0c7e.7046.0001    DYNAMIC     Et0/1
Total Mac Addresses for this criterion: 2





