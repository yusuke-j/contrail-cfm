After fabric configuraiton

```
root@leaf_1# show | display set | no-more
set version 18.4R1.8
set groups __contrail_basic__ snmp community public authorization read-only
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then community add COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then accept
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term100 then accept
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from community COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 then reject
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then as-path-prepend "9999 9999 9999"
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then accept
set groups __contrail_basic__ policy-options community COM-MAINTENANCE members 9999:9999
set groups __contrail_basic__ protocols l2-learning global-mac-table-aging-time 1800
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn from family inet-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn then next-hop self
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn from family inet6-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn then next-hop self
set groups __contrail_overlay_bgp__ routing-options router-id 10.27.201.101
set groups __contrail_overlay_bgp__ routing-options route-distinguisher-id 10.27.201.101
set groups __contrail_overlay_bgp__ routing-options autonomous-system 64512
set groups __contrail_overlay_bgp__ routing-options resolution rib bgp.rtarget.0 resolution-ribs inet.0
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 type internal
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-address 10.27.201.101
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 hold-time 90
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 import REJECT-MAINTENANCE-MODE
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family evpn signaling
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family route-target
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 export _contrail_ibgp_export_policy
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 vpn-apply-export
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 multipath
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 10.27.201.104 peer-as 64512
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 from protocol evpn
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 then load-balance per-packet
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in from community community-esi-in
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in then accept
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term default-term then reject
set groups __contrail_overlay_evpn__ policy-options community community-esi-in members target:64512:7999999
set groups __contrail_overlay_evpn__ routing-options forwarding-table export EVPN-LB
set groups __contrail_overlay_evpn__ protocols evpn encapsulation vxlan
set groups __contrail_overlay_evpn__ protocols evpn extended-vni-list all
set groups __contrail_overlay_evpn__ switch-options vtep-source-interface lo0.0
set groups __contrail_overlay_evpn__ switch-options route-distinguisher 10.27.201.101:7999
set groups __contrail_overlay_evpn__ switch-options vrf-import import-evpn
set groups __contrail_overlay_evpn__ switch-options vrf-target target:64512:7999999
set groups __contrail_overlay_evpn_access__ protocols evpn multicast-mode ingress-replication
set groups __contrail_overlay_evpn_access__ switch-options vrf-target auto
set groups __contrail_overlay_lag__
set groups __contrail_overlay_multi_homing__
set apply-groups __contrail_basic__
set apply-groups __contrail_overlay_bgp__
set apply-groups __contrail_overlay_evpn__
set apply-groups __contrail_overlay_evpn_access__
set apply-groups __contrail_overlay_lag__
set apply-groups __contrail_overlay_multi_homing__
set system root-authentication encrypted-password "$6$V27YvPpq$pSc2H8joTRyIwJXCh64sZlbOihIxk8iYf9yKkCvOTb0H2Ufq/ugFjO/AvsYgVmN0ObCZGyvhNJCuLxAbPR55K0"
set system services ssh root-login allow
set system host-name leaf_1
set system syslog user * any emergency
set system syslog file messages any notice
set system syslog file messages authorization info
set system syslog file interactive-commands interactive-commands any
set system extensions providers juniper license-type juniper deployment-scope commercial
set system extensions providers chef license-type juniper deployment-scope commercial
set interfaces xe-0/0/0 unit 0 family inet address 10.27.1.102/24
set interfaces xe-0/0/1 unit 0 family inet address 10.10.10.1/24
set interfaces em0 unit 0 family inet address 172.27.115.3/22
set interfaces em1 unit 0 family inet address 169.254.0.2/24
set interfaces lo0 unit 0 family inet address 10.27.201.101/32
set snmp community public authorization read-only
set forwarding-options storm-control-profiles default all
set routing-options static route 0.0.0.0/0 next-hop 172.27.112.1
set protocols ospf area 0.0.0.0 interface all interface-type p2p
set protocols ospf area 0.0.0.0 interface em0.0 disable
set protocols lldp interface all
set protocols igmp-snooping vlan default
set vlans default vlan-id 1
```


