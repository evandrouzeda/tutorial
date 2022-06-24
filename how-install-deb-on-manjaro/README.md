# How to install .deb on manjaro (arch linux)

A good alternative is to see if yay has the package. simple install
```
pamac install yay
```
```
yay package-name
```

The package that convert .deb is debtap, but it is only available on AUR.
So first u'll need to install pacaur

```
sudo pacman -S pacaur
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
