M300 - NetworkChuck Coffee on Kubernetes
========================================

## Einleitung
Diese Wikiseite zeigt eine kleine Einführung in Kubernetes. NetworkChunk (ein berühmter "nerd" Youtuber) hat uns motiviert, uns mit Kubernetes zusammenzusetzen. Mit hilfe von NetworkChunk konnte wir Schritt für Schritt eine eigene Umgebung aufbauen. Da er selbst auf docker hub sein eigenes image freigestellt hat, konnten wir es natürlich für unser Projekt benutzen. Unser Ziel war es mit Rettung von Ihm, seine Umgebung aufzustellen. Damit es in Betrieb genommen wird, haben wir noch von Ihm 100$ Gutschein erhalten, damit wir auf der Plattform (Linode Cloud Hosting) unseren Kubernetes cluster erstellen können. Nun wollen wir euch das Thema näher bringen und wir zeigen euch alles step by step. VIEL SPASS!

Hier noch der YT-Kanal von NetworkChunk: https://www.youtube.com/c/NetworkChuck

## Inhaltsverszeichnis
* 01 - [Service-Aufbau](#-01---Service-Aufbau)
* 02 - [Umsetzung](#-02---Umsetzung)
* 03 - [NetworckChunk Coffee on Kubernetes setup](#-03---NetworckChunk-Coffee-on-Kubernetes-setup)
* 04 - [Testing](#-04---Testing)
* 05 - [Quellenverzeichnis](#-05---quellenverzeichnis)


## 01 - Service-Aufbau

Mit diesem Link haben wir den Gutschein erhalten: https://www.linode.com/lp/youtube-viewers/?ifso=networkchuck&utm_source=influencer&utm_medium=video&utm_campaign=networkchuck
1. Linode Konto erstellen, User-Info angeben
2. Cluster erstellen
  --> Node Pools auswählen (wir empfehlen 3 gleiche Node Pools)
  
  ![image](https://user-images.githubusercontent.com/91592611/178302642-bd4c6e11-37c4-4407-b636-ac564601d760.png)
  

3. VM (von der Schule erhalten)
4. Visual Studio Code für configs


## 02 - Umsetzung

Bevor wir anfangen möchten wir euch kurz schildern, was Linode ist und wie wir auf einen Kubernetes Cluster erstellt haben.
Linode bereitet einfache Bereitstellung von Cloud Compute, Speicherung und Vernetzung in Sekundenschnelle mit einer voll funktionsfähigen API, CLI und einer benutzerfreundlichen Cloud-Manager-Oberfläche. Einfach gesagt, es ist ein Cloud-Provider.

### Konto erstellen:

Geh auf diesem Link: https://www.linode.com/lp/youtube-viewers/?ifso=networkchuck&utm_source=influencer&utm_medium=video&utm_campaign=networkchuck
1. Klicke nun auf die 3 möglichen anmelde Funktionen.

![image](https://user-images.githubusercontent.com/91592611/178303994-1bd20bd3-25bf-41c5-802c-630ff0449d3c.png)

2. Nachdem Login gib deine User-Informationen an und deine Kreditkarte
3. Nachdem man alle Daten eingegeben hat, sollte man nun auf das Dashboard zugreifen

![image](https://user-images.githubusercontent.com/91592611/178304917-135e0992-c62c-4a36-8bec-aeadcf4019ef.png)

## 03 - NetworckChunk-Coffee-on-Kubernetes-setup

1. Zuerst muss man die neuste Version von KubeCTL installieren: curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl

![image](https://user-images.githubusercontent.com/91592611/178323838-75664999-3e41-44e3-9295-0fd399e32d8d.png)

2. Nach der Installation fügen wir mit diesem command "chmod +x ./kubeclt" die Ausführungsberechtigung für alle Benutzer zu den vorhandenen Berechtigungen hinzu.

![image](https://user-images.githubusercontent.com/91592611/178324287-cde6ee62-16b1-41be-934a-ef1408ab80c8.png)

3. Wir verschieben das Paket nach /usr/local/bin/kubectl mit diesem command "sudo mv ./kubeclt /usr/local/bin/kubeclt

![image](https://user-images.githubusercontent.com/91592611/178324616-4e060fd5-dd56-4000-932a-8bf787342c67.png)

4. Da wir ja im Linode einen Cluster erstellt haben, müssen wir diese zuerst mit unserem Rechner verbinden. Dies machen wir indem wir das config von Linode im "kubeconfig.yaml" kopieren und das machen wir mit folgendem command:
    --> sudo nano kubeconfig.yaml

![image](https://user-images.githubusercontent.com/91592611/178325246-ccbc9494-895a-4914-84df-688ce82d7933.png)
Kubeconfig hinzufügen und dann speichern.

![image](https://user-images.githubusercontent.com/91592611/178325369-90e4a80e-9eb0-4dcc-952f-d1a375d0c7fb.png)

5. Nachdem man das config-file hinzugfügt hat, folgt nun die Verbidung:
    --> export KUBECONFIG=kubeconfig.yaml
    
![image](https://user-images.githubusercontent.com/91592611/178325930-4ba7169a-fb89-402d-836b-cc1b5d3a9cb9.png)

6. Nachdem die Verbindung aufgebaut ist, möchte wir überprüfen, ob wir die Nodes auf unserem Gerät sehen
    --> kubectl get nodes
    
![image](https://user-images.githubusercontent.com/91592611/178359332-25b181de-347d-45d2-94ec-7a10425159fe.png)

7. Falls Ihr noch die Kubernetes Cluster Info wissen möchtet:
    -> kubectl cluster-info
    
![image](https://user-images.githubusercontent.com/91592611/178360004-3dafd9f8-32a6-4590-abf0-25dd249a1793.png)

8. Nun kommen wir zum wichtigen Part, nämlich müssen wir noch den image ausführen und das macht man so:
    -->  kubectl run networkchuckcoffee –-image=thenetworkchuck/nccoffee:pourover –-port=80
    --> kubectl get pods

![image](https://user-images.githubusercontent.com/91592611/178361650-22ecacd7-bb41-43cf-a141-71a67c9d889f.png)

![image](https://user-images.githubusercontent.com/91592611/178361752-428dd792-48c0-4389-aa61-f3c4802d579a.png)

9. Wenn man mehr Informationen aus den Pods rausholen möchtet, dann macht man das mit diesem command:
    --> kubectl decribe pods

![image](https://user-images.githubusercontent.com/91592611/178362109-9366d713-9cfb-4631-a33d-763dcf93bb80.png)

10. Nachdem die Verbindung Online ist, muss man an unserem Master (Linode) sagen, was man alles ausführen möchte. Für das erstellen wir einen yaml file und fügen folgendes rein und dann ausführen.
    --> nano nccoffedeployment.yaml
    --> kubectl apply -f nccoffedeployment.yaml

![image](https://user-images.githubusercontent.com/91592611/178362964-371b3ae9-be25-451e-b49c-095026447c50.png)

![image](https://user-images.githubusercontent.com/91592611/178363215-85cab79b-e967-482e-be97-4e24f40cbcff.png)


11. Momentan kann man die Webseite noch nicht erreichen, deswegen sollte man jetzt die Webseite aufschalten. Mit Kubernetes muss man einen Service «deployen», um die Pods zu exposen. Dies ist ein Loadbalancer, dieser exposed die Pods zugleich Loadbalanced er die verschiedenen Pods.

![image](https://user-images.githubusercontent.com/91592611/178363724-8b80e8a1-7878-4671-a4b8-cb2591643c83.png)

12. Damit wir auf unsere Umgebung zugreifen kann, muss man einen yaml-file erstellen und folgendes hinzufügen und dann ausführen:
    --> nano coffee-service.yaml
    --> kubectl apply -f coffee-service.yaml
    
![image](https://user-images.githubusercontent.com/91592611/178364135-b4e8de28-8161-4255-a84d-373a42a4fafb.png)

![image](https://user-images.githubusercontent.com/91592611/178364367-61736a73-8ac3-4728-b5fa-c3f311a72a2a.png)

13. Nun sollte unsere Umgebung verfügbar sein, aber bevor wir überprüfen, wollen wir wissen, ob wir unser service auch sehen:
    --> kubeclt get services
Mit diesem command kann man die IP Adresse herauslesen und die ist auch in Linode unter "Node Balancer" zu finden.
![image](https://user-images.githubusercontent.com/91592611/178364557-5d65bfa0-2a1a-4e8b-b546-71c5b2674eb1.png)

<img width="947" alt="image" src="https://user-images.githubusercontent.com/91592611/178364824-fb9331d5-7ce5-49ba-9a08-f2087eeeccdb.png">

## 04 - Testing

Im Linode sowie auch lokal findet man die IP-Adresse der Umgebung. Nun kann man einen Browser öffne und die IP-Adresse eingeben:

Output:

![image](https://user-images.githubusercontent.com/91592611/178365086-dbe88801-11dd-469d-82ae-68259701edcf.png)

#### Ich hoffe wir konnten euch Kubernetes näher bringen und wünschen euch viel spass mit unserer Anleitung!

## 05 - Quellenverzeichnis

YT-NetworkChuck: https://www.youtube.com/watch?v=7bA0gTroJjw&t=577s

NetworkChuck Hilfsmittel: https://networkchuck.com/kubernetes/
