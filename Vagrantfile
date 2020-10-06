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
  config.vm.define "fedora32" do |machine|
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
  config.vm.define "opensuse15" do |machine|
    machine.vm.box = "generic/opensuse15"
  end
  config.vm.define "arch" do |machine|
    machine.vm.box = "generic/arch"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pacman -Sy archlinux-keyring --noconfirm"
  end
  config.vm.define "alpine" do |machine|
    machine.vm.box = "generic/alpine312"
  end
  config.vm.define "freebsd11" do |machine|
    machine.vm.box = "generic/freebsd11"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y py37-ansible"
  end
  config.vm.define "freebsd12" do |machine|
    machine.vm.box = "generic/freebsd12"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y py37-ansible"
  end
  config.vm.define "openbsd" do |machine|
    machine.vm.box = "generic/openbsd6"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo /usr/sbin/pkg_add -v ansible"
  end
  config.vm.define "netbsd8" do |machine|
    machine.vm.box = "generic/netbsd8"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkgin -y update && pkgin -y install ansible"
  end
  config.vm.define "dragonflybsd" do |machine|
    machine.vm.box = "generic/dragonflybsd5"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Cleaning up...' && sudo hammer prune-everything /"
  end
  config.vm.define "openindiana" do |machine|
    machine.vm.box = "Toasterson/openindiana-hipster"
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
