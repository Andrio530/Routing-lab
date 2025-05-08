<h1 align="center">🌐 Protocolos de Roteamento</h1>
<p align="center">
  Laboratório de roteamento avançado com <strong>Ubuntu Server</strong>, focado em <strong>FRRouting</strong> e práticas reais de redes para administradores Linux.
</p>

<p align="center">
  <a href="https://ubuntu.com/server"><img src="https://img.shields.io/badge/Linux-Ubuntu--Server-2c3e50?style=for-the-badge&logo=ubuntu&logoColor=white"/></a>
  <a href="https://netfilter.org/"><img src="https://img.shields.io/badge/iptables-NAT%20%26%20Firewall-red?style=for-the-badge"/></a>
  <a href="https://www.frrouting.org/"><img src="https://img.shields.io/badge/FRRouting-OSPF%20RIP-green?style=for-the-badge"/></a>
  <a href="https://www.virtualbox.org/"><img src="https://img.shields.io/badge/VirtualBox-Network%20Emulator-orange?style=for-the-badge"/></a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Status-100%25%20Completed-brightgreen?style=for-the-badge&logo=github" alt="Project Status Badge"/>
</p>

---

## 🔍 Visão Geral / Lab Overview

Ambiente de laboratório voltado à prática de roteamento em Linux com múltiplos cenários reais, configurando OSPF e RIP.
---

## 📁 Estrutura do Projeto

/routing-lab/ │ ├── 📄 README.md │ ├── 📄 cenario1_ospf.md │ ├── 📄 cenario2_rip.md │ ├── 📄 frr-instalation.md │ ├── 📄 Topologia.md │
---

## 📚 Índice de Conteúdo 

### ▶️ Documentação dos Cenários

- [🌐 Cenário 1 – OSPF com FRRouting (Dinâmico)](./cenario1_ospf.md)
- [📡 Cenário 2 – RIP com FRRouting (Dinâmico)](./cenario2_rip.md)

### ⚙️ Instalação, Configuração e Topologia

- [📥 Instalação do FRRouting (FRR)](./frr-instalation.md)
- [🧱 Topologia](./Topologia.md)
---

## 🧠 Tecnologias Utilizadas / Technologies Used

| Tecnologia         | Finalidade / Purpose                           |
|--------------------|--------------------------------------------------|
| `FRRouting (FRR)`   | Protocolos dinâmicos: OSPF, BGP, RIP, etc.       |
| `traceroute`, `tcpdump` | Testes de tráfego e análise de pacotes           |

---

## ✅ Pré-requisitos

- Ubuntu Server (em VM)
- Pelo menos 2 NICs (virtuais ou físicas)
- VirtualBox, Proxmox ou similar
- Terminal com acesso sudo (ex: MobaXterm ou SSH)

---

## 🧑‍💻 Autor / Author

<p align="center">
Desenvolvido e documentado por <a href="https://github.com/Andrio530"><strong>@Andrio530</strong></a><br/>
</p>
