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
