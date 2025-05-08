# 📡 Cenário 01 – Roteamento Dinâmico com OSPF / Dynamic Routing with FRR + OSPF

Neste cenário, usamos quatros servidores Ubuntu com FRRouting configurado para OSPF, compartilhando automaticamente rotas entre redes locais.

---

## 🧱 Topologia da Rede

A topologia segue conforme a que descrita dentro do `README.md`.
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
Habilitar ipv4.forward para todos os roteadores
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

## ▶️ Tempo de convergência (Simulação de queda)
Utilize o ping para verificar se há comunicação:
```bash
ping 10.0.X.X
```
---
Em um roteador visualize as interfaces com a tabela dos ips de comunicação:
```bash
watch -n 1 ip route
```
Em outro roteador derrube uma das interfaces de comunicação e verifique a tabela:
```bash
sudo ip link set enp0sX down
```
Reconecte o link e meça o tempo até a conexão voltar :
```bash
sudo ip link set enp0sX up
```

## ▶️ Tamanho da tabela de roteamento
Verifique a tabela de roteamento:
```bash
ip route
```
---
Contabilize a quantidade de linhas que aparecem na tabela.

## ▶️ Delay
Verificar o tempo de entrega do pacote:
```bash
traceroute 10.0.X.X
```
---
O comando retorna os hops e o delay.

## ▶️ Quantidade de pacotes e bytes
Verificar a quantidade de pacotes e o tamanho por interface:
```bash
ip -s link
```
---


