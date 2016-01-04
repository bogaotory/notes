# notes
**Security**
*(RHEL/CentOS 7 64-Bit)*

```
# wget http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
# rpm -ivh epel-release-7-5.noarch.rpm
# yum repolist
# yum install fail2ban
# cat /etc/fail2ban/jail.conf
# vim /etc/fail2ban/jail.local
  [DEFAULT]
  bantime = 3600 # an hour
  findtime = 3600
  maxretry = 3
  
  [sshd]
  enabled = true
# systemctl start fail2ban
# systemctl enable fail2ban
# journalctl -lfu fail2ban
```
- [Enable EPEL repository](http://www.tecmint.com/how-to-enable-epel-repository-for-rhel-centos-6-5/)
- [Install fail2ban](http://unix.stackexchange.com/questions/171567/installing-fail2ban-on-centos-7)
```
# yum search sudo
# yum install sudo.x86_64
# visudo
Enable wheel group
# adduser user_name
# passwd user_name
# gpasswd -a user_name wheel
```
- [Sudo on CentOS](http://blog.zwiegnet.com/linux-server/add-user-to-sudoers-group-centos/)

**Docker on CentOS 7**
```
# yum update
# tee /etc/yum.repos.d/docker.repo <<-'EOF'
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/$releasever/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF
# yum install docker-engine
# service docker start
# docker run hello-world
# chkconfig docker on

# usermod -aG docker user_name
```
- [Install Docker on CentOS](https://docs.docker.com/engine/installation/centos/)
