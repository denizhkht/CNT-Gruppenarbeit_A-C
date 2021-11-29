# CNT Projekt

Wir haben uns überlegt, was wir im Rahmen dieses CNT Cloud Projektes anhand der gegebenen Anforderungen machen könnten, was vielleicht sogar in einem echten Business Case verwendet werden könnte bzw. so nah kommt, damit wir etwas davon mitnehmen können.

Wir haben uns am Beispiel mit einem Webshop bedient und uns überlegt, wie dieser Skalierbar aufgebaut werden kann und haben zumindest einen Teil davon aufgebaut.

Somit haben wir uns entschieden mit den 3 Cloud Plattformen AWS, Azure und die TBZ eigene MaaS zu arbeiten und eine von uns bereits erstellte Website über einen Loadbalancer zur Verfügung zu stellen. Mit einem DNS wollten wir eine Namensauflösung erreichen, welches am Schluss jedoch nicht geklappt hat.


Hier nun die Dokumentation zu den gegebenen Kompetenzpunkten:

# Kompetenzen A

### A1
**Ich kenne Services | Ich kann Services in VMs verteilen | Ich kann VMs für Services einsetzen**

Wir haben für dieses Projekt verschiedene Services wie Bind9, Apache2 und HAProxy in verschiedenen VM's installiert und eingesetzt. Dies auf verschiedenen Cloud Plattformen wie Azure, AWS und dem TBZ MaaS.

### A2
**Ich habe etwas von (SSH) Public/Private Keys gehört | Ich kann (SSH) Public/Private Key erklären | Ich kann selber (SSH) Public/Private Keys erstellen und einsetzen**

Für die Verbindung zum MaaS haben wir Bitvise verwendet.
Bitvise kann mit folgendem [Link](https://www.bitvise.com/download-area) heruntergeladen werden.
Mit folgenden Screenshots wird aufgezeigt wie man mit Bitvise ein SSH Key Pair generieren kann und diese anschliessend im MaaS verwenden kann.

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h29_14.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h15_29.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h26_27.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h26_56.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h27_12.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h27_22.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h27_39.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A2/2021-11-08_16h28_04.png)

### A3
**Ich kann mich mit einer VM verbinden | Ich kann mich, mittels dem SSH Protokoll, mit einer VM verbinden | Ich kann einen SSH Key erstellen und diesen für die Verbindung zur VM verwenden**

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A3/2021-11-08_17h13_29.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A3/2021-11-08_17h15_13.png)

![](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/A3/2021-11-08_17h15_02.png)


### A4
**Ich kann ein paar Linux Pakete aufzählen | Ich kann Linux Pakete installieren | Ich kann Linux Pakete suchen und installieren**

In diesem Projekt wurden unteranderem folgende Pakete mit dem Befehl apt install installiert.

* ZIP (Komprimierung)
* Apache2 (Web Service)
* Bind9 (DNS Service)
* HAProxy (Proxy Service)

Die Pakete kann man in Linux Foren, Google oder mit dem Befehlen `apt search` oder `apt-cache search` finden.

### A5
**Ich kann ein paar Linux Befehle aufzählen | Ich kann ein paar Linux Befehle verwenden | Ich kann Linux Befehle einsetzen und deren Funktion erklären**

In diesem Projekt wurden unteranderem folgende Befehle verwendet.

* echo (Text an Datei anzuhängen)
* sudo (Superuser do)
* apt install (Installation von Applikations Paketen)
* systemctl "Service" restart (Neustart eines Services)
* cd (gehe zu)
* ls (Ordner Inhalt anzeigen)

***
# Kompetenzen B

### B1
**Ich kenne Infrastructure as Code | Ich kann Infrastructure as Code erklären | Ich kann Infrastructure as Code mit Beispielen erklären**

Mit Infrastructure as a Code werden Konfigurationsdateien erstellt, die Ihre gesamten Infrastrukturspezifikationen enthalten, wodurch Sie Konfigurationen einfacher bearbeiten und verteilen können. Es stellt außerdem sicher, dass Sie jedes Mal dieselbe Umgebung provisionieren. Zudem kann man so automatisiert Server mit Services zur Verfügung stellen. Die Infrastruktur ist auch jedes mal gleich provisioniert egal ob damit eine oder 1000 Machinen erstellt werden.

In unserem Beispiel haben wir die Services Apache2 Webservice und einen HAProxy anhand eines Cloud-Init Skripts im CLI automatisiert erstellt. Dies auf AWS, MaaS wie auch auf Azure.


### B2
**Ich kenne Produkte für Automatisierung | Ich kann VMs, anhand der Cloud-init Beispiele automatisiert aufsetzen | Ich kann VMs mit eigenen Cloud-init Scripten aufsetzen**

Wir kennen die Möglichkeit mit einem Cloud-Init Skript Server mit Services automatisiert zu installieren. Auch haben wir von Terraform gehört.

