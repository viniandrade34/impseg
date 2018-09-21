
# Projeto Integrador - Implementação de Segurança

## Instituto de Ensino Superior de Brasília - IESB  

### Objetivo  
  Implementar uma rede de segurança para proteção de servidores web.

### Justificativa  

### Etapas  
  Será implementado um pfSense como firewall, um serviço de páginas web com o Apache 2 e um proxy reverso com o Squid.  
  Todos os servidores ficarão atrás do proxy Reverso e do Firewall.  

  Serão usados:
  pfSense versão 2.4.3
  Squid versão 4.2
  Apache versão 2
  Virtualbox versão 


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
