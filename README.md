
# Instituto de Ensino Superior de Brasília - IESB

## Projeto Integrador - Implementação de Segurança  
#### Nome: Vinicius Capitulino de Andrade  
#### Matrícula: 1786105015    


## Projeto de Segurança  
### Objetivo  
  Implementar uma rede de segurança para proteção de servidores web.

### Justificativa  
  O avanço das tecnologias criou um novo cenário onde a maioria dos serviços são providos via web.  
  A proteção em várias camadas, aliada a boas políticas de rede trazem uma maior segurança as infraestruturas de servidores.  
  Se a normatização adota no Brasil e internacionalmente, no caso de sites que provêem serviços na internet, garantem uma padronização de configurações que garantirão o melhor desempenho das aplicações, a disponibilidade, confiabilidade e integridade das comunicações feitas com estes servidores.
### Etapas  
  Será implementado um pfSense como firewall, um serviço de páginas web com o Apache 2 e um proxy reverso com o Squid.  
  Todos os servidores ficarão atrás do proxy Reverso e do Firewall.  

##### Softwares Usados:
  pfSense versão 2.4.3  
  Squid versão 4.2  
  Apache versão 2  
  Virtualbox versão 5.2.18  


##### Instalação e configuração da infraestrutura
  Foram instaladas quatro máquinas virtuais, sendo uma como firewall (pfSense), uma como proxy reverso (Debian 9), uma como servidor web (Debian 9) e uma como cliente (Debian 9).


###### Virtual Box
  Redes internas:  
  projeto1 - rede dos usuários 192.168.1.0/24  
  projeto2 - rede dos servidores 192.168.2.0/24  

  Máquinas Virtuais:
  Firewall - pfSense  
  Revproxy - Squid  
  WebServer - Apache  
  Clientedeb  

##### Configuração das Máquinas Virtuais  
###### Firewall

  Interfaces de rede:  
  Eth0 - 192.168.1.1
  Eth1 - 192.168.2.1
  Eth2 - Bridge na rede da máquina física para acesso a internet  

  Configurações de firewall(semanalmente revisadas):
   - Bloqueado tráfego IPV4/IPV6 de pacotes com IPs inválidos na internet para saída pela porta Eth2.
   - Bloqueado o tráfego IPV4/IPV6 TCP e UDP vindos da rede dos clientes diretamente para a rede dos servidores.
   - Habilitado o tráfego IPV4/IPV6 TCP de toda rede de usuários pela porta 80 para a rede dos servidores
   - Habilitado qualquer tipo de tráfego saindo e entrando para a interface Eth2 com destino a rede dos usuários.
   - Habilitado saída de pacotes TCP e UDP da rede dos servidores para a rede dos clientes.


##### Servidor Web
  Eth0 - 192.168.2.10  
  Serviço Web rodando em Apache 2  

##### Proxy Reverso  
  Eth0 - 192.168.2.100  
  Eth1 - 192.168.1.100  
  Serviço de proxy reverso rodando em Squid  

  Regras do proxy reverso:
  - Todo tráfego que chega pela porta 80 e 443 é verificado seu "payload" e entregue as informações solicitadas dos servidores requeridos.  

##### Cliente
  Eth0 - 192.168.1.2

### Conclusão  
  Concluído o projeto todos os clientes somente acessarão os serviços por intermédio do proxy reverso.
  Todo tráfego vindo da interface dos usuários ou da internet será filtrado pelo firewall e repassado ao  
  proxy reverso que intermediará as solicitações feitas aos servidores.   
  Este tipo de implementação trás maior segurança para as aplicações que rodam no servidor, garantindo   
  a disponibilidade para todos os usuários e maior performance dos serviços.
