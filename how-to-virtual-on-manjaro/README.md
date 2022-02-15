# How to create a virtual host on Manjaro using Apache (httpd)

Set host name on hosts

```
sudo nano /etc/hosts
```

After installed pacaur, now u can install debtap

```
pacaur -S debtap
```

With debtap installed execute the command below to init debtap

```
sudo debtap -u
```

Now is possible to convert .deb

```
debtap your_package.deb
```

And finally use pacman to install the converted pkg

```
sudo pacman -U your-converted-pakage.pkg.tar.zst
```
