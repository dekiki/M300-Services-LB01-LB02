M300 - NetworkChuck Coffee on Kubernetes
========================================

### Einleitung
Diese Wikiseite zeigt eine kleine Einführung in Kubernetes. NetworkChunk (ein berühmter "nerd" Youtuber) hat uns motiviert, uns mit Kubernetes zusammenzusetzen. Mit hilfe von NetworkChunk konnte wir Schritt für Schritt eine eigene Umgebung aufbauen. Da er selbst auf docker hub sein eigenes image freigestellt hat, konnten wir es natürlich für unser Projekt benutzen. Unser Ziel war es mit Rettung von Ihm, seine Umgebung aufzustellen. Damit es in Betrieb genommen wird, haben wir noch von Ihm 100$ Gutschein erhalten, damit wir auf der Plattform (Linode Cloud Hosting) unseren Kubernetes cluster erstellen können. Nun wollen wir euch das Thema näher bringen und wir zeigen euch alles step by step. VIEL SPASS!

Hier noch der YT-Kanal von NetworkChunk: https://www.youtube.com/c/NetworkChuck

# Inhaltsverszeichnis

### Service-Aufbau 
Mit diesem Link haben wir den Gutschein erhalten: https://www.linode.com/lp/youtube-viewers/?ifso=networkchuck&utm_source=influencer&utm_medium=video&utm_campaign=networkchuck
1. Linode Konto erstellen, User-Info angeben
2. Cluster erstellen
  --> Node Pools auswählen (wir empfehlen 3 gleiche Node Pools)
  
  ![image](https://user-images.githubusercontent.com/91592611/178302642-bd4c6e11-37c4-4407-b636-ac564601d760.png)
  

3. VM (von der Schule erhalten)
4. Visual Studio Code für configs


### Umsetzung
Bevor wir anfangen möchten wir euch kurz schildern, was Linode ist und wie wir auf einen Kubernetes Cluster erstellt haben.
Linode bereitet einfache Bereitstellung von Cloud Compute, Speicherung und Vernetzung in Sekundenschnelle mit einer voll funktionsfähigen API, CLI und einer benutzerfreundlichen Cloud-Manager-Oberfläche.

### Konto erstellen:

Geh auf diesem Link: https://www.linode.com/lp/youtube-viewers/?ifso=networkchuck&utm_source=influencer&utm_medium=video&utm_campaign=networkchuck
1. Klicke nun auf die 3 möglichen anmelde Funktionen.

![image](https://user-images.githubusercontent.com/91592611/178303994-1bd20bd3-25bf-41c5-802c-630ff0449d3c.png)

2. Nachdem Login gib deine User-Informationen an und deine Kreditkarte
3. Nachdem man alle Daten eingegeben hat, sollte man nun auf das Dashboard zugreifen

![image](https://user-images.githubusercontent.com/91592611/178304917-135e0992-c62c-4a36-8bec-aeadcf4019ef.png)

### NetworckChunk Coffee on Kubernetes setup:
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

6. 
## Testing
Text

## Quellen
Text
