---
title: openvpn
date: 2017-10-31 21:12:52
categories: vpn
tags: vpn
---

###  1 打开终端并安装openvpn用以下命令
``` bash
sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome
```
{% asset_img step1.png %}

### 2 打开网络菜单，转到“VPN连接”，然后点击“配置VPN…”。
{% asset_img step2.png %}

### 3 Click on "Add".
{% asset_img step3.png %}

### 4 Click on "Import a saved VPN configuration...".
{% asset_img step4.png %}

### 5 Click on "Create".
{% asset_img step5.png %}

### 6 Download the OpenVPN configuration, unzip it and import the .ovpn file.
{% asset_img step6.png %}

### 7 Enter your login credentials and click on "Save...".
{% asset_img step7.png %}

### 7a Switch to "Advanced Configuration" and in the tab "TLS Authentication" check "Use additional TLS authentication". Select the file "StaticKey.pem" from the configuration and set the "Key Direction" to "0". Confirm with "OK".
{% asset_img step7a.png %}

### 8 Open the network menu to establish a VPN connection. 
Switch to "Advanced Configuration" and in the tab "TLS Authentication" check "Use additional TLS authentication". Select the file "StaticKey.pem" from the configuration and set the "Key Direction" to "0". Confirm with "OK".
{% asset_img step8.png %}

### 9 If connection has been successfully established, the status is shown in the menu bar. You can manage your VPN connection in the network settings.
{% asset_img step9.png %}






