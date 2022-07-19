# Guacamole

#### O Apache Guacamole é uma aplicação web HTML5 que pode ser usado para acessar remotamente máquinas Linux e Windows.


Guacamole não é um aplicativo da web independente e é composto de muitas partes. Na verdade, o aplicativo da Web pretende ser simples e mínimo, com a maior parte do trabalho pesado realizado por componentes de nível inferior.

<a href="url"><img src="https://guacamole.apache.org/doc/0.9.0/images/guac-arch.png" align="center" height="548" width="388" ></a>








Os **usuários** se conectam a um servidor Guacamole com seu navegador da web. O cliente Guacamole, escrito em JavaScript, é servido aos usuários por um servidor web dentro do servidor Guacamole. Uma vez carregado, este cliente se conecta de volta ao servidor via HTTP usando o protocolo Guacamole.

O aplicativo da web implantado no servidor Guacamole lê o protocolo Guacamole e o encaminha para guacd, o proxy Guacamole nativo. Esse proxy realmente interpreta o conteúdo do protocolo Guacamole, conectando-se a qualquer número de servidores de desktop remoto em nome do usuário.

O protocolo Guacamole combinado com guacd fornece agnosticismo de protocolo: nem o cliente Guacamole nem o aplicativo da web precisam estar cientes de qual protocolo de desktop remoto está realmente sendo usado.


### O protocolo Guacamole
O aplicativo da Web não entende nenhum protocolo de área de trabalho remota. Ele não contém suporte para VNC ou RDP ou qualquer outro protocolo suportado pela pilha Guacamole. Na verdade, ele só entende o protocolo Guacamole, que é um protocolo para renderização de exibição remota e transporte de eventos. Embora um protocolo com essas propriedades tenha naturalmente as mesmas habilidades que um protocolo de área de trabalho remota, os princípios de design por trás de um protocolo de área de trabalho remota e do protocolo Guacamole são diferentes: o protocolo Guacamole não se destina a implementar os recursos de um ambiente de área de trabalho específico.

Como um protocolo de interação e exibição remota, o Guacamole implementa um superconjunto de protocolos de desktop remoto existentes. Adicionar suporte para um determinado protocolo de área de trabalho remota (como RDP) ao Guacamole envolve escrever uma camada intermediária que "traduz" entre o protocolo de área de trabalho remota e o protocolo Guacamole. Implementar tal tradução não é diferente de implementar qualquer cliente nativo, exceto que esta implementação em particular é renderizada em um display remoto ao invés de um local.

A camada intermediária que trata dessa tradução é o guacd.


### Instalação

yum -y install epel-release wget

wget -O /etc/yum.repos.d/home:felfert.repo http://download.opensuse.org/repositories/home:/felfert/Fedora_19/home:felfert.repo

yum -y install cairo-devel freerdp-devel gcc java-1.8.0-openjdk.x86_64 libguac libguac-client-rdp libguac-client-ssh libguac-client-vnc \
libjpeg-turbo-devel libpng-devel libssh2-devel libtelnet-devel libvncserver-devel libvorbis-devel libwebp-devel openssl-devel pango-devel \
pulseaudio-libs-devel terminus-fonts tomcat tomcat-admin-webapps tomcat-webapps uuid-devel