Für unsere Server mit den Services Apache2 und HAProxy haben wir eigene Cloud-Init Skripts geschrieben um diese zu installieren und die benötigten Dateien für die Website von einem Github Repository mit wget herunterzuladen und mit zip zu entpacken und danach im Webservice bereitzustellen.

Für den HAProxy haben wir ein Cloud-Init Sktipt erstellt, welches neben der Installation von HAProxy mit echo die Konfigurationsdateien anpasst.

[Webservice Cloud-Init](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/configfile/website_cloud-init.yml) <br>
[HAProxy Cloud-Init](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/configfile/haproxy_cloud-init.yml)

Beim HAProxy Cloud-Init Skript müssen die folgenden Werte "server1 name", "public IP 1" und "server2 name", "public IP 2" noch angepasst werden, da wir die public IP's der Server noch nicht kennen.

### B3
**Ich kenne Cloud-init | Ich kenne die wichtigsten Cloud-init Einträge und habe diese Dokumentiert | Ich habe Cloud-init mit Beispielen Dokumentiert**

Die wichtigsten zu nennenden Cloud-Init Einträge sind die folgenden:

* users: Dient zum Erstellen und konfigurieren von Usern.
* packages: Beschreibt, in einem Array, welche Linux Packages installiert werden sollen.
* runcmd: Beschreibt, in einem Array, welche Shell (sh) Befehle ausgeführt werden sollen.
* write_files: dient zum Erstellen von (Konfigurations-)Dateien.

Für unsere Cloud-Init Skripts verwenden wir die Befehle "packages:" und "runcmd:"

Hier ein Beispiel, welches all die wichtigsten Einträge verwendet:
![Beispiel Cloud-Init Skript](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/B3/Cloud-init_Beispiel.png)

### B4
**Ich habe von der Markdown Language YAML gehört | Ich kann den Aufbau einer YAML Datei erklären | Ich kann eine valide YAML Datei erstellen, z.B. mit VSCode**

Wir haben von der YAML Markdown Language gehört und haben das YAML Format verwendet um unsere Cloud-Init Dateien zu speichern.

Hier der Link zu unseren selbst erstellten Cloud-Init Skripts basierend auf dem YAML Format:
[HA Proxy Cloud-Init Skript](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/configfile/haproxy_cloud-init.yml) <br>
[Webservice Cloud-Init Skript](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/configfile/website_cloud-init.yml)

