# 🧪 LAB — VLAN Trunk e Native VLAN

## ⚠️ Aviso
Este laboratório **já está configurado**.  
Caso deseje refazê-lo, será necessário **wipar os nodes** antes de iniciar.

---

## 🎯 Objetivo do LAB
Configurar e validar a comunicação entre switches utilizando **trunking 802.1Q**, aplicando uma **Native VLAN** adequada, assegurando o funcionamento correto das VLANs de usuários e de gerenciamento.

<img width="1585" height="652" alt="Image" src="https://github.com/user-attachments/assets/b84513bb-c7f1-410c-9255-38e03af8ffc0" />

---

## ✅ Tarefas do LAB

### **1. Criar as VLANs**
- VLAN **10** – Recursos Humanos  
- VLAN **20** – Financeiro  
- VLAN **99** – Gerência (Native VLAN)

---

### **2. Associar as VLANs às portas**
- Configurar portas de **acesso** para as VLANs 10 e 20  

---

### **3. Configurar o Trunk entre os switches**
- Habilitar encapsulamento **802.1Q**  
- Configurar as portas de uplink como **trunk**  
- Permitir apenas as VLANs necessárias: **10, 20 e 99**

---

### **4. Definir a Native VLAN**
- Configurar a **VLAN 99** como Native VLAN  
- Evitar o uso da VLAN 1 conforme boas práticas de segurança

---

### **5. Testar conectividade**
- Verificar comunicação entre dispositivos pertencentes à **mesma VLAN** através do trunk  
- Validar a conectividade de gerenciamento via **VLAN 99**  
- Utilizar comandos de verificação (ex.: `show interfaces trunk`) para confirmar o estado do trunk

---

## 📌 Resultados Esperados
- Trunk **802.1Q** operacional  
- VLAN **99** configurada corretamente como Native VLAN  
- Comunicação funcional entre dispositivos de mesma VLAN  
- Rede segmentada de forma segura e adequada

