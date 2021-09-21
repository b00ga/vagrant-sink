Vagrant.configure("2") do |config|
  config.vm.provision "ansible", type: "shell",
    inline: "echo Provisioning..."

  config.vm.synced_folder "playbooks", "/ansible"

  config.vm.define "centos6" do |machine|
    machine.vm.box = "generic/centos6"
  end
  config.vm.define "centos7" do |machine|
    machine.vm.box = "generic/centos7"
  end
  config.vm.define "centos8" do |machine|
    machine.vm.box = "generic/centos8"
  end
  config.vm.define "fedora33" do |machine|
    machine.vm.box = "bento/fedora-32"
  end
  config.vm.define "fedora34" do |machine|
    machine.vm.box = "bento/fedora-32"
  end
  config.vm.define "ubuntu1604" do |machine|
    machine.vm.box = "ubuntu/xenial64"
  end
  config.vm.define "ubuntu1804" do |machine|
    machine.vm.box = "ubuntu/bionic64"
  end
  config.vm.define "ubuntu2004" do |machine|
    machine.vm.box = "bento/ubuntu-20.04"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo apt install -y ansible"
  end
  config.vm.define "debian10" do |machine|
    machine.vm.box = "bento/debian-10"
  end
  config.vm.define "debian11" do |machine|
    machine.vm.box = "generic/debian11"
  end
  config.vm.define "opensuse15" do |machine|
    machine.vm.box = "generic/opensuse15"
  end
  config.vm.define "arch" do |machine|
    machine.vm.box = "generic/arch"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pacman -Sy archlinux-keyring --noconfirm"
  end
  config.vm.define "alpine312" do |machine|
    machine.vm.box = "generic/alpine312"
  end
  config.vm.define "alpine313" do |machine|
    machine.vm.box = "generic/alpine313"
  end
  config.vm.define "alpine314" do |machine|
    machine.vm.box = "generic/alpine313"
  end
  config.vm.define "freebsd11" do |machine|
    machine.vm.box = "generic/freebsd11"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y py38-ansible"
  end
  config.vm.define "freebsd12" do |machine|
    machine.vm.box = "generic/freebsd12"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y py38-ansible"
  end
  config.vm.define "freebsd13" do |machine|
    machine.vm.box = "generic/freebsd13"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y py38-ansible"
  end
  config.vm.define "openbsd" do |machine|
    machine.vm.box = "generic/openbsd6"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo /usr/sbin/pkg_add -v ansible coreutils && sudo ln -s /usr/local/bin/gchown /usr/bin/chown"
  end
  config.vm.define "netbsd8" do |machine|
    machine.vm.box = "generic/netbsd8"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkgin -y update && pkgin -y install ansible"
  end
  config.vm.define "netbsd9" do |machine|
    machine.vm.box = "generic/netbsd9"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkgin -y update && pkgin -y install ansible && ln -s /usr/pkg/bin/python3.8 /usr/bin/python3"
  end
  config.vm.define "dragonflybsd" do |machine|
    machine.vm.box = "generic/dragonflybsd6"
    ###machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.synced_folder "playbooks", "/ansible", type: "nfs"
    machine.vm.network "private_network", ip: "192.168.168.5"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Cleaning up...' && sudo hammer prune-everything /"
  end
  config.vm.define "openindiana" do |machine|
    machine.vm.box = "openindiana/hipster"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && pfexec pkg install ansible"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.provisioning_path = "/ansible"
    ansible.compatibility_mode = "2.0"
    ansible.verbose = false
  end

end
