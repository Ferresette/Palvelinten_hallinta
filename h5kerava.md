## x) Lue ja tiivistä

- Saltilla Apache2 konfiguraatiot orjille.
- Miten etsitään erilaisia tiedostoja jos niitä muutetaan GUI:n kautta.
- Miten erilaisia tiedostoja voidaan muuttaa komennoilla.

## a) CSI Kerava. Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi. Selitä kaikki käyttämäsi parametrit ja format string 'man find' avulla.

Aloitin suorittamaan tehtävää Teron vinkeistä löytyvällä komennolla https://terokarvinen.com/2023/configuration-management-2023-autumn/.

    find -printf '%T+ %p\n'

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/42b6fb5c-9637-4374-9fc8-ade2436d2e9d)

Seuraavaksi aloin tutkimaan parametrien tarkoituksia. Käytin komentoa man find, mistä löytyi todella kattavasti infoa kyseisen komennon toiminnasta.

    find - pääkomento millä lähdetään etsimään tiedostoja ja hakemistoja.
    
    -printf '%T+ %p\n' - Määrittää tulostusmuodon
    
    '%T - Kertoo ajankohdan, voi tarkentaa lisäämällä T perään esim y (year), m (month) tai d (day)
    
    %p\n' - Tiedoston nimi ja rivinvaihto

## b) Gui2fs. Muokkaa asetuksia jostain graafisen käyttöliittymän (GUI) ohjelmasta käyttäen ohjelman valikoita ja dialogeja. Etsi tämä asetus tiedostojärjestelmästä.

Lähdin toteuttamaan kyseistä tehtävää vaihtamalla sijaintini Amerikkaan Chicagoon. 

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/891bd798-e5ed-4845-a2e7-5f094c965252)

Lähdin kokeilemaan find komennolla, jotta löytäisin että onko muutoksia tehty tiedostoihin. Alla olevan kuvan perusteella, localtime kansiossa on käyty ja sen alapuolella on config tiedostoja. Tämän perusteella voisi päätellä, että aikaa on muutettu.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/37004422-2d71-46c5-aa78-709a58f027fd)

## c) Komennus. Tee Salt-tila, joka asentaa järjestelmään uuden komennon.

Aloitin tehtävän luomalla kokeilu.sls tiedoston. 

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/18478b69-16d6-405e-95a1-37161a13e49f)

Seuraavaksi siirsin kyseisen tiedoston hakemistoon /srv/salt

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/b9643516-d540-4609-b786-2ae90553cf8e)

Lähdin kokeilemaan tämän jälkeen, toimiko kyseinen muutos komennolla

        sudo salt '*' state.apply kokeilu

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/90a983ae-2113-4f3c-8e67-3f8460ad18eb)

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/77182598-30f6-4700-976b-1692f5cf0780)

Komento toimi molemmilla orjilla.

## d) Apassi. Tee Salt-tila, joka asentaa Apachen näyttämään kotihakemistoja.

Apache2 webbipalvelin minulla oli jo valmiiksi asennettuna ja se oli myös päällä. 

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/517be3a3-60be-4ed5-9419-de86783b77e5)

Lähdin hyödyntämään teron sivulla annettuja neuvoja. https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/ 

Siirryin kansioon srv/salt/apache2 ja lisäsin tekstieditoriin seuraavan tekstin.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/a8cfa398-9278-4e65-a34b-9589ee7b4764)









