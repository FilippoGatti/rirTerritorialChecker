# RIR Territorial Checker

Uno strumento specialistico progettato per la pronta identificazione di stabilimenti a **Rischio di Incidente Rilevante (RIR)** — ai sensi della Direttiva Seveso — all'interno di un comune target o nei comuni immediatamente confinanti.

Il tool risolve il problema della frammentazione dei dati territoriali, permettendo di incrociare la cartografia ufficiale con database tabellari.

## Funzionalità

L'applicazione è una Single Page Application che integra due moduli:

1.  **Analizzatore Topologico:** Elabora i confini amministrativi per mappare le adiacenze. Grazie all'uso di un indice spaziale **R-Tree**, è in grado di processare l'intero territorio nazionale in pochi secondi direttamente nel browser.
2.  **Motore di Ricerca Incrociata:** Caricando un dataset in formato Excel (elenco stabilimenti RIR), il sistema estrae automaticamente tutte le occorrenze relative al comune selezionato e a tutti i comuni confinanti, garantendo una visione d'insieme del rischio d'area.

## Caratteristiche Tecniche

* Non richiede installazione, server o database. Funziona interamente lato client (browser).
* I dati caricati (Excel/JSON) vengono elaborati nella memoria RAM locale e non vengono mai trasmessi o salvati su server esterni.
* Utilizza le librerie **Turf.js** per i calcoli geometrici e **RBush** per l'indicizzazione spaziale ad alta velocità.
* Gestione dinamica delle colonne Excel per adattarsi a modifiche del database o a diverse fonti.

## Dataset di Riferimento

Il progetto include il file `adiacenze_italia_2026.json`, che contiene la rete di vicinato di tutti i comuni italiani calcolata sui confini amministrativi più recenti. Questo permette di:
* Superare i limiti dei confini regionali durante le analisi.
* Identificare rischi transfrontalieri (es. stabilimento in provincia limitrofa ma confinante).

## Fonti

I dati cartografici utilizzati per la generazione delle adiacenze sono derivati dalle basi territoriali ufficiali:
* **ISTAT (Istituto Nazionale di Statistica):** Confini amministrativi 2026. I dati sono rilasciati sotto licenza Creative Commons Attribuzione (CC BY 3.0 IT).
* **Elaborazione:** La creazione del file GeoJson è stata eseguita tramite software GIS, mentre la trasformazione topologica e la semplificazione delle geometrie sono state eseguite tramite script personalizzati inclusi in questo repository.

## Licenza

Questo progetto è distribuito sotto **Licenza MIT**. 
È possibile utilizzare, copiare e modificare il software per qualsiasi scopo, a condizione che venga mantenuta la citazione dell'autore originale e il riferimento alla licenza.
