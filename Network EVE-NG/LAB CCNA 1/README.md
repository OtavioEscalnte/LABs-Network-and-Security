# 📘 Lab CCNA 1

O objetivo desse lab é registrar todas as configurações feitas nos dispositivos da topologia: **R1, R2, SW1, SW2, SW3, PC1, PC2 e Server**.

---

⚠️ **Aviso importante:** Para refazer o laboratório, é necessário **wipar os nodes** antes de iniciar novamente.

## 🗺️ Topologia
A topologia utilizada contém:
- **3 Switches:** SW1, SW2, SW3  
- **2 Roteadores:** R1 e R2  
- **Hosts:** PC1, PC2 e um Server  
- **Duas redes principais:**  
  - **192.168.100.0/24**  
  - **200.200.200.0/24**

---

# ✅ Etapas Realizadas

## 🔹 Task 1 — Configuração dos Hostnames e Domínio
Configurei em todos os dispositivos os respectivos nomes conforme a topologia:

- `SW1`, `SW2`, `SW3`, `R1`, `R2`

E defini o domínio padrão:

- `ip domain-name cln.com`
---

## 🔹 Task 2 — Configuração Manual do Clock em R1
Ajustei manualmente o relógio do roteador para garantir timestamps e logs corretos.

---

## 🔹 Task 3 — Configuração de IPs em R1, PC2 e Server

### **R1**
| Interface | IP | Máscara | Descrição |
|----------|-----------|---------------|-----------|
| fa0/0 | 192.168.100.1 | 255.255.255.0 | #REDE192# |
| fa1/0 | 200.200.200.1 | 255.255.255.0 | #REDE200# |

### **Hosts**
- **PC2:** `192.168.100.100/24`  
- **Server:** `200.200.200.100/24`

---

## 🔹 Task 4 — R1 como Servidor DHCP
Configurei o R1 como servidor DHCP para ambas as redes.

### Rede 192.168.100.0/24
- Pool: `192.168.100.200` → `192.168.100.254`  
- Default Gateway: `192.168.100.1`  
- DNS: `8.8.8.8`  

### Rede 200.200.200.0/24
- Pool: `200.200.200.200` → `200.200.200.254`  
- Default Gateway: `200.200.200.1`  
- DNS: `8.8.8.8`  

Configurei **PC1** e **R2** como clientes DHCP.

---

## 🔹 Task 5 — CDP
No R1:
- Ativei **CDP** globalmente    
- Desabilitei o CDP na interface conectada à rede `200.200.200.0/24` (fa1/0)

---

## 🔹 Task 6 — Interfaces de Gerenciamento dos Switches

| Dispositivo | IP | Gateway |
|-------------|----------------------|------------------|
| **SW1** | 192.168.100.50/24 | 192.168.100.1 |
| **SW2** | 192.168.100.51/24 | 192.168.100.1 |
| **SW3** | 200.200.200.50/24 | 200.200.200.1 |

Configurações aplicadas na VLAN 1 em cada switch.

---

## 🔹 Task 7 — SSHv2 em R1, R2

Configurações aplicadas:
- Apenas **SSHv2**
- Usuário: `CCNA`
- Senha Secret: `cisco`
- Timeout: **60s**
- Retries: **2**
- Senha do modo enable: `cisco123`

---

## 🔹 Task 8 — Console Seguro em R1
Configurei o console do R1 para usar autenticação com o usuário criado anteriormente.

---

## 🔹 Task 9 — Ajustes Administrativos em R1
No R1:

- Banner MOTD
- Desabilitei o **exec-timeout** no console e no SSH  
- Ativei **logging synchronous**  
