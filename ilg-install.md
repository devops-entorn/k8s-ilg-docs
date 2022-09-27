# ENTORN ilg.cat v2223 Documentació

**Autor: Oriol Boix Anfosso** ([github](https://github.com/orboan))

```Els drets d'ús estan cedits, durant el curs acadèmic 2022-2023, i per a finalitats educatives al Departament d'Informàtica de l'Institut La Guineueta de Barcelona (Catalunya).```


## Instal·lació de l'Entorn sobre un sistema Windows

**Prerequisits**: 

- 8 Gb RAM mínim, 16Gb recomanats.
- 100 Gb SSD mínim, 150 Gb recomanats (espai lliure necessari).
- Aquesta implementació de l'Entorn per a ilg.cat és compatible només amb processadors Intel / AMD x86_64.
- Windows 10 versió > 1903, Windows 11, Windows Server 2019 en endavant.
- Windowns Subsystem for Linux, versió 2.
- Ubuntu per a WSL.
- Docker Desktop amb Kubernetes / Rancher Desktop.
- Helm.


### Instal·lació de WSL v2

A un terminal PowerShell **com a Administrador**, executem:

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

**Ara reiniciem l'ordinador**.

A continuació, descarreguem i instal·lem el següent paquet:

[Darrera versió del Nucli de Linux per a WSL 2](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)


**Establim la versió 2 de WSL com a versió per defecte**: obrim PowerShell com a administrador, i executem:

```
wsl –set-default-version 2
```


### Instal·lació d'Ubuntu per a WSL

Obrim Microsoft Store i cerquem _Ubuntu_.

Descarreguem i instal·lem Ubuntu per a WSL.

Un cop instal·lat des del Microsoft Store, cal arrencar l’Ubuntu (clicar a Launch) perquè s’acabi d’instal·lar: **Haureu de crear un usuari per a Ubuntu**. 

_Nota: recordeu la contrasenya que establiu per a l'usuari, la necessitareu._


**Recomanable**: Executem la següent comanda a un PowerShell com a administrador:

```
wsl --set-version Ubuntu 2
```

Si la versió d'Ubuntu que s'ha instal·lat és la 22.04 (per exemple), executaríem:

```
wsl --set-version Ubuntu-22.04 2
```


### Instal·lació de Docker Desktop

[Descarreguem i instal·lem](https://docs.docker.com/desktop/install/windows-install/) la darrera versió de Doker Desktop per a Windows.

Un cop instal·lat Docker Desktop, cal ajustar-ne la configuració:


_General_:

- Start Docker Desktop when you log in:  activat només si tens >= 16 Gb RAM.
- Expose daemon ... without TLS: **activat**
- Use the WSL 2 based engine: **activat**
- Use Docker Compose v2: **activat**
- la resta d'opcions, **desactivades**


_Resources > WSL integration_:

- Enable integration with my default WSL 2 distro: **activat**
- Enable additional distros > Ubuntu: **activat**


_Docker Engine_:

- experimental: canviar de _false_ a _true_


_Kubernetes_:

- Enable Kubernetes: **activat**


_Software updates_:

- **Ho desactivem tot**


Finalment, cliquem al botó "**Apply and Restart**".


### Instal·lació de Helm

Helm és un gestor de paquets de Kubernetes. Des del terminal del bash d’Ubuntu, l’instal·larem:

```
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null

sudo apt-get install apt-transport-https --yes

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list

sudo apt-get update
sudo apt-get install helm

```


### Instal·lació de l'Entorn

Obrim un PowerShell com a Administrador, i executem:

```
d:\
mkdir entorn
attrib +h entorn
```

Obrim un terminal d'Ubuntu i executem:

```
cd /mnt/d/entorn
git clone https://github.com/entorn-io/k8s-ilg-min.git
cd k8s-ilg-min
./entorn-pull.sh
./entorn-install.sh
./entorn-start.sh
```

**Atenció**: quan executeu ``./entorn-pull.sh`` es descarregueran de dockerhub 5 imatges de docker. En finalitzar aquest script se us mostraran les imatges descarregades. Si no en són 5 (menys de 5) cal executar de nou aquest script abans d'executar el següent script ``./entorn-install.sh``.

> Per a saber quines i quantes imatges de docker que contenen al nom **entorn** tenim descarregades, podem executar la següent comanda: ``docker images | grep entorn``. N'hem de tenir 5 (en cas contrari, cal executar de nou ``./entorn-pull.sh``)

