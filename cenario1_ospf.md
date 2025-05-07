# 📡 Cenário 01 – Roteamento Dinâmico com OSPF / Dynamic Routing with FRR + OSPF

Neste cenário, usamos quatros servidores Ubuntu com FRRouting configurado para OSPF, compartilhando automaticamente rotas entre redes locais.

---

## 🧱 Topologia da Rede

![Topologia](images/minha-imagem.png)

---

## 🎯 Objetivo

- Instalar e habilitar o FRRouting (FRR)
- Configurar o daemon `ospfd` nos dois roteadores
- Anunciar redes locais via OSPF
- Verificar aprendizado dinâmico de rotas

---

## 📂 Arquivos de configuração

- `/etc/frr/daemons`  
  Ativar os serviços OSPF:
  ospfd=yes

- `/etc/frr/frr.conf`

```bash
!
router ospf
network 10.0.0.0/24 area 0
network 192.168.10.0/24 area 0
!
```

## 🔍 Verificações úteis:
```bash
vtysh -c "show ip ospf neighbor"
vtysh -c "show ip route ospf"
```

## ▶️ Execução via script
Utilize o script frr_startup.sh após instalar o FRR:
```bash
sudo bash frr_startup.sh
```
---

📘 Próximo passo sugerido

* Adicionar mais roteadores e áreas OSPF

* Simular queda de interface e failover
