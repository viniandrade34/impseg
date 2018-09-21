
# Projeto Integrador - Implementação de Segurança

## Instituto de Ensino Superior de Brasília - IESB  

### Objetivo  
  Implementar uma rede de segurança para proteção de servidores web.

### Justificativa  

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

  Configurações de firewall:
   - Bloqueado tráfego de pacotes com IPs inválidos na internet para saída pela porta Eth2
   - Habilitado o tráfego TCP de toda rede de usuários pela porta 80 para a rede dos servidores
   - Habilitado qualquer tipo de tráfego saindo e entrando para a interface Eth2 com destino a rede dos usuários.
   - Habilitado saída de pacotes TCP e UDP da rede dos servidores para a rede dos clientes.


##### Servidor Web
  192.168.2.10

  Proxy Reverso
  192.168.2.100

  Cliente
  192.168.1.2



### Conclusão  
  Concluído o projeto todos os clientes somente acessarão os serviços por intermédio do proxy reverso.  
  Este tipo de implementação trás maior segurança para as aplicações que rodam no servidor, garantindo   
  a disponibilidade para todos os usuários.
