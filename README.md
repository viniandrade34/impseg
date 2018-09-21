
# Projeto Integrador - Implementação de Segurança

## Instituto de Ensino Superior de Brasília - IESB  

### Objetivo  
  Implementar uma rede de segurança para proteção de servidores web em uma rede local com saída para internet.

### Justificativa  

### Etapas  
  Será implementado um pfSense como firewall, um serviço de pagina web com o Apache um proxy reverso com o squid.  
  Todos os servidores ficarão atrás de um proxy Reverso e um Firewall.  

  Serao usados:
  pfSense versao 2.4.3
  squid
  Apache2

  Uma configuracao com 3 servidores e 1 cliente sera feita.

  Configuracoes da rede

  internet - rede de acesso a internet  
  projeto1 - rede dos usuarios 192.168.1.0/24  
  projeto2 - rede dos servidores 192.168.2.0/24  


  Firewall
  192.168.1.1
  192.168.2.1

  Servidor Web
  192.168.2.10

  Proxy Reverso
  192.168.2.100

  Cliente
  192.168.1.2



### Conclusão  
  Concluído o projeto todos os clientes somente acessarão os serviços por intermédio do proxy reverso.  
  Este tipo de implementação trás maior segurança para as aplicações que rodam no servidor, garantindo   
  a disponibilidade para todos os usuários.
