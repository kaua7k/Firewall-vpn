# 🔥 Firewall com pfSense + VPN

## 📌 Visão Geral
Este projeto demonstra a implementação de um **firewall avançado** utilizando o **pfSense**, com a configuração de uma **VPN site-to-site** para comunicação segura entre redes remotas. O objetivo é garantir **segurança, controle de tráfego e criptografia** de dados para conexões externas.

## 🛠️ Tecnologias Utilizadas
- 🏢 **pfSense** - Firewall e roteamento
- 🔒 **OpenVPN/IPSec** - Conexão VPN segura
- 🌐 **Regras de Firewall e NAT** - Controle de tráfego
- 📊 **Monitoramento e Logs** - Análise de pacotes

---

## 📜 Arquitetura da Rede

🔹 **Rede Local (LAN 1 - Matriz):** `192.168.1.0/24`
🔹 **Rede Remota (LAN 2 - Filial):** `192.168.2.0/24`
🔹 **Firewall pfSense como Gateway**
🔹 **VPN configurada para comunicação segura entre as redes**

📌 **Topologia do Projeto**
[aqui](50590619-ca1d-43f7-85aa-7c86caeecd40.png)

---

## 🚀 Configuração Passo a Passo

### 1️⃣ Instalação do pfSense
- Baixe a ISO do **pfSense** [aqui](https://www.pfsense.org/download/)
- Instale em uma máquina virtual (VMWare/VirtualBox) ou em um hardware dedicado
- Configure **Interface WAN** (IP público) e **Interface LAN** (rede interna)

### 2️⃣ Configuração da VPN OpenVPN
#### 🔹 Criando o Servidor VPN
1. Acesse o painel do pfSense (`https://SEU-IP`)
2. Vá para **VPN > OpenVPN > Servers**
3. Adicione um novo servidor com:
   - Protocolo: `UDP`
   - Porta: `1194`
   - Rede da VPN: `10.10.10.0/24`
4. Configure autenticação com **certificados e usuários**
5. Exporte o perfil de conexão para os clientes

#### 🔹 Criando as Regras de Firewall para VPN
```bash
pass in on OpenVPN from any to 192.168.1.0/24
pass in on OpenVPN from any to 192.168.2.0/24
```

#### 🔹 Configuração do Cliente VPN (Filial)
1. Instale o **OpenVPN Client**
2. Importe o perfil gerado pelo servidor pfSense
3. Conecte e verifique a comunicação entre as redes

### 3️⃣ Configuração de NAT e Regras de Firewall
- Permitir tráfego entre as redes LAN e VPN
- Bloquear acessos indesejados com **ACLs**

### 4️⃣ Monitoramento e Logs
- Utilize o **Dashboard do pfSense** para visualizar conexões
- Configure alertas para tentativas de acesso não autorizadas

---

## 🔍 Testes e Validações
✅ Ping entre dispositivos da matriz e filial via VPN
✅ Teste de conexão remota com OpenVPN Client
✅ Logs de acesso no pfSense
✅ Simulação de ataque para testar bloqueios

---

## 📜 Conclusão
Esta implementação garante **segurança avançada** para redes distribuídas, protegendo dados e facilitando acesso remoto seguro. O **pfSense** é uma solução poderosa para firewall e VPNs, essencial para empresas e profissionais de TI.

Se tiver dúvidas ou sugestões, me avise! 🚀

🔗 **Conecte-se comigo:** [LinkedIn](https://www.linkedin.com/in/kaua7k/)
