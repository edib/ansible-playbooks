# ansible-playbooks
created/edited/improved ansible playbooks.

Ubuntu 14.04 and 16.04 system referenced.

```
# sudo pip install pysphere
```
If you use self signed ssl sertificate on vcenter server, you may not pass the following error.


"SSLError: ("bad handshake: Error([('SSL routines', 'ssl3_get_server_certificate', 'certificate verify failed')],)",)
"
then you have to do the following workaround for pysphere module.

```
# vi /usr/lib/python2.7/dist-packages/ansible/modules/core/cloud/vmware/vsphere_guest.py
```

add these lines after first comment block.
```
import requests, ssl
requests.packages.urllib3.disable_warnings()
try:
     _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
     pass
else:
     ssl._create_default_https_context = _create_unverified_https_context
```

vmware osid reference:
https://www.vmware.com/support/developer/vc-sdk/visdk2xpubs/ReferenceGuide/vim.vm.GuestOsDescriptor.GuestOsIdentifier.html