Unter diesem Link kann das Skript validiert werden:
[YAMLvalidator](http://www.yamllint.com/)

### B5
**Ich kenne Versionsverwaltungssysteme wie Git | Ich kann die Cloud-init Scripte in einem Git Repository ablegen | Ich kann die Cloud-init Scripte mit Dokumentation (z.B. als Markdown) in einem Git Repository ablegen**

Wir haben für unser Projekt einen Github Repository erstellt wo wir unsere Konfigurationsdateien wie auch die weiteren Dateien wie die Website abgelegt haben um diese auch mit den Cloud-Init Skripts bei der installation herunterzuladen und für die Konfiguration zu verwenden.

Hier in diesem Wiki Dokumentieren wir unser Projekt mit Markdown in unserem Github Repository.

### B6
**Ich kenne Git Funktionen wie git clone | Ich kenne Git Funktionen zur Repository Pflege wie git pull, commit und push | Ich kann ein Git Repository mittels dem SSH Protokoll nachführen**

Für Git gibt es folgende wichtige Funktionen:

* git init
* git status
* git add
* git pull
* git commit
* git push
* git log

Um sein Github Repository über SSH zu managen muss man sich mit folgenden SSH Befehlen an Github verbinden und anmelden:
* ssh -i "PrivatKeyFile" -T "username"@github.com

Mittels z.B. Bitvise kann ein Key Pair generiert werden (siehe Punkt A2) wo der Public Key auf Github hochgeladen werden kann.
![GitHub SSH Key](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/B6/GitHubSSHKey.png)

Danach kann mit den Befehlen via SSH das Repository bearbeitet werden.

***
# Kompetenzen C

### C1
**Ich kenne die Cloud Services | Ich kann die Cloud Services erklären | Ich kann die Cloud Services einsetzen**

Einfach ausgedrückt sind Cloud Services die Bereitstellung von Computing-Services, einschliesslich Servern, Speicher, Datenbanken, Netzwerken und Software über das Internet („die Cloud“), um schnellere Innovationen, flexible Ressourcen und Skalierbarkeit zu erreichen.

Im Rahmen dieses Projekts haben wir somit von den Vorteilen der Cloud Services, in diesem Fall AWS, Azure und der TBZ eigenen MaaS, gebrauch gemacht.

### C2
**Ich kenne Cloud CLIs | Ich kann die Funktionsweise von Cloud CLI erklären und habe diese Dokumentiert | Ich kann Cloud CLI Tools einsetzen und habe diese mit Beispielen Dokumentiert**

In diesem Projekt wurden die VMs in AWS und Azure über das Command Line Interface (CLI) erstellt.

**AWS:**

Für unsere Webserver für das Projekt haben wir auf AWS eine Sicherheitsgruppe erstellt und den Port 80 (http) und 22 (ssh) von aussen zugänglich gemacht. Dies wurde mit den folgenden Befehlen über das AWS CLI gemacht:

`aws ec2 create-security-group --group-name CNT --description "Security Gruppe fuer Webseiten des CNT Projektes"`

`aws ec2 authorize-security-group-ingress --group-name CNT --protocol tcp --port 22 --cidr 0.0.0.0/0`

`aws ec2 authorize-security-group-ingress --group-name CNT --protocol tcp --port 80 --cidr 0.0.0.0/0`

![AWS CLI Security Group creation and modification](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/AWS_CLI_Securitygroup.png)

Wir haben für dieses Projekt zwei Ubuntu Server 20.04 VMs mit dem folgenden Befehl erstellt:

`aws ec2 run-instances --image-id ami-0a49b025fffbbdac6 --security-group-ids CNT --instance-type t2.micro --count 2 --key-name CNT --user-data file://website_cloud-init.yml` <br>
_Der Parameter --key-name CNT benutzt den RSA key CNT welcher bereits in AWS erstellt wurde in der Vergangenheit._

![AWS CLI VM creation](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/AWS_CLI_VMcreation.png)

Befehl um alle Instanzen des Types t2.micro anzuzeigen, dies wird benötigt um die Public IPs der Instanzen herauszufinden.

`aws ec2 describe-instances --filters "Name=instance-type,Values=t2.micro"`

![AWS ec2 show instances](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/AWS_CLI_show_instances.png)

Virtuelle Machinen (EC2 Instanzen) welche über den oben genannten Befehl erstellt wurden.
![AWS VMs created over CLI](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/AWS_instances_created_over_CLI_new.png)

**Azure:**

Für unseren HAProxyserver für das Projekt haben wir auf Azure eine Resourcengruppe mit dem folgendem Befehl erstellt:

`az group create --name CNT --location switzerlandnorth`

![Azure CLI resource group creation](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/Azure_CLI_Securitygroup.png)

Mit dem folgendem Befehl haben wir einen HAProxyserver und die dazugehörigen SSH Keys erstellt.

`az vm create --resource-group CNT --name HAProxy --image UbuntuLTS --size Standard_D2_v4 --location switzerlandnorth --generate-ssh-keys --custom-data haproxy_cloud-init.yml`

![Azure CLI VM Erstellen](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/Azure_CLI_VMcreation.png)

Damit man auf den obenerstellten HAProxyserver von extern zugreifen kann wurden noch die Ports 22 (ssh) und 80 (http) mit dem folgendem Befehl aufgemacht:

`az vm open-port --port 80 --port 22 --resource-group CNT --name HAProxy` 

HAProxyserver welcher über das Azure Command Line Interace  mit den oben gennanten Befehlen erstellt wurde.

![Azure Virtuelle Machinen](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C2/Azure_VM_created_over_CLI.png)   
### C3
**Ich kann mittels Lift und Shift Services in die Cloud verschieben, mit Dokumentation | Ich kann mittels Lift und Reshape Services in die Cloud verschieben, mit Dokumentation**

Die Cloud und Cloud Services kommen immer mehr. Es soll immer mehr vereinfacht und mit wenig administrativem Aufwand in der Cloud betrieben werden. 
Oft können Services direkt einfach in die Cloud migriert werden, also Lift and Shift.
In vielen Fällen ist es jedoch ratsam nicht einfach lift and Shift zu machen, sondern vorgängig zu überlegen, was optimiert und verbessert werden kann. Z.B. ob eine Datenbank dezentral zum eigentlichen Service gebaut werden kann und z.B. im PaaS betrieben werden kann. So können die Applikationsserver skalierbar gemacht werden und mittels z.B. Cloud-Init Skripts automatisiert installiert werden. Dies nennt man Lift and Reshape.

### C4
**Ich kann VMs auf einer Cloud erstellen | Ich kann VMs auf mindestens 2 Cloud erstellen | Ich kann VMs auf mindestens 3 Cloud erstellen**

Für dieses Projekt wurden VMs auf MaaS (DNS Server), Azure (HAProxy) und  AWS (Webserver) aufgesetzt. <br>

**MaaS**
![MaaS](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C4/2021-11-14_18h21_10.png)

**Azure**
![Azure](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C4/Azure_VM_created_over_CLI.png)

**AWS**
![AWS](https://github.com/denizhkht/CNT-Gruppenarbeiten/blob/main/Dokumentation_Screenshots/C4/AWS_instances_created_over_CLI_new.png)
