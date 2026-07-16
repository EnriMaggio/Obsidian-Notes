#### Data: 04/11/2024 - 15:48

![[Pasted image 20241105095311.png]]

é il primo esempio di cyber weapon nel mondo. Questo attacco è molto sofisticato per vari motivi
- sfruttamento di quattro vulnerabilità 0 day
- complessità avanzata del codice
- grandezza del codice (500k)
- furto di due certificati da CA
- target specifici plc

Stuxnet era un worm molto avanzato che si pensa sia stato creato dagli stati uniti in conbutta con israele ai danni della campagna nucleare dell'iran.

Il target principale erano i PLC (computer specializzati che in questo caso controllavano le centrifughe) sfruttando vulnerabilità al software Step7 che vanno interagire direttamente con i plc

La fase di reconaissance è più un errore del governo iraniano, che ha mostrato in televisione l'interno degli uffici e anche gli stabilimenti della centrale nucleare. Oltre allo spionaggio di cui non si saprà tecnicamente niente, si è verificato una sorta di [[SHOULDER SURFING]]
Essendo il complesso iraniano una struttura "Air gapped", ovvero un sistema chiuso che funziona all'interno senza interfacciarsi all'esterno (niente accesso ad internet) il worm è stato introdotto tramite una chiavetta usb infetta contenente

- autorun.inf malevolo
- il payload malevolo

L'autorun.inf è un file che permette a windows ci eseguire automaticamente un file all'interno della chiavetta quando viene inserita nella porta usb. L'autorun in stuxnet non andava a eseguire un file esterno ma il payload malevolo era contenuto all'interno di esso

![[Pasted image 20241105101647.png]]

In aggiunta stuxnet sfruttò la o day vulnerabilità di [[LNK windows]], usandolo come scorciatoia per puntare al codice del worm piuttosto che windows shell, l'icona del LNK veniva visto dal windows explorer e caricava l'icona che però andava ad eseguire il codice senza interazione umana. Questa vulnerabilità entrava in azione se autorun era disattivato da windows

![[Pasted image 20241105101441.png]]

Dopo l'installazione sui computer ormai infetti, il worm prova a contattare uno dei due server usando il protocollo HTTP

- www. mypremierfutbol .com 
- www. todaysfutbol. com

Serve all'attaccante per ricevere le informazioni di interesse e anche per inviare aggiornamenti al worm 

Il worm si avvale anche di tecniche di elevazione dei privilegi

Il target che il worm modificava erano i plc che giravano il software step7, gli attaccanti hanno sfruttato la libreria dinamica s7otbxdx.dll che ha il compito di comunicare effettivamente con il plc per leggere o modificare il codice, stuxnet wrappava questa libreria 

![[Pasted image 20241105102602.png]]
![[Pasted image 20241105102720.png]]

Il codice del plc modificato serviva ad aumentare la velocità in termini di hertz delle centrifughe della centrale nucleare per farle esplodere, ma questo avvenne dopo 30 giorni dall'installazione del worm. In questo tempo il worm raccoglieva dati sulla centrifughe, in modo da rimostrarli al prossimo test delle centrifughe per mascherare il vero flusso controllo controllato dagli attaccanti (è come mettere in una telecamera di sicurezza di una banca in loop una scena tranquilla dove non avviene niente quando in realtà sta accadendo tutt'altro) ovviamente a insaputa degli ingegneri

![[Pasted image 20241105103743.png]]
#### REFERENZE: https://www2.cs.arizona.edu/~collberg/Teaching/466-566/2012/Resources/presentations/2012/topic9-final/report.pdf, https://www.youtube.com/watch?v=EOPLN-MVKY4&pp=ygUHc3R1eG5ldA%3D%3D