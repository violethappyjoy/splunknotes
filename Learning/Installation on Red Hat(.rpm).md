ref.: [Installation Manual](https://docs.splunk.com/Documentation/Splunk/9.4.0/Installation/InstallonLinux)
1. Download RPM package using wget
2. If needed, change permission on the file.
   ```bash
   chmod 644 splunk_package_name.rpm
```
3. Invoke the following command to install the Splunk Enterprise RPM in the default directory `/opt/splunk`. 
   ```bash
   rpm -i splunk_package_name.rpm
```
4. (Optional) To install Splunk in a different directory, use the `--prefix` argument.)
   ```bash
   rpm -i --prefix=/<new_dir_prefix> splunk_package_name.rpm
```
### Replace an existing Splunk Enterprise installation with RPM package
Run `rpm` with the `--prefix` flag and reference the existing Splunk Enterprise directory.
```bash
rpm -i --replacepkgs --prefix=/splunkdirectory/ splunk_package_name.rpm
```
### Automate RPM installation with Red Hat Linux Kickstart
If you want to automate an RPM install with Kickstart, edit the kickstart file and add the following.
```Bash
./splunk start --accept-license
./splunk enable boot-start
```
boot-start line is optional
