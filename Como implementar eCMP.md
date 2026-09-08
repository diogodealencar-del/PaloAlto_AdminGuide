

Como implementar eCMP (Balanceamento de carga) no Palo Alto Firewall
Visão geral

Equal Cost Multipath (ECMP) é um novo recurso introduzido no PAN-OS 7.0. Ele fornece suporte multicaminho para rotas de
"custo igual" que vão para o mesmo destino. Há um máximo de 4 caminhos de custo iguais suportados

Sem esse recurso, se houver várias rotas de custo igual para o mesmo destino, o roteador virtual escolhe uma dessas rotas a
partir da tabela de roteamento e a adiciona à sua tabela de encaminhamento; não usará nenhuma das outras rotas a menos
que haja uma paralisação na rota escolhida.

O balanceamento de carga ECMP é feito no nível da sessão, não no nível do pacote — o início de uma nova sessão é quando
o firewall (ECMP) escolhe um caminho de custo igual

Este artigo foca na configuração básica para alcançar o ECMP no firewall

## Detalhes

Topologia utilizada para este artigo:
## =======================




Configuração da interface:



Nota: ethernet1/1 e ethernet1/11 são interfaces isp configuradas em diferentes zonas L3-Untrust e VPN, respectivamente.
No entanto, essas interfaces podem ser configuradas na mesma região também


Configuração de rota com ambas as rotas padrão com "custo igual":




Política NAT para poder direcionar o tráfego pela internet:



Nota: Se ambas as interfaces de ISP estiverem na mesma região, as interfaces de destino precisarão ser adicionadas à diretiva
NAT como na captura de tela a seguir:




Configuração  da  diretiva  de  segurança  para  permitir  o  tráfego:  (cobre  ambos  os  cenários  quando  as  interfaces  estão  na
mesma ou zona diferente)




Ativando o ECMP no firewall:





## Nota:
- Max Path 2 significa que apenas 2 caminhos de custo iguais serão instalados na tabela FIB. Se houver mais de 2 caminhos
de custo igual que precisam ser instalados na tabela FIB, altere o valor do Max Path. O valor máximo suportado é 4.
- O método  de balancete  de  carga  pode ser  selecionado  de  acordo  com  a exigência.  Para  obter mais  informações  sobre o
algoritmo de equilíbrio de carga, clique aqui
- Habilitar o Retorno Simétrico se o pacote de resposta for enviado na mesma interface em que o pacote de solicitação entrou.


Verifique se o ECMP está funcionando:

Monitor > Registros de tráfego (com zona diferente)




Monitor > Registros de tráfego (com a mesma zona)




A rota instalada para ECMP tem um sinalizador "E" nele:





