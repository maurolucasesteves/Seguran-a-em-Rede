# Segurança-em-Rede
Curso Alura para Teste de Segurança 

Teremos o computador do hacker, que será o Kali Linux.
Começaremos o curso falando o que o hacker poderá usar como vantagem de alguns equipamentos de rede, como o hub. E, por meio de uma análise de protocolo, visualizar o que a vítima está acessando. Depois, veremos de quais formas o hacker tentará comprometer o funcionamento de um switch. Ele o fará, por meio de um programa de emulação que veremos também, para tentar visualizar o que está trafegando do lado da vítima, e obter informações que ele não deveria.

Quais são algumas das limitações que possuímos no uso dos hubs?
Os hubs não conseguem “aprender” qual equipamento está conectado em cada porta. Dessa forma, ele repassa a informação para todas as suas portas, causando uma lentidão em nossa rede, assim como uma potencial vulnerabilidade de segurança visto que um usuário mal-intencionado poderá fazer o uso de análises de protocolos de rede para decifrar o que uma possível vítima estava acessando.

Iremos agora verificar o que um usuário mal intencionado poderá fazer para analisar protocolos que estão passando na rede.

Abra o Wireshark, que deve ter sido instalado junto com o GNS3.
Escolha a placa de rede de seu computador.
No filtro, coloque o protocolo HTTP.
Como fizemos no vídeo, abra um site que utilize o protocolo HTTP, por exemplo o blog da Alura.
Volte para o Wireshark e procure pela requisição GET.
Tente encontrar na análise mais detalhada, informações da página acessada. Qual o resultado?
Vamos repetir a análise do Wireshark.

Caso tenha interrompido a análise, clique no botãoWireshark_botao
Entre agora no link: http://exemplo-login-fraco-alura.herokuapp.com/login (A página poderá demorar alguns segundos para aparecer)
Coloque um usuário e senha de sua preferência e clique em Logar
Clique com o botão direito do mouse em Inspecionar Elemento e veja como está o HTML desse formulário. Qual requisição está sendo usada?
Em seguida, volte ao Wireshark e procure pela requisição encontrada. É possível ver o usuário e senha digitados?
Antes de realizar os ataques precisamos fazer o download de nossas máquinas virtuais:

Primeiramente, realize o download do VirtualBox para seu sistema operacional, ele irá gerenciar nossas máquinas virtuais
Posteriormente realize o download da máquina do hacker, o Kali Linux (64 bits).

 Instalando o GNS3
 Vamos realizar a instalação do GNS3 programa que será capaz de emular equipamentos de rede e que já vem instalado o Wireshark:

Acesse este https://github.com/GNS3/gns3-gui/releases/tag/v1.5.2 e faça o Download referente ao seu sistema operacional.

Windows: GNS3-1.5.2-all-in-one.exe
Mac: GNS3-1.5.2.dmg
Linux: GNS3-1.5.2.source.zip
Durante o processo de instalação, desmarque a opção referente ao SolarWinds Response e marque todas as outras opções, inclusive o Npcap
Caso a instalação pergunte no fim se queremos uma licença trial do SolarWinds selecionamos a opção No

Qual seria uma das formas mais efetivas que um hacker pode vir a comprometer o funcionamento de um switch?
Uma das formas seria "lotar" a memória do switch com uma grande quantidade de endereços mac. Uma vez que a memória do switch esteja cheia, o switch não conseguirá mais distinguir quem está conectado em cada porta e passa a atuar como um hub.
O hacker pode vir a comprometer o funcionamento de um switch ao "lotar" essa memória com uma série de endereços mac. Uma vez que essa memória está cheia, o Switch não consegue distinguir que máquina está conectada em cada porta e dessa forma, ele passará a atuar como se fosse um hub.
Abra o GNS3 e caso o programa pergunte se desejamos configurar um servidor, clique no botão Cancel.
Salve o nome do projeto como Switch.
Na aba lateral esquerda:

Clique no segundo ícone e arraste o Switch para a área de trabalho
Clique no terceiro ícone e arraste para área de trabalho o ícone Host.
Clique no terceiro ícone e arraste para a área de trabalho dois ícones VPCS que serão os computadores virtuais do GNS3.
Clique no sexto ícone, dos cabos e conecte os computadores em uma entrada do Switch. No ícone host, escolha a placa de rede do VirtualBox.
O resultado final deverá estar parecido com a imagem abaixo:
[image](https://user-images.githubusercontent.com/50851060/208672988-32c03f34-fcf5-48bf-ab2b-90db6608b63f.png)
Em seguida, clique no botão verde Start. Feito isso, todas as portas deverão estar com a cor verde.
Na sequência, clique no botão de Console que está ao lado do botão de Start.
Vá ao VirtualBox, inicialize o Kali Linux
Abra o terminal no Kali Linux e verifique o endereço IP através do comando ifconfig.
[image]https://s3.amazonaws.com/caelum-online-public/seguranca-redes/Kali_ip.JPG
Para que os equipamentos possam se comunicar, eles precisam estar na mesma rede. Configure o PC1 e PC2 para estarem na mesma rede do Kali Linux, usando a seguinte comando: ip [endereço IP] [máscara de rede]. Por exemplo:
[image]https://s3.amazonaws.com/caelum-online-public/seguranca-redes/Console_ip.JPG
Ao configurar os endereços IP nos dois computadores virtuais, faça um PING contínuo entre eles através do comando ping [IP] -t.

Clique com o botão direito do mouse no link conectado ao Hacker, e selecione a opção Start Capture.
Vá até o terminal do Kali Linux e realize o ataque para "lotar a memória" do Switch através do comando macof -i [interface].
No Wireshark, coloque um filtro para ver a comunicação entre os outros dispositivos: ip.addr==[endereço IP de um dos VPCS].

