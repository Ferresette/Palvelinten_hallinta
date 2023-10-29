#
x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
Karvinen 2023: Create a Web Page Using Github
-Tässä opetellaan tekemään nettisivu käyttäen Githubia
Karvinen 2023: Run Salt Command Locally
-Toimii Windows ja Linux ympäristössä
-Käytetään yleensä kontrolloimaan monia orjakoneita verkkoympäristössä.
a) Asenna Salt (salt-minion) koneellesi.
  -Asennettu
b) Viisi tärkeintä. Näytä esimerkit viidestä tärkeimmästä Saltin tilafunktiosta: pkg, file, service, user, cmd. Analysoi ja selitä tulokset.
  pkg = pkg.installed on varmistus siitä, että paketti on asennettu järjestelmään. Mahdollistaa ohjelmistopakettien asennuksen ja hallinnan eri alustoilla. pkg.removed poistaa asennetun treen.
  file = file.managed tekee uuden kansion paikallisesti. Tein Teron sivujen ohjeiden mukaisella komennolla kansion. Toisella komennolla lisäsin sisältöä edelliseen tiedostoon. Viimeinen komento file.absent
poistaa kyseisen tiedoston. Succeeded teksti lopussa.
service = service.running komento ei minulla toiminut, mutta ajattelisin että tämän tarkoituksena olisi startata web-palvelin asetusten muuttamisen jälkeen. Ja service.dead komento pysäyttäisi kyseisen palvelimen.
user = user.present loin uuden käyttäjän sen mukana tuli home sekä käyttäjäryhmä. user.absent poistaa tehdyn käyttäjän ja sen tiedot.
cmd = käytin cmd.run komentoa mikä suorittaa komennon järjestelmässä. Tehtävänannossa oleva komento loi tiedoston cmdn kautta tmp/foo. Succeeded teksti lopussa.
  
c) Idempotentti. Anna esimerkki idempotenssista. Aja 'salt-call --local' komentoja, analysoi tulokset, selitä miten idempotenssi ilmenee.
  -Ideana on että komentoja voi suorittaa useasti peräkkäin ilman haittavaikutuksia. Esimerkiksi testaamalla onko joku palvelu käynnissä. Jos palvelu on käynnissä komennon suoritettua, ei tapahdu mitään.
  jos palvelu ei ole käynnissä se pyrkii käynnistämään palvelun.
d) Tietoa koneesta. Kerää tietoja koneesta Saltin grains.items -tekniikalla. Poimi kolme kiinnostavaa kohtaa, näytä tulokset ('grains.item osfinger virtual') ja analysoi ne.
  -Käytin komentoa grains.items. Kyseinen komento antaa kaiken mahdollisen tiedon ympäristöstä. Esimerkiksi näyttää minulle käyttöjärjestelmän mikä on Debian. Näen myös ip-osoitteeni samasta paikasta.
  löytyy myös group name mikä on: root ja host mikä on: testi.

 ## Lähteet:
https://terokarvinen.com/2023/configuration-management-2023-autumn/
https://terokarvinen.com/2021/salt-run-command-locally/

  
