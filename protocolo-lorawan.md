# Entenda o protocolo LoRaWAN utilizado em aplicações de internet das coisas.
*13 de maio de 2019*

*Por Poliana de Moraes*

Este artigo traz uma visão geral sobre o protocolo LoRaWAN que é amplamente utilizado em aplicações de internet das coisas que necessitam de alcance a longas distâncias como cidades e agricultura.

A LoRa Alliance é uma organização fundada em 2015 por líderes industriais do mercado da tecnologia e tem como objetivo padronizar as redes de comunicação de grandes áreas e baixa potência (LPWAN) para implantar as tecnologias IoT, M2M e aplicações industriais em todo o mundo. Neste contexto foi criado o protocolo LoRaWAN um padrão aberto referente a camada de enlace de dados do modelo OSI baseado na tecnologia proprietária da Semtech chamada LoRa.

O protocolo LoRaWAN define a arquitetura e todo o mecanismo de operação para a rede. Considerando a enorme preocupação atual de ataques cibernéticos, LoRaWAN foi desenvolvido estabelecendo a segurança de dados fim-a-fim.  Este trabalho apresenta os mecanismos de segurança definidos no protocolo LoRaWAN.

A comunicação no protocolo LoRaWAN é bidirecional.  As mensagens enviadas dos dispositivos ao servidor são assíncronas e, portanto, o dispositivo só conecta-se ao servidor e envia mensagem quando necessário. Já as mensagens enviadas do servidor para os dispositivos são classificadas em 3 classes, buscando assim a eficiência no consumo energético do dispositivo. Abaixo são apresentadas as 3 classes:

+ Classe A - Sensores operados a bateria:  envio de mensagens ao dispositivo ocorre em 2 pequenas janelas (+/- 20 micro segundos) que são abertas após o dispositivos enviarem mensagem ao servidor. Esta é a estratégia que possibilita menor consumo energético.

+ Classe B - Atuadores operados a bateria:  além da estratégia utilizada na classe A, esta classe também especifica janelas de tempo para envio de mensagens aos dispositivos.  No entanto, neste caso é necessário o envio de beacons para sincronizar o tempo.

+ Classe C - Dispositivos essencialmente alimentados: a janela de recepção de mensagens fica aberta permanentemente, sendo fechada somente quando o dispositivo está transmitindo mensagem. Porém, há um alto consumo energético.

Os dispositivos devem satisfazer pelos menos a propriedade descrita na classe A.

A pilha de protocolo consiste em 3 camadas: camada física, camada de enlace de dados e camada de aplicação, como mostrado na figura abaixo.

![](figuras/pilha-LoRa.avif)

+ A camada de aplicação ocupa-se dos dados que são transmitidos na rede.

+ A camada de enlace de dados implementa o protocolo LoRaWAN de acordo com a versão do protocolo e tipo de mensagem definidos.

+ A camada física é implementada pela tecnologia de transmissão de dados sem fio LoRa.


A rede LoRa é formada pela conexão de um grande número de dispositivos.  É aplicada a topologia estrela na qual os dispositivos enviam mensagens via radiofrequência para o gateway.  Como não há um gateway específico associado aos dispositivos, mais de um gateway pode receber a mensagem.  Os gateways transmitem a mensagem via conexão IP para o servidor de rede, no qual o pacote de dados é analisado.  Após, a mensagem é enviada ao servidor de aplicação correspondente, onde o dado é processado. Para os casos onde o dispositivo é ativado somente quando ocorre sua primeira conexão a rede, é necessário o servidor de ativação. 

Cada componente tem sua função específica no sistema:

![](figuras/rede-lorawan.avif)

+ Dispositivos:  responsáveis por coletar e transmitir os dados na rede.  Eles podem ser móveis ou fixos.

+ Gateway: responsáveis por transferirem as mensagens dos dispositivos ao servidor de rede correspondente.

+ Servidor  de  rede:  responsável  por  gerenciar  toda  a  rede.   Este  servidor  elimina as mensagens duplicadas e realiza a verificação da autenticidade das mensagens. Após, faz o roteamento da mensagem ao servidor de aplicação ou servidor de ativação correspondente.

+ Servidor de aplicação: responsável por processar e tomar todas as ações relacionadas com os dados. É o servidor final.

+ Servidor de ativação:  responsável pela autenticação dos dispositivos.  Ele gera as chaves raízes do dispositivo e do DevEUI. Também executa a operação que gera as chaves de sessão associadas e o endereço do dispositivo.

Quais aplicações você acredita ser interessante a aplicação do protocolo LoRaWAN?

#embarcados #IoT #projeto #inovação #software #hardware
