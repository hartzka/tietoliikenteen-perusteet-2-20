---
path: '/osa-5/5-langaton'
title: 'Langaton verkko'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata langattomien verkkoje toimintaa ja ongelmia.
- Osaat kertoa mikä on WLAN ja miten viestit kulkevat sen ja langallisen verkon välillä.
- Tiedät mikä on tukiasema ja osaat kuvata sen perustoiminnan.

</text-box>

## Langaton verkko

Kaikille langattomille verkoille on yhteistä se, että käyttäjien laitteet (voidaan kutsua myös solmuiksi tai isäntäkoneiksi) ovat langattomasti yhteydessä verkon palvelut tarjoavaan tukiasemaan. Tällainen langaton linkki käyttäjän laitteen ja tukiaseman välillä toimii yleensä radioaalloilla. Niiden ongelma on se, että linkin kuuluvuusalue on rajattu, joten laitteen ja tukiaseman etäisyys on rajallinen. Langaton linkki on tyypillisesti toteutettu radioaalloilla, jolloin kaikki tukiaseman läheisyydessä olevat laitteet voivat kuulla kaiken liikenteen. Toisaalta radioallot vaimenevat etäisyyden kasvaessa. Tietoliikenteessä tästä puhutaan signaalin vaimenemisena. Signaalia (eli radioaaltoja) häiritsevät myös muiden laitteiden aiheuttamat häiriöt ja erilaisista pinnoista tapahtuvat heijastumiset. NÄiden seikkojen vuoksi kuuluvuus tukiaseman ja käyttäjän laitteen välillä voi vaihdella, vaikka molemmat laitteet olisivat paikallaan.

Langattomalle verkolle erityistä haastetta tuo kuitenkin käyttäjien laitteiden liikkuminen. Yhä useammin käytämme laitteita, joita kannetaan mukana ja jotka ovat yhdistettynä verkkoon myös liikkuessaan. Vaikka laite voi vaihtaa paikkaa myös langallisessa verkossa, niin se on siirtymisen aikana poissa verkosta. Langattomassa verkossa laite voi olla yhteydessä tukiasemaan myös silloin kun se liikkeessä.

