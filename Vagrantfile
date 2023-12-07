Vagrant.configure("2") do |config|
  config.vm.provision "ansible", type: "shell",
    inline: "echo Provisioning..."

  config.vm.synced_folder "playbooks", "/ansible"

  config.vm.define "alma9" do |machine|
    machine.vm.box = "generic/alma9"
  end
  config.vm.define "alma8" do |machine|
    machine.vm.box = "generic/alma8"
  end
  config.vm.define "centos9s" do |machine|
    machine.vm.box = "generic/centos9s"
  end
  config.vm.define "centos8s" do |machine|
    machine.vm.box = "generic/centos8s"
  end
  config.vm.define "centos7" do |machine|
    machine.vm.box = "generic/centos7"
  end
  config.vm.define "fedora39" do |machine|
    machine.vm.box = "bento/fedora-39"
  end
  config.vm.define "fedora38" do |machine|
    machine.vm.box = "bento/fedora-38"
  end
  config.vm.define "ubuntu2204" do |machine|
    machine.vm.box = "ubuntu/jammy64"
  end
  config.vm.define "ubuntu2004" do |machine|
    machine.vm.box = "ubuntu/focal64"
  end
  config.vm.define "debian12" do |machine|
    machine.vm.box = "bento/debian-12"
  end
  config.vm.define "debian11" do |machine|
    machine.vm.box = "bento/debian-11"
  end
  config.vm.define "debian10" do |machine|
    machine.vm.box = "bento/debian-10"
  end
  config.vm.define "opensuse15" do |machine|
    machine.vm.box = "generic/opensuse15"
  end
  config.vm.define "tumbleweed" do |machine|
    machine.vm.box = "opensuse/Tumbleweed.x86_64"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Updating repos...' && \
               sudo zypper --non-interactive --gpg-auto-import-keys refresh && \
               sudo zypper --non-interactive update"
  end
  config.vm.define "arch" do |machine|
    machine.vm.box = "archlinux/archlinux"
  end
  config.vm.define "alpine318" do |machine|
    machine.vm.box = "boxomatic/alpine-3.18"
  end
  config.vm.define "alpine317" do |machine|
    machine.vm.box = "generic/alpine317"
  end
  config.vm.define "alpine316" do |machine|
    machine.vm.box = "generic/alpine316"
  end
  config.vm.define "alpine315" do |machine|
    machine.vm.box = "generic/alpine315"
  end
  config.vm.define "freebsd13" do |machine|
    machine.vm.box = "generic/freebsd13"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y sysutils/ansible"
  end
  config.vm.define "freebsd12" do |machine|
    machine.vm.box = "generic/freebsd12"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo pkg install -y sysutils/ansible"
  end
  config.vm.define "openbsd" do |machine|
    machine.vm.box = "generic/openbsd7"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && sudo /usr/sbin/pkg_add -v ansible coreutils && sudo ln -s /usr/local/bin/gchown /usr/bin/chown"
  end
  config.vm.define "netbsd9" do |machine|
    machine.vm.box = "generic/netbsd9"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing ansible...' && \
               sudo pkgin -y update && \
               pkgin -y install ansible"
  end
  config.vm.define "netbsd8" do |machine|
    machine.vm.box = "generic/netbsd8"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Preparing NetBSD package manager...' && \
               VER=`uname -r` && \
               sudo sed -i \"s/8.0/$VER/\" /usr/pkg/etc/pkgin/repositories.conf && \
               sudo pkgin -y update && \
               echo 'Installing ansible python deps with pkgin...' && \
               sudo pkgin -y install py311-pip py311-jinja2 py311-markupsafe \
                             py311-yaml py311-cryptography py311-cffi \
                             py311-packaging py311-cparser py311-resolvelib && \
               echo 'Installing ansible with pip...' && \
               sudo pip3 install ansible && \
               echo 'export LANG=\"en_US.UTF-8\"' | sudo tee -a /etc/profile" 
  end
  config.vm.define "dragonflybsd" do |machine|
    machine.vm.box = "generic/dragonflybsd6"
    machine.vm.synced_folder "playbooks", "/ansible", type: "rsync"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Cleaning up...' && sudo hammer prune-everything / && \
               echo 'Installing ansible...' && sudo pkg install -y sysutils/ansible && \
               echo 'export LANG=\"en_US.UTF-8\"' | sudo tee -a /etc/profile"
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
