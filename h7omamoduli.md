# Miniprojekti

Tarkoituksena minulla on tehdä miniprojektini hyödyntäen Saltia ratkaisemaan jokin tarve. Hetken mietinnän jälkeen päädyin testaamaan palomuurisääntöjen hallintaa. Projektin suoritan yhdella masterilla ja kahdella orjalla.

Alkutöikseni lähdin käynnistämään koneitani projektiani varten. 

    tmaster
    t001
    t002

Koneet käynnissä, kävin hyväksymässä avaimet.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/5c04a99c-0e76-49ef-8416-0c0bdd2a8bcb)

Sekä vielä varmistetaan, että yhteydet toimii.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/5c8cd4e0-43c2-479f-8e7b-4cf502d1de84)

Aloitin luomalla uuden hakemiston /srv/salt/

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/808049db-ea45-46b8-a015-f8d744880474)

Tämän jälkeen lähdin tekemään kyseiseen hakemistoon firewall.sls tekstitiedostoa, mikä määrittelisi palomuurisääntöjä.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/4f485e82-c690-4fb1-85cf-723317abb0ee)

Ensimmäiset haasteet tulivat vastaan kun lähdin ajamaan komentoa orjille. Aloin selvittämään mistä ongelma voisi kiikastaa.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/35f72f50-1258-45a6-8bb3-b0920fca09ae)

Hetken selvittelyjen jälkeen ymmärsin, että minulta puuttuu palomuurin hallintatyökalu, joten lähdettiin asentamaan sitä komennolla

    sudo salt '*' pkg.install firewalld

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/dcd66f91-1fee-4737-853a-cb4e14224a21)

Hommat alkoivat näyttää jo paljon lupaavammalta, lähdetään kokeilemaan uudestaan ajamaan tilaa orjille.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/887eabcc-a5ba-411c-974d-f630169ae5eb)

Punaiseen törmättiin taas että heilahti, käsittääkseni sls tiedostossa on jotain feilua. Lähdin tarkastelemaan tiedostoa. Löysin, että permanent attribuuttia ei hyväksytä, joten poistin sen ja kokeilin ajaa uudestaan orjille. Tila muuttui hieman paremman näköiseksi, mutta silti on mutkia matkassa.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/116f729a-4bee-4db3-bf31-6bbd37ffb80f)

Kuvaa tulkitakseni pystyy sanomaan, että SSH portti onnistuttiin saamaan sallituksi, mutta HTTP portin poistossa oli ongelma. sls tiedoston muuttaminen HTTP portin suhteen ei auttanut, joten lähdin manuaalisesti sulkemaan ne orjiltani.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/74466e14-f1f0-475f-ad1f-f720eeb8d252)

Lopputuloksena sain nyt muutettua orjille SSH portit haluttuun tilaan, mutta HTTP portit jouduin sulkemaan manuaalisesti. Alla olevissa kuvissa näkyy onnistuneet muutokset, eli SSH portit ovat auki ja HTTP portit ovat suljettuna.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/e933d8f2-0fca-4a04-ab66-68fc15d1206f)

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/c4d58a2f-c2fa-4aa1-bcf9-8f8bd78a6ad0)

Itseäni jäi hieman häiritsemään, miksi HTTP - portin sulkeminen ei onnistunut automaattisesti. Kokeilin monia eri komentoja tilan saavuttamiseksi, mutta päädyin lopputulokseen, että kyseinen palomuurin hallintatyökalu ei välttämättä tukenut kyseistä toimintoa.

Alla vielä kuva lopullisesta sls filestä, verrattuna ylempänä olevaan jouduin siis poistamaan HTTP -portin määritykset niiden toimimattomuuden vuoksi.

![image](https://github.com/Ferresette/Palvelinten_hallinta/assets/148973799/d11c0058-a58b-4266-a68a-ab8d849b3679)


## References

https://terokarvinen.com/2023/configuration-management-2023-autumn/

https://terokarvinen.com/2021/salt-run-command-locally/

https://terokarvinen.com/2023/salt-vagrant/

chat.openai.com

https://docs.saltproject.io/en/latest/topics/tutorials/firewall.html






