```
root@spine_1# show | display set | no-more
set version 18.4R1.8
set groups __contrail_basic__ snmp community public authorization read-only
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then community add COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then accept
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term100 then accept
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from community COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 then reject
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then as-path-prepend "9999 9999 9999"
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then accept
set groups __contrail_basic__ policy-options community COM-MAINTENANCE members 9999:9999
set groups __contrail_basic__ protocols l2-learning global-mac-table-aging-time 1800
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn from family inet-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn then next-hop self
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn from family inet6-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn then next-hop self
set groups __contrail_overlay_bgp__ routing-options router-id 10.27.201.104
set groups __contrail_overlay_bgp__ routing-options route-distinguisher-id 10.27.201.104
set groups __contrail_overlay_bgp__ routing-options autonomous-system 64512
set groups __contrail_overlay_bgp__ routing-options resolution rib bgp.rtarget.0 resolution-ribs inet.0
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 type internal
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-address 10.27.201.104
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 hold-time 90
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 import REJECT-MAINTENANCE-MODE
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family evpn signaling
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family route-target
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 export _contrail_ibgp_export_policy
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 vpn-apply-export
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 cluster 0.0.0.100
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 multipath
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 from protocol evpn
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 then load-balance per-packet
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in from community community-esi-in
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in then accept
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term default-term then reject
set groups __contrail_overlay_evpn__ policy-options community community-esi-in members target:64512:7999999
set groups __contrail_overlay_evpn__ routing-options forwarding-table export EVPN-LB
set groups __contrail_overlay_evpn__ protocols evpn encapsulation vxlan
set groups __contrail_overlay_evpn__ protocols evpn extended-vni-list all
set groups __contrail_overlay_evpn__ switch-options vtep-source-interface lo0.0
set groups __contrail_overlay_evpn__ switch-options route-distinguisher 10.27.201.104:7999
set groups __contrail_overlay_evpn__ switch-options vrf-import import-evpn
set groups __contrail_overlay_evpn__ switch-options vrf-target target:64512:7999999
set groups __contrail_overlay_evpn_gateway__
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 1 from protocol direct
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 1 then accept
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 2 from protocol static
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 2 then accept
set groups __contrail_overlay_evpn_type5__ routing-options forwarding-table chained-composite-next-hop ingress evpn
set apply-groups __contrail_basic__
set apply-groups __contrail_overlay_bgp__
set apply-groups __contrail_overlay_evpn__
set apply-groups __contrail_overlay_evpn_gateway__
set apply-groups __contrail_overlay_evpn_type5__
set system root-authentication encrypted-password "$6$ZJu/Ois7$VZQ.oXz1c8CURWp34yt1bDDorSWdhy398mf5LwK4bSLlfFdWLXMJGYtxgAp5gPpgWgGR.BqK5uU79K9EiXoik."
set system services ssh root-login allow
set system host-name spine_1
set system syslog user * any emergency
set system syslog file messages any notice
set system syslog file messages authorization info
set system syslog file interactive-commands interactive-commands any
set system extensions providers juniper license-type juniper deployment-scope commercial
set system extensions providers chef license-type juniper deployment-scope commercial
set interfaces xe-0/0/1 unit 0 family inet address 10.27.1.101/24
set interfaces xe-0/0/2 unit 0 family inet address 10.27.2.101/24
set interfaces xe-0/0/3 unit 0 family inet address 10.27.3.101/24
set interfaces em0 unit 0 family inet address 172.27.115.235/22
set interfaces em1 unit 0 family inet address 169.254.0.2/24
set interfaces lo0 unit 0 family inet address 10.27.201.104/32
set snmp community public authorization read-only
set forwarding-options storm-control-profiles default all
set routing-options static route 0.0.0.0/0 next-hop 172.27.112.1
set protocols ospf area 0.0.0.0 interface all interface-type p2p
set protocols ospf area 0.0.0.0 interface em0.0 disable
set protocols lldp interface all
set protocols igmp-snooping vlan default
set vlans default vlan-id 1
```

