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


