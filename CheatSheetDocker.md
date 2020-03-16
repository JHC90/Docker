# Cheatsheet - Docker in Ubuntu

## Install-Quick&Dirty unter Linux via CLI
Vorraussetzung ist dass ein Linux bereits ausgerollt und einsatz fähig ist. Hier eben das Szenario dass ein Docker Linux Server bereitsteht und nicht auf Windows gearbeitet wird. [LinuxBestPractiseLink](https://github.com/JHC90/Linux)



* sudo apt install curl<br>
* curl -fsSL https://get.docker.com -o get-docker.sh<br>
* sh get-docker.sh
* docker version
<hr>
## hinzufügen des Linux users zur DockerFroup
dadurch muss nicht immer sudo vroab geschrieben werden, bevor man mit Docker Arbeitet || erst nach einem relog am linux möglich
> sudo usermod -a -G docker $USER
<hr>
# Basic Interaction mit Docker
<table style="width:100%">
  <tr>
    <th>Command</th>
    <th>Umsetzung</th>
    <th> mögliche Parameter</th>
  </tr>
  <tr>
    <td>docker version"</td>
    <td>liefert die Version</td>
    <td></td>
  </tr>
  <tr>
    <td>docker info</td>
    <td>Konfigurations Einsicht</td>
    <td></td>
  </tr>
  <tr>
    <td>docker image ls -a</td>
    <td>zeigt alle image Dateien des Servers</td>
    <td></td>
  </tr>
  <tr>
    <td>docker container ls:</td>
    <td>zeigt alle laufenden & nicht laufenden Container</td>
    <td></td>
  </tr>
 
  
  
<table>

<hr>
# Interaktion mit einem Container
<table style="width:100%">
  <tr>
    <th>Command</th>
    <th>Umsetzung</th>
    <th> mögliche Parameter</th>
  </tr>
  <tr>
    <td>docker container run <mark>ImageName</mark></td>
    <td>startet einen Container, wenn das Image lokal heruntegeladen ist. Wenn kein Image lokal exisitert, wird dieses heruntergeladen & anschließend ein Container erstellt</td>
    <td> <a href="./0_ExampleCommandRunDocker.md">FullExample</a> </td>
  </tr>
   <tr>
    <td>docker container stop <mark>ContainerName</mark> </td>
    <td>Stoppt den etwaigen Container. der name kann über docker container ls herausgefunden werden</td>
    <td></td>
  </tr>
  
  <tr>
    <td>docker container rm <mark> Abkürzung | ContainerName</mark></td>
    <td>löschen eines erstellten containers mittels der abkürzung, das stoppt nur den Container, löscht nicht das image</td>
    <td></td>
  </tr>
  <tr>
    <td>docker container logs <mark>ContainerName</mark></td>
    <td>hier kann man ggf das erste Passwort sehen, abhängig von der Appli</td>
    <td></td>
  </tr>
  <tr>
    <td>docker exec -it <mark>ContainerName</mark> "bash"</mark></td>
    <td>hiermit kann man von dem docker server in den container hineinnavigieren um auf cli ebene von dem Container zu interagieren. das wird verwendet wenn der Container bereits läuft</td>
    <td><a href="./1_CreateShareDriveBetweenServerAndImage.md">ExampleForSharedBetweenContainer&Serer</a>
    || mit exit auf der cli von dem container kann ich wieder zurück zum docker server switchen ||  das basis system von den Container ist zwar debian, das heißt aber nciht dass debian vollständig vorhanden ist. wenn ich bsp einen ubuntu container erstelle, habe ich alle tools von ubuntu (apt-package manager)
    </td>
  </tr>
  <tr>
    <td>docker container run -it <mark>ContainerName</mark> "bash"</mark></td>
    <td>Starten eines Containers direkt in die Shell des Containers</td>
    <td>
    </td>
  </tr>
  
<table>

<hr>
# Inspect Container

<table style="width:100%">
  <tr>
    <th>Command</th>
    <th>Umsetzung</th>
    <th> mögliche Parameter</th>
  </tr>
  <tr>
    <td>docker container top <mark>ContainerName</mark> </mark></td>
    <td>zeigt die laufenden Prozesse in einem contaner </td>
    <td></td>
  </tr>
   <tr>
    <td>docker container instpect <mark>ContainerName</mark> </mark></td>
    <td>liefert ein JSON array über den laufenden Container retour </td>
    <td></td>
  </tr>
   <tr>
    <td>docker container stats <mark>ContainerName</mark> </mark></td>
    <td>liefert live Infomration über die Ressourcen des Containers </td>
    <td>hier muss nicht notgedrungen ein containername mitgegeben werden, da hier </td>
  </tr>

  
<table>

<hr>
# Networking

<table style="width:100%">
  <tr>
    <th>Command</th>
    <th>Umsetzung</th>
    <th> mögliche Parameter</th>
  </tr>
  <tr>
    <td>docker network ls</td>
    <td>zeigt alle erreichbaren virtuellen Netzwerke</td>
    <td></td>
  </tr>
  <tr>
    <td>docker network inspect <mark>NetworkName</mark></td>
    <td>zeigt alles container in JSON welche dem Netzwerk sind</td>
    <td></td>
  </tr>
  <tr>
    <td>docker network create --driver</td>
    <td></td>
    <td>docker network create mynetwork</td>
  </tr>
  <tr>
    <td>docker container run -d --name nginxNew --network <mark>NetworkName</mark>< nginx</td>
    <td>erstellen eines containers und beim erstellen des Containers hinzufügen zu einem Netzwerk</td>
    <td>docker container run -d --name nginxNew --network <mark>NetworkName/id</mark>< nginx</td>
  </tr>
  <tr>
    <td>docker network connect<br><br>docker network connect <mark>NetworkName/id</mark> <mark>ContainerName/id</mark></td>
    <td>kann man sich vorstellen wie neue nic rein und dann eben aus zwei netzwerken erreichbar </td>
    <td>docker network connect 8bcda234bed4 db</td>
  </tr>
  <tr>
    <td>docker network disconnect</td>
    <td>kann man sich vorstellen wie neue nic raus und dann eben nur noch eine</td>
    <td></td>
  </tr>
<table>


<hr>
# hier die Veröffneltichung von Container

<table style="width:100%">
  <tr>
    <th>Command</th>
    <th>Umsetzung</th>
    <th> mögliche Parameter</th>
  </tr>
  <tr>
    <td>docker commit <mark>Container-id</mark> <mark>Container-id</mark><mark>„Image-Name“</mark></td>
    <td>commit </td>
    <td>BSP:  docker commit c52186187013 jhc1990/test</td>
  </tr>
<table>
