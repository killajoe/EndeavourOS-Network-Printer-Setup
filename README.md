# EndesavourOS Network Printing Setup:

currently working on a convinience setup to enable network printing automatically:

![2023-08-11_11-39](https://github.com/killajoe/EndeavourOS-Network-Printer-Setup/assets/16797647/a6d1a4ce-2785-4695-85f3-62c85c52f855)


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

```wget https://raw.githubusercontent.com/killajoe/EndeavourOS-Network-Printer-Setup/main/Convenience-printer-installation  &&  chmod +x Convenience-printer-installation && ./Convenience-printer-installation```

Possible to use this on the installer from welcome too:
![add-script](https://github.com/killajoe/EndeavourOS-Network-Printer-Setup/assets/16797647/e31e730c-92d1-4048-a18d-6e60fc7637ed)

pressing the button right bottom "Fetch your install customization file (advanced)"  and paste the raw script url into the popup field.. 

```https://raw.githubusercontent.com/killajoe/EndeavourOS-Network-Printer-Setup/main/Convenience-printer-installation```

For this to work you will need to choose printing support (Cups) in Packages screen (only available for online install methods):
![add-printer-packages](https://github.com/killajoe/EndeavourOS-Network-Printer-Setup/assets/16797647/08de096c-c471-4487-8d03-db67bd133ca5)


