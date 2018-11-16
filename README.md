
# Instituto de Ensino Superior de Brasília - IESB

## Projeto Integrador - Implementação de Segurança  
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


  Máquinas Virtuais:  
  Firewall - pfSense  
  Revproxy - Squid  
  WebServer - Apache  
  Clientedeb - Debian 9

![vbox](https://user-images.githubusercontent.com/26367807/48631373-85e43000-e9a5-11e8-88da-dc2d5b3d2b1b.png)


###### Virtual Box
  Redes internas:  
  projeto1 - rede dos usuários 192.168.1.0/24  
  projeto2 - rede dos servidores 192.168.2.0/24  

![redesprojeto](https://user-images.githubusercontent.com/26367807/48632050-153e1300-e9a7-11e8-9ae2-5edc5813993b.png)

##### Configuração das Máquinas Virtuais  
###### Firewall

  Interfaces de rede:  
  Eth0 - 192.168.1.1  
  Eth1 - 192.168.2.1  
  Eth2 - Bridge na rede da máquina física para acesso a internet  

![redesinternas](https://user-images.githubusercontent.com/26367807/48631833-977a0780-e9a6-11e8-89c4-2b24f9e679b2.png)

  Configurações de firewall(semanalmente revisadas):  
   - Bloqueado tráfego IPV4/IPV6 de pacotes com IPs inválidos na internet para saída pela porta Eth2.
   - Bloqueado o tráfego IPV4/IPV6 TCP e UDP vindos da rede dos clientes diretamente para a rede dos servidores.
   - Habilitado o tráfego IPV4/IPV6 TCP de toda rede de usuários pela porta 80 para a rede dos servidores
   - Habilitado qualquer tipo de tráfego saindo e entrando para a interface Eth2 com destino a rede dos usuários.
   - Habilitado saída de pacotes TCP e UDP da rede dos servidores para a rede dos clientes.

![firewallinternet](https://user-images.githubusercontent.com/26367807/48635668-f8f2a400-e9af-11e8-9784-d489e5bad1e8.png)

![firewallclientes](https://user-images.githubusercontent.com/26367807/48635689-0871ed00-e9b0-11e8-8f9f-32dbb12bc2bc.png)

![firewallservidores](https://user-images.githubusercontent.com/26367807/48635717-17f13600-e9b0-11e8-9f65-666678a33c98.png)

![firewallrotas](https://user-images.githubusercontent.com/26367807/48635753-2ccdc980-e9b0-11e8-8e82-1a905f316952.png)



##### Servidor Web
  Enp0s3 - 192.168.2.10  
  Serviço Web rodando em Apache 2  
  
  ![apache2](https://user-images.githubusercontent.com/26367807/48635801-538c0000-e9b0-11e8-9714-33166d8c472b.png)

##### Proxy Reverso  
  Enp0s8 - 192.168.2.100  
  
  Serviço de proxy reverso rodando em Squid  

  Regras do proxy reverso:
  - Todo tráfego que chega pela porta 80 é verificado seu "payload" e entregue as informações solicitadas dos servidores requeridos.  
  
  ![squid](https://user-images.githubusercontent.com/26367807/48636572-70293780-e9b2-11e8-9bc1-7dd15afea53b.png)
  

##### Cliente
  Enp0s3 - 192.168.1.2

  ![cliente](https://user-images.githubusercontent.com/26367807/48636745-e62d9e80-e9b2-11e8-9bfd-672653d7343c.png)

  ![paginaweb](https://user-images.githubusercontent.com/26367807/48636845-2c82fd80-e9b3-11e8-9e90-54ed499f4cfb.png)
### Conclusão  
  Concluído o projeto todos os clientes somente acessarão os serviços por intermédio do proxy reverso.
  Todo tráfego vindo da interface dos usuários ou da internet será filtrado pelo firewall e repassado ao  
  proxy reverso que intermediará as solicitações feitas aos servidores.   
  Este tipo de implementação trás maior segurança para as aplicações que rodam no servidor, garantindo   
  a disponibilidade para todos os usuários e maior performance dos serviços.
