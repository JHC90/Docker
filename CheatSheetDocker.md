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
    <td> <a href="./0_ExampleCommandRunDocker.md">FullExample</a></td>
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
    <td>hiermit kann man von dem docker server in den container hineinnavigieren um auf cli ebene von dem Container zu interagieren</td>
    <td><a href="./1_CreateShareDriveBetweenServerAndImage.md">ExampleForSharedBetweenContainer&Serer</a>
    || mit exit auf der cli von dem container kann ich wieder zurück zum docker server switchen
    </td>
  </tr>
  
<table>

<hr>
hier die Veröffneltichung von Container

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
  <tr>
  
<table>
