# Cattle not pets

## x) 
Cattle & pets on DevOps filosofia. Mikä pyrkii siihen, että infastruktuuria ja palvelimia käsiteltäisiin helposti korvattavan karjana eikä lemmikkeinä.
Ideana on helpottaa automaatiota, skaalautavuutta sekä ongelmatilanteiden nopeaa korjaamista.

## a)  
Aloitin Vagrantin asennuksen ja asensin sen.
    
![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/c931afab-f3a2-45dd-b7d1-030018bdb0a0)


## b)
Asensin cmd vagrantin ja yhdistin sen toiseen koneeseen ssh avulla. Sekä kokeilin, että netti toimii.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/57fb15e8-528d-4cfe-86bc-3749adfa2c4a)


## c)
Tein kolme eri konetta ja myös salt herran sekä orjan käyttämällä teron koodia. Syötin koodin valmiina olevaan Vagrantfileen notepadissa ja tallensin sen users\kakko\vagrant\debian tiedostoon. Minkä jälkeen siirryin samaan tiedostoon komentorivissä ja syötin koodin. 

    >vagrant up
    
## ![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/6b1a82b2-2a7c-4451-86a4-1435fca55cc0)

## d) 
Kirjauduin sisään tmasterilla

     >vagrant ssh tmaster 
 
![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/973fd8f5-6b4c-4b1e-9945-5e75fcb0bbbd)

Lähdin hyväksymään avaimet
    $sudo salt-key -A

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/c22ac0d0-0a78-415f-84e6-20a3ebe3b26f)

 Avaimet hyväksytty

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/51847d00-d279-4e33-8885-5dcf12cb5630)

Sekä testasin vielä yhteyden

    $sudo salt '*' test.ping

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/ee4e9cfc-b772-4ac0-a1fa-db5adc973bbc)

## e)
Seuraavaksi lähdin kokeilemaan idempotentteja komentoja verkon yli. Ensimmäinen komento oli hyvin pitkä tulostus, joten lyhensin sitä toisella komennolla.

    $ sudo salt '*' state.single file.managed '/tmp/see-you-at-terokarvinen-com'
    $ sudo salt --state-output=terse '*' state.single file.managed '/tmp/see-you-at-terokarvinen-com'

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/0cae68de-451e-4df9-b2ae-eea07f8488c2)


## f)
Seuraava tehtävä oli kerätä tietoa grains.item komennolla, käytin seuraavia.

    $sudo salt '*' grains.items
    $sudo salt '*' grains.item osfinger ipv4

Ensimmäinen komento näytti käytännössä kaiken mahdollisen tiedon ympäristöstä, toinen näytti ip-osoitteet.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/c65aab01-b12f-4660-ada6-b6ea450d9b3a)

## g)
Seuraavaksi ajamaan lähdin ajamaan shell-komentoa. Pyysin ip-osoiteitta kyseisellä komennolla.

    $sudo salt '*' cmd.run 'hostname -I'

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/c7986418-b3da-4781-91b9-0566158612bd)

## h)
Aloin tekemään infraa koodina, käytin teron sivulta löytämää pohjaa. Tein ensiksi tiedoston, jonka jälkeen avasin tekstieditorin muokkausta varten.

    $ sudo mkdir -p /srv/salt/hello
    $ sudoedit /srv/salt/hello/init.sls

Syötin seuraavan tekstin aukeavaan tekstieditoriin.

    /tmp/infra-as-code:
      file.managed

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/8265a7ff-863c-4a02-81da-7cd4848a6f62)

Tarkastin sen lisäksi tiedot cat komennolla.

Käytin myös seuraava komentoa ja lisäsin myös tekstiä top.sls tiedostoon.

    $ sudoedit /srv/salt/top.sls

Tässä kyseinen teksti lisättynä top.sls tiedostoon

    base:
      '*':
        - hello

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/44542f33-2196-497f-b671-70760e104d1f)

Lopputulemana muutos tehty onnistuneesti.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/5219123e-9121-47f3-9c6d-bd346af30146)

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/9ae6a9d2-5ca8-4f66-a833-3f8ceb2c4730)


## References
https://terokarvinen.com/2023/configuration-management-2023-autumn/#h2-karjaa

https://terokarvinen.com/2023/salt-vagrant/

https://tuomasvalkamo.com/CMS-course/week-6/









    











