ref.: [Installation Manual](https://docs.splunk.com/Documentation/Splunk/9.4.0/Installation/InstallonLinux)
1. Expand the tar file into an appropriate directory using the `tar` command:
```bash
   tar xvzf splunk_package_name.tgz
```
2. The default installation directory is `splunk` in the current working directory. To install into `/opt/splunk`, use the following command:
   ```bash
   tar xvzf splunk_package_name.tgz -C /opt
```