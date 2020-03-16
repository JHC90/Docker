<h5><a name="_Toc4480368">Operativ</a> </h5>

<p class=MsoNormal>Bevor wir die Images herunterladen und erzeugen wird
zunächst das spätere Sharelaufwerk mittels des Befehles:</p>

<p class=MsoNormal>mkdir ~/SQLData </p>

<p class=MsoNormal>in dem Home-Laufwerk des Users, in meinem Fall „labadmin“ erzeugt.
An diesem zentralen Verzeichnis sollen später die Daten zwischen dem Host und
den Docker Containern ausgetauscht werden.</p>

<p class=MsoNormal>Außerdem gewähren wir dem user docker in unserem Lab volle
administrationsrechte mittels:</p>

<p class=MsoNormal><span lang=EN-GB>sudo usermod -a -G docker $USER</span></p>

<p class=MsoNormal>Dies ist in unseren Lab-Szenario bedenklos umzusetzen, da
wir mit keinen sensiblen/produktiven/schützenswerten, sondern ausschließlich
mit fiktiven Daten arbeiten. Für Produktivumgebungen ist Docker grundsätzlich
nicht gedacht, da hier auch das Sicherheitskonzept nicht „state oft he art“
ist. Aber auch für Entwicklungsumgebungen könnte man über ein geeignetes
Rechtesystem verwaltet in Linux etwas Sicherheit in das Lab bringen. Der
Einfachheit zu liebe wurde dieser Schritt übersprungen und der Verwaltungsuser
Docker und labadmin gänzlich mit den nötigen sudo-Rechten ausgestattet.</p>

<p class=MsoNormal>&nbsp;</p>

<p class=MsoNormal>&nbsp;</p>

<p class=MsoNormal>Für unser Test-Lab beschaffen wir uns einen unabhängigen
Container, von</p>

<p class=MsoNormal>                <b><u>MS-Hub</u></b></p>

<p class=MsoNormal style='margin-left:35.4pt'><u>sudo docker container run -d
-p 1433:1433 --name MSSQLMicHub -e 'ACCEPT_EULA=Y' -e
'SA_PASSWORD=YourStrong!Passw0rd' -v ~/SQLData:/home/dockertest/SQLData
mcr.microsoft.com/mssql/server:2017-latest</u></p>