```
root@spine_1# show | display set | no-more
set version 18.4R1.8
set groups __contrail_basic__ snmp community public authorization read-only
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then community add COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then accept
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term100 then accept
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from community COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 then reject
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then as-path-prepend "9999 9999 9999"
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then accept
set groups __contrail_basic__ policy-options community COM-MAINTENANCE members 9999:9999
set groups __contrail_basic__ protocols l2-learning global-mac-table-aging-time 1800
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn from family inet-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn then next-hop self
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn from family inet6-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn then next-hop self
set groups __contrail_overlay_bgp__ routing-options router-id 10.27.201.104
set groups __contrail_overlay_bgp__ routing-options route-distinguisher-id 10.27.201.104
set groups __contrail_overlay_bgp__ routing-options autonomous-system 64512
set groups __contrail_overlay_bgp__ routing-options resolution rib bgp.rtarget.0 resolution-ribs inet.0
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 type internal
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-address 10.27.201.104
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 hold-time 90
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 import REJECT-MAINTENANCE-MODE
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family evpn signaling
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family route-target
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 export _contrail_ibgp_export_policy
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 vpn-apply-export
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 cluster 0.0.0.100
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 multipath
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 10.27.201.101 peer-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 10.27.201.102 peer-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 10.27.201.103 peer-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 172.27.112.143 peer-as 64512
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 from protocol evpn
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 then load-balance per-packet
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in from community community-esi-in
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in then accept
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term default-term then reject
set groups __contrail_overlay_evpn__ policy-options community community-esi-in members target:64512:7999999
set groups __contrail_overlay_evpn__ routing-options forwarding-table export EVPN-LB
set groups __contrail_overlay_evpn__ protocols evpn encapsulation vxlan
set groups __contrail_overlay_evpn__ protocols evpn extended-vni-list all
set groups __contrail_overlay_evpn__ switch-options vtep-source-interface lo0.0
set groups __contrail_overlay_evpn__ switch-options route-distinguisher 10.27.201.104:7999
set groups __contrail_overlay_evpn__ switch-options vrf-import import-evpn
set groups __contrail_overlay_evpn__ switch-options vrf-target target:64512:7999999
set groups __contrail_overlay_evpn_gateway__
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 1 from protocol direct
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 1 then accept
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 2 from protocol static
set groups __contrail_overlay_evpn_type5__ policy-options policy-statement dummy_type5 term 2 then accept
set groups __contrail_overlay_evpn_type5__ routing-options forwarding-table chained-composite-next-hop ingress evpn
set apply-groups __contrail_basic__
set apply-groups __contrail_overlay_bgp__
set apply-groups __contrail_overlay_evpn__
set apply-groups __contrail_overlay_evpn_gateway__
set apply-groups __contrail_overlay_evpn_type5__
set system root-authentication encrypted-password "$6$ZJu/Ois7$VZQ.oXz1c8CURWp34yt1bDDorSWdhy398mf5LwK4bSLlfFdWLXMJGYtxgAp5gPpgWgGR.BqK5uU79K9EiXoik."
set system services ssh root-login allow
set system host-name spine_1
set system syslog user * any emergency
set system syslog file messages any notice
set system syslog file messages authorization info
set system syslog file interactive-commands interactive-commands any
set system extensions providers juniper license-type juniper deployment-scope commercial
set system extensions providers chef license-type juniper deployment-scope commercial
set interfaces xe-0/0/1 unit 0 family inet address 10.27.1.101/24
set interfaces xe-0/0/2 unit 0 family inet address 10.27.2.101/24
set interfaces xe-0/0/3 unit 0 family inet address 10.27.3.101/24
set interfaces em0 unit 0 family inet address 172.27.115.235/22
set interfaces em1 unit 0 family inet address 169.254.0.2/24
set interfaces lo0 unit 0 family inet address 10.27.201.104/32
set snmp community public authorization read-only
set forwarding-options storm-control-profiles default all
set routing-options static route 0.0.0.0/0 next-hop 172.27.112.1
set protocols ospf area 0.0.0.0 interface all interface-type p2p
set protocols ospf area 0.0.0.0 interface em0.0 disable
set protocols lldp interface all
set protocols igmp-snooping vlan default
set vlans default vlan-id 1
```


