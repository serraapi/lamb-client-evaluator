<p align="center">
  <img src="icona_avaluador.png" width="110" alt="Logotip de l'Avaluador de converses">
</p>

<h1 align="center">LAMB Client Evaluator</h1>

<p align="center">Recull les notes dels clients simulats i les passa a un Excel</p>

---

Eina web estàtica (un sol fitxer HTML) que acompanya el **LAMB Client Generator**. Llegeix les converses que l'alumnat ha tingut amb els clients simulats, n'extreu la nota que el client ha posat en mode avaluació, comprova que no s'hagi manipulat i ho exporta tot a un Excel per passar les notes a l'Atenea (Moodle).

No cal instal·lar res: n'hi ha prou d'obrir el fitxer HTML en un navegador. Els fitxers es llegeixen al navegador i no s'envien enlloc.

### Característiques principals

* **Lectura directa de l'Atenea:** accepta el `.zip` de «Baixa totes les trameses» d'una tasca i identifica cada alumne pel nom del fitxer. També accepta fitxers `.txt` solts.
* **Notes verificades:** en acabar l'avaluació, el client escriu una línia oculta i xifrada (`[//]: # (REF: …)`) amb les notes de cada criteri. L'eina la desxifra i, si l'alumne ha retocat la taula visible, compta la nota del codi i n'avisa.
* **Avisos:** detecta si falta la línia, si té codis inventats o fora de lloc, si és d'un client que no s'ha carregat, si dos alumnes han lliurat la mateixa conversa, si un alumne n'ha lliurat més d'una o si l'avaluació és provisional.
* **Càlcul amb la rúbrica:** recalcula el total amb la fórmula 1,5 × (A + B) + C + … + I, sense els criteris N/O i normalitzat sobre 100.
* **Protecció bàsica i avançada:** els clients amb protecció bàsica funcionen sense fer res. Per als que tenen protecció avançada (una clau pròpia per client), s'activa **Protecció avançada** i s'hi arrossega el JSON del client un sol cop: la clau queda desada al navegador. El commutador s'activa sol quan arriba una conversa amb una clau desconeguda.
* **Visor de converses:** cada conversa es pot obrir en un panell lateral amb bombolles de xat, redimensionable o en finestra flotant.
* **Gestió de la llista:** permet treure converses d'una en una o seleccionar-ne diverses.
* **Exportació a Excel (`.xlsx`):** alumne, ID de l'Atenea, notes per criteri, total proposat, avisos i una columna **Nota validada** per al professor.
* **Interfície en català, castellà i anglès,** amb tema clar i fosc.

> Les notes són **propostes de la IA**: cal revisar els avisos i comprovar-ne algunes abans de donar-les per bones.

### Com es fa servir

**Abans de l'activitat**

1. Fes el client amb el **Generador de Clients v0.6.3** o posterior.
2. Si vols una clau pròpia per al client, activa el mode avançat del generador i, a la pestanya **Avaluació**, tria la protecció **avançada**.
3. Crea una **tasca** a l'Atenea amb lliurament de fitxers.

**Alumnes**

1. En acabar l'entrevista, escriuen el codi d'avaluació («Code 42» per defecte) i esperen que el client avaluï l'entrevista.
2. Al menú **⋯** de la conversa trien **Download → Plain text (.txt)**.
3. Pugen el `.txt` a la tasca, sense editar-lo.

**Professor**

1. A la tasca, **Mostra totes les trameses → Baixa totes les trameses**.
2. Obre l'avaluador i arrossega el `.zip` a la zona gran.
3. Si el client té protecció avançada, activa **Protecció avançada** i, el primer cop, arrossega-hi el JSON del client.
4. Revisa els avisos i obre les converses que calgui.
5. Descarrega l'Excel, omple la columna **Nota validada** i passa les notes a l'Atenea.

### Compatibilitat

* Converses de clients fets amb el **LAMB Client Generator v0.6.3** o posterior.
* Converses exportades en `.txt` des del xat de LAMB (Open WebUI).
* Qualsevol navegador actual (Chrome, Edge, Firefox, Safari).
