<h1 align="center">🌐 Protocolos de Roteamento</h1>
<p align="center">
  Laboratório de roteamento avançado com <strong>Ubuntu Server</strong>, focado em <strong>iproute2</strong>, <strong>iptables</strong>, <strong>FRRouting</strong> e práticas reais de redes para administradores Linux.
</p>

<p align="center">
  <a href="https://ubuntu.com/server"><img src="https://img.shields.io/badge/Linux-Ubuntu--Server-2c3e50?style=for-the-badge&logo=ubuntu&logoColor=white"/></a>
  <a href="https://man7.org/linux/man-pages/man8/ip.8.html"><img src="https://img.shields.io/badge/iproute2-Routing-blue?style=for-the-badge"/></a>
  <a href="https://netfilter.org/"><img src="https://img.shields.io/badge/iptables-NAT%20%26%20Firewall-red?style=for-the-badge"/></a>
  <a href="https://www.frrouting.org/"><img src="https://img.shields.io/badge/FRRouting-OSPF%2FBGP-green?style=for-the-badge"/></a>
  <a href="https://gns3.com/"><img src="https://img.shields.io/badge/GNS3-Network%20Emulator-orange?style=for-the-badge"/></a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Status-100%25%20Completed-brightgreen?style=for-the-badge&logo=github" alt="Project Status Badge"/>
</p>

---

## 🔍 Visão Geral / Lab Overview

Ambiente de laboratório voltado à prática de roteamento em Linux com múltiplos cenários reais, configurando NAT, PBR, e OSPF com ferramentas amplamente usadas na indústria.

A lab environment to practice Linux-based routing using real-world scenarios, configuring NAT, policy routing (PBR), and dynamic OSPF routing with market-relevant tools.

---

## 📁 Estrutura do Projeto / Project Structure

/advanced-linux-routing-lab/ │ ├── 📄 README.md │ ├── 📁 docs/ │ ├── 📄 scenario_01_static_routing.md │ ├── 📄 scenario_02_policy_routing.md │ ├── 📄 scenario_03_nat_gateway.md │ ├── 📄 scenario_04_frr_ospf.md │ ├── 📄 frr_installation.md │ ├── 📄 tools_installation.md │ ├── 📄 netplan_basics.md │ └── 📄 ascii_topologies.md │ ├── 📁 scripts/ │ ├── 📄 static_routing.sh │ ├── 📄 policy_routing.sh │ ├── 📄 nat_config.sh │ ├── 📄 frr_startup.sh │ └── 📄 README.md

---

## 📚 Índice de Conteúdo / Content Index

### ▶️ Documentação dos Cenários / Lab Scenarios

- [🗺️ Cenário 1 – Roteamento Estático](./docs/scenario_01_static_routing.md)
- [🧭 Cenário 2 – Roteamento com Políticas (PBR)](./docs/scenario_02_policy_routing.md)
- [🌐 Cenário 3 – NAT Gateway com iptables](./docs/scenario_03_nat_gateway.md)
- [📡 Cenário 4 – OSPF com FRRouting (Dinâmico)](./docs/scenario_04_frr_ospf.md)

### ⚙️ Instalações e Configuração / Installations & Setup

- [📥 Instalação do FRRouting (FRR)](./docs/frr_installation.md)
- [🔧 Instalação de Ferramentas de Diagnóstico](./docs/tools_installation.md)
- [🧷 Configuração de IP Estático com Netplan](./docs/netplan_basics.md)
- [🧱 Topologias ASCII](./docs/ascii_topologies.md)

### 🖥️ Scripts de Execução / Execution Scripts

- [`static_routing.sh`](./scripts/static_routing.sh) – Roteamento Estático
- [`policy_routing.sh`](./scripts/policy_routing.sh) – PBR (Policy-Based Routing)
- [`nat_config.sh`](./scripts/nat_config.sh) – NAT Gateway
- [`frr_startup.sh`](./scripts/frr_startup.sh) – Inicialização OSPF (FRR)

---

## 🧠 Tecnologias Utilizadas / Technologies Used

| Tecnologia         | Finalidade / Purpose                           |
|--------------------|--------------------------------------------------|
| `iproute2`          | Gerenciar rotas, regras e tabelas de roteamento |
| `iptables`          | NAT, redirecionamento e segurança de pacotes    |
| `FRRouting (FRR)`   | Protocolos dinâmicos: OSPF, BGP, RIP, etc.       |
| `Netplan`           | Configuração de IP estático no Ubuntu Server     |
| `iperf3`, `tcpdump` | Testes de tráfego e análise de pacotes           |

---

## ✅ Pré-requisitos

- Ubuntu Server (em VM ou bare metal)
- Pelo menos 2 NICs (virtuais ou físicas)
- VirtualBox, Proxmox ou similar
- Terminal com acesso sudo (ex: MobaXterm ou SSH)

---

## 🧩 Próximos Desafios / Next Steps

- Simular HA com múltiplos gateways
- Integrar firewall UFW com regras por interface
- Adicionar controle de banda por QoS (`tc`, `htb`)
- Monitorar rotas com Zabbix ou Prometheus

---

## 🧑‍💻 Autor / Author

<p align="center">
Desenvolvido e documentado por <a href="https://github.com/Emersoft76"><strong>@Emersoft76</strong></a><br/>
<em>Administrador de Redes com foco em ambientes Linux, roteamento e soluções modernas baseadas em nuvem e segurança.</em>
</p>
