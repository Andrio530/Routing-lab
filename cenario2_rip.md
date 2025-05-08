# Cenário 2 – RIP com FRR Routing

## 🧱 Topologia da Rede

A topologia segue conforme a que descrita dentro do `README.md`.
---

## 🎯 Objetivo
- Implementar e analisar o protocolo RIP com FRRouting (FRR)
- em uma topologia com múltiplos caminhos, testando reconvergência,
- tabelas de roteamento, pacotes de atualização e comportamento em falhas.
---

# ⚙️ Configuração do FRR - RIP

---
# Etapa 1: Habilitar o daemon RIP no arquivo `/etc/frr/daemons` 
```bash
sudo nano /etc/frr/daemons
```
# Altere: ripd=no → ripd=yes

# Reinicie o serviço do FRR
```bash
sudo systemctl restart frr
```
# Etapa 2: Configuração dos roteadores no VTYSH

# ---------- 🖥️ R1 ----------
```bash
vtysh
configure terminal
hostname R1
interface enp0s3
 ip address 10.0.12.1/24
 no shutdown
interface enp0s8
 ip address 10.0.14.1/24
 no shutdown
router rip
 network 10.0.12.0/24
 network 10.0.14.0/24
exit
write
exit
```

# ---------- 🖥️ R2 ----------
```bash
vtysh
configure terminal
hostname R2
interface enp0s3
 ip address 10.0.12.2/24
 no shutdown
interface enp0s8
 ip address 10.0.23.1/24
 no shutdown
interface enp0s9
 ip address 10.0.24.2/24
 no shutdown
router rip
 network 10.0.12.0/24
 network 10.0.23.0/24
 network 10.0.24.0/24
exit
write
exit
```
# ---------- 🖥️ R3 ----------
```bash
vtysh
configure terminal
hostname R3
interface enp0s3
 ip address 10.0.23.2/24
 no shutdown
router rip
 network 10.0.23.0/24
exit
write
exit
```
# ---------- 🖥️ R4 ----------
```bash
vtysh
configure terminal
hostname R4
interface enp0s3
 ip address 10.0.14.2/24
 no shutdown
interface enp0s8
 ip address 10.0.24.1/24
 no shutdown
router rip
 network 10.0.14.0/24
 network 10.0.24.0/24
exit
write
exit
```
---
# 📊 Métricas para avaliação
---

# ➤ Ver tabela de roteamento:
```bash
vtysh -c 'show ip route'
```

# ➤ Monitorar pacotes de atualização RIP:
```bash
vtysh
debug rip events
debug rip packet
```

# ➤ Delay / reconvergência:
# Desligue interface para simular falha e veja a reação do RIP:
```bash
sudo ip link set dev enp0s3 down
ping 10.0.23.2
traceroute 10.0.23.2
```

# ➤ Ver taxa de transmissão por interface (sem instalar nada):
```bash
ip -s link show enp0s3
```

---
# 🧪 Testes realizados
---
# - Interface entre R1 e R2 foi desligada
# - Reconvergência foi observada pelo novo caminho via R4
# - Tempo de resposta medido com ping e traceroute
# - Pacotes RIP observados com debug

# ------------------------------------------
# 📁 Estrutura do repoistório
# ------------------------------------------
# Routing-lab/
# ├── cenario1_ospf.md
# ├── cenario2_rip.md  ← (este arquivo)
# └── topologia.png
