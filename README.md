# salt-env-bootstrap
Ansible playbooks which create salt environment
## Libvirt network with access to the Internet.
 Playbooks relies on prepared network inside libvirt with next paramaters:
```xml
<network connections='6'>
  <name>default</name>
  <uuid>f613dad9-6db8-44ab-aee2-664c2efdf970</uuid>
  <forward mode='nat'>
    <nat>
      <port start='1024' end='65535'/>
    </nat>
  </forward>
  <bridge name='virbr0' stp='on' delay='0'/>
  <mac address='52:54:00:b4:a9:d8'/>
  <ip address='192.168.122.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.122.2' end='192.168.122.254'/>
      <host mac='52:54:00:78:b1:14' name='a-master' ip='192.168.122.160'/>
      <host mac='52:54:00:f2:5e:88' name='a-worker1' ip='192.168.122.202'/>
      <host mac='52:54:00:bc:c1:ef' name='a-worker2' ip='192.168.122.163'/>
      <host mac='52:54:00:14:1f:90' name='a-worker3' ip='192.168.122.2'/>
      <host mac='52:54:00:a8:1b:fc' name='a-worker4' ip='192.168.122.237'/>
      <host mac='52:54:00:86:c3:40' name='a-worker5' ip='192.168.122.102'/>
      <host mac='52:54:00:92:2c:72' name='a-worker6' ip='192.168.122.240'/>
    </dhcp>
  </ip>
</network>
```
**N.B.:** In further versions libvirt and libvirt network setup will be also
handled by _ansible_.

## Execution of playbooks
 To be able run playbooks please **prepare** libvirt first with your values as
 shown above.
* Clone repository
```
git clone https://github.com/Iyozhikov/salt-env-bootstrap
cd salt-env-bootstrap
```
* Modify _hosts_ file according to your configuration of libvirt network from
first step mentioned above.
* Run playbooks with virthost root password
```
ansible-playbook -v deploy.yml -k
```
