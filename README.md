# Guacamole
O Apache Guacamole é uma aplicação web HTML5 que pode ser usado para acessar remotamente máquinas Linux e Windows.


Guacamole não é um aplicativo da web independente e é composto de muitas partes. Na verdade, o aplicativo da Web pretende ser simples e mínimo, com a maior parte do trabalho pesado realizado por componentes de nível inferior.

<a href="url"><img src="https://guacamole.apache.org/doc/0.9.0/images/guac-arch.png" align="center" height="548" width="388" ></a>








Os **usuários** se conectam a um servidor Guacamole com seu navegador da web. O cliente Guacamole, escrito em JavaScript, é servido aos usuários por um servidor web dentro do servidor Guacamole. Uma vez carregado, este cliente se conecta de volta ao servidor via HTTP usando o protocolo Guacamole.

O aplicativo da web implantado no servidor Guacamole lê o protocolo Guacamole e o encaminha para guacd, o proxy Guacamole nativo. Esse proxy realmente interpreta o conteúdo do protocolo Guacamole, conectando-se a qualquer número de servidores de desktop remoto em nome do usuário.

O protocolo Guacamole combinado com guacd fornece agnosticismo de protocolo: nem o cliente Guacamole nem o aplicativo da web precisam estar cientes de qual protocolo de desktop remoto está realmente sendo usado.
