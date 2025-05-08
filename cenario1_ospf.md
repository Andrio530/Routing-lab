# 📡 Cenário 01 – Roteamento Dinâmico com OSPF / Dynamic Routing with FRR + OSPF

Neste cenário, usamos quatros servidores Ubuntu com FRRouting configurado para OSPF, compartilhando automaticamente rotas entre redes locais.

---

## 🧱 Topologia da Rede

![Topologia](Topologia.png)

---

## 🎯 Objetivo

- Instalar e habilitar o FRRouting (FRR)
- Configurar o daemon `ospfd` nos quatros roteadores
- Anunciar redes locais via OSPF
- Verificar aprendizado dinâmico de rotas

---

## 📂 Arquivos de configuração

- `/etc/frr/daemons`  
  Ativar os serviços OSPF:
  ospfd=yes

- `/etc/frr/frr.conf`

Configuração Router 1
```bash
!
sudo vtysh
configure terminal
router ospf
interface enp0s3
ip address 10.0.12.1/24
interface enp0s8
ip address 10.0.14.1/24
exit
network 10.0.12.0/24 area 0
network 10.0.14.0/24 area 0
end
!
```

Configuração Router 2
```bash
!
sudo vtysh
configure terminal
router ospf
interface enp0s3
ip address 10.0.12.2/24
interface enp0s8
ip address 10.0.23.1/24
interface enp0s9
ip address 10.0.24.1/24
exit
network 10.0.12.0/24 area 0
network 10.0.23.0/24 area 0
network 10.0.24.0/24 area 0
end
!
```

Configuração Router 3
```bash
!
sudo vtysh
configure terminal
router ospf
interface enp0s3
ip address 10.0.23.2/24
exit
network 10.0.23.0/24 area 0
end
!
```
Configuração Router 4
```bash
!
sudo vtysh
configure terminal
router ospf
interface enp0s3
ip address 10.0.14.2/24
interface enp0s8
ip address 10.0.24.2/24
exit
network 10.0.14.0/24 area 0
network 10.0.24.0/24 area 0
end
!
```
Habilitar ipv4.forward
Para cada roteador habilitar o ipv4.forward
```bash
!
sudo sysctl net.ipv4.ip_forward=1
!
```

## 🔍 Verificações úteis para tabelas de roteamento e conexões vizinhas:
```bash
vtysh -c "show ip ospf neighbor"
vtysh -c "show ip route ospf"
```

## ▶️ Reinicialização do FRR
Reinicialize cada roteador posteriormente configuração:
```bash
systemctl restart frr
```
---

📘 Próximo passo sugerido

* Adicionar mais roteadores e áreas OSPF

* Simular queda de interface e failover
