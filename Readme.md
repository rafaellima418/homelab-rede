🏠 **Homelab - Segmentação de Rede com VLANs, MikroTik e Firewall**



🚀 **Sobre o Projeto**



Este projeto demonstra a implementação de uma **arquitetura de rede segmentada e segura**, utilizando VLANs, roteador MikroTik e switch gerenciável.



O ambiente foi construído como parte da minha consolidação para a área de **Redes e Segurança da Informação**, com foco em **cenários reais**, aplicando conceitos como segmentação, controle de tráfego e redução da superfície de ataque.



\---



🎯 **Objetivos**



\* Segmentar a rede em zonas isoladas (LAN/Wi-Fi, LAB e IoT/Guest)

\* Evitar movimentação lateral entre dispositivos

\* Permitir acesso controlado entre redes específicas

\* Garantir acesso à internet para todas as VLANs

\* Aplicar boas práticas de firewall e segurança



\---



🧠 **Visão da Arquitetura**



\* Provedor em modo bridge (PPPoE)

\* Roteador realizando roteamento entre VLANs

\* Switch gerenciável com VLANs 802.1Q

\* Access Points em modo AP

\* Ambiente de laboratório isolado (Proxmox)



\---



🌐 **Estrutura da Rede**



| VLAN | Nome | Sub-rede        | Finalidade                        |

| ---- | ---- | --------------- | --------------------------------- |

| 10   | LAN  | 192.168.10.0/24 | Rede principal (PCs e Wi-Fi)      |

| 30   | LAB  | 192.168.30.0/24 | Ambiente de laboratório (Proxmox) |

| 50   | IoT  | 192.168.50.0/24 | Dispositivos IoT e Guests         |



\---



🔌 **Topologia Física**



\* WAN → MikroTik (PPPoE)

\* MikroTik → Switch (porta trunk)

\* Switch:



&#x20; \* Porta 2 → Desktop (VLAN 10)

&#x20; \* Porta 3 → Proxmox (VLAN 30)

&#x20; \* Porta 4 → Deco AX3000 (Wi-Fi principal - VLAN 10)

&#x20; \* Porta 5 → AX1800 (Wi-Fi IoT e Guest - VLAN 50)



\---



🧩 **Implementação das VLANs**



**Switch (Camada 2)**



\* VLAN 10 → Untagged (portas de acesso)

\* VLAN 30 → Tagged (uplink) + Untagged (porta do LAB)

\* VLAN 50 → Tagged (uplink) + Untagged (porta do IoT/Guest)



**MikroTik (Camada 3)**



\* Interfaces VLAN criadas na bridge

\* Roteamento entre VLANs configurado

\* DHCP Server ativo por VLAN



\---



🔐 **Estratégia de Firewall**



&#x20;**Objetivo de Segurança**



\* Bloquear comunicação entre VLANs

\* Permitir acesso à internet

\* Permitir acesso controlado da LAN ao LAB



\---



**Lógica das Regras (Ordem Importante)**



1\. Aceitar conexões **established/related**

2\. Permitir VLAN 30 → Internet

3\. Permitir VLAN 50 → Internet

4\. Permitir LAN → LAB (acesso controlado)

5\. Bloquear VLAN 30 → redes internas

6\. Bloquear VLAN 50 → redes internas



\---



🧪 **Testes e Validação**



\* ✔ Dispositivos recebem IP correto por VLAN

\* ✔ Wi-Fi IoT/Guest não acessa LAN nem LAB

\* ✔ LAB está isolado da rede principal

\* ✔ LAN acessa o Proxmox corretamente

\* ✔ Internet funciona em todas as VLANs

\* ✔ Regras de firewall funcionando conforme esperado



\---



🔒 **Melhorias de Segurança Aplicadas**



\* Segmentação de rede com VLANs

\* Isolamento de tráfego entre zonas

\* Redução da superfície de ataque

\* Controle de acesso entre redes

\* Proteção do roteador contra acesso de IoT/Guest



\---



🛠️ **Tecnologias Utilizadas**



\* MikroTik RouterOS

\* VLAN (802.1Q)

\* PPPoE

\* Firewall stateful

\* Switch gerenciável TP-Link

\* Proxmox VE



\---



📊 **Habilidades Demonstradas**



\* Arquitetura de redes

\* Configuração de VLANs (Layer 2 e Layer 3)

\* Criação e análise de regras de firewall

\* Roteamento entre redes

\* Troubleshooting (diagnóstico e resolução de problemas reais)



\---



📷 **Evidências**



Adicionar imagens como:



\* Configuração de VLANs no switch

\* Regras de firewall no MikroTik

\* Diagrama da rede

\* Interface do Proxmox



\---



🔮 **Próximos Passos**



\* Implementação de VPN (WireGuard)

\* Monitoramento (Zabbix / Grafana)

\* Centralização de logs (Syslog)

\* Evolução para modelo Zero Trust



\---



👨‍💻 **Autor**



Projeto desenvolvido como parte da minha evolução na área de **Redes e Segurança da Informação**, com foco em aprendizado prático e cenários reais.



Estou continuamente aprimorando este ambiente para simular infraestruturas corporativas.



