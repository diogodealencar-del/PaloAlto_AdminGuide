

Começando: Captura de pacotes

## Resolução

O primeiro lugar a ir é o menu Captura de pacotes na GUI, onde você pode gerenciar filtros, adicionar estágios de captura e baixar
facilmente capturas.


Antes de começarmos, há algumas coisas que você deve saber:
- Quatro filtros podem ser adicionados com uma variedade de atributos.
- As capturas de pacotes são baseadas em sessão, de modo que um único filtro é capaz de capturar tanto o cliente2server
quanto o server2client.

- Os pacotes são capturados no plano de dados vs na interface (isso explica a próxima bala).
- Pré-Parse Match é um recurso que pode capturar todos os arquivos antes de serem processados pelos motores que
estão funcionando no plano de dados, o que pode ajudar a solucionar problemas onde um motor pode não estar
aceitando corretamente um pacote de entrada. Esta opção deve ser usada somente se instruída por suporte e em um
tempo de baixo volume do dia, pois irá capturar tudo.
- Quando a filtragem é ativada, novas sessões são marcadas para filtragem e podem ser capturadas, mas as sessões
existentes não estão sendo filtradas e podem precisar ser reiniciadas para poder capturá-las.
- As sessões descarregadas não podem ser capturadas, portanto, o descarregamento pode precisar ser desativado
temporariamente. Uma sessão descarregada exibirá o processamento 'layer7 : concluído' nos detalhes da sessão
do show.
É muito para lembrar, mas tudo fará sentido depois que você tentar a sua mão em um par de capturas de pacotes de vários
protocolos, eu prometo!

Vamos adicionar um par de filtros:


Os filtros 1 e 3 são meus filtros reais: quero verificar conexões do meu cliente no IP 192.168.0.34 fazendo conexões HTTP na
porta 80 TCP para 198.51.100.97 e conexões SSH na porta 22 TCP para 198.51.100.1

Os filtros 2 e 4 são meus filtros 'backup': mencionei anteriormente que a captura de pacotes está ciente da sessão, mas apenas no
caso de algo acontecer com o pacote de retorno rio acima que faz com que ele falhe correspondendo à minha regra NAT (talvez
um dispositivo upstream mutila a porta de origem ou faça algo estranho ao número da sequência), eu costumo definir uma regra
de retorno para pegar quaisquer pacotes perdidos que seriam descartados devido à sua não correspondência.

Se agora mudarmos o botão filtragem para ON, os filtros serão aplicados a quaisquer novas sessões que correspondam aos
critérios:


Uma maneira simples de verificar se o filtro está funcionando é verificar se os contadores globais estão aumentando se uma nova
sessão é iniciada.
Do CLI, eu executo este comando:

> show counter global filter delta yes packet-filter yes


Global counters:
Elapsed time since last sampling: 2.647 seconds

--------------------------------------------------------------------------------
Total counters shown: 0
--------------------------------------------------------------------------------

E nenhum contador é exibido.
- "delta sim" indica que quero ver contadores que aumentaram desde a última vez que executei este comando.
- 'packet-filter sim' indica que quero ver apenas contadores globais que combinem com meus filtros.
Se eu atualizar meu navegador e executar o comando novamente:

> show counter global filter packet-filter yes delta yes

Global counters:
Elapsed time since last sampling: 2.630 seconds

name value rate severity category aspect description
--------------------------------------------------------------------------------
pkt_sent                     22 8 info packet pktproc Packets transmitted
pkt_outstanding              22 8 info packet pktproc Outstanding packet to be transmitted
session_allocated            4  1 info session resource Sessions allocated
session_installed            4  1 info session resource Sessions installed
appid_proc                   2  0 info appid pktproc The number of packets processed by
Application identification
appid_use_dfa_1              2  0 info appid pktproc The number of packets using the second DFA
table
nat_dynamic_port_xlat        4  1 info nat resource The total number of dynamic_ip_port NAT
translate called
dfa_sw                       8  3 info dfa pktproc The total number of dfa match using software
ctd_sml_opcode_set_file_type 1  0 info ctd pktproc sml opcode set file type
aho_sw                       5  1 info aho pktproc The total usage of software for AHO
ctd_pkt_slowpath             4  1 info ctd pktproc Packets processed by slowpath
--------------------------------------------------------------------------------
Total counters shown: 11
--------------------------------------------------------------------------------


Você vai ver que há um monte de contadores. Eu adicionei um link para mais algumas informações sobre contadores globais no
final deste artigo, e nós estaremos cobrindo-os mais em um episódio futuro. Mas por enquanto, enquanto houver contadores,
devemos estar prontos para ir.

