# Como executar serviço em segundo plano (Ex. nodejs)

Na primeira linha do arquivo principal é preciso inserir
```
#!/usr/bin/env node
```
Para executar em segundo plano é preciso criar um serviço no daemon

```
sudo nano /etc/systemd/system/myapp.service
```

e dentro do arquivo inserir o código
  
```shell
[Unit]
Deion=descricao myapp

[Service]
ExecStart=/path/to/myapp/index.js
Restart=always
User=nobody
Group=nogroup
Environment=PATH=/usr/bin:/usr/local/bin
Environment=NODE_ENV=production
WorkingDirectory=/path/to/myapp

[Install]
WantedBy=multi-user.target
```
> Salvar: ctrl + o

> Sair: ctrl + x

Depois de ter salvo o serviço, reinicie o daemon

```
sudo systemctl daemon-reload
```
em seguida inicie o serviço
```
sudo systemctl start livmqtt
```
depois é preciso habilitar o serviço para iniciar junto com o início do sistema
```
sudo systemctl enable livmqtt
```
para os logs
```
journalctl -u myapp
```
para ver as portas em uso
```
sudo netstat -tulpn | grep LISTEN
```
