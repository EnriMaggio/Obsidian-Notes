siccome opengl è soltanto una libreria per sviluppare applicazioni grafiche, oltretutto con più versioni, servono altri tools di supporto per girare una intera applicazione grafica
- [glfw](https://www.glfw.org/)
	una libreria api che permette di creare finestre e fare da window manager, è un intermediario tra sistema operativo e l'applicazione grafica. Inoltre gestisce gli eventi generati dall'utente 
	![[Pasted image 20250904121525.png]]
- visual studio
- cmake
- [glad](https://glad.dav1d.de/) 
	siccome opengl è uno standard o una specificazione, sta al produttore di driver di gpu, implementare questo standard in un driver per schede video specifiche in modo quest'ultime possono supportarlo
	Glad è una loading library che fornisce tutto il caricamento dei puntatori di funzione a OGL e le costanti (#define) per OGL moderno in modo automatico, se no bisognerebbe caricare manualmente
	ad esempio
	![[Pasted image 20250904120502.png]]
	![[Pasted image 20250904120520.png]]
	in questo se la versione di opengl del computer è vecchia rispetta alla versione di opengl dell'applicazione che deve girare su quel computer, quest'ultimo segnalerà errori e simboli non riconosciuti 
	![[Pasted image 20250904121019.png]]
	la soluzione che hanno pensato è quella che ogni sistema operativo fornise una libreria dinamica per una versione minima di opengl (es 1.1)
	![[Pasted image 20250904120950.png]] ogni funziona di estensione nuova deve essere caricata usando un meccanismo di getprocaddress del sistema operativo.
	Qua è dove entra in gioco glad o librerie simili, perchè è molto probabile che le funzioni di estensione da caricare siano moltissime e autonomamente non si può gestire tutti questi puntatori
--- 
[link video](https://www.youtube.com/watch?v=LzwXHuMu6PU)