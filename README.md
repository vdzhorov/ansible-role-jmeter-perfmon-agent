# jmeter-perfmon-agent

Role for installing Apache Jmeter perfmon agent on a target host. Read more at https://jmeter-plugins.org/wiki/PerfMon/.

## Prerequisites

- geerlingguy.java role

## Additional configuration

It is recommended to set the following properties for your Jmeter:

* jmeterPlugin.perfmon.interval - metrics collection interval in milliseconds
* jmeterPlugin.perfmon.useUDP - true/false, enabling UDP connection try after failed TCP connection attempt
* jmeterPlugin.perfmon.label.useHostname - true/false, enable using "short" hostnames, default pattern is ([\w\-]+)\..*
* jmeterPlugin.perfmon.label.useHostname.pattern - string (escaped), regular expression to extract hostname (first group is matched)
e.g. Default pattern would be: jmeterPlugin.perfmon.label.useHostname.pattern=([\w\-]+)\..*
e.g. Pattern for EC2 us-east/west subdomain matching: jmeterPlugin.perfmon.label.useHostname.pattern=([\w\-]+\.us-(east|west)-[0-9]).*
* forcePerfmonFile - true/false, enabling it makes JMeter to write JTL file with perfmon metrics in the current directory

Thse properties can be set in $JMETER_INSTALL_FOLDER/bin/jmeter.properties

### Deployment

Example playbook:

```
- hosts: java_app_servers
  roles:
    - 'vdzhorov.ansible-role-jmeter-perfmon-agent'
```

### Built With

* [Ansible 2.8](https://docs.ansible.com/ansible/2.8/index.html)

### Authors

* **Valentin Dzhorov** - *Initial work* - [vdzhorov](https://github.com/vdzhorov)

### Company

* **Delta.BG**

### License

This project is licensed under the MIT License.
