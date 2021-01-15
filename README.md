# DHCP Auto Install

By default, unconfigured Cisco IOS devices attempt to download a config file named router-confg or router.cfg (Autoinstall feature)

[Autoinstall Configuration guide reference](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/fundamentals/configuration/15mt/fundamentals-15-mt-book/cf-autoinstall.html
)

# Cisco Communities

https://community.cisco.com/t5/networking-documents/automated-workaround-for-cscvw63161/ta-p/4272812/show-comments/true#comment-on-this



# Router-config
In lab testing, we were able to successfully create the guest-share directory, and automatically reboot unconfigured cat9k switches with the following router-confg file that is loaded automatically by the device:

router-config:

```
file prompt quiet
do mkdir flash:guest-share
!
kron occurrence reload in 1 oneshot
policy-list reload
kron policy-list reload
cli reload
!
end
```