Em seguida, você vai configurar os estágios — há 4:
- estágio de queda é onde os pacotes são descartados. As razões podem variar e, para esta parte, os contadores globais
podem ajudar a identificar se a queda foi devido a uma política negar, uma ameaça detectada ou outra coisa.
- receber o estágio captura os pacotes à medida que eles instroem o firewall antes de entrarem no mecanismo de firewall.
Quando o NAT estiver configurado, esses pacotes serão pré-NAT.
- transmitir pacotes de capturas de estágio como eles saem do mecanismo de firewall. Se o NAT estiver configurado,
estes serão pós-NAT.
- o estágio de firewall captura pacotes no estágio de firewall.

Para cada etapa, você pode atribuir um nome para o arquivo de saída e definir um pacote máximo ou contagem de byte:




Quando todas as etapas desejadas estiverem definidas, você pode mudar o botão de captura para ON, ou usar o CLI, limpar as
sessões existentes primeiro — para garantir que nenhuma sessão esteja ativa desde antes dos filtros serem ativados — e usar o
seguinte comando para iniciar a captura:


> clear session all

All sessions cleared

> debug dataplane packet-diag set capture on

Packet capture is enabled

Agora você pode iniciar as sessões que gostaria de capturar. Para verificar se a sessão foi iniciada, use o comando da sessão do
show:

> show session all

