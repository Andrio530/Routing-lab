# Configuração de Rede no VirtualBox para Laboratório de Roteamento

## 🎯 Objetivo
Esta documentação explica passo a passo como configurar as **interfaces de rede** no VirtualBox para replicar a topologia de roteadores Linux (FRR).

---

## 1. Criar as VMs

1. Abra o VirtualBox e clique em **“New”**.  
2. Nomeie como `R1`, escolha **Linux / Ubuntu (64-bit)**.  
3. Aloque ≥512 MB RAM, 1 CPU, disco ≥2 GB.  
4. Repita para `R2`, `R3`, `R4`.

---

## 2. Modos de Rede

| Adapter | Modo          | Uso                                     | Configuração no VBoxManage                           |
|:-------:|:--------------|:----------------------------------------|:------------------------------------------------------|
| enp0s3  | Internal Network | Conexão **R1↔R2**, **R2↔R3**, **R1↔R4**, **R2↔R4** :contentReference[oaicite:10]{index=10} | `VBoxManage modifyvm R1 --nic1 intnet --intnet1 labnet` |
| (opcional) | NAT          | Acesso à Internet, sem afetar rotas internas :contentReference[oaicite:12]{index=12} | `VBoxManage modifyvm R1 --nic3 nat`                   |

> **Nota:** use o mesmo **Internal Network name** (`labnet`) em todas as VMs para que as interfaces se enxerguem.

---

## 3. Atribuir Interfaces por Roteador

### R1
- **Adapter 1 (enp0s3):** Internal Network `net12`  
- **Adapter 2 (enp0s8):** Internal Network `net14`

### R2
- **Adapter 1 (enp0s3):** Internal Network `net12`  
- **Adapter 2 (enp0s8):** Internal Network `net23`  
- **Adapter 3 (enp0s9):** Internal Network `net24`

### R3
- **Adapter 1 (enp0s3):** Internal Network `net23`  

### R4
- **Adapter 1 (enp0s3):** Internal Network `net14`  
- **Adapter 2 (enp0s8):** Internal Network `net24`

---

## 4. Ajustes no Ubuntu (Netplan)

Edite `/etc/netplan/01-netcfg.yaml` em cada VM:

```yaml
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: no
      addresses: [<IP>/24]
    enp0s8:
      dhcp4: no
      addresses: [<IP>/24]
