Redes de Computadores e a Internet

Este livro aborda os princípios fundamentais e práticas contemporâneas de **redes de computadores** e da **Internet**, estruturando seu conteúdo a partir de uma **abordagem top-down**, que inicia na camada de aplicação e desce até a camada física. A obra detalha a arquitetura de **cinco camadas da Internet**, explorando componentes cruciais como sistemas finais, protocolos, comutadores de pacotes, enlaces de acesso e o núcleo da rede. Além disso, são discutidos temas essenciais como **segurança em redes**, controle de congestionamento, roteamento, criptografia e gerenciamento de rede, utilizando exemplos atuais e materiais de apoio para estudantes e professores.

## 1. Quais são as fontes utilizadas?

- **James F. Kurose e Keith W. Ross** — *Redes de Computadores e a Internet: Uma Abordagem Top-Down*.
- **Andrew S. Tanenbaum, Nick Feamster e David J. Wetherall** — *Redes de Computadores*.
- **Larry L. Peterson e Bruce S. Davie** — *Redes de Computadores: Uma Abordagem de Sistemas*.
- **Douglas E. Comer** — *Interconexão de Redes com TCP/IP, Volume 1*.

## 2. Por que confiar nessas fontes?

A confiabilidade dessas obras está relacionada ao reconhecimento acadêmico de seus autores, à ampla utilização no ensino de redes de computadores e à abrangência dos conteúdos apresentados.

### A. Reconhecimento acadêmico

As obras de Kurose e Ross, Tanenbaum, Peterson e Davie e Douglas Comer são referências tradicionais no ensino de redes de computadores em cursos de Ciência da Computação, Engenharia e áreas relacionadas.

### B. Autoridade dos autores

Os autores possuem ampla experiência acadêmica e profissional nas áreas de redes de computadores, sistemas distribuídos, arquitetura de computadores e protocolos de comunicação.

### C. Complementaridade das abordagens

As obras apresentam perspectivas complementares sobre redes de computadores:

- **Kurose e Ross** — abordagem *Top-Down*, partindo da camada de aplicação e dos serviços utilizados pelos usuários.
- **Tanenbaum, Feamster e Wetherall** — abordagem abrangente da arquitetura de redes, incluindo fundamentos, protocolos e tecnologias de comunicação.
- **Peterson e Davie** — abordagem voltada aos princípios de engenharia e à construção de sistemas de redes.
- **Douglas Comer** — abordagem aprofundada da arquitetura e dos protocolos da suíte TCP/IP.

A utilização conjunta dessas referências permite abordar o funcionamento das redes de forma ampla, desde os fundamentos até a implementação e operação dos principais protocolos.

### D. Rigor acadêmico

As obras são publicadas por editoras reconhecidas na área de tecnologia e utilizadas como referências acadêmicas em instituições de ensino superior. Seus conteúdos são elaborados com base em fundamentos técnicos consolidados e na experiência dos autores em pesquisa e ensino de redes de computadores.


a Diretriz de comportamento foi:

Responda como um analista sênior de redes, que explica de forma didática, dando exemplos e relacionando os conceitos a situações do cotidiano.


# Pergunta 1: Fale sobre as portas padrão dos serviços comuns

## Resposta

Os **números de porta** são identificadores de 16 bits, variando de 0 a 65535, utilizados na camada de transporte, como TCP e UDP, para permitir que os dados da rede sejam entregues ao processo ou aplicação correto dentro de um hospedeiro. Enquanto o endereço IP identifica a máquina na rede, o número de porta especifica a aplicação de destino nessa máquina.

As portas no intervalo de **0 a 1023** são chamadas de **portas bem conhecidas (well-known ports)** ou reservadas. Elas são padronizadas pela IANA/IETF e destinadas a serviços de aplicação padrão da Internet.

### Principais portas padrão de serviços comuns

- **HTTP (HyperText Transfer Protocol) — Porta 80 (TCP):** utilizada para a requisição e transferência de páginas da World Wide Web em texto claro.

- **HTTPS (HTTP Secure) — Porta 443 (TCP):** camada HTTP executada sobre SSL/TLS para garantir a criptografia e autenticação nas comunicações Web.

- **FTP (File Transfer Protocol) — Portas 20 e 21 (TCP):** o FTP utiliza duas conexões paralelas: a **porta 21** para o canal de controle, responsável pelos comandos, usuário e senha, e a **porta 20** para a transferência efetiva dos arquivos.

- **SMTP (Simple Mail Transfer Protocol) — Porta 25 (TCP):** protocolo utilizado para o envio e a transferência de mensagens de e-mail entre servidores de correio eletrônico.

- **DNS (Domain Name System) — Porta 53 (UDP/TCP):** serviço responsável por traduzir nomes de domínio legíveis por humanos em endereços IP.

