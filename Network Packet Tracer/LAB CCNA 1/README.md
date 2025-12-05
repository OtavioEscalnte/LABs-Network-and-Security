# 🧪 CCNA LAB 1

Foi utilizado como referência o workbook de: **Yasser Ramzy Auda – CCIE# 45694 | CCSI# 34215**  

---
<img width="1345" height="440" alt="Image" src="https://github.com/user-attachments/assets/bcdc67c8-b8d2-4c4d-b8d3-3f4538841a71" />

## 🔧 Configurações por dispositivo

### R1
- Hostname: **R1**; domínio: **cln.com**.
- Interfaces:
  - Gig0/0: IPv4 **10.0.0.1/8** — IPv6 **2001:1:1:1::1/64**.
  - Gig0/1: IPv4 **11.0.0.1/8** — IPv6 **2001:2:2:2::1/64**.
- Roteamento dinâmico: **OSPFv2** (process-id 1, área 51) com Router-ID **1.1.1.1**; redes IPv4 locais anunciadas na área 51.
- Rotas IPv6 estáticas adicionadas para alcançar redes remotas (next-hops via R2 conforme topologia).
- NTP: apontado para **12.0.0.100**.
- Backup: running-config copiada para servidor **TFTP 12.0.0.100** (arquivo salvo como referência).

### R2
- Hostname: **R2**; domínio: **cln.com**.
- Interfaces:
  - Gig0/0: IPv4 **12.0.0.2/8** — IPv6 **2001:3:3:3::2/64**.
  - Gig0/1: IPv4 **11.0.0.2/8** — IPv6 **2001:2:2:2::2/64**.
- Roteamento dinâmico: **OSPFv2** (process-id 1, área 51) com Router-ID **2.2.2.2**; redes IPv4 locais anunciadas.
- Rotas IPv6 estáticas configuradas para alcançar a rede do R1 e outras redes do laboratório.
- NTP: apontado para **12.0.0.100**.

### R3
- Hostname: **R3**; domínio: **cln.com**.
- Interfaces:
  - Gig0/0: IPv4 **10.0.0.3/8** — IPv6 **2001:1:1:1::3/64**.
- Roteamento dinâmico: **OSPFv2** (process-id 1, área 51) com Router-ID **3.3.3.3**; redes IPv4 locais anunciadas.
- **Rota default IPv6** configurada em R3 apontando para o R1 (garante saída para destinos IPv6 fora do seu segmento).
- NTP: apontado para **12.0.0.100**.

### PC1
- IPv4: **10.0.0.100/8** (gateway na interface de R1/R3 conforme topologia).
- IPv6: **2001:1:1:1::100/64**.
- Usado para testes de conectividade dentro da rede 10.0.0.0/8 e 2001:1:1:1::/64.

### Server
- IPv4: **12.0.0.100/8**.
- IPv6: **2001:3:3:3::100/64**.
- Serviços: servidor TFTP e servidor NTP (endereço usado por todos os roteadores: **12.0.0.100**).

---

## 🔁 Roteamento e Protocolos
- **OSPFv2** implementado em todos os roteadores:
  - Process ID: **1**
  - Área: **51**
  - Router-IDs: R1=**1.1.1.1**, R2=**2.2.2.2**, R3=**3.3.3.3**
  - Todas as redes IPv4 locais foram anunciadas na área 51 para troca de rotas internas.
- **Rotas IPv6**:
  - R3: rota default IPv6 (`::/0`) apontando para R1.
  - R1 e R2: rotas estáticas IPv6 para alcançar redes remotas, garantindo reachability entre segmentos IPv6.
- Observação: OSPFv2 foi usado apenas para IPv4 (não foi implementado OSPFv3 neste lab).

---

## 🗂️ Serviços e Operações
- **TFTP**: servidor em **12.0.0.100** usado para backup remoto da configuração (running-config) do R1.
- **NTP**: servidor de tempo em **12.0.0.100** configurado em todos os roteadores para sincronização de relógio e timestamps.
- **Domain Name**: domínio configurado como **cln.com** para padronização.



