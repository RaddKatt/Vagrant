# Shared Folder
Vagrant can easily share folders between the localhost and VM, so you can use all the development tools that you like to use from your localhost, without having to add them to your virtual machine.

* [Default Shared Folder](#default-shared-folder)
* [Example: Add a Shared Folder](#example-add-a-shared-folder)
* [Disable the Default Shared Folder](#disable-the-default-shared-folder)

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
    To add a shared folder, first create a new stanza in your Vagrantfile, <code>config.vm.synced_folder</code>. The first argument is the directory on the local machine, and the second argument is where the shared folder will live on the VM:<br /><br />
    <code><b>$ vim Vagrantfile</b></code>
    <pre>
    # Share an additional folder to the guest VM. The first argument is
    # the path on the host to the actual folder. The second argument is
    # the path on the guest to mount the folder. And the optional third
    # argument is a set of non-required options.
    # config.vm.synced_folder "../data", "/vagrant_data"
    <b>config.vm.synced_folder "opt", "/opt"</b></pre></li>
  <li>
    To apply the changes, you must restart the VM. To do this, Vagrant has the command <code>vagrant reload</code>:<br /><br />
    <pre><b>$ vagrant reload</b>
    ==> default: Attempting graceful shutdown of VM...
    ==> default: Checking if box 'ubuntu/xenial64' version '20190325.0.0' is up to date...
    ==> default: Clearing any previously set forwarded ports...
    ...
    ==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
    ==> default: flag to force provisioning. Provisioners marked to run always will still run.</pre>
  </li>
  <li>
  To verify the shared folder, connect to your Vagrant VM and check the folder location. It should match the new local folder you created:
  <pre>
  <b>$ vagrant ssh</b>
    Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-143-generic x86_64)
    ...
  <b>vagrant@ubuntu-xenial:~$ ls -l /opt</b>
    total 4
    -rw-r--r-- 1 vagrant vagrant 47 Mar 30 17:03 test.txt</pre>
  </pre>
  </li>
</ol>

## Disable the Default Shared Folder
If you would like to disable the default Vagrant shared folder, `/vagrant`, you may do so by adding this stanza to your Vagrantfile with a third argument, `disabled: true`:<br /><br />
<code><b>$ vim Vagrantfile</b></code>
<pre>
# Share an additional folder to the guest VM. The first argument is
# the path on the host to the actual folder. The second argument is
# the path on the guest to mount the folder. And the optional third
# argument is a set of non-required options.
# config.vm.synced_folder "../data", "/vagrant_data"
<b>config.vm.synced_folder ".", "/vagrant", disabled: true</b>
config.vm.synced_folder "opt", "/opt"</pre>