after vgp configure
```
root@leaf_1# show | display set | no-more
set version 18.4R1.8
set groups __contrail_basic__ snmp community public authorization read-only
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then community add COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then accept
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term100 then accept
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from community COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 then reject
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then as-path-prepend "9999 9999 9999"
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then accept
set groups __contrail_basic__ policy-options community COM-MAINTENANCE members 9999:9999
set groups __contrail_basic__ protocols l2-learning global-mac-table-aging-time 1800
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn from family inet-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn then next-hop self
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn from family inet6-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn then next-hop self
set groups __contrail_overlay_bgp__ routing-options router-id 10.27.201.101
set groups __contrail_overlay_bgp__ routing-options route-distinguisher-id 10.27.201.101
set groups __contrail_overlay_bgp__ routing-options autonomous-system 64512
set groups __contrail_overlay_bgp__ routing-options resolution rib bgp.rtarget.0 resolution-ribs inet.0
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 type internal
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-address 10.27.201.101
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 hold-time 90
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 import REJECT-MAINTENANCE-MODE
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family evpn signaling
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family route-target
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 export _contrail_ibgp_export_policy
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 vpn-apply-export
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 multipath
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 10.27.201.104 peer-as 64512
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 from protocol evpn
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 then load-balance per-packet
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in from community community-esi-in
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in then accept
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term default-term then reject
set groups __contrail_overlay_evpn__ policy-options community community-esi-in members target:64512:7999999
set groups __contrail_overlay_evpn__ routing-options forwarding-table export EVPN-LB
set groups __contrail_overlay_evpn__ protocols evpn encapsulation vxlan
set groups __contrail_overlay_evpn__ protocols evpn extended-vni-list all
set groups __contrail_overlay_evpn__ switch-options vtep-source-interface lo0.0
set groups __contrail_overlay_evpn__ switch-options route-distinguisher 10.27.201.101:7999
set groups __contrail_overlay_evpn__ switch-options vrf-import import-evpn
set groups __contrail_overlay_evpn__ switch-options vrf-target target:64512:7999999
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 flexible-vlan-tagging
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 native-vlan-id 1001
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 mtu 9192
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 encapsulation extended-vlan-bridge
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 unit 0 vlan-id 1001
set groups __contrail_overlay_evpn_access__ protocols evpn multicast-mode ingress-replication
set groups __contrail_overlay_evpn_access__ switch-options vrf-target auto
set groups __contrail_overlay_lag__
set groups __contrail_overlay_multi_homing__
set apply-groups __contrail_basic__
set apply-groups __contrail_overlay_bgp__
set apply-groups __contrail_overlay_evpn__
set apply-groups __contrail_overlay_evpn_access__
set apply-groups __contrail_overlay_lag__
set apply-groups __contrail_overlay_multi_homing__
set system root-authentication encrypted-password "$6$V27YvPpq$pSc2H8joTRyIwJXCh64sZlbOihIxk8iYf9yKkCvOTb0H2Ufq/ugFjO/AvsYgVmN0ObCZGyvhNJCuLxAbPR55K0"
set system services ssh root-login allow
set system host-name leaf_1
set system time-zone Asia/Tokyo
set system syslog user * any emergency
set system syslog file messages any notice
set system syslog file messages authorization info
set system syslog file interactive-commands interactive-commands any
set system extensions providers juniper license-type juniper deployment-scope commercial
set system extensions providers chef license-type juniper deployment-scope commercial
set interfaces xe-0/0/0 unit 0 family inet address 10.27.1.102/24
set interfaces em0 unit 0 family inet address 172.27.115.3/22
set interfaces em1 unit 0 family inet address 169.254.0.2/24
set interfaces lo0 unit 0 family inet address 10.27.201.101/32
set snmp community public authorization read-only
set forwarding-options storm-control-profiles default all
set routing-options static route 0.0.0.0/0 next-hop 172.27.112.1
set protocols ospf area 0.0.0.0 interface all interface-type p2p
set protocols ospf area 0.0.0.0 interface em0.0 disable
set protocols lldp interface all
set protocols igmp-snooping vlan default
set vlans default vlan-id 1
```


