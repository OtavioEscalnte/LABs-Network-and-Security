# 📘 CCNA LAB 2

Este repositório documenta os passos realizados para a resolução das tarefas do workbook de *Yasser Ramzy Auda – CCIE# 45694 / CCSI# 34215*.  
O objetivo é registrar todas as configurações aplicadas nos dispositivos da topologia: **R1, SW1, SW2, PC1, PC2, PC3 e PC4**.

<img width="950" height="625" alt="Image" src="https://github.com/user-attachments/assets/f04bd07d-8c26-4b33-9535-4aadb4b1eb12" />
---

# ✅ Etapas Realizadas

## 🔹 Task 1 — Hostnames e Domínio
Configurei o hostname de todos os dispositivos conforme a topologia:

- R1  
- SW1  
- SW2  

E defini o domínio:

- CLN.com


---

## 🔹 Task 2 — Criação das VLANs em SW1 e SW2

Criei as seguintes VLANs em **ambos os switches**:

| VLAN ID | Nome      |
|---------|-----------|
| 2       | VENDAS    |
| 3       | TI        |
| 999     | SEM-USO    |

---

## 🔹 Task 3 — Associação das Interfaces às VLANs
Associação dos PCs às VLANs conforme a tabela:

| PC  | VLAN |
|-----|------|
| PC1 | 2 |
| PC2 | 3 |
| PC3 | 2 |
| PC4 | 3 |

As portas correspondentes nos switches foram configuradas como **access** e atribuídas aos respectivos IDs.

---

## 🔹 Task 4 — Trunks
Configurei interfaces trunk nos seguintes enlaces:

- **SW1 ↔ SW2**  
- **SW1 ↔ R1**

Os trunks utilizam protocolo **802.1Q**, permitindo apenas as VLANs relevantes.

---

## 🔹 Task 5 — Hardening das portas não utilizadas
Em **SW1** e **SW2**:

- Todas as interfaces não utilizadas foram colocadas na VLAN **999 (SEM-USO)**
- E foram **shutdown** para reforçar a segurança da camada 2

---

## 🔹 Task 6 — Router-on-a-Stick no R1
Configurei o **R1** como Router on Stick, criando subinterfaces para atuar como default gateway das VLANs:

- VLAN 2 → Gateway: `2.0.0.1`
- VLAN 3 → Gateway: `3.0.0.1`

Cada subinterface recebeu encapsulamento **802.1Q** correspondente.

---

## 🔹 Task 7 — R1 como Servidor DHCP
Configurei o **R1** como servidor DHCP para todos os PCs:

| PC  | IP            | Máscara      | Gateway      | VLAN |
|-----|---------------|--------------|--------------|------|
| PC1 | 2.0.0.100     | 255.0.0.0    | 2.0.0.1      | 2 |
| PC2 | 3.0.0.100     | 255.0.0.0    | 3.0.0.1      | 3 |
| PC3 | 2.0.0.200     | 255.0.0.0    | 2.0.0.1      | 2 |
| PC4 | 3.0.0.200     | 255.0.0.0    | 3.0.0.1      | 3 |

Criei dois escopos DHCP:

### 🔸 VLAN 2 (VENDAS)
- Pool da rede `2.0.0.0/8`
- Endereços reservados conforme PCs  
- Default Gateway: `2.0.0.1`

### 🔸 VLAN 3 (TI)
- Pool da rede `3.0.0.0/8`
- Endereços reservados conforme PCs  
- Default Gateway: `3.0.0.1`
