# UsefulCommands
Commands that I find useful

## Running Homeassistant in KVM on a Intel Nuc
- Via bios, enable autoboot if system power fails
- Install kvm

`virsh list --all`

`virsh start homeassistant`

### Auto start KVM-machine on boot

put a file named startmyvm.service inside /etc/systemd/system
```
[Unit]
Description=Autostartmyvmpls

[Service]
ExecStart=/home/sebbe/Desktop/VMs/autostartmyvm.sh

[Install]
WantedBy=multi-user.target
```

Start service: `sudo systemctl start startmyvm.service`
Enable service to work on reboot: `sudo systemctl enable startmyvm.service`

Status of service: `systemctl status startmyvm`


### Network for kvm
```
### För Att ge nätverk till kvm-maskinen och access från nätverket:
cat /etc/netplan/00-installer-config.yaml:
# This is the network config written by 'subiquity'
network:
#  renderer: NetworkManager
  ethernets:
    eno1:
      dhcp4: true
  version: 2
  bridges:
    br0:
      dhcp4: yes
      interfaces:
             - eno1
      parameters:
        stp: true
```


### Auto-attach usb-device to kvm:

`lsusb -v`
sudo virsh attach-device domain_name --file usbdevice.xml --persistent

 ```
usbdevice.xml:
<hostdev mode='subsystem' type='usb'>
    <source startupPolicy='optional'>
      <vendor id='0x10c4'/>
      <product id='0xea60'/>
    </source>
  </hostdev>
```



----
## Crontab
Runs a pythonscript every minut and logs error to pv.txt

` * * * * * PYTHONPATH=/home/sebstr/.local/lib/python2.7/site-packages/ python /home/sebstr/master/cronjob.py -V > /home/sebstr/pv.txt 2>&1 `


----

## Hyper-V

**enable hyper-v** `bcdedit /set hypervisorlaunchtype auto`

----

## Cryptography

-- in CMDER

**To get sha256 checksum** `sha256sum filename`

**Load file with gpg** also see `gpg --help`
`gpg --import filename` and then `gpg --fingerprint`
