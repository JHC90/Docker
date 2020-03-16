<h2><a name="_Toc4480367">Exemplarische Befehlsaufschlüsselung am Beispiel
MS-SQL Server</a></h2>

<p class=MsoNormal>Bei der Instanz-Erstellung muss außerdem über Schalter der
Container soweit mit Umgebungsvariablen konfiguriert werden sodass dieser
entsprechend mit seiner Umwelt kommunizieren kann. Konkret an einem Beispiel veranschaulicht
bedeutet dies, dass mittels des Schalters:</p>

<div style='border:solid windowtext 1.0pt;padding:1.0pt 4.0pt 1.0pt 4.0pt;
margin-left:35.25pt;margin-right:0cm'>

<p style='margin:0cm;margin-bottom:.0001pt;border:none;padding:0cm'><a
name="_Hlk531006516"><span style='font-size:11.0pt;font-family:"Calibri",sans-serif;
background:fuchsia'>&nbsp;</span></a></p>

<p style='margin:0cm;margin-bottom:.0001pt;border:none;padding:0cm'><span
lang=EN-GB style='font-size:11.0pt;font-family:"Calibri",sans-serif;background:
fuchsia'>docker container run</span><span lang=EN-GB style='font-size:11.0pt;
font-family:"Calibri",sans-serif'> <span style='background:aqua'>-e 'ACCEPT_EULA=Y'</span>
<span style='background:red'>-e 'SA_PASSWORD=yourStrong(!)Password'</span> <span
style='background:lime'>-p 1433:1433</span> <span style='background:darkcyan'>-d</span>
<span style='background:purple'>-name MSSQLServerDOCKER </span>-<span
style='background:yellow'>v ~/SQLData:/home/dockertest/SQLData </span><span
style='background:lightgrey'>microsoft/mssql-server-linux:2017-CU8</span></span></p>

<p style='margin:0cm;margin-bottom:.0001pt;border:none;padding:0cm'><span
lang=EN-GB style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

</div>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span lang=EN-GB style='font-size:11.0pt;font-family:
"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Der
Befehl <span style='background:fuchsia'>docker container run </span>ist der
Basic Command um eine Instanz eines Images / einen individuellen Container zu
starten. Wie beschrieben wird etwaig das Image heruntergeladen und dann
entsprechend aus dem Image heraus ein individueller Container erzeugt.</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Der
Schalter Environment / <span style='background:aqua'>-e 'ACCEPT_EULA=Y' </span>besagt
lediglich, dass die End User Licence von Microsoft ausführenden humanen Person akzeptiert
wird.</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Der
User System Administrator (SA) spielt in der Umgebung des MSSQL Servers eine
sehr zentrale Rolle. Daher muss dieser beim Erzeugen einer Instanz vorab mit
einem entsprechenden Passwort konfiguriert werden. Dies wird mittels des
Schalters <span style='background:red'>-&nbsp;e&nbsp;SA_PASSWORD=yourStrong(!)Password'
</span>erreicht-</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Der
grüne Sektor bedeutet, dass der Host, auf dem für MS-SQL-Server defaultmäßigen
Port 1433 an der Hostinternen FW lauscht und diesen Port bei Ansprache an den
MSSQL-Server defaultmäßigen Port 1433 an den Container weiterleitet. Somit ist gewährleistet,
dass auf einem running Container von dem Zugrundeliegenden Host-Operating
System durch das Virtuelle Ubuntu auf dem <span style='background:lime'>Port
1433 </span>hin zudem Container auf dem <span style='background:lime'>Port 1433
</span>zugegriffen werden kann.</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Mittels
des Schalters <span style='background:darkcyan'>detach| -d</span> wird festgelegt,
dass dieser Container zwar auf der CLI aufgerufen wird, aber im Hintergrund
läuft. Somit kann die aktuelle CLI Sitzung weiter genutzt werden.</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Mittels
des Schalters <span style='background:purple'>-name MSSQLServerDOCKER </span>wird
festgelegt unter welchem Namen die Instanz angesprochen werden kann.  Der
Status einer Instanz kann ein und ausgeschaltet sein. Wie bereits oben
beschrieben haben jedoch laufende Container für die Kommunikation mit der
Umwelt entsprechend eine IP-Adresse. Diese Adresse kann jedoch mit einem
„reboot“ eines Containers erneuern. Aus diesem Grunde ist innerhalb der Docker
Container-Verwaltung die Namenszuweisung der Container in Zusammenhang mit
einem internen DNS-Dienst fest verankert. </span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Ein
weiteres zentrales Element ist das Einbinden von einem Shared Laufwerk zwischen
dem Hostsystem(Ubuntu) und dem Container. Dies wird mittels <span
style='background:yellow'>v&nbsp;~/SQLData:/home/dockertest/SQLData </span>erledigt.
Hierbei muss davor beachtet werden, dass das Verzeichnis ~/SQLSData auf Ubuntu
eben angelegt wird.</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:0cm;margin-left:35.25pt;
margin-bottom:.0001pt'><span style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Im
letzten Schritt muss der Name der Imagedatei und das dazugehörige Repository angegeben
werden. In diesem Falle laden wir das Image aus dem Default-Repository (Docker
Hub) herunter. Für diese Aufgabe ist die Zeile: <span style='background:lightgrey'>microsoft/mssql-server-linux:2017-CU8
</span>verantwortlich.</span></p>

<span style='font-size:11.0pt;line-height:107%;font-family:"Calibri",sans-serif;
color:#2F5496'><br clear=all>
</span>


