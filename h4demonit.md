## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves, vain kohdat

    Infra as Code - Your wishes as a text file | Mahdollistaa toiveiden ilmaisemisen tekstitiedostona.
  
    top.sls - What Slave Runs What States | Määrittelee, mitä tehtäviä kullakin alikoneella suoritetaan.

Salt contributors: Salt overview, kohdat

    Rules of YAML | Säännöt ja sen yksinkertainen rakenne.
  
    YAML simple structure | Kolme perus elementtiä. Scalars, lists, Dictionaries.
  
    Lists and dictionaries - YAML block structures | Perustuu lohkorakenteisiin. Käytetään yleensä kahta välilyöntiä, eikä tabulaattoria. Merkinnät osoitetaan väliviivalla sekä välilyönnillä.

Salt contributors: Salt states, kohdat

    State modules | Saltin rakennuspalikat, määrittää toiminnot jotka Saltin tulee suorittaa järjestelmässä.
  
    The state SLS data structure | Käyttävät YAML:ia järjestelmän halutun tilan määrittämiseen.
  
    Organizing states | SLS tiedostojen järkevää jäsentämistä, ryhmittelyä. Auttaa hallintaa ja luettavuutta.
  
    The top.sls file | Keskeinen osa Saltin määritysten hallintaa. Linkittää järjestelmän komponentit stateihin. Mahdollistaa konfiguraatioiden kohdennetun soveltamisen.
  
    Create the SSH state | Kuinka SSH-palvelu tulee määrittää tai hallita Saltin avulla.
    
    Create the Apache state | Apache palvelimen asennus tai hallintaa liittyvien toimien ja konfiguraatioiden määrittämisen Saltilla.

## a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.

Tein ensiksi Vagrantilla yhden herran ja kaksi orjaa. Loin avaimet ja testasin yhteyden. Loin kansion /srv/salt/hello ja avasin sen init.sls ja kirjoitin sinne Hei maailma.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/88a376e1-ed1c-4046-803e-9801ff5fd279)

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/9f554ea6-116a-4c6e-b595-c02ed2b94536)


## b) Top. Tee top.sls niin, että tilat ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply".

Loin top.sls tiedoston kyseisillä tiedoilla. 

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/3949c3aa-63e1-4397-b3e7-bfd7062f4ca9)

Ajoin sen jälkeen komennolla sudo salt '*' state.apply onnistuneesti.


## c) Apache. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy.





Ensin käsin, vasta sitten automaattisesti.
Kirjoita tila sls-tiedostoon.
pkg-file-service
Tässä ei tarvita service:ssä watch, koska index.html ei ole asetustiedosto
## d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.
Tämä tehtävä on helpointa tehdä tavallisella virtuaalikoneella, jota Vagrant ei ohjaa.
Löydät oikean asetuksen katsomalla SSH:n asetustiedostoa
Nyt tarvitaan service-watch, jotta demoni käynnistetään uudelleen, jos asetustiedosto muuttuu masterilla