--------------------------------------------------------------------------------
ID          Application    State   Type Flag  Src[Sport]/Zone/Proto (translated IP[Port])
Vsys                                          Dst[Dport]/Zone (translated IP[Port])
--------------------------------------------------------------------------------
32637        web-
browsing   ACTIVE  FLOW  NS   192.168.0.34[61903]/trust/6  (198.51.100.230[31547])
vsys1                                          198.51.100.97[80]/ISP1  (198.51.100.97[80])
32635        ssh            ACTIVE  FLOW  NS   192.168.0.34[61901]/trust/6  (198.51.100.230[5281
## 2])
vsys1                                          198.51.100.1[22]/ISP1  (198.51.100.1[22])

Quando você terminar, a captura pode ser desligada, ligando o botão de volta para a posição OFF ou usando o comando de
depuração:

> debug dataplane packet-diag set capture off

Packet capture is disabled

> debug dataplane packet-diag clear filter-marked-session all

Unmark All sessions in packet debug


Agora serão capturados arquivos disponíveis para download que você pode analisar com Wireshark:


After you download the pcaps, you may need to merge the transmit and receive files together:
- The receive stage will have the client private IP to the web server public IP, and the returning packet from the web server
public IP  to the firewall external IP (receive stage is pre-NAT).
- The transmit stage will have the firewall external IP (client NAT) to the server public IP, and the returning public IP to the
client private IP.
As that may be a little confusing when you're trying to follow TCP stream, you'll want to take note of this important difference
between those two files.



These two stages will ensure you are able to verify if NAT is being applied properly. You can also see if there is any difference
between the packets sent out and received from both client and server perspective.

The merged result should look something like this and allows you to compare packet-per-packet what is being sent out and what is
being received.





Alguns artigos úteis para ajudá-lo a entender melhor como os pacotes fluem através do sistema:
Qual é o significado dos contadores globais?
Sequência de fluxo de pacotes no PAN-OS


Plano de gestão

Para solucionar problemas de conectividade com o plano de gerenciamento, o comando tcpdump incorporado pode ser usado
para capturar informações úteis:
admin@myNGFW> tcpdump filter "port 53"
Press Ctrl-C to stop capturing

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
## ^C
16 packets captured
32 packets received by filter
0 packets dropped by kernel

A saída resultante é armazenada em um arquivo mgmt.pcap no plano de gerenciamento:
admin@myNGFW> view-pcap mgmt-pcap mgmt.pcap
15:24:07.512889 IP 10.0.0.1.36606 > 10.0.0.98.domain:  49243+ PTR? 0.0.0.10.in-addr.arpa. (41)
15:24:07.513106 IP 10.0.0.98.domain > 10.0.0.1.36606:  49243 NXDomain 0/1/0 (100)
15:24:17.196515 IP 10.0.0.1.45455 > 10.0.0.98.domain:  3126+ PTR? 0.0.0.10.in-addr.arpa. (41)
15:24:17.196762 IP 10.0.0.98.domain > 10.0.0.1.45455:  3126 NXDomain 0/1/0 (100)
15:24:31.126186 IP 10.0.0.1.57230 > 10.0.0.98.domain:  2978+ A?
panos.wildfire.paloaltonetworks.com. (53)
15:24:31.126196 IP 10.0.0.1.57230 > 10.0.0.98.domain:  55173+ AAAA?
panos.wildfire.paloaltonetworks.com. (53)
15:24:31.161436 IP 10.0.0.98.domain > 10.0.0.1.57230:  2978 4/0/0[|domain]
15:24:31.194586 IP 10.0.0.98.domain > 10.0.0.1.57230:  55173 2/0/0[|domain]
15:25:56.746679 IP 10.0.0.1.46048 > 10.0.0.98.domain:  43532+ A? wildfire.paloaltonetworks.com.
## (47)
15:25:56.746689 IP 10.0.0.1.46048 > 10.0.0.98.domain:  16653+ AAAA?
wildfire.paloaltonetworks.com. (47)
15:25:56.794940 IP 10.0.0.98.domain > 10.0.0.1.46048:  43532 1/0/0 (63)
15:25:56.795553 IP 10.0.0.98.domain > 10.0.0.1.46048:  16653 0/1/0 (131)
15:25:59.038459 IP 10.0.0.1.51804 > 10.0.0.98.domain:  23806+ A?
panos.wildfire.paloaltonetworks.com. (53)
15:25:59.038471 IP 10.0.0.1.51804 > 10.0.0.98.domain:  31471+ AAAA?
panos.wildfire.paloaltonetworks.com. (53)
15:25:59.071431 IP 10.0.0.98.domain > 10.0.0.1.51804:  23806 4/0/0[|domain]
15:25:59.113552 IP 10.0.0.98.domain > 10.0.0.1.51804:  31471 2/0/0[|domain]

Confira este artigo para obter informações adicionais como capturar pacotes (tcpdump) na interface de gerenciamento





Informações adicionais

- Para controlar o tamanho do arquivo de captura de pacotes, um único arquivo é limitado a 200mb e um segundo arquivo é
criado automaticamente uma vez que o tamanho é excedido, ambos os arquivos agirão como um buffer de anel onde o arquivo
pcap principal é usado para escrever dados de captura ativo e o arquivo *.pcap.1 é usado como um buffer. Uma vez que o pcap
primário atinge sua capacidade novamente, o arquivo buffer é descartado, o arquivo principal é renomeado para *.pcap.1 e um
novo arquivo primário é iniciado. Mais informações aqui: Qual é a limitação do tamanho do arquivo de captura de pacotes no PAN-
## OS?
- Para pequenas capturas, pode ser útil capturar tudo em um único arquivo, por isso é possível ter cada captura de estágio para o
mesmo nome de arquivo. Por favor, esteja ciente da limitação acima mencionada no tamanho e da visibilidade reduzida para cada
etapa. O método recomendado é sempre ter um arquivo individual por etapa.

Uma vez que o PAN-OS 8.1.0, os filtros podem ser adicionados para sub-redes de origem e rede, isso está
disponível apenas através do CLI e NOT WebGU Eu:
admin@firewall> debug dataplane packet-diag set filter match
+ destination           Destination IP address
+ destination-netmask   Destination netmask              <<<< new option for network
+ destination-port      Destination port
+ ingress-interface     Ingress traffic interface name
+ ipv6-only             IPv6 packet only
+ lacp                  LACP packet
+ non-ip                Non-IP packet
+ protocol              IP protocol value
+ source                Source IP address
+ source-netmask        Source netmask                     <<<< new option for network
+ source-port           Source port
|                     Pipe through a command
<Enter>               Finish input

admin@firewall> debug dataplane packet-diag set filter match source 192.168.1.0 source-netmask
## 24

admin@firewall> debug dataplane packet-diag set filter match destination 192.168.2.0
destination-netmask 24

admin@firewall> debug dataplane packet-diag show setting

DP dp0:

--------------------------------------------------------------------------------
Packet diagnosis setting:
--------------------------------------------------------------------------------
Packet filter
Enabled:                   no
Match pre-parsed packet:   no
Index 1: 192.168.1.0/24[0]->0.0.0.0/0[0], proto 0 <<<<<<<<< network is captured /24
ingress-interface any, egress-interface any, exclude non-IP
Index 2: 0.0.0.0/0[0]->192.168.2.0/24[0], proto 0 <<<<<<<<< network is captured /24

ingress-interface any, egress-interface any, exclude non-IP
--------------------------------------------------------------------------------

Nota: Tenha cuidado ao permitir capturas amplas da rede, pode haver muitos pacotes resultantes de alto consumo de CPU de
dataplane e possível impacto no tráfego.
