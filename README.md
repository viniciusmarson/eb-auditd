# Auditd in Elastic Beanstalk 

This repository contains the Elastic Beanstalk extensions configuration to install and configure auditd.


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

So I added in my audit_service.config the command to create the auditd folder