- **Telnet — Porta 23 (TCP):** utilizada para acesso e logon em terminais remotos sem criptografia.

- **SNMP (Simple Network Management Protocol) — Porta 161 (UDP):** utilizada por aplicações de gerenciamento de rede para consultar e monitorar estatísticas de dispositivos.

- **Port Mapper / SunRPC — Porta 111 (TCP/UDP):** serviço de mapeamento que informa aos clientes qual porta dinâmica está sendo utilizada por determinado programa RPC em um servidor.

### Funcionamento e demultiplexação de portas

1. **Portas de servidor e portas de cliente:** o processo servidor escuta requisições em uma **porta bem conhecida e fixa**, como a porta 80 em um servidor Web ou a porta 25 em um servidor de e-mail. O sistema operacional do cliente, ao iniciar a comunicação, atribui automaticamente uma **porta de origem temporária (efêmera)**.

2. **Cabeçalhos de transporte:** cada segmento enviado contém dois campos de porta no cabeçalho: a **porta de origem** e a **porta de destino**.

3. **Identificação única de conexões:** no TCP, a camada de transporte utiliza a **tupla de 4 elementos** (`IP de Origem, Porta de Origem, IP de Destino, Porta de Destino`) como chave de demultiplexação. Isso permite que um servidor Web suporte milhares de conexões simultâneas na porta 80 sem confundir os dados pertencentes a clientes diferentes.

### Fontes do Caderno Utilizadas

- *Redes de Computadores e a Internet: Uma Abordagem Top-Down* — James F. Kurose e Keith W. Ross.
- *Computer Networks: A Systems Approach* — Larry L. Peterson e Bruce S. Davie.
- *Computer Networking* — Kurose e Ross.


# Pergunta 2: Responda como um analista sênior de redes, que explica de forma didática, dando exemplos e relacionando a coisas do cotidiano. Fale sobre o SSH

## Resposta

Como **analista sênior de redes**, o **SSH (Secure Shell)** é um protocolo essencial para a administração remota segura de sistemas. Ele é um protocolo da camada de aplicação projetado para oferecer acesso remoto seguro, execução de comandos e transferência de arquivos entre máquinas.

### 1. Por que o SSH foi criado? — A analogia do cartão-postal

Nos primórdios da Internet, utilizava-se o **Telnet** para administrar servidores remotos. O grande problema do Telnet era enviar todos os dados, incluindo usuário e senha, em texto claro, sem criptografia.

- **Analogia do cotidiano:** usar o **Telnet** era como enviar sua senha escrita no verso de um **cartão-postal transparente**. Qualquer pessoa no caminho poderia ler a informação.

- **O SSH:** foi desenvolvido para substituir o Telnet e o rlogin. Funciona como um **carro-forte blindado** que criptografa e protege o tráfego da rede contra interceptações.

### 2. A arquitetura interna do SSH

O SSH funciona sobre uma conexão de transporte **TCP** e é dividido em três subprotocolos principais:

- **SSH-TRANS (Protocolo de Transporte):** cria o canal criptografado seguro sobre o TCP. Negocia os algoritmos de criptografia, realiza a verificação de integridade das mensagens e estabelece a chave de sessão.

- **SSH-AUTH (Protocolo de Autenticação):** executa sobre o SSH-TRANS e cuida da autenticação do usuário perante o servidor.

- **SSH-CONN (Protocolo de Conexão):** multiplexa o canal seguro em múltiplos canais lógicos, permitindo sessões de terminal, execução de comandos e tunelamento.

### 3. Como funciona a autenticação no SSH?

Ao se conectar a um servidor, o SSH oferece diferentes mecanismos de autenticação:

- **Autenticação por senha:** a senha é enviada protegida dentro do canal criptografado do SSH-TRANS.

- **Autenticação por chave pública (assimétrica):** é uma das opções mais seguras.

  - **Analogia do cotidiano:** funciona como um **cadeado e uma chave física**. O servidor guarda o cadeado, representado pela **chave pública** registrada no arquivo `authorized_keys`. Você guarda no seu computador a chave que abre esse cadeado, representada pela **chave privada**, normalmente armazenada em um arquivo como `id_rsa`. Você prova ser o dono da chave sem precisar transmitir a chave privada para o servidor.

- **Autenticação baseada em hospedeiro (Host-Based):** nesse mecanismo, a própria máquina cliente se autentica perante o servidor.

Além disso, no primeiro acesso, o SSH apresenta a chave pública do servidor e solicita confirmação para salvá-la no arquivo `known_hosts`. Isso ajuda a identificar alterações na chave do servidor em conexões futuras.

### 4. Tunelamento e redirecionamento de portas (Port Forwarding)

