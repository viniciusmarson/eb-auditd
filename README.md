# Auditd in Elastic Beanstalk 

This repository contains the Elastic Beanstalk extensions configuration to install and configure auditd.

##### [00_auditd_packages.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/00_auditd_packages.config)

Install auditd 

##### [01_auditd_log_aws_conole.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/01_auditd_log_aws_conole.config)

Add the auditd log file in the Elastic Beanstalk log console


##### [02_auditd_conf.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/02_auditd_conf.config)

Overwrite the auditd configuration

##### [03_auditd_rules.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/03_auditd_rules.config)

Create auditd rules file

##### [04_auditd_commands.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/04_auditd_commands.config)

Run some commands to ensure that audid will run in a new instance

##### [05_auditd_service.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/05_auditd_service.config)

Configure EB to monitor the auditd to ensure that it is always running


&nbsp;
### Some errors that I had 

When I started to configure my auditd I was having the following error:

```sh
Starting auditd:                    [FAILED]
```

I could found the origin of this error in:

```sh
/var/log/messages
```

The reason of the error ? auditd did not create the log folder:

```sh
/var/log/auditd
```

So I added in my [04_auditd_commands.config](https://github.com/viniciusmarson/eb-auditd/blob/master/.ebextensions/04_auditd_commands.config) the command to create the auditd folder
