# yeti-switch
Yeti -  Softswitch SIP de Classe 4 com faturamento integrado e subsistema de roteamento inteligente. A solução destina-se a atuar como SBC distribuído nas redes dos provedores de serviços que estão trabalhando utilizando o protocolo SIP. O sistema suporta uma variedade de algoritmos de roteamento inteligentes. Projeto fork => https://yeti-switch.org/docs/en/index.html.

Yeti Softswitch lida com sinalização SIP e tráfego RTP. Suporta transcodificação, CDRs detalhados (mais de 100 campos) permitem salvar todos os parâmetros necessários para faturamento, depuração e relatórios analíticos. Yeti Softswitch suporta roteamento inteligente de LCR/ASR/ACD por vários critérios. Abaixo está uma pequena lista de recursos suportados.

# Sinalização e processamento RTP
=> SIP v2.0 sobre transporte UDP, TCP e TLS;
=> Suporte IPv6. Configuração de resolução flexível;
=> SRTP com mecanismo DTLS e SDES;
=> Envia/Recebe DTMF (aplicativo SIP INFO/DTMF, aplicativo SIP INFO/DTMF-RELAY, evento de telefone RTP) com capacidade de transcodificar entre eles em qualquer combinação;
=> Desconexão automática de chamdas no tempo limite (timeout) do RTP configurado por Gateway;
=> Temporizador de Sessão SIP;
=> Método de SIP UPDATE;
=> Configuração flexível para passagens NAT (vários modos RTP simétricos, ping RTP);
=> Failover de DNS SRV e Balaceamento de Carga;
=> Reescrita de códigos de desconexão para repostas de fornecedores e clientes;
=> Transcodificação de estatísticas RTCP/RTP;
=> Negociação de CODECs inteligentes - Classificação SDP, filtragem de fluxos de áudio, normalização da localização da linha de conexão, etc.
=> Normalização de fluxos RTP (alinhamento de sequência e carimbo de data/hora);
=> No dialogo (in-dialog) OPÇÕES/UPDATE/re-INVITE/PRACK com processamento local ou relay;
Configurações especiais para trabalhar com sistemas que usam implementação SIP não padrão;
=> Fax T.38;
=> Registros SIP de saída;
=> Registros SIP de entrada (REGISTRAR). A terminação de chamadas para Gateways com IP dinâmico é suportada.

# CODECs compatíveis
=> g711 alaw/ulaw;
=> g722;
=> g729;
=> iLBC;
=> speex;
=> gsm;
=> adpcm;
=> OPUS.

# Autorização
=> Endereço IP do originador;
=> Autorização de nome de usuário/senha;
=> DST, prefixos SRC;
=> Domínio SIP R-URI;
=> Cabeçalho SIP personalizado;
=> Geolocalização do nó de sinalização;
=> Servidor RADIUS externo.

# Roteamento
=> Reencaminhamento transparente para o cliente. Configuração flexível para as condições de quando usar a próxima rota;
=> Reescrita ou passagem transparente dos códigos de desconexão para o cliente;
=> Configuração LCR flexível (controle de qualidade, limite de preços). Possibilidade de implementação rápida de qualquer algoritmo alternativo desejado;
=> Controle de capacidade para Gateways, destinos, empresas, contas;
=> Lista de bloqueios, baseada em número de origem e destino e regras de tradução por número;
=> Possibilidade de reescrever/modificar identificador de chamadas, DNIS em qualquer estágio de roteamento;
=> Roteamento baseado em tempo;
=> Estatística e controle de qualidade para cada destino;
=> Agrupamento de Gateways e balanceamento de carga para casos em que o fornecedor fornece vários Gateways para a terminação;
=> Possibilidade de rejeitar silenciosamente convites SIP não autorizados (reduz o tráfego parasita de bots que procuram as vulnerabilidades nos sistemas telefônicos - reais para o trabalho através da rede da Internet);
=> Roteamento baseado em tags para criar regras flexíveis, como roteamento e cobrança com base na origem.