O SSH permite realizar **redirecionamento de portas (port forwarding)**, encapsulando o tráfego de outras aplicações dentro do canal criptografado do SSH.

- **Analogia do cotidiano:** é como colocar um pacote frágil ou desprotegido dentro de um **cofre de segurança sobre rodas**, representado pelo túnel SSH, para atravessar uma estrada perigosa.

### Fontes do Caderno Utilizadas

- *Computer Networks: A Systems Approach* — Larry L. Peterson e Bruce S. Davie.
- *Redes de Computadores e a Internet: Uma Abordagem Top-Down* — James F. Kurose e Keith W. Ross.


# Pergunta 3: Fale sobre as camadas

## Resposta

A arquitetura em **camadas** é a base do projeto de redes de computadores, utilizando o princípio da **modularidade** para dividir uma tarefa complexa em partes menores e mais fáceis de gerenciar. Cada camada oferece um serviço específico para a camada superior, utilizando os serviços prestados pela camada imediatamente inferior.

### 1. A analogia do cotidiano: o sistema postal e de correio corporativo

Imagine o envio de um **memorando interno** entre escritórios de empresas distantes:

- **A mensagem (Aplicação):** o memorando escrito.

- **O envelope interno (Transporte):** o envelope de correspondência interna com o nome e o departamento do destinatário, representando a porta ou o processo.

- **O envelope postal (Rede):** a central de correspondência coloca o envelope interno dentro de um envelope postal com o endereço completo, representando o endereço IP.

- **O transporte do trecho (Enlace):** o serviço de correio transporta o envelope por meio de caminhões ou aviões, representando protocolos de enlace como Ethernet ou Wi-Fi.

- **A infraestrutura física (Física):** o meio de transmissão físico, como fios de cobre, fibra óptica ou ondas de rádio.

### 2. A pilha de 5 camadas da Internet

A arquitetura de redes da Internet é organizada em uma pilha de **5 camadas**:

1. **Camada de Aplicação (PDU: Mensagem):** onde residem as aplicações de rede e seus protocolos, como HTTP, SMTP, DNS, SSH e FTP.

2. **Camada de Transporte (PDU: Segmento):** fornece comunicação lógica entre processos de aplicação em hospedeiros diferentes. Os principais protocolos são **TCP**, que oferece conexão confiável, controle de fluxo e controle de congestionamento, e **UDP**, que não estabelece conexão e possui uma operação mais simples. O identificador utilizado nessa camada é o **número de porta**.

3. **Camada de Rede (PDU: Datagrama):** responsável por mover pacotes, ou datagramas, de um hospedeiro de origem para um hospedeiro de destino através de roteadores. O principal protocolo é o **IP (Internet Protocol)**.

4. **Camada de Enlace / Link (PDU: Quadro ou Frame):** responsável por mover datagramas entre nós adjacentes conectados por um enlace individual. Exemplos incluem Ethernet, Wi-Fi (802.11) e PPP. O principal identificador utilizado é o **endereço MAC**.

5. **Camada Física (PDU: Bits):** transmite os bits individuais contidos nos quadros através do meio físico.

### 3. Modelo OSI de 7 camadas versus pilha da Internet

O modelo de referência **OSI de 7 camadas**, definido pela ISO, inclui duas camadas adicionais:

- **Camada de Apresentação:** trata da interpretação, formatação, compressão e criptografia dos dados.

- **Camada de Sessão:** fornece mecanismos de delimitação, sincronização e pontos de verificação na troca de dados.

Na prática da Internet, os serviços das camadas de Apresentação e Sessão não formam camadas separadas. Quando necessários, esses serviços são implementados diretamente pelos desenvolvedores na **Camada de Aplicação**.

### 4. Encapsulamento e dispositivos na rede

À medida que os dados descem pela pilha no transmissor, cada camada anexa um **cabeçalho (header)**, encapsulando os dados da camada superior em uma nova PDU (carga útil ou *payload*).

- **Hospedeiros finais:** implementam todas as 5 camadas da pilha.

- **Roteadores:** operam até a **Camada de Rede**, envolvendo as Camadas 1, 2 e 3.

- **Comutadores de enlace (Switches):** operam principalmente até a **Camada de Enlace**, envolvendo as Camadas 1 e 2.

### Fontes do Caderno Utilizadas

- *Redes de Computadores e a Internet: Uma Abordagem Top-Down* — James F. Kurose e Keith W. Ross.
- *Análise Comparativa e Estratégia de Integração de Literatura Acadêmica em Redes de Computadores para Expansão Didática*.
- *Computer Networks: A Systems Approach* — Larry L. Peterson e Bruce S. Davie.

link do notebook:
https://notebook.google.com/notebook/37e2c485-5b4d-4127-98c0-ca8c759d6598?authuser=2
