## Laboratorio Vagrant

>Elementos necesarios para el desarrollo del LaboratorioVagrant:

- Vagrant 2.2.16
- GIT Bash

Pasos a seguir para la creacion del LaboratioVagrant:

>1. Creacion directorio labvagrant
`````
$ mkdir labvagrant

`````
>2. Inicializamos vagrant en el repositorio "labvagrant"
`````
$ vagrant init

A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.

`````
>4. En defecto nos creara un "Vagrantfile" el cual modificaremos segun lo requerido
`````
$ vim Vagrantfile

# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
#### CUANTAS MAQUINAS VIRTUALES QUIERES CREAR?
VM_NUMBER=6
  (1..VM_NUMBER).each do |i|
    config.vm.define "vm_lab_#{i}" do |node|
        node.vm.box = "centos/7"
        node.vm.hostname = "vm#{i}"
        node.vm.network :private_network, ip: "10.10.10.1#{i}"
          node.vm.provider "virtualbox" do |vb|
             vb.cpus = 1
             vb.memory = "256"
          end
    end
  end
end

`````
>5. A continuacion crearemos las maquinas virtuales descriptos en el Vagrantfile
`````
$ vagrant up

Bringing machine 'vm_lab_1' up with 'virtualbox' provider...
Bringing machine 'vm_lab_2' up with 'virtualbox' provider...
==> vm_lab_1: Box 'centos/7' could not be found. Attempting to find and install...
    vm_lab_1: Box Provider: virtualbox
    vm_lab_1: Box Version: >= 0
==> vm_lab_1: Loading metadata for box 'centos/7'
    vm_lab_1: URL: https://vagrantcloud.com/centos/7
==> vm_lab_1: Adding box 'centos/7' (v2004.01) for provider: virtualbox
    vm_lab_1: Downloading: https://vagrantcloud.com/centos/boxes/7/versions/2004.01/providers/virtualbox.box
Download redirected to host: cloud.centos.org
    vm_lab_1:
    vm_lab_1: Calculating and comparing box checksum...
==> vm_lab_1: Successfully added box 'centos/7' (v2004.01) for 'virtualbox'!
==> vm_lab_1: Importing base box 'centos/7'...
==> vm_lab_1: Matching MAC address for NAT networking...
==> vm_lab_1: Checking if box 'centos/7' version '2004.01' is up to date...
==> vm_lab_1: Setting the name of the VM: labvagrant_vm_lab_1_1623770782595_15462
==> vm_lab_1: Clearing any previously set network interfaces...
==> vm_lab_1: Preparing network interfaces based on configuration...
    vm_lab_1: Adapter 1: nat
    vm_lab_1: Adapter 2: hostonly
==> vm_lab_1: Forwarding ports...
    vm_lab_1: 22 (guest) => 2222 (host) (adapter 1)
==> vm_lab_1: Running 'pre-boot' VM customizations...
==> vm_lab_1: Booting VM...
==> vm_lab_1: Waiting for machine to boot. This may take a few minutes...
    vm_lab_1: SSH address: 127.0.0.1:2222
    vm_lab_1: SSH username: vagrant
    vm_lab_1: SSH auth method: private key
    vm_lab_1:
    vm_lab_1: Vagrant insecure key detected. Vagrant will automatically replace
    vm_lab_1: this with a newly generated keypair for better security.
    vm_lab_1:
    vm_lab_1: Inserting generated public key within guest...
    vm_lab_1: Removing insecure key from the guest if it's present...
    vm_lab_1: Key inserted! Disconnecting and reconnecting using new SSH key...
==> vm_lab_1: Machine booted and ready!
==> vm_lab_1: Checking for guest additions in VM...
    vm_lab_1: No guest additions were detected on the base box for this VM! Guest
    vm_lab_1: additions are required for forwarded ports, shared folders, host only
    vm_lab_1: networking, and more. If SSH fails on this machine, please install
    vm_lab_1: the guest additions and repackage the box to continue.
    vm_lab_1:
    vm_lab_1: This is not an error message; everything may continue to work properly,
    vm_lab_1: in which case you may ignore this message.
==> vm_lab_1: Setting hostname...
==> vm_lab_1: Configuring and enabling network interfaces...
==> vm_lab_1: Rsyncing folder: /cygdrive/c/Users/Beto/labvagrant/ => /vagrant
==> vm_lab_2: Box 'centos/7' could not be found. Attempting to find and install...
    vm_lab_2: Box Provider: virtualbox
    vm_lab_2: Box Version: >= 0
==> vm_lab_2: Loading metadata for box 'centos/7'
    vm_lab_2: URL: https://vagrantcloud.com/centos/7
==> vm_lab_2: Adding box 'centos/7' (v2004.01) for provider: virtualbox
==> vm_lab_2: Importing base box 'centos/7'...
==> vm_lab_2: Matching MAC address for NAT networking...
==> vm_lab_2: Checking if box 'centos/7' version '2004.01' is up to date...
==> vm_lab_2: Setting the name of the VM: labvagrant_vm_lab_2_1623770873765_83143
==> vm_lab_2: Fixed port collision for 22 => 2222. Now on port 2200.
==> vm_lab_2: Clearing any previously set network interfaces...
==> vm_lab_2: Preparing network interfaces based on configuration...
    vm_lab_2: Adapter 1: nat
    vm_lab_2: Adapter 2: hostonly
==> vm_lab_2: Forwarding ports...
    vm_lab_2: 22 (guest) => 2200 (host) (adapter 1)
==> vm_lab_2: Running 'pre-boot' VM customizations...
==> vm_lab_2: Booting VM...
==> vm_lab_2: Waiting for machine to boot. This may take a few minutes...
    vm_lab_2: SSH address: 127.0.0.1:2200
    vm_lab_2: SSH username: vagrant
    vm_lab_2: SSH auth method: private key
    vm_lab_2:
    vm_lab_2: Vagrant insecure key detected. Vagrant will automatically replace
    vm_lab_2: this with a newly generated keypair for better security.
    vm_lab_2:
    vm_lab_2: Inserting generated public key within guest...
    vm_lab_2: Removing insecure key from the guest if it's present...
    vm_lab_2: Key inserted! Disconnecting and reconnecting using new SSH key...
==> vm_lab_2: Machine booted and ready!
==> vm_lab_2: Checking for guest additions in VM...
    vm_lab_2: No guest additions were detected on the base box for this VM! Guest
    vm_lab_2: additions are required for forwarded ports, shared folders, host only
    vm_lab_2: networking, and more. If SSH fails on this machine, please install
    vm_lab_2: the guest additions and repackage the box to continue.
    vm_lab_2:
    vm_lab_2: This is not an error message; everything may continue to work properly,
    vm_lab_2: in which case you may ignore this message.
==> vm_lab_2: Setting hostname...
==> vm_lab_2: Configuring and enabling network interfaces...
==> vm_lab_2: Rsyncing folder: /cygdrive/c/Users/Beto/labvagrant/ => /vagrant

`````
>6. Verificamos el estado de las maquinas virtuales creadas
`````
$ vagrant status

Current machine states:

vm_lab_1                  running (virtualbox)
vm_lab_2                  running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.

`````
>7. Por ultimo validamos las interfaces de red en ejecucion de cada maquina virtual
`````
$ vagrant ssh vm_lab_1

[vagrant@vm1 ~]$ hostname
vm1
[vagrant@vm1 ~]$ ifconfig
-bash: ifconfig: command not found
[vagrant@vm1 ~]$ sudo su
[root@vm1 vagrant]# ifconfig
bash: ifconfig: command not found
[root@vm1 vagrant]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:4d:77:d3 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global noprefixroute dynamic eth0
       valid_lft 85806sec preferred_lft 85806sec
    inet6 fe80::5054:ff:fe4d:77d3/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:af:a3:5b brd ff:ff:ff:ff:ff:ff
    inet 10.10.10.11/24 brd 10.10.10.255 scope global noprefixroute eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:feaf:a35b/64 scope link
       valid_lft forever preferred_lft forever
[root@vm1 vagrant]# ll
total 0
[root@vm1 vagrant]# ls
[root@vm1 vagrant]# Connection to 127.0.0.1 closed by remote host.
Connection to 127.0.0.1 closed.

`````
prueba 03
