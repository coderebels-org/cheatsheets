# Create a sftp-only user restricted to home directory

(works on linux servers)

Configures a group "sftponly", a user of this group,
prohibit shell login and limit to his home directory.
Contents of this directory are assigned to the user
and in .ssh/authorized_keys put the PubKey of the user.

# First add the configuration to sshd_config:

    $ vi /etc/ssh/sshd_config

```
# >>>>>>>>>>>>>>>>>>>>>>>
# This section must be placed at the very end of sshd_config
Match Group sftponly
    ChrootDirectory %h
    ForceCommand internal-sftp
    AllowTcpForwarding no
# <<<<<<<<<<<<<<<<<<<<<<<
```

restart ssh service

    $ service ssh restart

add the group:

    $ groupadd sftponly

The following steps are necessary for each user, example user is 'vtest'
    
```
$ useradd vtest
$ usermod vtest -g sftponly
$ usermod vtest -s /bin/false
$ usermod vtest -d /var/www/virttest
$ cd /var/www/virttest/
$ chown -R vtest *                   (or restrict to some files/directories)
```
Finally place user's pubkey in file authorized_keys

```
$ mkdir .ssh
$ cd .ssh/
$ vi authorized_keys  >>>>>>>>>>> Insert vtest's pubkey!
```
