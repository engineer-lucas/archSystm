Exemplo de Comunicação Cliente-Servidor em Java
Este projeto demonstra uma arquitetura básica de comunicação entre um cliente e um servidor usando Sockets em Java. A aplicação permite que um cliente se conecte a um servidor, envie uma mensagem e receba uma resposta.

Estrutura do Projeto
O projeto é composto por três classes principais, localizadas no pacote ClientServer:

Server.java: A classe do servidor que aguarda por conexões de clientes na porta 12345. Ele recebe uma mensagem do cliente e envia uma resposta. O servidor usa ServerSocket para ouvir a porta e Socket para gerenciar a conexão com o cliente.

Client.java: A primeira classe cliente que se conecta ao servidor, envia a mensagem "Olá, Servidor! Aqui é o cliente 1" e imprime a resposta recebida do servidor.

Client2.java: A segunda classe cliente que também se conecta ao servidor na mesma porta, envia a mensagem "Sou o segundo cliente servidor!" e imprime a resposta do servidor.

Requisitos
Java Development Kit (JDK) instalado.

Como Executar
Para rodar este projeto, você precisa iniciar o servidor primeiro e depois os clientes.

Compile as classes Java:
Abra o terminal na pasta do projeto e compile os arquivos .java.

Bash

javac ClientServer/Server.java ClientServer/Client.java ClientServer/Client2.java

Inicie o Servidor:
Em um terminal, execute a classe Server. O servidor ficará "ouvindo" pela porta 12345.

Bash

java ClientServer.Server
Você verá a mensagem: Servidor iniciado e aguardando conexões na porta 12345....

Inicie os Clientes:
Abra novos terminais para cada cliente. Execute a classe Client em um terminal e a classe Client2 em outro.

Terminal 1 (Cliente 1):

Bash

java ClientServer.Client
Terminal 2 (Cliente 2):

Bash

java ClientServer.Client2
Observação Importante sobre a Execução
A implementação do Server.java aceita apenas uma conexão por vez. Quando um cliente se conecta, o servidor aceita a conexão, processa a mensagem e, em seguida, encerra a sua execução.

Se você tentar conectar o Client2.java depois que o primeiro cliente já se conectou, o servidor não estará mais ativo, e o segundo cliente irá gerar um erro de conexão. Para testar ambos os clientes, você deve executar o servidor novamente após a finalização da primeira conexão.

Como o Código Funciona
A comunicação é baseada em Sockets e Streams de Dados.

ServerSocket vs. Socket: O servidor usa ServerSocket para "escutar" a porta 12345. Quando uma solicitação de conexão chega, o método accept() do servidor cria um novo objeto Socket para lidar com essa comunicação específica com o cliente. Do lado do cliente, a classe Socket é usada para iniciar a conexão com o servidor.

Fluxos de Entrada e Saída (I/O Streams):

Para enviar mensagens, o cliente e o servidor usam um PrintWriter. O PrintWriter é um "escritor" eficiente para texto.

Para receber mensagens, ambos usam um BufferedReader. O BufferedReader atua como um "leitor" eficiente, esperando que uma linha completa de texto chegue antes de processá-la.

Tratamento de Erros: O bloco try-catch é usado para lidar com possíveis erros, como a falha ao conectar a um servidor ou problemas de leitura/escrita de dados. O try-with-resources garante que os recursos como Sockets e Streams sejam fechados automaticamente, liberando a memória e a porta.
