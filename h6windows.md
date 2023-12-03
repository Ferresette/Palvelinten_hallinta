## x) Lue ja tiivistä.

**Halonen, Rajala ja Ollikainen 2023: Installing Windows 10 on a virtual machine**

Käytännössä kerrotaan miten Windows asennetaan virtuaalikoneelle. Linkit asennussivulle, kerrotaan asetukset mitkä olisi suotava laittaa asennusvaiheessa.
Harjoitellaan myös miten testataan yhteyden toimintaa ympäristössä.

**LSB Workgroup, The Linux Foundation 2015: Filesystem Hierarchy Standard**

FSH on dokumentti, mikä määrittelee Linuxin järjestelmän rakenteen ja tiedostosijainnit. Käytännössä neuvoo miten tiedostot ja hakemistot tulisi järjestää Linuxin käyttöjärjestelmässä.
Ohjeistaa missä ne pitäisi olla, jotta kaikki toimisi yhteensopivasti keskenään.

## a) Asenna Windows virtuaalikoneeseen.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/48bb49c3-854a-4113-aab8-645dcb42fad3)

Sain kyseisen viestin, ja koitin selvitellä mistä johtuu. Kokeilin uudelleen lataamalla ISO tiedostoa sekä muokkaamalla asetuksia ohjeiden avulla mitä löysin netistä tämän ongelman ilmetessä.
Mikään ei oikeastaan auttanut ratkaisemaan itselläni tätä ongelmaa, mutta monessa ohjeessa luki, että hyvin mahdollinen syy on ettei tietokoneella ole tarpeeksi muistia.
Tulin siihen lopputulokseen, että vika johtuu tästä, sillä kyseinen tietokone millä olen tehnyt harjoituksia ei ole parhaasta päästä.

Tutustuin itse suorittamisen sijasta ohjeisiin https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md miten Windows oitaisiin asennettu virtuaalikoneelle.

## b) Asenna Salt Windowsille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut.

Saltin asennus on myös hieman vaikeaa, jos ei ole edes Windows palvelinta joten turvauduin taas lukemaan artikkeleita kyseisestä toimenpiteestä.

https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/windows.html hyödynsin kyseistä linkkiä, mitä kautta selvitin miten kyseinen asennus tapahtuisi.

Käytännössä ladattaisiin Saltin lataustiedosto Windowsille, minkä jälkeen se ajettaisiin siellä. Määriteltäisiin Masterille ja Minionille nimet ja viimeisteltäisiin asennus.

Tämän jälkeen komennolla voitaisiin testata onnistunut asennus komennolla,

    salt-call --local --version

## c) Kerää Windows-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.

grains.items toiminto käytännössä kertoo sinulle tietoja ympäristöstä tai koneesta riippuen komennosta. Etsin netistä tietoa millaisia eri komentoja voisi käyttää. https://docs.saltproject.io/en/latest/ref/modules/all/salt.modules.grains.html

    salt '*' grains.item os* - saisi tietoja käyttöjärjestelmään liittyen

    salt '*' grains.item mem_total - voi selvittää koneiden yhteismuisti määrän

    salt '*' grains.item roles - näkisi eri koneiden roolit tai ryhmät


## d) Kokeile Saltin file -toimintoa Windowsilla.

File -toiminnon käyttö mahdollistaa tiedostojen hallinnan ja tarkistamisen. Esimerkiksi luominen, poistaminen, kopiointi tai muokkaaminen. Etsin taas netistä vähän esimerkki komentoja, kun en itse päässyt kokeilemaan.

    salt '*' file.file_exists C:\polku\tiedosto.txt - jos haluaisit tarkistaa, onko tietty tiedosto olemassa tietyillä Windows-koneilla. Vastauksena tulisi True tai False riippuen onko tiedostoa olemassa.

    salt '*' file.touch C:\polku\uusi_tiedosto.txt - luo uuden tiedoston annettuun polkuun

    salt '*' file.remove C:\polku\tiedosto.txt - poistaa tiedoston

    salt '*' file.set_mode C:\polku\tiedosto.txt 777 - antaisi 777 oikeudet kyseiselle tiedostolle

## e) Kokeile jotain itsellesi uutta toimintoa Saltista Windowsilla.

Lähdin jälleen netistä etsimään tietoa itselleni uusiin komentoihin, löysin seuraavia komentoja mitkä olivat itselleni uusia.

    salt '*' win_timezone.get_zone - kertoo windows koneiden käyttämän aikavyöhykkeen

    salt '*' win_timezone.set_zone 'Eastern Standard Time' - kyseisellä komennolla olisi mahdollista vaihtaa aikavyöhykettä


## References

https://docs.saltproject.io/en/latest/ref/modules/all/salt.modules.grains.html

https://terokarvinen.com/2023/configuration-management-2023-autumn/

https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md

https://terokarvinen.com/2018/04/18/control-windows-with-salt/



