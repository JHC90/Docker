# Jupyter-Notebook

Command from Video
> docker run -it --rm --name ds -p 8888:8888 jupyter/datascience-notebook



**Erweiterung um Diskspace From Docker-Server**
> docker run -it --rm --name ds -p 8888:8888 -v /mnt/Avnukia:/mnt/Avnukia jupyter/datascience-notebook


Am Managementlaptop die IP von dem Ubuntu-Serer + rest vom oberen Cmmand

---
## Meine Erweiterungen
1. in diesem SchrittWill ich 
   1. Storage reinbringen
   2. , dass die Jupyternotebooks immer im Storage und nicht in dem Container gespeichert werden => Jupyter soll immer an dieser Stelle Geöffnet werden

> docker run -it --name ds-TestObject -p 8888:8888 -v /mnt/Avnukia:/mnt/Avnukia jupyter/datascience-notebook

=> Check up mit Bash ob das Verzeichnis existiert im Container

=> ggf beim instanzieren change, sodass wir in das Work-Verzeichnis den Folder anhängen


Konsole vom Container (bspw via Webinterface =>  || oder via docker exec-it ds bash => jetzt bin ich auf der Bash von dem Container)

---

### Install Tensorflow @ my dell Server 
conda install tensorflow
pip install tensorflow
