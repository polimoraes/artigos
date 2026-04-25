# Como o protocolo LoRaWAN garante a segurança dos dados.
*20 de maio de 2019*
*Por Poliana de Moraes*

No artigo anterior apresentamos o protocolo LoRaWAN, neste artigo temos como objetivo demonstrar suas propriedades que buscam garantir a segurança dos dados.

O LoRaWAN é um protocolo que implementa criptografia de fim-a-fim,  os dados são criptografados dos dispositivos finais até o servidor de aplicativos [2].  As propriedades fundamentais suportadas são:

• Autenticação mútua: assegura a autenticidade dos dispositivos, garantindo que apenas dispositivos autorizados conectem-se a rede.
• Proteção a integridade: garante que as mensagens não foram modificadas.
• Confidencialidade: garante que a mensagem não será lida por terceiros.

O LoRaWAN utiliza o algoritmo criptográfico padrão AES combinado com modo operacional. Os dados são criptografados na camada de aplicação pelo AES-CTR e acompanha um contador para evitar a repetição do pacote.  Além disso, temos na camada de enlace de dados  a  geração  de  um  código  de  integridade  de  mensagem  (MIC)  calculado  com AES-CMAC para evitar a adulteração de pacotes.

Desta forma,  o protocolo utiliza 2 camadas de segurança,  uma na rede e outra na aplicação.  A criptografia na camada de rede assegura a autenticidade do dispositivo, enquanto a criptografia na camada de aplicação garante a autenticidade e integridade dos dados.  Como os dados são criptografados antes e o servidor de rede não possui a chave de  segurança  para  descriptografá-los,  o  operador  da  rede  não  tem  acesso  aos  dados  da aplicação.

Existem 2 conjuntos de chaves de segurança: as chaves raízes e as chaves de sessão:

As chaves raízes são usadas para ativação do dispositivo na rede.

• AppKey:  é uma chave AES-128 definida durante a fabricação do dispositivo para sua ativação na rede após primeira conexão.
• NwkKey:  é uma chave AES-128 definida durante a fabricação do dispositivo para sua ativação na rede após primeira conexão.

Chaves de sessão são usadas para troca de dados na rede após o dispositivo ter sido ativado.

• AppSKey: é usada pelo servidor de aplicação e pelo dispositivo para criptografar e decriptografar o pacote de dados.
• FNwkSIntKey:  é uma chave de segurança de sessão para o dispositivo usar para cálculo do MIC em mensagens enviadas.
• SNwkSIntKey:  é uma chave de segurança de sessão para o dispositivo usar para verificação do MIC em mensagens recebidas.
• NwkSEncKey:  é uma chave de segurança de sessão para o dispositivo usar paracriptografar e decriptografar os comandos MAC.

Cada dispositivo deve ter seu conjunto único de chaves, assim se a chave for divulgada somente um dispositivo será afetado.

O dispositivo deve ser ativado ao integrar a rede LoRaWAN. Existem duas formas para a ativação acontecer:

• Ativação por Personalização (ABP)
A ativação por personalização não executa o processo de ativação,  portanto não há necessidade de chaves raízes.  Neste caso, as 4 chaves de sessão e o endereço do dispositivo são diretamente gravadas no dispositivo e nos demais componentes correspondentes na rede.

• Ativação pelo Ar (OTAA) 
As chaves raízes e o DevEUI são geradas no servidor de ativação e gravadas durante processo de manufatura ou comissionamento no dispositivo. Quando o dispositivo é conectado pela primeira vez na rede, o servidor de rede receberá uma solicitação de ativação e a encaminhará ao servidor de ativação associado.  O servidor de ativação checa a autenticidade do dispositivo e usa as chaves raízes e o DevEUI  para derivar as chaves de sessão e o endereço do dispositivo. A chave de sessão de aplicação é encaminhada ao servidor de aplicação, as chaves de sessão de rede são encaminhadas ao servidor de rede.  O servidor de ativação também encaminha ao servidor de rede a mensagem de aceitação do dispositivo e as informações de endereço do dispositivo de 32-bit e o conjunto de dados que permitem ao dispositivo a geração das chaves de sessão para início de troca de dados. 

Quando analisados os dois processos de ativação existentes, pode se dizer que para aplicações que necessitam de maior segurança a ativação pelo ar é mais indicada.

Quais vulnerabilidades você consegue identificar no protocolo LoRaWAN?

#embarcados #IoT #projeto #inovação #software #hardware
