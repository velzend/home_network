# home_network
Diagram and configuration, etc. of my network at home

http://go.drawthe.net 

```yaml
diagram:
  fill: "white"
  rows: 5
  columns: 5
  gridLines: false
title:
  color: black
  fill: none
  logoFill: white
  stroke: black
  text: "Home network"
  subText: "description of our home network"
  type: bar
  author: "Dennis van Velzen"
groupDefaults: &groupDefaults
  fill: "none"
  color: black
  stroke: black
connectionDefaults: &connectionDefaults
  color: "black"
  stroke: "black"
cisco: &cisco
  x: "+1"
  color: "#004BAF"
  fill: "white"
  iconFamily: "cisco"
  icon: "router"
  iconFill: "#004BAF"
  iconStrokeWidth: .25
  preserveWhite: true
  stroke: "none"
icons:
  router1:
    <<: *cisco
    x: 0
    y: 1
    text: "MikroTik Router"
    metadata:
      serial number: 87F208AC6F8E/607
      platform: RouterOS
      brand: MikroTik
      model: hEX S RB760iGS
      E01: CC:2D:E0:F6:94:D7
      E06: CC:2D:E0:F6:94:DC
  ntu:
    <<: *cisco
    x: 0
    y: 3
    text: "NTU"
    icon: communicationsserver
    metadata:
      serial number: ""
      platform: 3
      brand: ""
      model: ""
      E01: ""
  switch:
    <<: *cisco
    x: 1
    y: 2
    text: "switch"
    icon: workgroupswitch
    metadata:
      serial number: ""
      platform: 3
      brand: 3com
      model: "Baseline Switch 2924 - SFP Plus (3CBLSG24)"
      MAC Addr: 00:1E:C1:21:65:E0
      WAN IP: ""
      LAN IP: "10.5.20.1"
      WLAN address range: "10.5.21.0/24"
      WLAN DHCP range: "10.5.21.10-252"
  accesspoint1:
    <<: *cisco
    x: 1
    y: 1
    text: "AP woonkamer"
    icon: dualmodeap
    metadata:
      serial number: ""
      platform: RouterOS
      brand: MikroTik
      model: "cAP ac"
      LAN IP: "10.5.21.1"
      E01: ""
  accesspoint2:
    <<: *cisco
    x: 2
    y: 1
    text: "AP zolder"
    icon: dualmodeap
    metadata:
      serial number: ""
      platform: RouterOS
      brand: MikroTik
      model: "cAP ac"
      LAN IP: "10.5.21.2"
      E01: ""
connections:
  - { <<: *connectionDefaults, endpoints: [switch, ntu:tagged vlan 4+6+7]}
  - { <<: *connectionDefaults, endpoints: [switch:vlan 4+7+100, router1] }
  - { <<: *connectionDefaults, endpoints: [switch:vlan 100, accesspoint1] }
  - { <<: *connectionDefaults, endpoints: [switch:vlan 100, accesspoint2] }

```

