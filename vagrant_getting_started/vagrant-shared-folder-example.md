# Shared Folder
Vagrant can easily share folders between the localhost and VM, so you can use all the development tools that you like to use from your localhost, without having to add them to your virtual machine.

## Default Shared Folder
By default, main Vagrant folder on your localhost (folder which contains your Vagrantfile) is shared on your VM in the folder `/vagrant`.

On Localhost:
<pre>
$ pwd
/Vagrant/vagrant_getting_started/boxes/ubuntu/xenial64
$ ls -l
total 96
-rw-r--r--  1 mradka  110264095   3063 Mar 30 09:20 Vagrantfile
-rw-------  1 mradka  110264095  41097 Mar 30 09:21 ubuntu-xenial-16.04-cloudimg-console.log
</pre>

On Vagrant VM:
<pre>
$ vagrant ssh
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-143-generic x86_64)
<b>vagrant@ubuntu-xenial:~$ ls -l /vagrant/</b>
total 48
-rw------- 1 vagrant vagrant 41097 Mar 30 16:21 ubuntu-xenial-16.04-cloudimg-console.log
-rw-r--r-- 1 vagrant vagrant  3063 Mar 30 16:20 Vagrantfile
</pre>

## Example: Add a Shared Folder

<ol>
  <li>
    To add a shared folder, create a new stanza in your Vagrantfile, `config.vm.synced_folder`. The first argument is the directory on the local machine, and the second argument is where the shared folder will live on the VM:<br />
    <code>$ vim Vagrantfile</code><br /><br />
    <pre>
    # Share an additional folder to the guest VM. The first argument is
    # the path on the host to the actual folder. The second argument is
    # the path on the guest to mount the folder. And the optional third
    # argument is a set of non-required options.
    # config.vm.synced_folder "../data", "/vagrant_data"
    <b>config.vm.synced_folder "opt","/opt"</b></pre></li>
  <li>
    Stuff
  </li>
</ol>