Tällä hetkellä käytössä on kahden täysin erilaisen tekniikan avulla toteutettujan langattomia verkkoja. Ethernet-verkkoja mukailevia [WLAN](https://fi.wikipedia.org/wiki/WLAN)-verkkoja, jotka noudattavat jotain IEEE:n standardoimaa tiedonsiirtotapaa. [IEEE:n standardin 802.11](https://fi.wikipedia.org/wiki/IEEE_802.11) eri versiot määrittelevät erilaisia langattomia verkkotekniikoita langattoman lähiverkon toteuttamiseen. Osa laitteista ja tukiasemista tulee näistä vain yhtä ja osa tukee usampaa erilaista versiota. Nämä standardi eri versiot on nimetty kirjaimilla a-n. 

Toinen yleinen langaton verkko on [matkapuhelinverkko](https://fi.wikipedia.org/wiki/Matkapuhelinverkko) ja eritysien sen välityksellä käytettävä mobiilidata. Matkapuhelinverkkojen tekniikkakin on standardoitua. Koska nämä ovat puhelinverkkoja, niin niitä on alunperin standardoitu alueittain kuten langallisiakin puhelinverkkoja. Kaikenlaisia puhelinverkkoja standardoi [kansainvälinen televiestintäliitto ITU](https://fi.wikipedia.org/wiki/Kansainv%C3%A4linen_televiestint%C3%A4liitto). ITU keskittyy lähinnä eri operaattoreiden välisten asioiden säätelyyn. Operaattoreiden toiminta-alueilla on myös muita standardointiorganisaatioita, jotka vaikuttavat käytettäviin tekniikoihin. Nykyisessä globaalissa tilanteessa alueelliset standardointiorganisaatiot tekevät yhteistyötä [3GPP](https://fi.wikipedia.org/wiki/3GPP):ssä, jotta tulevat standardit olisivat mahdollisimman yhteensopivia eri puolilla maailmaa. Euroopassa näiden verkkojen standardoinnista vastaa [ETSI](https://fi.wikipedia.org/wiki/ETSI). 

Matkapuhelinverkkojen, joita kutsutaan myös mobiiliverkoiksi, kehitystä on jaettu sukupolviin. Toisen sukupolven (2G) verkot käyttivät GSM-tekniikkaa. Sen jälkeen siirryttiin [3G](https://fi.wikipedia.org/wiki/3G)-verkkoihin. Nyt on jo käytössä [4G](https://fi.wikipedia.org/wiki/4G)-verkkoja, mutta ne eivät vielä ole käytettävissä kaikkialla. Tällä hetkellä standardointi kohdistuu tulevan 5G-verkon tekniikoihin. Tavoitteena on sekä nopeuttaa signaalin kulkua verkossa (pienentää etenemisviivettä) että samanaikaisesti lisätä siirrettävän datan määrää aikayksikköä kohti (eli kasvattaa verkon nopeutta).

Muita tunnettuja langattomia standardoituja verkkoja ovat [Bluetooth](https://fi.wikipedia.org/wiki/Bluetooth) ja [ZigBee](https://fi.wikipedia.org/wiki/ZigBee). 

Tarkastelemme tällä kurssilla kuitenkin lähinnä WLAN-verkkojen toimintaa. Yleiset langattomaan liikennöintiin liittyvät seikat kuitenkin soveltuvat kaikille langattomille verkoille.


## Ad hoc -verkko

Langaton verkko voidaan rakentaa myös ilman tukiasemia. Tällöin puhutaan niin sanotuista ad hoc -verkoista, joiden toiminnallisuuden verkon rakentaja määrittelee täysin itsenäisesti. Tällaisen verkon ei tarvitse noudattaa mitään standardeja, mutta verkon toteuttajan on kuitenkin hyvä tietää kyseisen alueen radiotaajuuksien käyttösäännöt, jotta ei vahingossakaan syyllisty rikokseen.

Yksinkertaisimmillaan ad hoc -verkko on vain kahden laitteen välinen, jolloin laitteiden välinen liikennöinti tehdään langattomasti suoraan laitteelta toiselle.  Laajimmillaan tällaiset ad hoc -verkot voivat olla useiden satojen sensorien omia verkkoja. Näistä langattomista sensoriverkoista on hyvä kuvaus englanninkielisessä wikipediassa sivulla [wireless sensor networks](https://en.wikipedia.org/wiki/Wireless_sensor_network).

Ad hoc -verkon koneet voivat siis suoraan kommunikoida vain omalla kuuluvuusalueellaan olevien muiden koneiden kanssa. Koska verkossa ei ole mitään palveluja suoraan tarjolla. Jos tällaisen verkon laitteen pitää kommunikoida kuuluvuusalueensa ulkopuolella olevien laitteiden kanssa, niin verkon pitää tarjota reititys näiden laitteiden välillä. Verkkon voidaan toki toteuttaa myös vaikka oma nimipalvelu ja verkon laitteiden tunnisteiden jakelu. Jonkun on siis tuotettava nämä palvelun tällaisen satunnaisverkon käyttäjille. 


Ad hoc -verkkojen käyttö tiettyihin specifeihin tarkoituksiin on vuosien varrella selvitelty paljonkin. WLANin toteutuksessa käytetyllä tekniikalla toteutettujan ad hoc -verkkoja kutsutaan usein  [mobiileiksi ad hoc -verkoiksi](https://fi.wikipedia.org/wiki/Mobile_ad-hoc_network) (MANET). Autoja ajatellaan on myös pohdittu erityisten [vehicular ad hoc -verkkojen](https://en.wikipedia.org/wiki/Vehicular_ad-hoc_network) toiminnallisuutta. Näiden verkkojen erityispiirre on vekon solmujen suuri liikenopeus.

## Langattoman verkon ongelmia

Signaalin heijastuminen ja siitä aiheutuva viive voi pahimmillaan sekoittaa alkuperäisen suoraan menevän ja heijastunutta reittiä hiukan kauemmin kulkevan signaalin siten, että vastaanottaja ei pysty enää selvittämään viestin sisältöä tästä yhteissignaalista. Usein heijastunut signaali on kuitenkin vaimentunut sen verran, että alkuperäinen signaali erottuu vastaanottajan kannalta riittävästi.

Koska signaali kulkee ilmateitse, niin maaston muodot voivat jopa kokonaan estää signaalin kulkemisen vastaanottajalle. Langattoman verkon toimnnan kannalta signaalin esteetön kulku on välttämätöntä ainakin lähettäjän ja vastaanottajan välillä. 

Langattomista verkoista on tunnistettu kaksi yleistä ongelmatilannetta, jota kutsutaan kätketyn aseman ja näkyvän aseman ongelmiksi. 

Kätketyn aseman (engl. hidden terminal) ongelmassa kaksi laitetta yrittää samanaikasesti viestiä kolmannelle. Nämä kaksi eivät kuitenkaan voi kuulla toistensa viestejä, koska ne eivät ole toistensa kuuluvuusalueella. Tämä voi johtua esimerkiksi maastoesteestä niiden välillä tai siitä, että ne ovat eri puolilla laitetta, jonka kanssa ne yrittävät kommunikoida.


KUVA pari. Joista toisesa kätketyn aseman ongelma ja toisessa näkyvän aseman ongelma

Näkyvän aseman (engl. exposed terminal) ongelmassa puolestaan laite kuulee toisen laitteen lähetyssignaalin ja jättää lähettämättä oman signaalinsa, vaikka signaalit eivät vastaanottajien kannalta mene sekaisin. Tällöin asemat ovat toistensa kuuluvuusalueella, mutta viestien vastaanottajat eivät kuulisi toisen aseman viestejä, joten niiden kannalta signaalien sekoittumista ei tapahtuisi.

Molemmat ongelmat heikentävät verkon toimintaa. Kätketyn asemant apauksessa molemmat lähetetyt viestit vaurioituvat ja se pitää lähettää myöhemmin uudelleen. Näkyvän aseman tapauksessa taas kaista jää käyttämättä, vaikka viesti olisi mennyt virheettömästi perille.

Koska näitä ongelmia ei voi langattomista verkoista poistaa, niin useimmissa verkoissa edellytetään, että kaikki virheettömästi vastaanotetut viestit kuitataan jo linkkikerroksen kuittauksella. Muistathan, että kuljetuskerroksen TCP-protokollakin käytti kuittauksia viestien perillemenon varmistamiseen. Nyt kuittauksia käytetään linkkikerroksella varmistamaan, että viesti meni perille. Kuittaukset lisäävät verkon liikennettä, mutta koska lähettäjällä ei langattomassa verkossa ole mahdollisuutta itse varmistua viestin perillemenosta, niin se joutuu turvautumaan vastaanottajan lähettämään kuittaukseen asian varmistamiseksi.


## WLAN / IEEE 802.11

IEEE 802.11 -tekniikalla toteutettu WLAN verkko on kotiverkoille tyypillinen langaton verkko. Myös yritysten omat sisäiset ja niiden asiakkailleen tarjoamat avoimet WLAN-verkot on toteutettu jollain IEEE 802.11 standardin versiolla.

Näistä verkoista ja niiden laitteista käytetään usein myös Wi-Fi nimitystä. Wi-Fi on rekisteröity tavaramerkki, jota hallinnoi Wi-Fi alliance (verkkosivu https://www.wi-fi.org/). Se myöntää yrityksille (maksua vastaan) oikeuden käyttää Wi-Fi sertifioitu merkkiä yrityksen valmistamissa verkkolaitteissa.


IEEE 802.11 -verkkojen tukiasemat palvelevat kukin omaa erillistä joukkoa laitteita. Jokainen tukiasema on erikseen yhdistetty langalliseen verkkoon.  Jokainen laite kommunikoi vain yhden tukiaeman kanssa. Jokaisella tukiasemalla on tunniste (Service Set ID, SSID) ja MAC-osoite. Tukiasema myös kommunikoi siihen liittyneiden laitteiden kanssa tietyllä kanavalla.

IEEE 802.11. jakaa käytettävän taajuusalueen (yleensä joko 2,4 giga hertsiä (GHz) tai 5 GHz) kanaviin, joita 2,4 GHx:n alueella on vähintään 11 (USA). Euroopassa kanavia on 13 ja Japanissa 14. Kanavilla varatut kapeat taajuuskaistat ovat limittäin (eli ne menevät osittain päällekkäin), jolloin vierekkäisillä kanavilla kommunikoivien laitteiden viestit voivat häiritä toisiaan. Kanavat 1, 6 ja 11 eivät ole keskenään päällekkäin, joten niitä voidaan käyttää vaikka laitteet kuulisivat toistensa viestejä. 

Tukiaseman kanava konfiguroitavissa. Jos mahdollista, niin tukiaseman kanava kannattaa valita niin, että se on mahdollisimman kaukana sen kuulemien tukiasemine kanavista. Näin kommunikointi tukiaseman ja siihen yhdistyneiden laitteiden välillä on mahdollisimman häiriötöntä.  HUomaa, että naapuritukiasemilla voi olla käytössä sama kanava. Tämä on yleisin syy siihen, että kotiverkon langaton tukiasema tuntuu pätkivän tai toimivan kovin hitaasti. Erityisesti kerrostaloissa tai kahviloissa tukiasema voi kuulla useiden muiden tukiasemien signaaleja. Jos niistä yksi tai useampia on samalla (tai hyvin läheisellä) kanavalla, niin ne eivät voi lähettää samaanaikaan, jolloin lähetyksiin tulee viiveitä. Ne voivat kyllä käyttää samaa kanavaa, mutta viestien lähetykset täytyy tehdä vuorotellen, jotta viestit voidaan vastaanottaa oikein. Jos siis havaitset ongelmia langattomassa liikenteess, niin kannattaa tarkistaa millä kanavilla kyseiseen kohtaan kuuluvat tukiasemat liikennöivät ja valita oman tukiaseman kanava mahdollisimman kauas muista sille kuuluvien tukiasemien kanavista. 

Koska WLANissa ei ole mitään koordinointia, niin usein tukiasemian samanaikaista kuulumista kutsutaan joskus Wi-Fi viidakoksi (engl. Wi-Fi jungle). Kun tällaisessa viidakossa yrittää yhdistää omaa tietokonettaan internetiin, niin valittavana voi olla useita langattomia lähiverkkoja ja niiden tukiasemia. 

Kun laite haluaa tällaisessa usean tukiaseman viidakossa liittyä verkkoon, niin sen pitää kiinnittyä (engl. associate) yhteen tukiasemaan. Se sisi tavallaan rakentaa 'näkymättömän langan' itsensä ja tukiaseman välille. Kaikki laitteen liikennöinti tapahtuu vain ja ainoastaan tämän tukiaseman kanssa. 

Ennen liittymistään laite voi vain passiivisesti hetken kuunnella liikennettä kaikilla kanavilla ja etsiä sieltä erityisiä merkkikehyksiä (engl. beacon frame). Niillä tukiasemat'mainostavat itseään.  Merkkikehyksessä on tukiaseman tunniste (SSID, service set ID) ja MAC-osoite. Näistä laite voi sitten valita haluamansa tukiaseman.

Vaihtoehtoisesti laite voi ennen liittymistään aktiivisesti lähettää kyselykehyksen (engl. probe), johon tukiasemat sitten vastaavat.

Standardit eivät millään tavalla määrittele kriteerejä, joiden mukaisesti laitteen pitäisi tukiaema valita. Laite saa tehdä valinnan haluallaan tavalla. Useimmiten laitevalmistajat käyttävät valintaperusteena signaalin voimakkuutta.

Kun laite on päättänyt, mihin tukiasemaan se haluaa kiinnittyä, niin se lähettää erityisen kiinnittymispyynnön (engl. association request frame), jonka tukiasema hyväksyy vastausviestillään. Nyt laite voi linkkikerroksen näkökulmasta liikennöidä muun verkon kanssa tukiaseman kautta, mutta ylempien kerrosten kannalta se ei vielä ole liittyneenä internetiin. Siltä puuttuu esimerkiksi vielä IP-osoite. Toki laitteen tarvitsevat varkkoyhteyteen liittyvät tiedot voi jo olla asetettuna laitteen konfigurointitietoihin, mutta yleensä langattomaan verkkoon liittyvä laite pyytää näitä tietoja DHCP-protokollalla.

Kuten monet avoimia Wi-Fi -verkkoja käyttäneet jo tietävätkin, niin monet palveluntarjoajat rajoittavat langattoman verkon käyttöä, jolloin tukiasemaan liittymisen yhteydessä voidaan edellyttää laitteen tai sen käyttäjän tunnistamista. Laitteen tunnistaminen voidaan tehdä käyttämällä ns. langattoman verkon salasanaa. Tällöin tukiasema hyväksyy kiinnittymispyynnön vain sellaisilta laitteilta, jotka osaavat antaa silleä oikealla salausmenetelmällä salatun oikean salasanan. Useimmat operaattorin myymät Wi-Fi -tukiasemat on nykyisin oletuarvoisesti suojattu tällä menetelmällä. Tällöin tukiaseman tunniste ja salasana on usein valmiina tukiaseman pohjassa olevassa tarrassa. Tukiasema voi tunnistaa laitteen myös laitteen käyttämän MAC-osoitteen avulla. Tällöin tukiasemalle on etukäteen kerrottu sallittujen laitteiden MAC-osoitteet.  Tätä ei enää pidetä kovin turvallisena vaihtoehtona, koska pahantahtoinen toimija voi helposti verkkoa kuuntelemalla saada selville sallittuja MAC-osoitteet. Koska nykyään laitteen MAC-osoite on helposti vaihdettavissa, pahantahtoisen toimijan on helppo kiinnittyä tällaiseen pelkästään MAC-osoitteilla suojattuun verkkoon.

Laitteen sijaan langattoman verkon haltija voi edellyttää käyttäjän tunnistamista. Tällöin tukiasema käyttää erillistä tunnistuspalvelua, johon käyttäjän pitää tunnistautua esimerkiksi käyttäjätunnuksella ja salasanalla. Tunnistautumisen jälkeen käyttäjän laitteella voi liikennöidä verkossa. Jätämme erilaisten käyttäjän tunnistuksen menetelmien tarkemman tarkastelun tietoturvakursseille, kuten Cyber security.

### Lähetysvuorojen jakely

IEEE 802.11 standardin mukaan toimivat verkot käyttävät kehysten yhteentörmäysten välttämiseen CSMA/CA menetelmää, johon jo tustuimme lyhyesti aiemmin. Siinähän tavoitteena oli erityisesti välttää yhteentörmäyksiä.   Katsotaan nyt tarkemmin miten tämä WLAN-verkoissa tehdään.

CSMA/CA:ssa edellytään, että lähettäjän pitää aina odottaa pieni hetki vapaata kanavaa kuunnellen ennenkuin lähetys voi alkaa. Näitä odotusaikoja on itseasiassa määritelty kaksi eri mittaista. SIFS (Short Inter-frame Spacing) on lyhyt ajanjakso, jota käytetään odotuksessa silloin, kun lähettäjä jo ennalta tietää että seuraavan kehyksen lähetysvuoro on oikeastaan sillä. Esimerkiksi datan vastaanottokuittauksien lähetys käyttää tätä lyhyempää odotusta. Lyhyt odotus tarvitaan jo pelkästään siihen, että alkuperäisen datan lähettäjän vaihtaa omat antenninsa lähetystilasta vastaanottotilaan.  Jos lähettäjä pyrkii lähettämään uuden datakehyksen, niin silloin se käyttää odotuksen kestona pidempää DIFS:iä (Distributed Inter-frame Spacing), jolla siis erotellaan eri lähettäjien eri datakehyksiä toisistaan. Koska SIFS on lyhyempi kuin DIFS, niin erilaiset kuittausviestit yms. saavat prioriteetin, jolloin ne lähetetään ensin ja pidemmät datakehykset joutuvan odottamaan hiukan kauemmin.

WLAN-verkkojen käyttämässä CSMA/CA:ssa lähettäjän yleisesti käyttävät lisäksi myös kanavan varausta. Koska varauskehykset ja niiden kuittaukset ovat huomattavan paljon lyhyempiä kuin varsinaiset datakehykset, niin yhteentörmäykset varauskehysten kesken ovat nopeita selvittää. Lähettäjähän ei kuuntele tuliko yhteentörmäys, joten jos yhteentörmäys tulee pitkän datakehyksen aikana, niin lähettäjä kuitenkin lähettää kehyksen kokonaan. Kätketyn aseman ongelman vuoksi tällainen yhteentörmäys on mahdollinen. Nyt varausviestien kanssa lähettäjä, odotettuaan tuon DIFS aikaa, lähettääkin varsinaisen ison datakehyksen sijaan pienen varauskehyksen (Request To Send, RTS), jossa se kertoo kuinka ison kehyksen se haluaa lähettää ja kuinka kauan lähetys tulee kestämään. Vastaanottaja vahvistgaa tämän varauksen erillisellä vahvistusviestillä (Clear To Send, CTS), jonka se lähettää heti SIFS ajan jälkeen, jolloin mikään muu asema ei vielä voi lähettää. Koska kuittaus tulee ison kehyksen vastaanottajalta, niin se tavoittaa kaikki ne laitteet, joiden mahdollinen lähetys voisi häiritä datakehyksen lähetystä. Ne osaavat nyt tämän kuittausviestin tietojen avulla odottaa koko datakehyksen lähetyksen ajan ennenkuin ne edes yrittävät omaa lähetystään. Näin alkuperäiseltä lähettäjältä kätkössä oleva asema saa tiedon lähetyksestä, jota ei itse muuten pysty havaitsemaan.


KUVA: Kirjan kuvasta 6.12 (editio 6) jonkunlainen oma versio  - liittyy siis tuohon edelliseen kappaleeseen

KUVA: Kuvassa on yhden data kehyksen lähetykseen liittyvät viestit eli ensin varaus ja varauksen vahvistus ja sitten varsinainen datakahys ja lopuksi vielä sen kuittaus.


### Langattoman verkon kehys


Langattoman verkon kehyksessä (katso kuva englanninkielisestä wikipediasta https://en.wikipedia.org/wiki/IEEE_802.11#Layer_2_%E2%80%93_Datagrams) on neljä osoitetta. Muistathan, että langallisen ethernet-verkon kehyksessä oli vain kaksi osoitetta (vastaanottajan MAC ja lähettäjän MAC). Langattomassa verkossa kehykselle on määriteltä neljä osoitekenttää, joista tosin yleensä ei käytetä kuin kolmea. Muista, että nämä kehykset ovat linkkikerroksella, jolloin kehysten osoitetiedot ovat MAC-osoitteita.

- osoite 1 on 
- osoite 2 on 
- osoite 3 on 
- osoite 4 on käytössä vain ad hoc -verkoissa, jolloin sillä voidaan 







<b>
o	osoitteiden käyttö: langattomalta internetiin, internestistä langattomalle

</b>


