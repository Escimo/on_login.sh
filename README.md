# Customize Login Screen for SSH Connections

## Ubuntu
Ubuntu makes this pretty easy. We can simply throw the above script into the directory `/etc/update-motd.d/`

```
sudo mv on_login.sh /etc/update-motd.d/05-info
sudo chmod +x /etc/update-motd.d/05-info
```

Once you log out and back in, we'll see that info!

## CentOS
CentOS takes just a little more work to setup.

We need to turn off (yes, off) SSH's PrintMotd option by editing `/etc/ssh/sshd_config` :
`
PrintMotd no
`

This stops printing from the plaintext /etc/motd and lets us print our own content.

We just need to restart sshd as so that takes affect:
```
sudo service sshd restart
```

Now we'll place our shell script into `/etc/profile.d`
```
sudo mv on_login.sh /etc/profile.d/login-info.sh
```
Then once we login, we'll see the output of our script!
