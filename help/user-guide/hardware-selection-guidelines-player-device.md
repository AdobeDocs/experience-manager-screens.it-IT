---
title: Linee guida per la selezione dell'hardware per i dispositivi del lettore
description: Linee guida per la selezione dell'hardware per i dispositivi del lettore
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# Linee guida per la selezione dell&#39;hardware per il dispositivo del lettore {#hardware-selection}

La sezione seguente fornisce le linee guida per la selezione dell’hardware per un lettore AEM Screens.

## Considerazioni importanti {#important-considerations}

* Sorgente sempre ***Commerciale*** o ***Industriale*** Componenti di livello sia per il lettore PC che per il display o il proiettore.

* Interagisci sempre con i fornitori che operano nel mercato del digital signage.
* Considera sempre fattori ambientali quali la temperatura ambiente e l’umidità relativa.
* Controllare sempre i requisiti di alimentazione e il condizionamento dell&#39;alimentazione.
* Esaminare attentamente le prestazioni richieste e le porte di I/O richieste per l&#39;applicazione.

## Configurazioni hardware {#hardware-configurations}

La tabella seguente riepiloga le configurazioni hardware con casi d’uso tipici per un progetto AEM Screens:

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>Configurazione lettore</strong></td>
   <td><strong>Processore</strong></td>
   <td><strong>Memoria</strong></td>
   <td><strong>SSD di storage</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>Visualizzazione</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>Casi d’uso tipici</strong></td>
  </tr>
  <tr>
   <td>Base</td>
   <td>Processore Intel® Atom dual-core, i3 o quad-core entry-level</td>
   <td><p>4 GB di memoria</p> <p>2 MB di cache</p> </td>
   <td><p>·ChromeOS 32 GB</p> <p>·Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI<br /> Ethernet/wireless,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Ciclo a schermo intero standard<br /> </li>
     <li>Ripartizione giornaliera</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Standard</td>
   <td>Quad-core, processore Intel® Core i5</td>
   <td><p>8 GB di memoria</p> <p>4 MB di cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/wireless,<br /> 2x USB</td>
   <td>
    <ul>
     <li>Contenuto dinamico a sorgente singola</li>
     <li>Interattivo semplice</li>
     <li>1-3 Layout di zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avanzate </td>
   <td>Quad-core con hyperthreading, processore Intel® Core i7</td>
   <td><p>16 GB di memoria</p> <p>8 MB di cache</p> </td>
   <td>256 GB</td>
   <td>GPU grafica dedicata</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet/wireless,<br /> 4x USB</td>
   <td>
    <ul>
     <li>4 o più aree di contenuto, riproduzione video simultanea</li>
     <li>Interattivo a più pagine</li>
     <li>Attivatori dati multi-sorgente</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
