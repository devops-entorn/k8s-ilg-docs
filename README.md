# ENTORN ilg.cat v2223 Documentació

**Autor: Oriol Boix Anfosso** ([github](https://github.com/orboan))

```Els drets d'ús estan cedits, durant el curs acadèmic 2022-2023, i per a finalitats educatives al Departament d'Informàtica de l'Institut La Guineueta de Barcelona (Catalunya).```


## Perfils de l'Entorn

Aquest Entorn està disponible en tres perfils:

> **Entorn DEV**: per a desenvolupament d'aplicacions.

> **Entorn BIO**: per a Data Science, Big Data i Bioinformàtica.

> **Entorn OPS**: per a devops.

## Entorn i Docker

En aquesta versió de l'Entorn us proporciona **docker preinstal·lat** i _ready for use_.

Així, i gràcies a la tecnologia docker, disposeu d'una sèrie de serveis addicionals preconfigurats. Estan explicats al notebook ``serveis_docker.ipynb``.

## Accés a aplicacions web desenvolupades i desplegades per l'alumne

El perfil **Entorn DEV** permet accedir a, desplegar i desenvolupar aplicacions web fetes amb qualsevol tecnologia (java, python, javascript, php ...).

### Desplegament d'aplicacions web desenvolupades amb Java

Per a aplicacions web java que necessitin d'un Servidor d'Aplicacions Java independent, l'Entorn perfil DEV proporciona **Jetty**. Llegiu-ne les instruccions que trobareu al notebook ``serveis_docker.ipynb``.

Per a aplicacions web java desenvolupades amb un framework (com ara Spring) que proporcioni de forma incrustada a la mateixa aplicació un Servidor d'Aplicacions, podeu seguir les instruccions de desplegament que hi ha al següent apartat.

### Desplegament d'aplicacions web desenvolupades amb qualsevol tecnologia

Per a aplicacions web desplegades de forma independent (amb el seu propi Servidor d'Aplicacions) o usant servidors en contenidors docker, s'hi pot accedir usant la següent URL:

```
https://local.entorn.io/user/{nomdusuari}/proxy/{port}/
```

on heu de substituir ``{nomdusuari}`` pel vostre nom d'usuari de l'entorn, i ``{port}`` pel port que hàgiu configurat pel qual la vostra aplicació o servidor està escoltant (NOTA: **no oblideu d'escriure la barra al final**).

**Alternativament**, usant _SSH tunnelling_:

Al sistema hoste, executeu:

```bash
ssh -p 2222 {nomdusuari}@localhost -N -f -L 8080:localhost:{port}
```

on, també, heu de substituir ``{nomdusuari}`` pel vostre nom d'usuari de l'entorn, i ``{port}`` pel port que hàgiu configurat pel qual la vostra aplicació o servidor està escoltant.

Podreu accedir a la vostra aplicació web usant un navegador local al sistema hoste amb la següent adreça:

```
http://localhost:8080
```

## Entorn, jupyterlab i Ubuntu

Entorn està basat en [jupyterlab](https://jupyter.org/) i [Ubuntu 22.04](https://ubuntu.com/blog/ubuntu-22-04-lts-released) amb entorn gràfic d'escriptori XFCE4.

### Exemples de notebooks:

Al directori ``nb_examples`` trobareu exemples d'us d'alguns notebooks.

### Llistat de Notebooks disponibles

En aquest entorn podeu treballar amb els següents notebooks:

- **Python 3**: nucli python 3.10 disponible a tots els perfils.
- **Python 3 (Entorn BIO)**: nucli python 3.10 amb les llibreries més comunes de _Data Science_, _Biopython_ i _Spark_ per a BigData.
- **Java 17**: nucli java 17 basat en jshell, disponible en tots els perfils.
- **Javascript**: nucli javascript basat en node, disponible en tots els perfils.
- **Typescript**: nucli typescript (javascript fortament tipat), disponible en tots els perfils.
- **Kotlin (Entorn DEV i BIO)**: nucli amb el llenguatge de programació Kotlin, que fa servir la JVM.
- **R (Entorn BIO)**: nucli R amb les llibreries de bioinformàtica i _Spark_ per a BigData.
- **Scala (Entorn DEV)**: nucli amb el llenguatge de programació Scala, que fa servir la JVM.
- **Scala (Entorn BIO)**: nucli Scala amb les llibreries _Spark_ per a BigData.
- **IMongo (Entorn DEV i BIO)**: nucli que connecta amb mongodb, per a treballar totes les comandes shell i javascript de mongodb en un notebook.
- **Bash (Entorn OPS)**: nucli bash, per a treballar shellscripting amb bash.
- **Ansible (Entorn OPS)**: nucli ansible.

## Aplicacions disponibles via Jupyterlab

A través de la **interfície web de jupyterlab** podem tenim disponibles les següents aplicacions:

- Entorn (tots els perfils):
    - **Ubuntu Desktop**
    - **Visual Studio Code**
    - **Diagram**
    - **Video Chat** 

- Entorn DEV:
    - **PGAdmin**: client web per a PostgreSQL.
    - **Jetty**: Jetty Application Server (Java).
    - **Jenkins**

- Entorn BIO:
    - **PGAdmin**: client web per a PostgreSQL.
    - **R Studio**: R Studio.

- Entorn OPS:
    - **Portainer**: portainer (client web per a docker). Credencials: admin/admin
    - **Jenkins**


Altres aplicacions accessibles des de l'Escriptori (_**Desktop**_):

- **Jetbrains IDEs**: Cross-platform Jetbrains IDEs.
- **Eclipse**: IDE Eclipse.
- **Modelio**: diagrames UML i altres. [modelio.org](https://www.modelio.org/)
- **Netbeans**: IDE Netbeans.
- **MySQL Workbench**: client desktop app for MySQL.
- **Postman**: eina per a Rest APIs.
- **Pencil Project**: Wireframes i diagrames.
