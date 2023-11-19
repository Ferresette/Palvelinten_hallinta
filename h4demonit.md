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

Aloitin asentamalla Apache2 Webbipalvelimen. Sen jälkeen tein kansion /srv/salt/apache2/ minkä jälkeen loin init.sls tiedoston. Asennukset onnistuivat ja tiedostoja muutettiin onnistuneesti.

Curlasin t001 ip osoitteen ja tässä näkyvät sivustolle tehdyt muutokset.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/1dca5f0e-c76f-4b03-a57e-5c7f355ab0a5)

Alempana näkyy orjien tilat, mitkä tuli komennolla sudo salt '*' state.apply apache2


![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/1e8367ba-68c6-40c9-a97a-0a3763206e28)


![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/4d63f3f0-01ce-45a7-8ffa-bc513c3fa19a)

Viimeisenä vielä kuva sls tiedostosta. 

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/504b2f38-f4f9-4bfa-ae81-e35fce5dbe0c)


## d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.

Löysin Teron ohjeistuksen SSH tekemiseen. Lähdin muokkaamaan srv/salt/sshd.sls tiedostoa ja lisäsin sinne kyseisen koodin.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/6226a971-dd35-47c8-bd47-1c6143b98859)

Tämän jälkeen lähdin muokkaamaan srv/salt/sshd_config tiedostoa.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/0e2b2493-c820-4346-bea1-b6d427ea5752)

Ajoin vielä komennon sudo salt '*' state.apply sshd mikä antoi onnistuneet tilat.

Asensin Netcatin, jotta voisin saada loput tiedot.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/f734bb15-e6e7-4352-af21-d02698eeb213)

Onnistunut.

## References 

https://terokarvinen.com/2023/configuration-management-2023-autumn/

https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh

https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/?fromSearch=salt%20file





