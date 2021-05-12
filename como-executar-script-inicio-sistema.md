# Como executar shell script no inicio do sistema
Abrir o crontab
```
sudo crontab -e
```
Colocar na ultima linha 
```
@reboot /etc/init.d/script.sh
```
Depois criar script no init.d
```
sudo nano /etc/init.d/script.sh
```
inserir dentro o código
```sh
#!/bin/sh
echo "teste"
```
em seguida torna script executavel
```
sudo chmod +x /etc/init.d/script.sh
```