# Billing
=> Escrita de CDR em tempo real. Possibilidade de pular a gravação de CDR para códigos de desconxóes específicos;
=> Bloqueio de tráfego em tempo real quando o limite de saldo é atingido;
=> Configuração flexível de planos de taxa e políticas de roteamento para fornecer rentabilidade ideal;
=> Intervalos de faturamento configuráveis, suporte da taxa de conexão;
=> Geração de faturas e documentos a partir de templates;
=> Cálculo de preço dinâmico para cliente a partir do preço real de terminação. Este modo é útil para vender tráfego para clientes confiáveis ​​pelo preço de custo mínimo;
=> Integração com sistemas externos;
=> Possibilidade de enviar CDRs para os sistemas externos (por exemplo, para análise antifraude);
=> API REST para modificação de dados (em desenvolvimento);
=> Sensores de interceptação legais. Permite configurar o espelhamento de tráfego para o equipamento externo sem afetar o funcionamento do sistema. É possível configurar diferentes sensores para diferentes trechos de chamada e Gateways. Neste momento o sistema suporta IP-IP e IP over Ethernet encapsulamento;
=> Suporte para receber informações sobre o limite superior da taxa para cada chamada do cabeçalho SIP personalizado pelo cliente;
=> Capacidade de mostrar informações sobre o custo real de terminação (taxas do fornecedor) para os clientes confiáveis ​​e informações sobre o custo para o cliente (útil no caso de cálculo de taxa dinâmica).

# Relatórios
=> Utilização da capacidade em tempo real para empresas, gateways, destinos;
=> Relatórios sobre destinos, clientes, fornecedores, tempo;
=> Exibição das chamadas ativas que estão passando pelo sistema. Capacidade de encerrar qualquer chamada ativa da interface da web;

# Administração
=> Atualização de tempo de inatividade zero. Todos os componentes podem ser atualizados sem interrupção de processamento de tráfego e violações de faturamento;
=> Clusterização. O dimensionamento do sistema é realizado com a adição de servidores ao cluster;
=> Possibilidade de configuração geo-distribuída que é controlada a partir de uma única interface. Essa configuração é tolerante a falhas para problemas de rede e hardware e fornece cobrança CDR correta após a reconexão entre as partes do sistema;
=> Interface web conveniente com possibilidade de encontrar simplesmente qualquer entidade do sistema. O registro de modificações de operadores de interface permite fornecer um alto nível de segurança. Exportação e importação com suporte para todos os objetos de base de configuração do sistema;
=> Tarefas demoradas são executadas em segundo plano para evitar o bloqueio da interface da web;
=> Todos os componentes são desenvolvidos e empacotados para uma única plataforma (Debian GNU/Linux) e podem ser configurados/atualizados usando o gerenciador de pacotes padrão (apt) OBS: Somente o projeto oficial!;
=> Interface CLI para sistema de roteamento. Permite gerenciar todos os nós de roteamento e usar ferramentas de depuração estendidas;
=> Gravação dos dumps para PCAP das chamadas para fornecer depuração simples. Os dumps registrados estão disponíveis por meio da interface da web;
=> Os CDRs têm grande quantidade de informações de depuração;
=> Economia de estatística RTP para cada fluxo;
=> Retenção automática de dados.

# Componentes
Yeti consiste nos seguintes componentes:
=> Servidor de roteamento de tráfego (módulo SEMS + YETI);
=> Daemon de gerenciamento - usado como armazenamento de configuração no cluster;
=> Balanceador de tráfego de entrada (Kamailio);
=> Banco de dados de roteamento (Postgresql);
=> Banco de dados CDR (Postgresql);
=> Armazenamento de dados em tempo real (Redis);
=> Interface da Web (RoR, ruby);
=> Interface CLI (python) [opcional];
=> Daemons de cálculo de estatísticas e faturamento de CDRs baseados em PGQ.

Yeti Switch é projetado como um sistema cluster, mas você pode executar todos os componentes em um servidor, bem como em diferentes hosts. Sistema Operacional suportado é Debian GNU/Linux, a única arquitetura suportada é a amd64.
