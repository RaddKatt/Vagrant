# Example: Shared Folder
Vagrant can be configured to easily share folders between the local host and VM, so you can use all the development tools that you like to use on your localhost, without having to add them to your virtual machine.

To add a shared folder, create a new stanza in your Vagrantfile:
<pre>
# Share an additional folder to the guest VM. The first argument is
# the path on the host to the actual folder. The second argument is
# the path on the guest to mount the folder. And the optional third
# argument is a set of non-required options.
# config.vm.synced_folder "../data", "/vagrant_data"
<b>config.vm.synced_folder "opt","/opt"</b>
</pre>
