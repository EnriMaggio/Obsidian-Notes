Il rilevamento discreto delle collisioni controlla le collisioni tra oggetti in momenti specifici nel tempo, in genere all'inizio di ogni frame o fase fisica. È un metodo efficiente dal punto di vista computazionale, ma può perdere le collisioni se gli oggetti si muovono molto rapidamente e si incrociano tra i controlli.

questo fenomeno è detto tunnelling ed è sempre possibilie nella collisione discreta, perchè se le particelle sono molto veloci, esse possono uscire dai bordi, oppure entrare dentro altre particelle tra due frame.

Per ridurre il rischio di tunneling si può:
- limitare la velocità della pallina
- aumentare i framerate dell'animazione