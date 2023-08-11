# EndesavourOS Network Printing Setup:

currently working on a convinience setup to enable network printing automatically:

![2023-06-18_16-02](https://github.com/killajoe/fileserver/assets/16797647/98fccaf0-d4b0-4269-a803-311445b26dce)

The script will create a new firewalld zone called network-printer.xml.

This service uses the same set as home preset with:
**ssh mdns samba-client dhcpv6-client**
Plus 2 extra services needed for network-printer setups to be enabled: **ipp, ipp-client**

The second change is to enable local hostname resolution systemwide what is disabled by default on arch packages by changing **/etc/nsswitch.conf**

```
-hosts: mymachines resolve [!UNAVAIL=return] files myhostname dns
+hosts: mymachines mdns_minimal [NOTFOUND=return] resolve [!UNAVAIL=return] files myhostname dns
```
You can use this on your own risk:

```wget https://raw.githubusercontent.com/killajoe/fileserver/main/Convenience-printer-installation  &&  chmod +x Convenience-printer-installation && ./Convenience-printer-installation```

Possible to use this on the installer from welcome too:
![2023-07-18_16-06](https://github.com/killajoe/fileserver/assets/16797647/6824a2e8-0793-4be5-abc8-9c754201988c)
pressing the button right bottom "Fetch your install customization file (advanced)"  and paste the raw script url into the popup field.. 

```https://raw.githubusercontent.com/killajoe/fileserver/main/Convenience-printer-installation```

For this to work you will need to choose printing support (Cups) in Packages screen (only available for online install methods):
![2023-07-18_16-20](https://github.com/killajoe/fileserver/assets/16797647/cd6d985c-ae7d-4d56-a995-a6fc124908a3)

