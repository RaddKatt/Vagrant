# Example: Share an additional folder to the guest VM.
Add the following stanza to your Vagrantfile:
<pre>
# Share an additional folder to the guest VM. The first argument is
# the path on the host to the actual folder. The second argument is
# the path on the guest to mount the folder. And the optional third
# argument is a set of non-required options.
# config.vm.synced_folder "../data", "/vagrant_data"
<b>config.vm.synced_folder "opt","/opt"<b>
</pre>
