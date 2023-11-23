# How to install .deb on manjaro (arch linux)

A good alternative is to see if yay has the package. simple install
```
pamac install yay
```
```
yay package-name
```
example with Google Chrome
```
yay google-chrome
```
The package that convert .deb is debtap, but it is only available on AUR.

Using **yay** u can install debtap

```
yay -S debtap
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
