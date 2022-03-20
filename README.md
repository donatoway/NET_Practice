# NET_Practice

# Cos'é il TCP/IP

Il protocollo TCP/IP indica l'uso combinato di 2 protocolli (un protocollo è un insieme di regole)
per la trasmissione di dati su internet, TCP (Trasmission Control Protocol) e IP (Internet Protocol).
Il protocollo TCP crea la connessione tra 2 host e gestisce la consegna da un sistema all'altro, mentre il protocollo IP fornisce le istruzioni per il trasferimento di dati. Per dividere questi 2 protocolli si utilizza una subnetMask

# Indirizzi IP publici e indirizzi IP privati

Public Ip : un indirizzo publico puó essere raggiunto direttamente dall' esterno quindi da internet ed é assegnato dal tuo router tramite il tuo Provider. Un Public Ip ti aiuta a connetterti dall'interno del tuo network all'esterno.

Private Ip: Un indirizzo Ip Privato é cio che il tuo router assegna al tuo device. Ogni device
dentro lo stesso network é assegnato un unico indirizzo Ip privato. Cosí è come comunicano i tuoi
device all'interno dello stesso network tra loro.

Quando un Network é connesso a internet non è possibile usare un IP address dal range PRIVATE IP ADDREES ovvero :

192.168.0.0 – 192.168.255.255 (65,536 IP addresses)

172.16.0.0 – 172.31.255.255   (1,048,576 IP addresses)

10.0.0.0 – 10.255.255.255     (16,777,216 IP addresses)


# SUBNET MASK

Una subnet Mask è un indirizzo composto da 32 bits usato per dividere un Network Address e un Host Address Nell' indirizzo IP . La Subnet Mask definisce il range di indirizzi IP che possono essere usati dentro un Network o una Subnet.


# Come trovare Il Network Address

Un'Interfaccia A ha le seguenti proprietá:

IP address | 104.198.241.125                                                  

Mask       | 255.255.255.128

Per determinare quale porzione dell'IP è il Network Address, abbiamo bisogno di Applicare la SubnetMask.
Convertiamo prima la Mask nella forma Binaria :

Mask | 11111111.11111111.11111111.10000000 

I bits di una mask corrispondenti all' 1 rappresentano il network address, mentre i rimanenti 0  rappresentano l'host address. Convertiamo adesso l'IP address nel suo binario.

IP address | 01101000.11000110.11110001.01111101

Mask       | 11111111.11111111.11111111.10000000

Applicano il bitwise And avremo (sovrapponendo i due binari) dove in entrambi i casi c'é un 1
prevale l'1 mentre negli altri casi 0 quindi:

Network address | 01101000.11000110.11110001.00000000

che in decimale equivale a 104.198.241.0

Come trovare il Range degli Host addresses

Per determinare quale Host Address dobbiamo usare nel nostro network, dobbiamo usare i Bits del nostro Ip Address dedicato All'host Address. Usiamo i precedenti Valori:

IP address | 01101000.11000110.11110001.01111101

Mask       | 11111111.11111111.11111111.10000000

Il Range Possibile é rappresentato dagli ultimi 7 bits che sono tutti 0. Quindi il Range sarà :

BINARY  | da 0000000 -  a 1111111

DECIMAL | da 0 - a 127

Per ottenere il nostro Range dei possibili indirizzi Ip assegnabili per il nostro Network, aggiungiamo il range dell'host address al Network Address. Il nostro Ip Address diventa

104.198.241.0 - 104.198.241.127

Tuttavia le estremità non sono utilizate poiche hanno usi specifici per usi specifici

104.198.241.0   | Reserved to represent the network address.


104.198.241.127 | Reserved as the broadcast address; used to send packets to all hosts of a network.


# CIDR Notation (/24)

La Mask puo inoltre essere rappresentata come Classless Inter-Domain Routing (CIDR). Questa
rappresenta la Mask con uno Slash "/"", seguito dal numero di bits  che servono come Network Address

Quindi, La Mask nell'esempio seguente 255.255.255.128, è /25, dato che ci sono 25 bits su 32
che rappresentano il Network Address.


# Come convertire un Ip decimale in binario :

Link : https://www.guidetti-informatica.net/2021/04/impara-i-numeri-binari-e-decimali-in-rete-parte-10/

# Come convertire un Numero binario in Decimale :

Link : https://www.wikihow.it/Convertire-un-Numero-dal-Sistema-Binario-a-Quello-Decimale

# Cos'è nuo Switch

Uno switch connette multipli devices insieme in un singolo network. A differenza del router, 
lo switch non ha nessuna interafaccia, ha solo il compito di distribuire i pacchetti all' interno del Network e non può comunicare direttamente al di fuori del suo network.

Se vuoi conoscere alcune curiosità sullo Switch : Link https://www.zerounoweb.it/techtarget/searchdatacenter/configurazione-di-rete-e-significato-dello-switch-tecnologia-storia-e-vantaggi/

# Cos'é un Router 

Un Router connette sia i devices ma anche diverse Reti Network  tra loro. Il Router ha un Interfaccia
per ogni Network a cui si connette.
Poiché il router separa diverse reti, l'intervallo di possibili indirizzi IP su una delle sue interfacce non deve sovrapporsi all'intervallo delle altre sue interfacce. Una sovrapposizione nell'intervallo di indirizzi IP implicherebbe che le interfacce si trovano sulla stessa rete.

https://betaingegneria.it/wp-content/uploads/2021/01/routing_intro.png

Tabelle di Routing

Una tabella di routing é una tabella di dati salvata in un router o un Network Host che da informazioni su come raggiungere e collegarsi al prossimo Network. In NetPractice,il routing
table è composto da 2 elementi:

Destination: Destinazione: la destinazione specifica un indirizzo di rete su cui un host è la destinazione finale dei pacchetti. Il percorso di default o 0.0.0.0/0, è il percorso che ha effetto quando nessun altro percorso è disponibile per un indirizzo di destinazione IP. Il percorso predefinito utilizzerà l'indirizzo dell'hop successivo per inviare i pacchetti in viaggio senza fornire una destinazione specifica. Il percorso predefinito corrisponderà a qualsiasi rete.

Next hop: The next hop refers to the next closest router a packet can go through. It is the IP address of the next router on the packet's way. Every single router maintains its routing table with a next hop address.



