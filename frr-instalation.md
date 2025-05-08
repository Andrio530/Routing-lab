```markdown
# 🛠️ Instalação do FRRouting (FRR) no Ubuntu Server
```
---

## 1. Atualizar pacotes

No Ubuntu Server (toda as VMs):
```bash
sudo apt update
sudo apt install frr frr-ripd frr-ospfd
```
## 2. Ativar os daemons

Edite /etc/frr/daemons:
```bash
rip=yes
ospfd=yes
```
## 3. Criar arquivo de configuração inicial para toda as interfaces
   Use o comando ip a para descobrir as interfaces ativas:
```bash
ip a
```

Crie /etc/frr/frr.conf com:
```
sudo vtysh
frr version 8.4
frr defaults traditional
hostname router
log file /var/log/frr.log
!
c t
router ospf
interface enp0sX
ip address 10.0.X.0/24
!
router ospf
 network 10.0.X.0/24 area 0
!
end
!
```
## 4. Habilitar e iniciar
```
sudo systemctl enable frr
sudo systemctl start frr
```
## 5. Reiniciar
```
sudo systemctl restart frr
```
## 6. Verificar
```
vtysh -c "show ip route"
   