irb追加したコンフィグ
```
root@leaf_1# show | display set | no-more
set version 18.4R1.8
set groups __contrail_basic__ snmp community public authorization read-only
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then community add COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term1 then accept
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE term term100 then accept
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from family evpn
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from community COM-MAINTENANCE
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 2
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 1
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 3
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 4
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 5
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 from nlri-route-type 6
set groups __contrail_basic__ policy-options policy-statement REJECT-MAINTENANCE-MODE term term1 then reject
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then as-path-prepend "9999 9999 9999"
set groups __contrail_basic__ policy-options policy-statement MAINTENANCE-MODE-underlay then accept
set groups __contrail_basic__ policy-options community COM-MAINTENANCE members 9999:9999
set groups __contrail_basic__ protocols l2-learning global-mac-table-aging-time 1800
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn from family inet-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet-vpn then next-hop self
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn from family inet6-vpn
set groups __contrail_overlay_bgp__ policy-options policy-statement _contrail_ibgp_export_policy term inet6-vpn then next-hop self
set groups __contrail_overlay_bgp__ routing-options router-id 10.27.201.101
set groups __contrail_overlay_bgp__ routing-options route-distinguisher-id 10.27.201.101
set groups __contrail_overlay_bgp__ routing-options autonomous-system 64512
set groups __contrail_overlay_bgp__ routing-options resolution rib bgp.rtarget.0 resolution-ribs inet.0
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 type internal
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-address 10.27.201.101
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 hold-time 90
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 import REJECT-MAINTENANCE-MODE
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family evpn signaling
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 family route-target
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 export _contrail_ibgp_export_policy
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 vpn-apply-export
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 local-as 64512
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 multipath
set groups __contrail_overlay_bgp__ protocols bgp group _contrail_asn-64512 neighbor 10.27.201.104 peer-as 64512
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 from protocol evpn
set groups __contrail_overlay_evpn__ policy-options policy-statement EVPN-LB term term1 then load-balance per-packet
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in from community community-esi-in
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term esi-in then accept
set groups __contrail_overlay_evpn__ policy-options policy-statement import-evpn term default-term then reject
set groups __contrail_overlay_evpn__ policy-options community community-esi-in members target:64512:7999999
set groups __contrail_overlay_evpn__ routing-options forwarding-table export EVPN-LB
set groups __contrail_overlay_evpn__ protocols evpn encapsulation vxlan
set groups __contrail_overlay_evpn__ protocols evpn extended-vni-list all
set groups __contrail_overlay_evpn__ switch-options vtep-source-interface lo0.0
set groups __contrail_overlay_evpn__ switch-options route-distinguisher 10.27.201.101:7999
set groups __contrail_overlay_evpn__ switch-options vrf-import import-evpn
set groups __contrail_overlay_evpn__ switch-options vrf-target target:64512:7999999
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 flexible-vlan-tagging
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 native-vlan-id 1001
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 mtu 9192
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 encapsulation extended-vlan-bridge
set groups __contrail_overlay_evpn_access__ interfaces xe-0/0/1 unit 0 vlan-id 1001
set groups __contrail_overlay_evpn_access__ protocols evpn multicast-mode ingress-replication
set groups __contrail_overlay_evpn_access__ switch-options vrf-target auto
set groups __contrail_overlay_lag__
set groups __contrail_overlay_multi_homing__
set apply-groups __contrail_basic__
set apply-groups __contrail_overlay_bgp__
set apply-groups __contrail_overlay_evpn__
set apply-groups __contrail_overlay_evpn_access__
set apply-groups __contrail_overlay_lag__
set apply-groups __contrail_overlay_multi_homing__
set system root-authentication encrypted-password "$6$V27YvPpq$pSc2H8joTRyIwJXCh64sZlbOihIxk8iYf9yKkCvOTb0H2Ufq/ugFjO/AvsYgVmN0ObCZGyvhNJCuLxAbPR55K0"
set system services ssh root-login allow
set system host-name leaf_1
set system time-zone Asia/Tokyo
set system syslog user * any emergency
set system syslog file messages any notice
set system syslog file messages authorization info
set system syslog file interactive-commands interactive-commands any
set system extensions providers juniper license-type juniper deployment-scope commercial
set system extensions providers chef license-type juniper deployment-scope commercial
set interfaces xe-0/0/0 unit 0 family inet address 10.27.1.102/24
set interfaces em0 unit 0 family inet address 172.27.115.3/22
set interfaces em1 unit 0 family inet address 169.254.0.2/24
set interfaces irb unit 1001 family inet address 10.10.10.254/24
set interfaces lo0 unit 0 family inet address 10.27.201.101/32
set snmp community public authorization read-only
set forwarding-options storm-control-profiles default all
set routing-options static route 0.0.0.0/0 next-hop 172.27.112.1
set protocols ospf area 0.0.0.0 interface all interface-type p2p
set protocols ospf area 0.0.0.0 interface em0.0 disable
set protocols lldp interface all
set protocols igmp-snooping vlan default
set vlans default vlan-id 1
set vlans vlan-1001 vlan-id 1001
set vlans vlan-1001 l3-interface irb.1001
```
