# vagrant-afl

When you want to mess around with afl in a hurry. Installs AFL on a ramdisk too, just to save you smashing up that tasty SSD. Heads up: Because this is using a ramdisk you'll lose all your files if the VM reboots. *don't blame me for losing all your 0days please :)*

## Usage:

- Get [Vagrant](https://www.vagrantup.com/)
- Get [Virtual Box](https://www.virtualbox.org/)
- `git clone https://github.com/JamieH/vagrant-afl`
- `cd vagrant-afl`
- `vagrant up`
- `vagrant ssh`
- `cd afl`
- `./afl-fuzz`