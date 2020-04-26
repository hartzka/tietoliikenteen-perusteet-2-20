---
path: '/osa-4/1-IPv4-IPv6'
title: 'IPv4 ja IPv6 osoitteet'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata IPv4 ja IPv6 osoitteet.
- Osaat selittää, miksi on siirrytty ja edelleen siirrytään IPv4 osoitteiden käytöstä kohti IPv6 osoitteiden käyttöä.

</text-box>


## Verkkokerroksen tehtävät

Verkkokerros huolehtii viestin välittämistä lähettäjältä vastaanottajalle. Verkkokerroksella toimivien laitteiden täytyy siis tietää jotain verkon rakenteesta ja siitä mistä päin verkkoa vastaanottaja löytyy.

Internetin etappivälitteisyys näkyy erityisesti verkkokerroksella. Jokainen verkkokerroksella toimiva laite voi vastaanottaa sille linkkikerroksella osoitettuja viestejä, joiden lopullinen vastaanottaja se ei ole. Kun laitteelle tulee viesti, jonka vastaanottaja se ei ole, on laitteella velvollisuus lähettää viesti edelleen kohti vastaanottajaa.

Verkkokerroksella laitteet tunnistetaan niiden IP-numeroista, joita usein myös IP-osoitteiksi kutsutaan.

## IP-osoite

IP-protokollasta on tällä hetkellä käytössä kaksi versiota perinteinen [IPv4](https://fi.wikipedia.org/wiki/IP) ja uudempi [IPv6](https://fi.wikipedia.org/wiki/IPv6). IPv4 on ollut Internetin verkkokerroksen välitysprotokolla koko Internetin olemassaolon ajan. Vieläkin kun puhutaan pelkästään IP:stä yleensä aina tarkoitetaan IP versiota 4.

Nämä versionumerot 4 ja 6 vaikuttavat oudoilta, mutta internetin dokumentaatiosta löytyy määrittelyt myös protokollan versioille 1,2,3 ja 5. Ne eivät ole käytössä.

## IPv4

IPv4:ssä [IP-osoitteen](https://fi.wikipedia.org/wiki/IP-osoite) pituus on 32-bittiä eli 4 tavua. Osoite ilmoitetaankin yleensä näiden tavujen numeroarvoina eli muodossa 10.12.34.216. Jokaisella internetiin suoraan liitetyllä laitteella täytyy olla uniikki osoite. Kuten jo tiedämme näitä osoitteita maailmanlaajuisesti hallinnoi IANA.

IP-osoite jaetaan aina kahteen osaan. Osoitteen alkuosa kertoo kyseistä osoiteavaruutta hallinnoivan operaattorin. Operaattori voi sitten jakaa hallitsemansa osoiteavaruuden osoitteet verkkolaitteille haluamallaan tavalla. Tämä rajapinta tunnistetaan verkon peitteen avulla. Verkonpeite on 32-bittinen sana, jonka alkupään bitit ovat ykkösiä ja loppupään bitit nollia. Ykkösbittien osa kertoo operaattorin tunnisteen ja nollabittien osa on sitten se alue osoitteista, joilla operaattorin hallinnoiman verkon laitteet tunnistetaan. Saman verkon laitteilla on aina sama alkuosa, jonka pituuden näkee suoraan tästä verkon peitteestä. Saman verkon laitteilla on kuitenkin oltava eri IP-osoitteet, jotta ne voidaan erottaa toisistaan. Verkon peite merkitään usein kauttaviivalla IP-osoitteen perään. Peite voi olla samassa muodossa kuin IP-osoite tai sitten se voidaan ilmaista kokonaisluvulla 0-32, jolloin kokonaisluku kertoo peitteen alkuosan ykkösbittien lukumäärän.

Alunperin näitä jakokohtia oli vain tavujen välissä ja silloin puhuttiin luokista A (ensimmäisen tavun jälkeen), B (toisen tavun jälkeen) ja C (kolmannen tavun jälkeen). Näiden perusluokkien lisäksi koko osoiteavaruuden lopusta on varattu osoitteita monilähetykseen (luokka D) ja tulevaan käyttöön (luokka E). Näihin käyttöihin varattuja osoitteita ovat IP-osoite 224.0.0.0 ja sitä suuremmat arvot. Käy katsomassa luokkakohtaiset IP-osoitteet wikipedian sivulta [IP-osoite](https://fi.wikipedia.org/wiki/IP-osoite).

Luokkajaon lisäksi sovittiin, että kaikki 127-alkuiset osoitteet ovat käytettävissä paikallisena osoitteena yhden verkkolaitteen sisällä. Tämä voidaan merkitä joko 127.0.0.0/255.0.0.0  tai 127.0.0.0./8.  Näistä erityisesti paikallisen koneen oma sisäinen osoite (engl. localhost) 127.0.0.1 tulee vastaan laitteen konfigurointitiedoissa. Huomaa, että tuo kauttaviivan jälkeinen merkintä /255.0.0.0 tai /8 kertoo samalla [aliverkon peitteen](https://fi.wikipedia.org/wiki/Aliverkko). Aliverkon peite kertoo kuinka monta monta bittiä osoitteen alusta on verkon tunnusta ja loput bitit ovat siis laitteiden erotteluun aliverkon sisällä. Verkon tunnistetta kuvastavat bitit ovat peitteessä ykkösiä ja verkon sisäistä vaihtuvaa osaa kuvaavat bitit nollia. Luvussa 255 on 8 bittiä, joten aliverkon peitettä 255.0.0.0. vastaava binäärinen esitys on 11111111 00000000 00000000 00000000. Tämän voi kirjoittaa lyhyemmin /8, jossa siis kerrotaan kuinka monta ykkösbittiä peitteessä on.

IPv4:n osoitteista on myös varattu tietyt alueet yksityisissä verkoissa käytettäviksi. Näillä yksityisverkojen osoitteilla ei saa liikennöidä julkisessa internetissä. Toisaalta ne voi ottaa käyttöön omassa suljetussa verkossa sen tarkemmin kysymättä keneltäkään.
Näistä ehkä eniten käytettyjä ovat  10.0.0.0/8 ja 192.168.0.0/16, koska ne noudattavat näitä vanhoja luokkarajoja. Kolmas yksityisverkon osoitealue 172.16.0.0/12 (tai 172.16.0.0/255.240.0.0)  eli osoitteet 172.16.0.1 – 172.31.255.255 on luokaton, koska siinä verkon peite katkeaa tavun sisällä.

Luokallisesta osoitteiden hallinnoinnista siirryttiin luokattomiin osoiterajoihin, koska näin saatiin joustavammin jaettua verkon osoiteavaruutta useammalle operaattoreille. Tätä kutsutaan termillä [luokaton reititys](https://fi.wikipedia.org/wiki/Luokaton_reititys) (engl. Classless InterDomain Routing, CIDR). CIDR:n mukaisesti operaattorin tunnisteen ja verkkolaitteen tunnisteen raja voidaan sijoittaa mihin kohtaan tahansa 32-bittisessä osoitteessa eikä vain tavurajoille.

Organisaatio saa aina käyttöönsä yhtenäisen osoitealueen. Alueen koon kertoo nimenomaan tuo aliverkon peite. Organisaatio saa edelleen jakaa tämän osoitealueen haluamallaan tavalla pienemmiksi aliverkoiksi. Otetaan esimerkiksi tuo yksityisverkon osoitealue 172.16.0.0/12. Voimme jakaa sen kahteen yhtäsuureen alueeseen 172.16.0.0/13 ja 172.24.0.0./13.  Miten nämä alueet on sitten laskettu? Otetaan tarkasteluun vain tuo toinen tavu, jossa muutoksia tapahtuu. 16 on binäärilukuna 10000, mutta koska meillä on kokonainen tavu, niin tavu on silloin 00010000. Kun teemme kaksi yhtä suurta aluetta, niin toinen alue on binäärilukuna 00010000 ja toinen 00011000 eli niiden ero on ykkösbitiä seuraavassa bitissä. Kun nämä muunnetaan takaisin kymmenjärjestelmän luvuiksi, niin saamme luvut 16 ja 24. Samalla myös aliverkon peitteen koko kasvoi yhdellä, koska siirsimme yhden bitin lisää verkkoja erottavaan osioon.  Jos haluamme jakaa sen kahdeksaan yhtä suureen alueeseen, niin silloin niiden osoitelueet ovat 172.16.0.0/15, 172.18.0.0./15, 172.20.0.0/15, ... 172.30.0.0/15. Tee tuo äskeisen kaltainen bittimuunnos itsenäisesti ja varmistu näin, että ymmärrät miten nuo verkkonumerot ja peitteet toimivat.

<quiz id="b51a8df2-9037-4de6-a12c-ef66d593d50c"></quiz>


## IPv6

[IPv6](https://fi.wikipedia.org/wiki/IPv6) osoitteet ovat tällä hetkellä käytössä Internetissä rinnan IPv4 osoitteiden kanssa. Valitettavasti nämä kaksi versiota eivät ole yhteensopivia, kuten seuraavassa aliluvussa näemme.

IPv6 osoitteet ovat 128-bittisiä eli huomattavan pitkiä verrattuna IPv4:n 32-bittisiin osoitteisiin. Tämän seurauksena osoitteita on käytettävissä yli 340 sekstiljoonaa.

IPv6:n osoitteet esitetään kahdeksana hexadesimaaliryhmänä, joissa kukin 4-merkkinen hexadesimaaliluku kuvaa 16 bitin mittaista osiota osoitteesta. Muistathan, että hexadesimaalilukujen kantaluku on 16, joten yhdellä hexadesimaaliluvulla voi kuvata 4-bittisen luvun. Nämä 4-merkkiset hexadesinaaliluvut erotetaan toisistaan kaksoispisteellä. Esimerkki osoitteesta 2001:0DB8:AC10:FE01:0000:0000:0000:0000.  Osoitetta kirjoitettaesssa alkunollat voi jättää pois ja nolla-alueen voi jättää tyhjäksi. Kaikki 8 osiota on kuitenkin tunnistettava, joten kaksoispisteitä ei saa jättää pois. Äskeinen osoite mahdollisimman tiiviisti kirjoitettuna on 2001:DB8:AC10:Fe01::::.

<a title="Ipv6_address.svg: Indeterminate
derivative work: BobbyPeru / Public domain" href="https://commons.wikimedia.org/wiki/File:Ipv6_address_leading_zeros.svg"><img width="512" alt="Ipv6 address leading zeros" src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/70/Ipv6_address_leading_zeros.svg/512px-Ipv6_address_leading_zeros.svg.png"></a>

KUVA: Kuva osoitteen purkamisesta (Lähde: wikimedia)

Koska IPv6:n osoiteavaruus valtava, on erikseen sovittu, että yksittäistä osoitetta operaattorilta pyytävä reititin saa tyypillisesti oman aliverkon, jonka peite on 64 bittiä. Esimerkiksi juuri edellä kuvatun osoitteen. Tähän aliverkkoon liittyvä laite puolestaan saa reitittimeltä aliverkon tunnisteen ja aliverkon peitteen. Osoitteen loput bitit (tyyppillisesti siis jälkimmäiset 64 bittiä) se voi määritellä itse. Automaattisessa konfiguroinnissa voidaan käyttää vaikkapa laitteen MAC-osoitetta apuna. MAC-osoitteen tavoitehan on yksilöidä laite linkkikerroksen tasolla. MAC-osoitteen pituus on 48 bittiä, joten se mahtuu vallan hyvin laitteen aliverkossa yksilöivään 64:ään bittiin. Itseasiassa osoitteen automaattiseen konfigurointiin on määritelty menetelmä, jolla MAC-osoitteen voi muuntaa IPv6 osoitteen osaksi laitteen (tai oikeammin sen verkkoyhteyden) tunnisteeksi.

Näiden isojen aliverkkojen tavoitteena on helpottaa iPv6-osoitteiden reititystä ja pitää reititystaulut kooltaan siedettävinä.

Siirtymä IPv6:n käyttöön on vahvasti käynnissä. Esimerkiksi googlen tilastojen mukaan maailmanlaajuisesti jo noin neljännes sen sivuille tulevista yhteyksistä käyttää IPv6:ta. IPv4-osoitteet on kaikki jaettu ja jos operaattorilta loppuvat osoitteet, se joutuu ostamaan niitä lisää joltain muulta. Tämä aiheuttaa näille operaattoreille paineita siirtyä käyttämään IPv6:tta, koska siellä on runsaasti osoitteita. Jos tilastotieto IPv6:den yleisyydestä kiinnostaa, niin verkkosivulta https://www.internetsociety.org/deploy360/ipv6/statistics/ löytyy linkkejä erilaisiin tilastoihin.


## Vastaanottajien määrä? - Erilaiset kommunikointitavat

Tällä kurssilla olemme keskittyneet etupäässä viestien siirtoon yhden lähettäjän ja yhden vastaanottajan välillä. Tämän [täsmälähetyksen](https://fi.wikipedia.org/wiki/T%C3%A4sm%C3%A4l%C3%A4hetys) (engl. unicast) lisäksi käytettävissä on myös [yleislähetys](https://fi.wikipedia.org/wiki/Yleisl%C3%A4hetys) (engl. broadcast) ja [ryhmälähetys](https://fi.wikipedia.org/wiki/Ryhm%C3%A4l%C3%A4hetys) (engl. multicast). Nämä kolme viestien lähetystapaa ovat käytössä IPv4:ssä. IPv6:ssa tarjolle tulee monilähetyksen erikoistapaus [jokulähetys](https://fi.wikipedia.org/wiki/Jokul%C3%A4hetys) (engl. anycast) ja poistuu mahdollisuus yleislähetykseen kaikille saman verkon laitteille.

Täsmälähetyksessä lähettäjä lähettää viestin täsmälleen yhdelle vastaanottajalle, joka tunnistetaan vastaanottajan IP-osoitteella. Tämä on yleisin tapa viestiä internetissä laitteiden välillä.

Yleislähetyksessä lähettäjä lähettää viestin kaikille laitteille, jotka voivat teknisesti kuulla sen lähettämät viestit. Tämä kuormittaa verkon toimintaa merkittävästi ja siksi on määritelty, että yleislähetykset ovat sallittuja vain saman aliverkon sisällä. IPv4:ssä on yksi täysin geneerinen yleislähetysosoite 255.255.255.255, jota mikään reititin ei välitä eteenpäin.  Jos samaan aliverkkoon kuuluvia osia on reitittimen eri puolilla ja yleislähetyksen on tarkoitus tavoittaa kaikki kyseisen aliverkon laitteet, niin pitää käyttää kyseisen aliverkon omaa yleislähetysosoitetta, jossa alkuosa on aliverkon tunniste ja loppuosa on pelkkiä ykkösbittejä. Wikipedian sivulla [yleislähetys](https://fi.wikipedia.org/wiki/Yleisl%C3%A4hetys) on yksi esimerkki tästä, käy lukemassa se.

Ryhmälähetystä käytetään silloin, kun lähettäjä haluaa lähettää vain yhden viestin, mutta toivoo sen menevän perille useammalle vastaanottajalle. Tyypillinen ryhmälähetystä käyttävä internetpalvelu on IPTV. Ei ole järkevää, että lähettäjä lähettäisi saman viestin erikseen jokaiselle vastaanottajalle. Se kuormittaisi sekä lähettäjää että verkko tarpeettomasti, kun kuitenkin viestin sisältö on täysin identtinen kaikille vastaanottajille. IPv4:ssä osoitteet 224.0.0.0 – 239.255.255.255 (eli luokka D) on varattu näille ryhmälähetyksille. IPv6:ssa puolestaan ryhmälähetys on otettu huomioon jo protokollan suunnitteluvaiheessa siten, että siinä on tuki useammille erilaisille ryhmille.  IPv4:ssä D-luokan osoitteita voi käyttää ryhmälähetyksissä vain saman aliverkon sisällä. Tällöin käytetään yleensä osoitetta 224.0.0.1. IPv6:ssa on varattu osoite ff02::1::::: tätä vastaavaan käyttöön.

Jokulähetys on tavallaan ryhmälähetyksen tai yleislähetyksen erikoistapaus. Siinä mahdollisia viestin vastaanottajia on useita, mutta yksi viesti päätyy kuitenkin vain yhdelle vastaanottajalle. Lähettäjä ei lähettäessään välitä mille ryhmän jäsenelle viesti päätyy, jokainen niistä osaa asian käsitellä. Tämän tyyppinen viestinlähetys sopii sellaiseen tilanteeseen, jossa palvelin on kuormituksen vuoksi monistettu ja kaikki kopiot ovat toiminnassa. Internetin nimipalvelu on hyvä esimerkki tämän kaltaisesta tilanteesta. Lähettäjä haluaa vastauksen nimipalvelukysymykseensä, mutta sitä ei kiinnosta, mikä auktorisoiduista nimipalvelijoista voisi siihen vastata. WWW-palvelu on toinen hyvä esimerkki. Isoilla toimijoilla on palvelimia eri puolilla internetiä ja käyttäjälle riittää, että joku niistä vastaa kyselyyn, mutta käyttäjälle ei ole väliä mistä vastaus tarkemmin ottaen tulee.

<quiz id="a53ea914-8396-4db0-87eb-da700b8d26de"> </quiz>



---
path: '/osa-4/2-IP-protokolla'
title: 'IP-protokolla'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata IP-protokollan toimintaperiaatteet ja sanomarakenteen.
- Osaa kertoa miten reititystaulua käytetään viestien edelleenlähetyksessä.

</text-box>

## IP

[IP-protokollan]( https://fi.wikipedia.org/wiki/IP) keskeinen tehtävä on huolehtia viesti lähettäjältä vastaanottajalle siten, että viesti liikuu verkossa aina yhden linkkivälin kerrallaan ja verkkokerroksen tasolla päätetään mihin linkkiin viesti seuraavaksi lähetetään. Oikeastaan IP ei ole vain yksi protokolla vaan oikeammin protokollaperhe, jonka eri protokollilla on omat tehtävänsä.
IP:n toimintaan liittyy keskeisenä elementtinä osoitteet, viestin rakenne ja viestin kuljettaminen eli reititys.  Osoitteet olemme jo käsitelleet aiemmin, joten käydään seuraavaksi läpi viestin rakenne


IP-prokollan mukaista viestiä kutsutaan IP-paketiksi (engl. packet). IP-paketin kuvan voit katsoa wikipediasta IP sivulta kohdasta [IPv4-paketti](https://fi.wikipedia.org/wiki/IP#IPv4-paketti)

IPv4:n mukaisen paketin kentät ovat seuraavat:
* **Ensimmäinen sana**  eli ensimmäiset 32 bittiä
* bitit 0-3: versionumero, joka IPv4:n tapauksessa on 4 ja bitteinä siis 0100
* bitit 4-7: otsakkeet pituus. Minimikokoinen otsake on kooltaan 5 32-bittistä sanaa, joten yleensä arvon on 5. Arvo voi olla enemmän, jos otsakkeen optiokentät ovat käytössä
* bitit 8-15: palveluluokka. Tämän tarkempi käsittely jää myöhemmille kursseille.
* bitit 16-31: paketin pituus tavuina. Tämä on siis paketin kokonaispituus sisältäen sekä otsakkeen että datan. Huomaa, että otsakkeen koko ilmoitettiin edellä sanoina, mutta tässä paketin koko on tavuina.
* **Toinen sana**  eli seuraavat 32 bittiä  eli bitit 32-63
* Tässä on paketin fragmentointiin eli pilkkomiseen ja kokoamiseen liittyvät kentät, fragmentin tunniste, lipukkeita ja fragmentin sijainti alkuperäisessä viestissä
* **Kolmas sana** eli bitit 64-95
* sanan ensimmäinen tavu: paketin elinaika, hyppylaskuri, eli kuinka monta edelleenlähetystä paketille saa korkeintaan tehdä. Reititin vähentää tätä aina yhdellä.
* sanan toinen tavu: Protokollan numero. Mille protokollalle data välitetään. Tyypillisiä arvoja ovat 6-TCP ja 17-UDP.
* sanan kolmas ja neljäs tavu: Tarkistussumma. Otsakkeen tarkistussumma, jotta sen oikeellisuus voidaan tarkistaa.
* **Neljäs sana** eli bitit 96-127
* Lähettäjän IPv4 osoite
* **Viides sana** eli bitit 128-159
* Vastaanottajan IPv4 osoite
* **Mahdolliset optiot** Näiden pitää olla myös kokonaisia 32-bittisiä sanoja. Yleensä näitä ei käytetä, joten data alkaa heti 5. sanan jälkeen

Otsakkeen lisäksi paketissa on sitten varsinainen data. Vastaanottajalla verkkokerros antaa tämän datan otsakkeen mukaiselle protokollalle, joka yleensä on kuljetuskerroksen protokolla. Joissakin tilanteissa kyseessä voi myös olla jokin verkkokerroksen omista protokollista.

IPv4:ssä on määritelty, että yhden lähetetyn paketin voi matkalla pilkkoa useammaksi eri paketiksi, eli alkuperäisen paketin paloiksi, joita kutsutaan fragmenteiksi. Kun paketti on pilkottu fragmenteiksi, nämä fragmentit kulkevat verkossa kuten mikä tahansa IP-paketti aina vastaanottajalle asti. Vasta vastaanottaja yhdistää fragmentit alkuperäiseksi paketiksi. Kun se on saanut alkuperäisen paketin kokonaisuudessaan, voi se antaa data-osion eteenpäin.

Fragmentointi edellyttää reitittimiltä lisätoiminnallisuutta ja hidastaa pakettien uudelleenlähetystä, kun niitä pitää muokata. Toisaalta fragmentointi on välttämätöntä, jos IP-paketti on suurempi kuin mitä linkkikerros pystyy kuljettamaan yhdessä kehyksessä. Mikäli pakettia ei voisi pilkkoa, sitä ei voisi lähettää eteenpäin, joten viestijöiden näkökulmasta se vain katoaisi matkalla.

IPv6:ssa suunnittelun lähtökohtana on ollut pakettien uudelleenlähetyksen mahdollisimman sujuva toiminta ja siksi siitä on jätetty kokonaan pois mahdollisuus pakettien fragmentointiin. Siinä on lähettäjälle tarjolla protokolla, jolla lähettäjä voi tarkistaa mikä on maksimipaketin koko reitillä lähettäjältä vastaanottajalle. IPv6:ssa reititin vain pudottaa liian suuren paketin, jota se ei voi lähettää eteenpäin. Se lähettää tällaisesta tilanteesta kontrolliprotokollan (Internet Control Message Protocol v6, ICMPv6) mukaisen viestin paketin alkuperäiselle lähettäjälle. Näin lähettäjä saa tiedon paketin maksimikoosta ja voi jatkossa huolehtia siitä, että lähetettävät paketit ovat tätä pienempiä.

[IPv6](https://fi.wikipedia.org/wiki/IPv6) pakettien otsakkeita on myös virtaviivaistettu. Otsake on kiinteänkokoinen (320 bittiä) eikä sisällä tarkistussummaa. Otsakkeen neljä ensimmäistä bittiä ovat versionumero kuten IPv4:ssä. Tämä on välttämätöntä, jotta pakettia käsittelevä solmu voi tunnistaa kumman protokollan mukainen viesti on kyseessä. IPv6:ssa näiden bittien arvo on siis 6 eli binäärilukuna 0110. Koska tämä kiinteä otsake ei aina riitä, IPv6 sallii, että datan alussa voi olla lisäotsakkeita, joiden tunnistamiseen on kiinteä kenttä. Tämä 'seuraava otsake' kenttä kertoo siis minkä protokollan mukainen otsake on datakentän alussa. Tässä käytetään samoja protokollanumeroita kuin IPv4:n kentässä 'protokolla numero'. Näin IPv6:n otsake saadaan pidettyä selkeänä ja yksinkertaisena reitittimien kannalta. Reitittimien ei tarvitse välittää näistä data-alueen tiedoista.


## Paketin kuljetus verkossa

Internetin toiminnalle keskeistä on, että verkkokerros osaa kuljettaa IP-paketin lähettäjältä vastaanottajalle. Verkkokerroksella pitää siis olla riittävästi toiminnallisuutta, jotta paketti voi edetä etappikerrallaan kohti vastaanottajaa ja lopulta päästä perille. Tätä verkon toiminnallisuutta kutsutaan reititykseksi. Paketti siis reititetään lähettäjältä vastaanottajalle. Tarkastellaan reitittimien yksityiskohtaisempaa toimintaa seuraavassa aliluvussa.  Koska internetissä ei normaalisti varata reittejä etukäteen, on reitittimillä oltava riittävä tieto verkon rakenteesta, jotta ne osaavat lähettää paketin eteenpäin oikeaan suuntaan. Tätä tietoa säilytetään reititystauluissa. Käymme tällä kurssilla läpi vain IPv4:n mukaiset reititystaulut.

Toisaalta verkossa liikkuu sekä IPv4:n että IPv6:n mukaisia paketteja. Jos reititin osaa käsitellä niitä molempia, niin silloin sille voi lähettää paketteja välitettäväksi kummalla tahansa versiolla. Jos reititin ei osaa käsitellä kuin IPv4:n mukaisia paketteja, niin sille ei kannata lähettää IPv6:n mukaisia paketteja, koska se vain pudottaa ne pois verkosta. Mikäli paketti pitää välittää verkossa tällaisten reitittimien kautta joudutaan tunneloimaan (engl. tunneling) eli rakentamaan tunneli, jossa toisen protokollan viesti kulkee toisen protokollan sisällä. Tällainen tunneli muodostetaan siis kahden sellaisen reitittimen välille, jotka hallitsevat kummankin protokollaversion. Tämä tehdään "piilottamalla" tuntematon protokollaversio tunnetun protokollan sisään.


### IPv4 Reititystaulu

Kun reititin saa linkistä paketin, niin sen täytyy päättää mihin linkkiin paketti lähetetään seuraavaksi. Tavoitteena reitittimellä on siis lähettää paketti edelleen sellaiseen linkkiin, jonka kautta se voi päästä vastaanottajalle. Päätös linkin valinnasta perustuu reititystaulun sen hetkiseen sisältöön.  Reitittimien lisäksi myös solmuilla (eli käyttäjien tietokoneilla, palvelimilla, yms.) on reititystaulu, jonka perusteella se tekee päätöksiä viestien lähettämisestä. Englanninkielisen wikipedian sivulla [Routing table](https://en.wikipedia.org/wiki/Routing_table) on esimerkki kotiverkkoon liitetyn tietokoneen reititystaulusta:

| Network Destination |	Netmask |	Gateway |	Interface |	Metric |
| ------------------- | --------------- | ------------- | -------------  | ------ |
| 0.0.0.0	| 0.0.0.0	    | 192.168.0.1	| 192.168.0.100 |	10 |
| 127.0.0.0 |	255.0.0.0	| 127.0.0.1	| 127.0.0.1	| 1 |
| 192.168.0.0 |	255.255.255.0 |	192.168.0.100 |	192.168.0.100 |	10 |
| 192.168.0.100	| 255.255.255.255 |	127.0.0.1	| 127.0.0.1	| 10 |
| 192.168.0.1 |	255.255.255.255 |	192.168.0.100	| 192.168.0.100 |	10 |

Tässä reititystaulussa on useita kenttiä. Ensimmäisenä on kohdeverkko (network destination) ja siihen liittyvä verkonpeite (netmask). Näillä yhdessä voidaan tunnistaa IP-paketin vastaanottajan osoitteen perusteella verkko, johon paketti pitää tältä laitteelta toimittaa. Huomaa, että kyseinen verkko ei välttämättä ole vastaanottajan oma verkko, vaan lähinnä suunta, johon tältä laitteelta tuohon osoitteeseen menevät viestit pitää lähettää. Yhdyskäytävä (gateway) kertoo siis "laitteen", jonka kautta kyseisen verkon voi saavuttaa. Rajapinta (interface) auttaa tunnistamaan paikallisen linkin, verkkokortin tai muun paikallinen rajapinnnan, jonka kautta liikenne yhdyskäytävälle kulkee. Viimeinen kenttä kustannus (metric) auttaa valitsemaan useammasta mahdollisesti vaihtoehdosta kustannusten kannalta parhaimman.

Koska tämä reititystaulu on kotiverkon laitteesta, niin siinä näkyy laitteen oma paikallinen, laitteen sisäinen osoite, 127.0.0.1 sekä laitteen oma IP-numero 192.168.0.100, jolla tunnistetaan laitteen oma verkkokortti. Lisäksi tästä reititystaulusta löytyy oletusyhdyskäytävän osoite 192.169.0.1, joka on kotiverkon NAT-reitittimen osoite.

Kuten huomaat, niin tässä reititystaulussa on varsin paljon rivejä. Jos voisimme katsoa internetin syövereissä olevan reitittimen reititystaulua, niin siinä näitä rivejä olisi paljon enemmän.

Käytämme seuraavissa tehtävissä yksinkertaisempaa reititystaulua, jossa kohdeverkko ja verkonpeite on yhdistetty, rajapinta on jätetty kokonaan pois ja yhdyskäytävä on saatettu korvata vain linkin numerolla. Joskus kustannuskin voi puuttua. Yllä oleva reititystaulu tällä tavalla yksinkertaistettuna voisi olla

| Osoite        |	linkki / (yhdyskäytävä/rajapinta) |
| ---------------- | --------------------- |
| x.x.x.x	(default)|  1 (192.168.0.1)	|
| 127.0.0.0/8 | 0 (127.0.0.1)	|
| 192.168.0.0/24 | 1  (samassa verkossa) |

Nyt 'x':llä merkityt osat osoitteesta ovat aliverkon sisäisiä laitenumeroita ja vain numerot kertovat reitityksen kannalta merkityksellistä tietoa osoitteesta. Koska käytämme luokatonta reititystä, niin reititin etsii reititystaulusta sen rivin, jonka osoitekentässä on pisin yhteinen alkuosa etsittävän osoitteen kanssa. Näin kaikki osoitteet, jotka eivät ala 127 tai 191.168.0 ohjataan reitittimelle ja viestit, jotka ovat omaan aliverkkoon 192.168.0.x kuuluvia, lähetetään vain aliverkkoon. Koneen sisäisiä viestejä 127 ei edes lähetetä verkkoon, vaan ne käsitellään koneen sisällä.

Joskus reititystaulusta (engl. router table) saatetaan käyttää englanniksi nimitystä forwarding table, ja joskus tuo uudelleenlähetystaulu on isommasta kaikki mahdolliset reitit kattavasta reititystaulusta poimittu osa, joka kattaa uudelleenlähetyksessä tarvittavien aktiivisten reittien tiedot. Suomeksi näistä molemmista käytetään yleensä  nimeä reititystaulu.

Seuraavassa tehtävässä tarvitset tätä reititystaulua:

| Osoite/peite  |	linkki |
| ---------------- | -------- |
| 140.24.7.0/26 |  m0 |
| 140.24.7.64/26 | m1 |
| 140.24.7.128/26 | m2 |
| 140.24.7.192/26 | m3 |
| 0.0.0.0./0 | m4 |

<quiz id="b2325dad-8de7-43fd-aed5-eb8f16a85487"></quiz>

Koska osoitteiden tulkinnan periaatteena on tuo pisin yhteinen alkuosa, on mahdollista yhdistellä reitittimen rivejä, jos ne kattavat yhdessä koko osoiteavaruuden. Esimerkiksi äskeisessä tehtävässä olleen reititystaulun osoitteet kaikki yhdessä voidaan kattaa osoitteella 140.24.7.0/24, joka voisi siis olla tälle reitittimelle liikennettä ohjaavan reitittimen reititystaulussa.

Luokaton reititys ja pisimmän yhteisen alkuosan käyttäminen antaa myös mahdollisuuden järjestellä verkon arkkitehtuuria uudelleen ilman, että laitteiden julkisia IP-osoitteita tarvitsee vaihtaa.  Edellä joku noista aliverkoista (vaikkapa 140.24.7.128/26) voitaisiin siirtää tästä reitittimestä jollekin muulle reitittimelle, vaikkapa tätä reititintä edeltävälle reitittimelle, jolloin sen reititystaulussa olisikin molemmat osoitealueet 140.24.7.0./24 ja 140.24.7.128/26, vaikka ne ovat päällekkäisiä. Se osaisi kuitenkin päätellä, että laitteelle 140.24.7.165 lähetetty viesti kuuluu lähettää tuon pienemmän osoitealueen 140.24.7.128/26 suuntaan eikä tuohon 140.24.7.0/24 suuntaan, koska sillä on  pidempi yhteinen alkuosa pienemmän verkon osoitteiden kanssa.  Suosittelen, että muunnat kaikki kolme osoitetta biteiksi ja lasket alkuosan yhteensopivien bittien lukumäärät ja näin varmistut siitä, että reititin oikeasti osaa tuon päätöksen tehdä näiden periaatteiden mukaan.

<quiz id="a1421fd0-806a-42c2-bc75-d52afe982742"></quiz>

Edellä jo tarkasteltiinkin osoiteavaruuden 140.24.7.0/24 jakamista neljään yhtä suureen osaan, joilla kullakin on 26 bittinen aliverkon peite, eli aliverkot eroavat toisistaan kahden bitin verran (bitit 24 ja 25, kun bitit numeroidaan alkaen nollasta). Olisimme ihan yhtä hyvin voineen jakaa osoiteavaruuden eri suuruisiin osiin esimerkiksi 140.24.7.0/25, 140.24.7.128/26 ja 140.24.7.192/26  tai 140.24.7.0/26, 140.24.7.62/26 ja 140.24.7.128/25. Nyt yksi alue kattaa puolet osoiteavaruudesta. Tarkasta binäärilukujen avulla, miksi emme voi yhdistää kahta keskimmäistä aluetta yhdeksi, vaan isomman yhtenäisen alueen pitää olla joko numeroavaruuden alussa tai lopussa.

<quiz id="a999dbaf-870e-4eb9-a8eb-e0323aa72347"></quiz>



### Tunnelointi

Voi halutessasi lukea tunneloinnista lyhyen kuvauksen englanninkielisen wikipedian sivulta [IP Tunnel](https://en.wikipedia.org/wiki/IP_tunnel)

Piirrä aluksi itsellesi kuva, jossa verkon reunoilla olevilla solmuilla A ja Z on IPv6:n mukaiset IP-osoitteet ja ne haluavat kommunikoida keskenään. Ne ovat siis eri aliverkoissa ja eri reunoissa piirrosta. Niiden aliverkot on yhdistetty internetiin reitittimillä (B ja Y), jotka osaavat aliverkon edellyttämää IPv6:sta ja internetin suuntaan ne osaavat myös IPv4:sta, koska reitittimet (C ja X), joiden kautta niiden viestit siirtyvät internetiin on vielä sen verran vanha, että se osaa vain IPv4:ää. Reitti C:n ja X:n välillä on olemassa, mutta sen yksityiskohdat eivät ole tiedossa.

Kuvassa on siis kuusi solmua A, B, C, X, Y ja Z, jotka on yhdistetty toisiinsa siten, että viestit A:lta voivat päätyä Z:lle ja päinvastoin.

Nyt A lähettää IPv6-paketin Z:lle. Tässä paketissa viestin lähettäjä on A ja vastaanottaja on Z. Koska reitti kulkee B:n kautta, niin tämä paketti ohjataan ensin B:lle. Reititin B ei voi suoraan lähettää viestiä eteenpäin, koska A:n lähettämä viesti on IPv6:n mukainen ja C osaa käsitellä vain IPv4:n mukaisia viestejä. Siksi "muodostetaan tunneli" B:n ja Y:n välille siten, että B laittaa IPv6:n  mukaisen paketin IPv4-paketin sisään dataksi. Tällä IPv4-paketilla lähettäjänä on B ja vastaanottajana Y. Nyt B:n ja Y:n välillä kulkee IPv4:n mukainen paketti, jonka C, X ja muut niiden välillä olevat reitittimet osaavat käsitellä ja ohjata oikeaan suuntaan.

Kun IPv4-paketti saapuu Y:lle, joka siis on kyseisen paketin vastaanottaja, niin Y havaitsee, että paketissa on sisällä IPv6-paketti. Y purkaa tuon IPv4 kuoren pois ja lähettää paljastuvan IPv6-paketin sen vastaanottajalle eli Z:lle.

Yllä on kuvattu niin sanottu [IP-in-IP](https://en.wikipedia.org/wiki/IP_in_IP) tunnelointi. Jo edeltävällä kurssilla käsittelimme virtuaalista yksityisverkkoa VPN:ää, jonka toiminta perustuu tunnelointiin. VPN:ssä tunnelissa voidaan kuljettaa useita eri protokollia, kun yllä kuvattu esimerkki IPv6:n lähettämisestä IPv4-paketissa koski vain yhtä protokollaa.

Yleensä tunneli toteutetaan käyttäen salaavaa [IPSec](https://fi.wikipedia.org/wiki/IPsec)-protokollaa, jolloin tunnelissa kulkeva tieto on salattua ja vain tunnelin muodostava kuori on salaamatonta. Se on tyypillisin protokolla myös VPN:n toteutuksessa. Joissakin suosituksissa korostetaan, että tunnelit pitäisi aina tehdä käyttäen salaavaa protokollaa, jolloin viestinnän turvallisuutta saadaan parannettua.

<quiz id="b425e36b-8f75-408b-94e9-ee2368bbc257"></quiz>


---
path: '/osa-4/3-reititys'
title: 'Reititys'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- osaat kuvata reitityksen periaatteellisella tasolla
- osaat muutaman keskeisen reititysalgoritmin ja osaat laatia tarvittavat reititystaulut näitä algoritmeja käyttäen

</text-box>



##  Reititys ja reititysalgoritmit

Reitittimet käyttävät reititystauluja pakettien edelleenlähetykseen. Jotta reititystaulut pysyvät hyödyllisinä verkon arkkitehtuurin muuttuessa niitä pitää päivittää. Reitittimen oman reititystaulun päivittäminen on reitittimen vastuulla.  Koko verkon reittien suunnittelu eli reititys voidaan tehdä keskitetysti, jolloin reititin saa valmiin reititystaulun, jonka sen sitten ottaa käyttöön. Tällainen keskitetty reittien laskenta sopii erityisesti staattiseen reititykseen, jolloin reititys päätetään ennalta ja se ei sitten enää muutu. Toki sitä voidaan käyttää dynaamisemmin, jolloin keskitetysti lasketaan aika ajoin uudet reitit ja päivitetään ne reitittimille. Reititin käyttää sitten näitä reittejä, kunnes ne joskus päivitetään sille uudelleen. Reitittimen näkökulmasta tämä on hyvin staattista reititystä, koska se vain noudattaa saamansa reititystaulua eikä tee siihen muutoksia. Nykyisessä internetissä kaikkien reittien laskeminen keskitetysti veisi aivan liian paljon aikaa, jolloin reittimuutokset tapahtuisivat todella hitaasti. Nopeampi reititystaulujen päivitys onnistuu vain hajautetuilla ja dynaamisilla reititysalgoritmeilla. Nämä algoritmit ovat hajautettuja, koska kaikki saman verkon reitittimet suorittavat kyseistä algoritmia ja vaihtavat tietoa (eli reititystauluja) toistensa kanssa. Ne ovat dynaamisia, koska reitittimet itse päivittävät oman reititystaulunsa.

Reititys voidaan suunnitella myös hierarkkisesti, siten että aliverkkojen (eli autonomisten alueiden) välinen reititys ja aliverkkojen sisäinen reititys tehdään erikseen. Niihin voidaan käyttää jopa eri menetelmiä. Koska koko internetin tasolla aliverkot ovat itsenäisiä autonomisia, niin aliverkojen oma, sisäinen reititys on täysin aliverkon oma asia. Se voidaan tehdä millä tahansa aliverkolle sopivalla tavalla. Internetissä tyypilliset verkon sisäiset reititysprotokollat ovat [Routing Information Protocol](https://fi.wikipedia.org/wiki/Routing_Information_Protocol) (RIP) ja [Open Shortest Path First](https://fi.wikipedia.org/wiki/OSPF) (OSPF). Sen sijaan aliverkkojen välinen reititys, jolla siis huolehditaan viestin kulkeminen eri verkkojen kautta vastaanottajalle, tehdään  samalla tavalla kaikkialla. Internetissä tähän käytetään [Boarder Gateway Protocol](https://fi.wikipedia.org/wiki/BGP) (BGP) -protokollaa.

Jätämme nuo internetin varsinaiset reititysalgoritmit niiden monimutkaisten yksityiskohtien vuoksi myöhemmille kursseilla. Tutustutaan nyt kahteen perusreititysalgoritmiin, jotka ovat useimpien algoritmien taustalla joko sellaisenaan tai muokattuna. Nämä kaksi reititysalgoritmia eroavat toisistaan erityisesti siinä, miten kattavan tiedon verkosta ja linkkien kustannuksista eli solmujen etäisyyksistä ne tarvitsevat.  Linkkitila-algoritmi (engl. link state algorithm)  tarvitsee täydellisen tiedon verkon rakenteesta, kun taas etäisyysvektorialgoritmille (engl. distance vector algorithm) riittää epätäydellinen kuva verkosta.

Verkkoja ja verkkoalgoritmeja käsitellään laajemmin tietorakenteet ja algoritmit -kurssilla.

Algoritmien näkökulmasta verkko on sellainen tietorakenne, joka sisältää solmuja ja niiden välisiä yhteyksiä eli linkkejä. Tämä voidaan merkitä G=(N,E), missä G on verkko eli graafi, N on solmujen (engl. node) joukko ja E on linkkien (engl. edge) joukko. Lisäksi merkitään, että c(x,y) on solmujen x ja y välisen linkin kustannus (engl. cost). Linkin kustannus voi olla sen nopeus, kaistanleveys, ruuhkaisuus, rahallinen hinta linkin käytöstä, tai jotain muuta, jolla on numeerinen arvo. Näissä esimerkeissä linkin kustannus on siirron kesto tai hinta kyseisen linkin kautta.

Reititysalgoritmin tavoitteena on siis löytää nopeimmat tai halvimmat reitit solmujen välille. Reitti voi kulkea muiden solmujen kautta, kunhan se kokonaiskustannus on mahdollisista reiteistä pienin.

Käydään näiden algoritmien toiminta läpi esimerkin avulla.

<img src="../img/reititysverkko1.svg" alt="Kuvassa on seitsemän solmua A-G. Nämä solmut muodostavat verkos, jossa on yhteydet ja niiden kustannukset seuraavasti (A-B,3), (A-C,2), (B-D,5), (C-D,2), (C-E,6), (D-F,2), (E-F,4), (E-G,3) ja (F-G,1)." >

KUVA: Kuvassa on esimerkkiverkko, jossa on 7 solmua ja näiden välillä kaikkiaan 9 linkkiä ja niiden kustannukset. Viestit kulkevat linkeissä molempiin suuntiin. Käytämme tätä verkkoa molempien algoritmien esittelyyn.


## Linkkitila-algoritmi

Linkkitila-algoritmi käyttää virittävää puuta reititystaulun muodostamisessa. [Virittävä puu](https://fi.wikipedia.org/wiki/Viritt%C3%A4v%C3%A4_puu) (engl. spanning tree) muodostaan kaikkien verkon solmujen välille yhteydet, siten että siinä ei enää ole syklejä. Tällaisia puita on useita, mutta reititystä varten pyritään löytämään minimikustannukset antava puu. Tähän minimikustannukset kuvaavaan puuhun valitut linkit muodostavat sitten reitityksessä käytettävät reitit solmujen välillä.
[Dijkstran algoritmi](https://fi.wikipedia.org/wiki/Dijkstran_algoritmi) tekee juuri tällaisen puun. Algoritmi ja sen toiminta on kuvattu tuossa wikipedian artikkelissa. Internetin reititysprotokollista OSPF käyttää Dijkstran algoritmia.

Käydään tässä läpi algoritmin toiminta äskeisessä kuvassa olleen esimerkkiverkon kanssa, kun puun juureksi valitaan solmu A:
* juuri s= A; S=tyhjä; Q={A,B,C,D,E,F,G}; d[A]=0; d[muut] voivat olla tässä vaiheessa äärettömiä
* Kierros yksi: u= A; Q={B,C,D.E,F,G} (koska sen etäisyys itseensä on 0 eli lyhin kaikista etäisyyksistä)
* S={A};  d[B]=3; d[C]=2; previous[B]=A; previous[C]=A
* Kierros kaksi: u=C; Q={B,D,E,F,G} {Eli seuraava tarkasteltava on C, koska siihen lyhin etäisyys}
* S={A,C}; d[D]=2+2=4; d[E]=2+6=8; previous[D]=C; previous[E]=C
* Kierros kolme: u=B; Q={D,E,F,G} {koska d[B]=3 on pienempi kuin D[D]=4 tai muut etäisyydet}
* S={A,C,B}; (d[D] pysyy arvossa 4, koska 4 < 3+5)
* Kierros neljä: u=D; Q={E,F,G}
* S={A,C,B,D}; d[B] pysyy ennallaan; d[F]=4+2=6; pevious[F]=D
* Kierros viisi: u=F; Q={E,G}   (koska d[F]<d[E])
* S={A,B,C,D,F}; d[E] pysyy ennallaan 8 < 10; d[G]=6+1=7, previous[G]=F
* Kierros kuusi: u=G; Q={E} (koska d[G]<d[E], jos yhtäsuuret, niin valitaan jompikumpi ilman tarkempaa sääntöä)
* S={A,B,C,D,F,G}; d[E] pysyy ennallaan
* Kierroksella seitsemän käsitellään viimeinen solmu E, mutta se ei aiheuta muutoksia tauluihin d tai previous
*

Algoritmin jälkeen meillä on etäisyydet d(A)=0; d(B)=3; d(C)=2; d(D)=4, d(E)=8, d(F)=6 sekä d(G)=7 ja previous(B)=A, previous(C)=A; previous(D)=C, previous(E)=C, previous(F)=D ja previous(G)=F. Simuloidessa tuon previous-taulun sijaan voin myös merkitä verkkopiirrokseen vastaavan linkin (kuten wikipedian kuvassa on tehty) Näistä voidaan sitten laatia reititystaulu A:lle

| kohde  | A lähettää solmun x suuntaan | kustannus |
|--------|----------------------| ----------|
| B  |  B  | 3 |
| C  |  C  | 2 |
| D  | C   | 4 |
| E  | C | 8 |
| F | C | 6 |
| G | C | 7 |


<quiz id="a68e9dfc-84a2-4634-8287-dc2c25be5fd3"> </quiz>


## Etäisyysvektorialgoritmi

Linkkitila-algoritmit tarvitsevat siis tiedon kaikkien linkkien kustannuksista ennen kuin algoritmia voidaan suorittaa. Niillä pitää siis olla niin sanotusta täydellinen kuva verkosta ennen suoritusta. Etäisyysvektorialgoritmissa käsitys koko verkon linkkien kustannuksista saa olla epätäydellinen. Algoritmia voidaan siis suorittaa samalla kun selvitetään kauempana olevien verkon osien tietoja.

Etäisyysvektorialgoritmien perusajatus on, että jokainen solmu laskee itsenäisesti sen hetkisillä tiedoilla etäisyyksiä kaikkiin sen tietämiin solmuihin. Sitten se vaihtaa tiedot naapuriensa kanssa ja saa näin tietoonsa etäisyyksiä kauempana oleviin solmuihin.

Useimmat etäisyysvektoriin perustuvat reititysprotokollat kuten RIP käyttävät Bellman-Fordin algoritmia etäisyysvektorien laskennassa ja tietojen vaihdossa. Myös autonomisten verkkojen reitityksessä käytettävässä BGP protokollassa on muunnelma Bellman-Fordin algoritmista tai vähintäänkin BGP soveltaa vastaavia periaatteita.

[Bellman-Fordin algoritmissa](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) solmulla on aina oma etäisyysvektori, jossa on tiedot kustannuksista kaikkiin solmuihin. Kun solmu saa naapureiden vektorit, niin se päivittää omaan vektoriinsa kaikki etäisyydet, siten, että d[xy]=min(d[xy], c(xz)+d[zy]). Tällä kaavalla x päivittää oman etäisyytensä solmuun y. Etäisyys pysyy samana d[xy] tai vaihtuu pienemmäksi z:n etäisyys y:hyn d[zy] + x:n ja z:n välisen linkin kustannus x(xz). Tämä laskenta tehdään joka kierroksella jokaisessa solmussa kaikille etäisyyksille. Kun algoritmia on suoritettu korkeintaan solmujen lukumäärän verran, niin jokaisen solmun etäisyysvektoriin on varmasti päivittynyt pienimmät etäisyyden muihin solmuihin.

 Nyt kaikki solmut päivittävät tietojaan joka kierroksella. Ne kaikki ylläpitävät omaa etäisyysvektoria distance=[A,B,C,D,E,F,G], jossa on siis solmun etäisyys kaikkiin muihin solmuihin. Tämän rinnalla niillä on tiedossa se, miltä solmulta tieto ko. etäisyyteen liittyen tuli. Eli previous -vektorissa on tieto solmusta z, jolle tämä solmu x lähettää kaikki solmulle y menevät viestit, koska c(xz)-d[zy] on minimi etäisyys xy, jonka x tietää.

Käydään siis tämän algoritmin toiminta läpi käyttämämme esimerkkiverkon kanssa:
* Kirjaan tähän vain solmun A tilanteen, muut solmut laskevat omia arvojaan vastaavasta joka kierroksella
* Aluksi A:n etäisyysvektori (distance) on [A 0,B 3,C 2,D -,E -,F -,G -] eli A tietää etäisyydet vain naapureihinsa
* Kierros yksi
* Tietojen vaihdossa A lähettää oman vektorinsa B:lle ja C:lle ja
* saa niiden vektorit B:[A 3,B 0,C -, D 5,E -,F -,G -] ja C: [A 2,B -,C 0, D 2,E 6,F -,G -]
* A päivittää oman vektorinsa A:[A 0,B 3,C 2,D 4,E 8,F -,G -], koska D:lle min(-, 3+5, 2+2) =4, joten predecessor[D]=C ja E:lle min 8, predecessor[E]=C
* Kierros kaksi
* A lähettää oman vektorin ja saa B:ltä B:[A 3,B 0,C 5, D 5,E -,F 7,G -] ja C:ltä C:[A 2,B 5,C 0, D 2,E 6,F 4,G 9]
* A päivittää nyt oman vektorinsa A:[A 0,B 3,C 2,D 4,E 8,F 6,G 11], joten  predecessor[E]=C , predecessor[F]=C ja predecessor [G]=C
* Kierros kolme
* A lähettää oman vektorinsa ja saa B:ltä B:[A 3,B 0,C 5, D 5,E 11,F 7,G 8] ja C:ltä C:[A 2,B 5,C 0, D 2,E 6,F 4,G 5]
* A päivittää nyt oman vektorinsa A:[A 0,B 3,C 2,D 4,E 8,F 6,G 7] predecessor[G]=C
* Tämä jälkeen A:n vektorin tieto ei muutu ellei verkon linkkien kustannuksissa tapahdu muutoksia.

Huomaa kuinka A:n tieto reitistä ja ennen kaikkea etäisyydestä G:hen muuttui kierrosten kaksi ja kolme välissä. Tämä johtuu siitä, että tuo kustannuksiltaan lyhyin reitti A:lta G:lle on pidempi, joten se sai ensin tiedon lyhyemmästä reitistä ja vasta myöhemmin pidemmästä, mutta nopeammasta (tai edullisemmasta) reitistä.

Käytännössä, kun laskee käsin näitä reittejä, niin usein on helpointa tehdä kaikista solmuista ja niiden etäisyysvektoreista matriisi

| solmu | A | B | C | D | E | F | G | reitti (predecessor) |
|-------|---|---|---|---|---|---|---|--------|
| A:n vektori | 0 | 3 | 2 | - | - | - | - | B via B ja C via C |
|B:n vektori | 3 |0|-|5|-|-|-| A via A ja D via D |
| C:n vektori | 2 | - | 0 | 2 | 6 | - | - | A via A, D via D ja E via E |
| D:n vektori | - | 5 | 2 | 0 | - | 2 | - | B via B, C via C ja F via F |
| E:n vektori | - | - | 6 | - | 0 | 4 | 3 | C via C, F via F ja G via G |
| F:n vektori | - | - | - | 2 | 4 | 0 | 1 | D via D, E via E ja G via G |
| G:n vektori | - | - | - | - | 3 | 1 | 0 | E via E ja F via F |

Tässä tuntemattomat etäisyydet on merkitty viivalla, mutta yhtä hyvin merkintänä olisi voinut olla ääretön. Vastaavasti solmun etäisyys itseensä on merkitty 0:ksi.

<quiz id="aac1f4a7-87fa-4b62-9f30-e1b9a4357330"> </quiz>

Etäisyysvektorireititys on näppärä, koska reittitiedot etenevät suhteellisen nopeasti verkossa. Etappivälitteisessä verkossa viestit etenevät muutenkin vain linkkivälin kerrallaan. Nyt reititin päivittää oman tietonsa ja sitten lähettää sen eteenpäin. Tällöin aina kierros kierrokselta tieto eteen verkossa ja tunnetut reitit pitenevät. Vastaavasti myös kustannusmuutokset etenevät tällä samalla nopeudella verkon solmujen välillä. Tästä käytetään joskus termiä "hyvät uutiset etenevät nopeasti" vastakohtana sille, että "huonot uutiset etenevät hitaasti".

Tarkastellaan tuota "huonojen uutisten hidasta etenemistä" pienessä esimerkkiverkossa. Tässä verkossa on vain kolme solmua ja ne on kytketty toisiinsa oheisen kuvan mukaisesti.  A:n ja B:n välinen liikenne kulkee C:n kautta, koska A:n ja B:n välisen yhteyden kustannus on suurempi.

<img src="../img/reititysverkko2.svg" alt="Kuvassa on kolme solmua A, B ja C. ne on yhdistetty toisiinsa ja kustannukset/etäisyydet ovat A-B 30, A-C 2 ja B-C 2">


Nyt sitten, jos A:n ja C:n välinen yhteys hidastuu arvoon 20, jonka A huomaa ja toimittaa seuraavassa päivityksessä tiedoksi C:lle ja B:lle. niin etäisyysvektorialgoritmilla menee useita kierroksia ennen kuin tilanne rauhoittuu. Tätä tarkoittaa huonojen uutisten hitaus. Tarkastellaan siis algoritmin toimintaa ja solmujen reitityspäätöksiä eri kierroksilla.  Voit simuloida tätä itsekin ja huomaat kuinka solmut muuttavat etäisyyksien arvioita vain aina kahdella per kierros. Ne olettavat viestin kulkevan aina toista kautta, jossa etäisyys näyttää pienemmältä. Tämä pienin etäisyys kasvaa vain kahdella per kierros.

<img src="../img/huonot-uutiset.svg" alt="Kuvassa on alkuosa etäisyysvektorireitityksen laskutoimituksista.">

KUVA: Kuvan laskutoimituksista on huomattavissa miten B:n ja C:n etäisyysarvio A:han vuorottelee solmujen välillä ja kasvaa vain kahdella per kierros. Tätä jatkuu kunnes arvo vihdoin saavuttaa A:n etäisyysarviot.

Hyvien uutisten kanssa tieto eteni viestien mukana aina laajemmalle. Huonojen uutisten kanssa voi valitettavasti tapahtua kuten äskeisessä esimerkissä, että tieto muuttuukin vain vakiolisäykselle yhtä kierrosta kohti. Tällöin mitään varsinaista ylärajaa ei saada sille, koska järjestelmä on taas vakaassa tilassa ja kaikilla on oikea tieto verkon sen hetkisestä tilanteesta. Englanniksi tällaista tilannetta kutsutaan termillä count-to-infinity.

Äskeisessä esimerkiksi ongelmaksi tulee se, että ajoittain B ja C kuvittelevat nopeimman reitin A:lle menevän toistensa kautta samaan aikaan. Tällöin B lähettää A:lle menevät viestit C:lle ja C lähettää ne puolestaan B:lle. Nämä viestit eivät voi tavoittaa A:ta, koska kumpikaan ei lähetä niitä A:lle.

Tämä nimenomainen ongelma voidaan korjata sillä, että solmu 'valehtelee' tietylle naapurille oman etäisyytensä äärettömäksi niihin solmuihin, jotka se reitittää kyseisen naapurin kautta. Näin solmu itse asiassa lähettää erilaiset etäisyysvektorit eri naapureilleen. Äskeisessä esimerkissä alkutilanteessa B lähettää A:lle vektorin B: (A 4, B 0, C 2), mutta C:lle vektorin (A -, B 0, C 2), koska se lähettää viestit A:lle C:n kautta. C lähettää saman vektorin sekä A:lle että B:lle, koska se ei reititä viestejä kummankaan kautta. Tällaista solmun tarkoituksellista valehtelua reitityssuuntaan kutsutaan englanniksi termillä poison-reverse.

Vaikka saimme tällä pienellä muutoksella katkaistua tässä esimerkissä tuon huonojen uutisten hitaan etenemisen, niin se ei ratkaise  kaikkia ongelmatilanteita.  (Esimerkiksi, jos otamme tähän kolmen solmun järjestelmään mukaan solmun D, jolla on yhteys vain solmuun B. Kun solmu D myöhemmin katoaa kokonaan verkosta A ja C aloittavat äskeistä esimerkkiä vastaavan pallottelun siitä mitä kautta ne D:n voivat tavoittaa. Koska kumpikin on lähettänyt viestit D:lle suoraan B:n kautta, niin tuon paluusuunnan asettaminen äärettömäksi ei auta.)







---
path: '/osa-4/4-reititin'
title: 'Reititin'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat yleisellä tasolla kuvata reitittimen rakenteen ja sen sisäisen toiminnallisuuden

</text-box>


## Reititin

Reitittimen perustehtävähän on ohjata sille saapuvat paketit oikeaan suuntaan eteenpäin. Tässä osiossa tarkastellaan reitittimen toimintaa ja rakennetta tähän perustehtävään liittyen. Wikipedian sivu [reititin](https://fi.wikipedia.org/wiki/Reititin) luettelee nykyaikaisen kotiverkon reitittimen tai oikeammin monitoimireitittimen muitakin tehtäviä, joista osa käsitellään muualla tällä kurssilla ja osa jätetään myöhemmillä kursseilla käsiteltäväksi.

Yhden paketin käsittely reitittimessä voidaan jakaa kolmeen vaiheeseen. Ensin paketti saapuu reitittimelle jonkun sisääntulon kautta. Sen jälkeen reititin tekee päätöksen mihin suuntaan paketti laitetaan. Viimeisenä vaiheena reititin lähettää paketin eteenpäin jonkun ulosmenon kautta. Reitittimen sisäisen toiminnallisuuden ja rakenteen pitää siis tukea pakettien siirtoa siihen kytkettyjen eri linkkien välillä. Useimmat verkkototeutukset perustuvat tällä hetkellä kaksisuuntaiseen yhteyteen, joten sama linkkiyhteys toimii joillekin paketeille sisääntulona ja joillekin toisille paketeille ulosmenona.

Reitittimien täytyy toki myös ylläpitää reititystietoa. Koska reititystietojen muutokset vaikuttavat pakettien ohjaukseen, niin joskus nämä kaksi toiminnallisuutta sijoitetaan loogisesti eri tasoille. Pakettien ohjaus kuuluu silloin datatasolle (engl. data plane), tätä tasoa voidaan kutsua vaihtoehtoisesti myös toimintatasoksi (engl. functional plane) ja verkkojen kohdalla jopa välitystasoksi (engl. forwarding plane). Nimityksessä on horjuvuutta sen mukaan halutaanko korostaa toiminnallisuutta vai dataa. Joka tapauksessa tästä tasosta erillinen kontrollitaso (engl. control plane) ohjaa ja valvoo sen toimintaa. Tietoverkkojen ja reitittimien osalta näiden tasojen toiminnallisuuden ero on siinä, että reititystietoihin liittyvät muutokset tehdään kontrollitasolla ja pakettien ohjaus tapahtuu datatasolla. Tällainen toiminnallisuuksien erotteleminen eri tasoille pitäisi jo tässä vaiheessa kurssia olla jonkunverran tuttua, koska olemme käyttäneet jo protokollapinoa, jossa on erilaisia kerroksia ja niillä erilaisia toiminnallisuuksia. Tasojen käyttö poikkeaa kuitenkin protokollapinosta yhdellä merkittävällä tavalla. Protokollapinossa jokaisen paketin käsittelyä tehdään tarvittaessa jopa pinon kaikilla kerroksilla ja pinojen toiminnallisuuksilla on järjestys. Sen sijaan datatason toiminnallisuus on riippumattomampaa kontrollitason toiminnasta. Pakettien ohjaus tapahtuu kokonaisuudessaan datatasolla ja kontrollitaso puuttuu toimintaan vain, kun on tarpeen päivittää ohjauspäätöksen taustalla olevia reititystietoja.

Kotrollitason toiminnot kävimme läpi jo edellisessä osassa, kun tutustuimme reititysalgoritmeihin. Tässä keskitytäänkin vain datatasoon, jolla reittimen pitää pystyä toimimaan hyvin tehokkaasti ja välittämään paketti nopeasti eteenpäin.

<img src="../img/4-4-reititin.svg" alt="Alla olevan kuvatekstin mukainen kuva"/>

KUVA: Kuvan yläosassa kontrollitaso, jossa vain yksi elementti "reitityspäätökset", kuvan alaosassa datataso, jossa useita sisääntuloja vasemmalla, arkkitehtuuri keskellä ja useita ulosmenoja oikealla. Sisääntuloista on suunnattu nuoli arkkitehtuurin, josta on nuoli jokaiseen ulosmenoon. Reitityspäätösten ja arkkitehtuurin välissä on kaksi suuntainen nuoli. Tasot on erotettu toisistaan vaakaviivalla (yhtenäinen tai katkoviiva). Jokaisessa sisääntulossa ja ulosmenossa on kolme laatikkoa, joista arkkitehtuuria lähin laatikko on jono, keskellä linkkikerroksen toiminnot ja ulommaisena linkin päätepiste. Kaikki nuolet datatasolla kuvaavat siis paketin kulkusuuntaa reitittimessä. Sisäänmenoissa nuolet ovat kohti arkkitehtuuria ja ulosmenoissa siitä poispäin.

## Sisääntulo

Paketit siis saapuvat reitittimeen sisääntulon kautta. Sisääntulossa on ensin linkin päätepiste, johon paketin sisältö saapuu fyysisen tason signaaleina. Siitä se päätyy linkkikerroksen käsittelyyn, jossa mm. poistetaan linkkikerroksen kehystiedot paketista. Linkkikerrokseen, sen toiminnallisuuteen ja linkkikerroksen kehyksen rakenteeseen tutustutaan tarkemmin seuraavassa luvussa. Linkkikerroksen jälkeen meillä on verkkokerrrokselle kuuluva IP-paketti, joka päätyy sisääntulon kolmanteen vaiheeseen.

Pakettiin kohdistuva reitityspäätös (eli ulosmenon valinta) tehdään yleensä jo sisäänmenon kolmannessa vaiheessa, jotta paketti saadaan mahdollisimman nopeasti eteenpäin. Yksinkertaisessa reitittimessä, joka käsittelee paketteja yksi kerrallaan tämän reitityspäätös voitaisiiin hyvin tehdä osana reitittimen arkkitehtuuria, mutta nykyaikaiset reitittimet osaavat käsitellä sisääntuloja ja ulosmenoja rinnakkain, joten päätös täytyy tehdä ennenkuin paketti ohjataan laitteen arkkitehtuurin mukaisesti oikeaa ulosmenoon.

Reitityspäätöksen yhteydessä myös paketin IP-otsakkeen tarvittavat kentät päivitetään. Reititin päivittää ainakin paketin elinaikaa, jonka vuoksi sen täytyy laskea IP-paketin otsakkeelle uusi tarkistussumma ja päivittää sekin. Huomaathan, että reitittimen pitää tietää, minkä version mukainen paketti on kyseessä, joten jo ennen reitityspäätöstä sen täytyy tarkistaa IP-paketin versionumero, jotta se osaa käsitellä paketin ja sen otsakkeen kentät oikein.

Kun sisääntulossa tiedetään mihin ulosmenoon paketti pitää ohjata se voidaan antaa arkkitehtuurille siirrettäväksi oikeaan ulosmenoon. Tässä vaiheessa paketti saattaa joutua hetken jonottamaan, jos esimerkiksi joku toinen paketti on juuri siirrossa samaan ulosmenoon tai arkkitehtuurissa ei muuten ole vapaata reittiä paketin siirtämiseksi.

Reitittimien suurin haaste ei ole pakettien välitys sinänsä vaan se, että pakettien välitykseen ei saisi kulua juurikaan aikaa. Jotta gigabitin reititin pystyy välittämään liikennettä tällä nopeudella se ei voi käyttää montaakaan nanosekuntia yhden paketin välittämiseen sisääntulon ulkoreunalta ulosmenon ulkoreunalle. Jos jos paketti ei joudu jonottamaan, niin sen pitää päästä reitittimen läpi muutamassa nanosekunnissa. Jos tämän prosessointiviive on paljon suurempi, niin silloin reititin ei pystykään välittämään liikennettä halutulla nopeudella. Hitaammalla nopeudella reitittimellä on enemmän aikaa paketin käsittelyyn ennenkuin seuraava paketti jo saapuu. Prosessointiviiveen päälle tulevat sitten mahdolliset jonotuksen aiheuttamat jonotusviiveet.


## Ulosmeno

Ulosmeno huolehtii sitten saapuneen paketin lähettämistä seuraavaan linkkiin. Kun paketti on päätynyt reittimen sisällä tänne asti sille tehdään vastaavia operaatioita kuin sisääntulossa, mutta päinvastaisessa järjestyksessä. Koska sisääntulossa on jo IP-paketin otsaketiedot päivitetty, niin täällä IP-paketti sijoitetaan linkkikerroksen kehyksen sisään. Tämän uuden kehyksen otsaketiedot päivitetään ja kun linkki on vapaa kehys lähetetään sinne. Koska linkki ei aina on heti vapaa, paketti voi joutua jonottamaan myös ulosmenossa kunnes linkki vapautuu.




## Arkkitehtuuri  (kytkentä sisäänmenojen ja ulostulojen välilllä)

Reitittimien toteutukselle on olemassa useita arkkitehtuurivaihtoehtoja.  Reititin voidaan toteuttaa ihan tavallisella tietokoneella, mutta tällöin liikennöintinopeus ei ole ihan yhtä suuri kuin pelkästään reititystehtävään suunnitellulla laitteella. Tietokoneen toiminta kurssilla on käsitelty muutamaa tapaa siirtää tietoja tietokoneen sisällä. Näissä tieto voitiin siirtää oheislaitteiden (tässä sisääntulo ja ulosmeno) välillä joko suoraan väylää pitkin tai niin että se ensin kopioitiin (väli)muistiin ja sitten sieltä seuraavalle laitteelle. Nämä tavat, muistin (engl. memory) välityksellä tai väylän (engl. bus) kautta, ovat käytössä myös varsinaisissa reitittimissä. Koska niiden perusmallissa vain yksi paketti kerrallaan voidaan siirtää jostain sisääntulosta johonkin ulosmenoon, ei niillä saada välttämättä toteutettu riittävän nopeita reitittimiä tilanteisiin, joissa reittimellä on paljon yhteyksiä, joita sen pitäisi välittää suurella nopeudella. Tällöin voidaan käyttää reitittimena arkkitehtuurina esimerkiksi erityistä kytkentäverkkoa (engl. interconnection network), jolloin eri sisääntuloista voidaan saman aikaisesti siirtää paketteja eri ulosmenoihin, kunhan kaikki sisääntulot ja ulosmenot ovat erillisiä.  Yhteen ulosmenoon voidaan siirtää vain yksi paketti kerrallaan.



## Jonotuksen syitä ja vaikutuksia

Nyt kun olemme hiukan tutustuneet myös reitittimen sisäiseen toimintaan ja rakenteeseen on helpompi hahmottaa erilaisia syitä reitittimessä syntyvälle jonotusviiveelle ja myös sille, miksi sen arviointi etukäteen on vaikeaa tai jopa mahdotonta.

Jokaiseen linkkiin liittyy tyypillisesti kaksi jonoa, toinen saapuville ja toinen lähteville paketeille. Itseasiassa näistä jonoista käytetään yleensä termiä puskuri (engl. buffer), koska ne säilyttävät viestejä tilapäisesti, eli puskuroivat niitä, ennen niiden etenemistä seuraavaan vaiheeseen.

Sisääntuloon saapuva paketti laitetaan jonoon, jos jonossa on tilaa. Jos jonossa ei ole tilaa, niin se (tai joku jo jonossa oleva) paketti pudotetaan pois. Tällöin paketti katoaa, koska se ei enää ole olemassa. Tästä jonoon saapuvan paketin hukkaamisesta käytetään myös englanninkielistä termiä drop-tail. Reititin voi tehdä pakettien kadottamista jo ennakoivasti ennen kuin puskuri on täynnä.  Tällaisessa aktiivisessa jonon hallinnassa (engl. active queue management) voidaan esimerkiksi paketti kadottaa ennakoivasti tietyllä todennäköisyydellä, jos jonon sen hetkinen pituus ylittää tietyn kynnysarvon, vaikkapa puolet tai kolme neljäsosaa maksimimäärästä.

Paketti voi viipyä sisääntulon jonossa, jos joko reitittimen arkkitehtuuri ei ehdi sitä siirtämään tai samaan ulosmenoon pitää siirtää myös muitakin paketteja. Tällöin siirtovuorossa oleva paketti ei pääse etenemään. Jonon ensimmäisen paketin siirron viivästymisestä käytetään joskus myös englanninkielistä termiä head-of-the-line blocking. Kun jonon ensimmäinen paketti ei pääse eteenpäin se estää myös kaikkia muita saman jonon paketteja etenemästä, koska jonoa puretaan aina järjestyksessä.

Ulosmenossakin voi muodostua jonoa (ja puskuri jopa täyttyä) esimerkiksi siksi, että samaa linkkiä käyttää useampi lähettäjä, jolloin reititin ei pääse lähettämään paketteja riittävän nopeasti, kun linkki on varattuna muille lähettäjille. Yllättävämpi syy ulosmenon jonon kasvuun on kuitenkin se, että samaa ulosmenoon tulee paketteja useammasta sisääntulosta. Jos oletetaan, että kaikki linkit toimivat samalla nopeudella, niin silloin jos usemmasta sisääntulosta tulee samalla hetkellä paketti samaan ulosmenoon, niin paketit joutuvat jonoon, koska ulosmeno voi lähettää vain yhden paketin samassa aikayksikössä kuin kaikkiin sisääntuloihin tulee yksi paketti jokaiseen. Juuri tällaista tilannetta varten reitittimissä on jonoja ja puskureita, jotta kaikki saapuvat paketit saadaan lähetettyä aikanaan.


Äskeinen kuva reitittimen toiminnasta on hyvin suppea todellisten markkinoilla olevien reitittimien toiminnasta. Vaikka ne kaikki edelleen toimivat reitittiminä ja välittävät liikennettä jollakin edellä kuvatulla tavalla, niin käytännössä ne tekevät paljon muutakin. Tyypillisesti niissä on esim. NAT toiminnallisuus, mahdollisuus DHCP palvelun käyttöön, erilaisia verkon turvallisuutta lisääviä piireitä kuten palomuuri (engl. firewall) tai sitä kehittyneempiä tunkeutumisen estojärjestelmiä (engl. intrusion prevention system) ja muutakin pakettien suodatusta. Jotkut reitittimet tarjoavat myös langattoman verkon tuen ja toiset syvemmälle verkkoon suunnitellut laitteet taas sisältävät enemmän portteja, jolloin ne pystyvät yhdistämään useampia laitteita.
Tässä vaihessa kurssia osaat jo etsiä reitittimen esitteestä ja informaatiosta tietoa, vaikka esitteessä onkin paljon vielä tuntemattomia käsitteitä.

Poimin tähän sattumanvaraisesti kahden eri valmistajan esitteet. Ciscolta on mukana [Cisco RV340, RV345, RV345P, and RV340W Dual WAN Security Router Data Sheet](https://www.cisco.com/c/en/us/products/collateral/routers/small-business-rv-series-routers/datasheet-c78-742350.html) ja  Ubiquitilta [EdgeRouter Data Sheet](https://dl.ubnt.com/datasheets/edgemax/EdgeRouter_DS.pdf).

Molemmissa esitteissä esiintyy lyhenne PoE. Aukikirjoitettuna se on [Power-over-Ethernet](https://fi.wikipedia.org/wiki/Power_over_Ethernet) eli tietokoneen tai muun verkkolaitteen tarvitsema sähkövirta voidaan toimittaa suoraan laitteet yhdistävässä ethernet-kaapelissa eikä erillistä virtajohtoa tarvita.

Laitteissa puhutaan myös kerrosten 2 ja 3 kytkimistä (engl. Layer 2 and Layer 3 switch). Nämä viittaavat protokollapinoon siten että kerros 2 on linkkikerrosja kerros 3 verkkokerros. Käytännössä tuollainen kerroksen 3 kytkin on reititin, jossa reitityspäätöksiä tehdään ohjelmiston sijasta laitteistolla. Jos asia kiinnostaa, niin lue lisää englanninkielisestä wikipedian artikkelista [Multilayer switch](https://en.wikipedia.org/wiki/Multilayer_switch).

<quiz id="b6e7f93c-91a7-44f7-a66e-f1c8c92e255a"> </quiz>



---
path: '/osa-4/5-muita-verkkokerroksen-protokollia.md'
title: 'Muita verkkokerroksen protokollia'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Tunnistat termin ICMP ja osaat yleisellä tasolla kertoa mikä se on
- Tunnistat termin IPsec ja osaat yleisllä tasolla kertoa mikä se on

</text-box>



## Muita verkkokerroksen protokollia

Edellä on käyty läpi verkkokerroksen tärkeimmän protokollan IP:n toiminnallisuutta. Verkkokerroksella on kuitenkin paljon muitakin protokollia. Englanninkielinen wikipedian sivu [Network_layer](https://en.wikipedia.org/wiki/Network_layer) luettelee niitä toistakymmentä. Tällä kurssilla tutustutaan niistä hyvin lyhyesti vain kahteen, jotka ovat vahvasti liitoksissa IP-protokollan kanssa. Kummankaan protokollan yksityiskohtaista toimitaa emme käy läpi. Se jää myöhemmille kursseille.


## ICMP

Internet Control Message Protocol (ICMP) on protokolla, jonka avulla verkon laitteet voivat välittää toisilleen tietoa verkon tilasta.

Ping ja traceroute käyttävät nimenomaan ICMP-paketteja verkon tilan selvittämiseen. Ping-komennolla voi kokeilla saavuttavatko paketit vastaanottavan koneen ja traceroute-komennolla voi selvittää mitä reittiä paketit lähettäjältä vastaanottajalle kulkevat.

Reitittimet voivat käyttää ICMP-paketteja kertomaan lähettäjälle, jos reititin pudottaa IP-paketin siksi, että sen elinaika (time-to-live, TTL) päättyy eli laskuri menee 0:aan. Reititin voisi kertoa lähettäjälle myös muista pakettien pudottamisista, mutta reitittimen oman kuormituksen hallinnan vuoksi tätä ei juurikaan käytännössä tehdä.

Jos protokolla yksityiskohtaisempi toiminta kiinnostaa, niin englanninkielisellä wikipedian sivulla [Internet Control Message Protocol](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol) on kuvattuna tarkemmin protokollan erilaiset viestityypit ja niihin liittyvät koodit.

<quiz id="a2588d5b-8147-4e48-bf4e-d69b0c9dc992"> </quiz>

## IPsec

[IPsec](https://fi.wikipedia.org/wiki/IPsec) ei ole vain yksi protokolla vain oikeammin protokollaperhe, kuten sen englanninkielinen nimi IP Security Architecture jo tavallaan kertoo.

IPsec on kehitetty huomattavasti itse internetiä myöhemmin ja sen tavoitteena on suojata IP-paketissa siirrettävä data salaamalla se. Vastaavaa palvelua tarjoaa kuljetuskerroksella TCP-yhteyksille [TLS](https://fi.wikipedia.org/wiki/TLS).

Virtuaaliset yksityisverkot (VPN) toteutetaan tyypillisesti juuri IPsec:llä. Silloin IPsec:iä käytetään tunnelointitilassa (engl. tunnel mode) ja alkuperäinen IP-paketti otsakkeineen on IPsecillä salattava ja kuljetettava data. IPsec:llä salattu paketti sijoitetaan sitten tavalliseen IP-pakettiin, jonka otsakkeita ei tietenkään voida salata, kun IP-paketteja ei internetissä salata. Näin saadaan kuitenkin tunnelissa salattua tuo alkuperäinen paketti otsakkeineen, koska se on vain data tässä salatussa IP-paketissa. Tunnelissa kulkevan salatun paketin vastaanottaja ja lähettäjä ovat piilossa niin kauan kuin paketti on tunnelissa, mutta jotta paketti voidaan toimittaa lopulliselle vastaanottajalleen, niin salaus on purettava, jonka jälkeen alkuperäisen paketin otsakkeissa olevat lähettäjän ja vastaanottajan IP-numerot ovat taas luettavissa.

Tämä IPsecin suhde virtuaalisten yksityisverkkojen yhtenä toteutusvaihtoehtona on suurin syy protokollan suppeaan esittelyyn tällä kurssilla.

<img src="../img/IPsec.svg"  alt="Kuvassa on protokollapinon kerrokset, joiden väliin on sijoitettu myös IPsec. Kerrokset ylhäältä lukien sovelluskerros, kuljetuskerror, verkkokerros, IPsec, verkkokerros, linkkikerros">

KUVA: Kuvassa on protokollapinon kerrokset, joiden väliin on sijoitettu myös IPsec tunnelointitilassa. IPsecin yläpuoliset sovellus-, kuljetus- ja verkkokerros ovat alkuperäisen IP-paketin mukaisia. IPsecin alapuoliset kerrokset puolestaan kohdistuvat IPsec:n tekemään uuteeen IP-pakettiin.


IPsec:iä voi käyttää myös kuljetustilassa (engl. transport mode), jolloin sen kuljettama data on kuljetuskerrokselta tullut segmentti. Tällöin salataan vain kuljetettava data, mutta otsaketiedot jäävät salaamatta. Protokolla sinänsä toimii samoin sekä tunnelointitilassa että kuljetustilassa, mutta sen oma data on erilainen. Kuljetustilassa sen data on TCP-segmentti, kun taas
tunnelointitilassa datana on IP-paketti.

Koska IPsec käyttää salausta on sekä lähettäjällä että vastaanottajalla oltava jokin jaettu salaisuus, tyypillisesti salausavain (engl. encryption key) tai avainpari, jolla data voidaan lähettäjällä salata (engl. encrypt) ja vastaanottajalla taas purkaa (engl. decrypt) ennen salausta olleeseen "selväkieliseen" muotoon.

Koska lähettäjällä ja vastaanottajalla on oltava sama symmetrisen salauksen avain, niin IPsec oikeastaan muodostaa yhteyden lähettäjän ja vastaanottajan välille, vaikka perinteisesti ja edelleen IP sinänsä on yhteydetön. IPsec tarjoaa useita erilaisia salausmenetelmiä, joten yhteyden aluksi lähettäjän ja vastaanottajan pitää sopia käytettävästä menetelmästä ja avaimista. Tätä varten ne muodostavat yksisuuntaisen loogisen yhteyden, jota kutsutaan englanniksi security association. Yhteys on yksisuuntainen, koska kun toimitaan verkkokerroksella, niin yksittäinen viesti kulkee aina vain yhteen suuhtaan lähettäjältä vastaanottajalle. Jos viestejä pitää kuljettaa myös toiseen suuntaan, niin sitä varten pitää muodostaa oma looginen yhteys.

IPsecissä on joitakin salausalgoritmeja käyttäviä menetelmiä, joita käytetään eri tarkoituksiin. Authentication Header (AH) menetelmällä voidaan taata datan muuttumattomuus (engl. data integrity) ja varmentaa lähettäjä (engl. host authentication). Varsinainen datan luottamuksellisuus (engl. confidentiality), eli se että muut eivät voi lukea datan sisältöä, saadaan AH:n sijaan Encapsulation Security Payload (ESP) -protokollalla.

Turvallinen avaintenhallinta on aina keskeinen ongelman tiedonsuojaukseen liittyvissä salausjärjestelmissä. IPsec:ssä on erillinen avaintenhallintaprotokolla Internet Key Exchange (IKE), jonka avulla avaimista voidaan sopia turvallisesti ilman, että muut verkossa olevat laitteet pystyvät tunnistamaan kommunikoinnin osapuolia.  IKEn sijaan avaimet voitaisiin toki asettaa kommunikoiville laitteille käsin, mutta isommissa järjestelmissä laitteita on aivan liikaa tähän tarkoitukseen.

Palataan vielä hetkeksi virtuaalisten yksityisverkkojen teemaan. Virtuaalinen yksityisverkko kahden aliverkon välillä voidaan siis toteuttaa IPsecillä siten, että tunnelointi tehdään aliverkkoja julkiseen verkkoon yhdistävissä reitittimissä. Pienimmillään toinen näistä aliverkoista voi olla käyttäjän tietokone ja suurimmillaan kyseessä voi olla ison organisaation koko sivukonttori. Toinen on tyypillisesti organisaation oma laaja verkko pääkonttorilla tai pääasiallisessa toimipaikassa. Tyypillisesti vain toisella aliverkolla on tunneloimaton yhteys internetiin.

<img src="../img/4-5-vpn.svg" alt= " Aliverkossa A on tietokone T1, jonka IP osoite on 158.34.128.78. Verkossa on myös muutama muu laite, joiden IP-osoitteita ei ole kerrottu. Laitteet on yhdistetty aliverkon reunalla olevaan reitittimeen R1, jonka aliverkon puoleinen IP-osoite on 158.34.23.1 ja julkisen internetin puoleinen osoite on 202.128.78.26. Reitittimen yhdistää toisen aliverkon B, reitittimeen R2 julkinen pilvimäinen internet, jonka läpi reitittimien välinen tunneli muodostaa suoran putken. Reitittimen R2 Internetin puoleinen IP-osoite on 158.34.2.10 ja aliverkon sisäpuolen IP-osoite on 158.34.79.5. Tässä toisessa aliverkossa on kuvattuna vain viestin vastaanottaja V2, jonka IP-osoite on 158.34.79.186. Lisäksi aliverkossa on muutama viivalla piirretty linkki, joiden toista päätä ei ole kuvattu.">

KUVA: Kuvassa kaksi aliverkkoa on yhdistetty virtuaaliseksi yksityisverkoksi. Näitä verkkoja yhdistävät reitittimet toimivat yhteistyössä ja tunneloivat kaikki aliverkosta A lähtevät viestit aliverkkoon B.


<quiz id="a9c31430-872f-4bed-8a59-e068b807198f"> </quiz>

Jos et saanut äskeistä tehtävää oikein, niin piirrä itsellesi alkuperäinen laitteen lähettämä IP-paketti ja sen jälkeen reitittimen lähettämä IP-sec paketti ja katso miten nuo lähettäjien ja vastaanottajien osoitteet menevät.



---
path: '/osa-4/6-yhteenveto'
title: 'Yhteenveto'
hidden: false
---


Neljännessä osassa tutustuttiin verkkokerroksen toimintaan tarkemmin. Reititys on sen keskeinen toiminto ja siksi opettelimmekin, miten keskenään erilaiset reititysalgorimit tekevät ja päivittävät reititystauluja.


Vastaa vielä alla olevaan kyselyyn.

<quiz id="a577df8a-83c4-46a6-bc3c-dabbacc116cf"></quiz>



---
path: '/osa-5/1-linkki-toiminta'
title: 'Yleistä linkkikerroksen toiminnasta'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat selittää linkkikerroksen toiminnallisuus (MAC- 
   osoitteet, bittivirheiden havaitseminen) ja ARP-protokollan 
   käyttö. 
- Osaat selittää yhteiskäyttöisen siirtokanavan varauksen ja käytön
- Osaat selittää, kuinka koneita voi yhdistellä lähiverkoiksi
- Osaat selittää reitittimen, kytkimen ja keskittimen erot 

</text-box>


## Linkkikerros

Linkkikerros huolehtii viestin välityksestä vain samassa aliverkossa olevien laitteiden välillä. Nämä laitteet voivat kommunikoida keskenään pelkän linkkikerroksen välityksellä. Verkkojen väliseen liikennöintiin tarvitaan reititystä ja reitittimiä. Muistathan, että reitittimet yhdistävät aliverkkoja toisiinsa, joten reitittimen kummallakin puolella on eri aliverkko ja siksi reitittimen täytyy lähetysvaiheessa muodostaa uusi linkkikerroksen kehys seuraavaa aliverkkoa varten.

Yhdessä aliverkossa olevat laitteet voivat havaita muiden saman aliverkon laitteiden lähettämän liikenteen, joten ne voivat suoraan vastaanottaa toisen laitteen lähettämän signaalin. Yhdessä aliverkossa on käytännössä vähintään kaksi laitetta, mutta laitteita voi olla useampiakin. Samaan aliverkkoon liitettävien laitteiden maksimimäärä riippuu käytettävästä verkkotekniikasta ja [verkon topologiasta](https://fi.wikipedia.org/wiki/Verkkotopologia). Esimerkiksi tähtiverkossa kytkimen porttien lukumäärä rajoittaa siihen liitettävien laitteiden lukumäärää. Väyläverkossa taas laitteiden fyysinen etäisyys tai oikeammin signaalin kulkuaika päästä päähän rajoittaa aliverkon kokoa. Renkaassa puolestaan rajoitteeksi tulee yhteen kierrokseen kuluva aika.

Wikipediassa on hyvä kuva erilaista topologioista: [https://fi.wikipedia.org/wiki/Tiedosto:Verkkotopologiat.png](https://fi.wikipedia.org/wiki/Tiedosto:Verkkotopologiat.png") 

* Väylässä laitteet littyvät vuorotellen samaan yhteen fyysiseen kaapeliin. Väylä on kuin jana, jolla on alkupiste ja loppupiste ja siinä välissä laitteita kiinni erikohdissa tätä janaa. Väylän laitteet voivat suoraan kommunikoida kaikkien muiden väylän laitteiden kanssa. 
* Tähdessä on keskipiste, johon kaikki laitteen yhdistyvät omilla johtimillaan. Tähden sakaroissa olevat laitteet voivat siis suoraan kommunikoida vain tähden keskipisteen kanssa, jonka pitää välittää viestejä sakaroiden välillä.
* Renkaassa laitteet on yhdistetty lyhyillä johtimilla suljetuksi ketjuksi. Rengas on kuin helminauha, jossa jokainen helmi on laite. Jokainen laite voi suoraan kommunikoida vain viereisten laitteiden kanssa. Viestin saaminen kauemmas renkaassa edellyttää, että matkan varressa olevat laitteet laittavat viestin eteenpäin.


Nykyisin tähtiverkko on ehkä kaikkein tyypillisin verkontopologia. Siinä verkon keskipisteessä on esimerkiksi linkkikerroksen kytkin, joka yhdistää verkon sakaroita toisiinsa. Yhdessä sakarassa on sitten reititin, jonka kautta tämä aliverkko on yhteydessä muualle. Kotiverkoissa usein kytkin ja reititin eivät ole erillisiä laitteita, vaan monitoimireititin toimii verkon keskipisteessä kotiverkon kytkimenä ja samalla reitittimenä ulkoverkon suuntaan. Tähtiverkkoja voidaan laajentaa useamman tähden kokoiseksi, kun yhteen sakaraan kiinnitetään toisen tähden keskipiste, kuten reititin, kytkin tai fyysisellä kerroksella toimiva keskitin tai toistin (engl. repeater).

## Linkkikerroksen tehtävät

Linkkikerroksen tehtävät liittyvät nimen omaan viestien siirtoon yhden fyysisen kerroksen yhteyden eli linkin yli. Linkkikerroksen pitää huolehtia, että kukin viesti pääse muuttumattomana linkin yli. Fyysisen kerroksen ominaisuuksista johtuen kanavassa voi kulkea vain yhden viestin tietoja yhdellä ajanhetkellä. 

Linkkikerroksen täytyy hallinoida lähettäjien vuorottelua kanavassa eli vuonvalvontaa. Vuonvalvonnan ratkaisut ovat erilaisia erilaisille fyysisille linkeille. Liikennöinti yhdessä linkissä voi olla yksisuuntaista (engl. half dublex) tai kaksisuuntaista (engl. full dublex), linkki voi olla langallinen tai langaton. Lisäksi kytkimet saattavat joutua puskuroimaan viestejä, koska osa kytkimistä osaa yhdistää samalla kommunikointitekniikalla toteutettuja eri nopeuksisia fyysisiä yhteyksiä toisiinsa. Esimerkiksi ethernet-kytkimessä voi olla nopeudeltaan sekä 10 Mb/s, 100 Mb/s että jopa 1 Gb/s portteja.

Viestin lähettäminen linkkiin ei siis saa häiritä mahdollisia muiden lähettämiä viestejä samassa linkissä. Tämä koskee erityisesti väylätopologiaa, jossa samassa kanavassa voi kulkea useiden eri lähettäjien viestejä. Koska viestit usein lähetetään sähköisinä signaaleina, jotka sekoittuvat toisiinsa helposti, on tärkeää, että kanavassa kulkee vain yhden lähettäjän viesti kerrallaan. Tällöin sanotaan, että lähettäjä on varannut kanavan omaan käyttöönsä. Tällaisia yhteiskäyttöisen kanavan varaamiseen liittyviä menetelmiä tarkastellaan hetken kuluttua aliluvussa lähetysvuorojen jakelu.

Linkkikerroksellakin vastaanottaja pitää tunnistaa, jotta viesti voidaan toimittaa oikealle vastaanottajalle. Tunnistamiseen tarvitaan vastaanottajan osoite. Linkkikerroksella tämä osoite on yleensä ethernet-verkon [MAC-osoite](https://fi.wikipedia.org/wiki/MAC-osoite), koska se on jo laitevalmistajan kyseiselle laitteelle etukäteen antama. Se on siis kiinteä laitteistoon liitetty osoite, joka alunperin ei voinut vaihtua. MAC-osoitteen 48 bittiä on jaettu kahteen osaan. Ensimmäiset 24 bittiä on laitevalmistajan tunniste ja jälkimmäiset 24 bittiä laitteen tunniste. Jokaisella valmistetulla laitteella, tai oikeammin verkkosovittimella, on oma maailmanlaajuisesti yksiklöivä tunniste.

Koska viesti ei saa muuttua matkalla on linkkikerroksen havaittava mahdolliset virheet ja tarvittaessa joko korjattava bittivirhe tai pudotettava paketti. Virheiden havaitsemisesta ja korjaamisesta on lisää seuraavassa aliluvussa.

## Osoitteen selvittäminen - ARP

Verkkokerroksella käytetty IP-osoite täytyy muuntaa MAC-osoitteeeksi, aivan kuten sovelluskerroksella käytetty laitenimi on muutettava IP-osoitteeksi.  IP-osoitetta vastaavan MAC-osoitteen selvittäminen onnistuu siihen tarkoitukseen suunnitellulla [ARP-protokollalla](https://fi.wikipedia.org/wiki/ARP_(protokolla)) (Address Resolution Protocol). 

Laitteen MAC-osoite on pysyvä (tai ainakin sen oletetaan olevan pysyvä). Sen sijaan laitteen IP-osoite vaihtuu ainakin silloin, kun laite vaihtaa yhden organisaation hallinnoimasta verkosta toisen organisaation verkkoon. MAC-osoitetta tarvitaan vain linkkikerroksella eli yhden aliverkon sisällä liikennöintiin. Aliverkon kannalta MAC-osoitteita ilmaantuu ja katoaa laitteiden mukana. 

Jokainen laite, joka toimii linkkikerroksen lisäksi myös verkkokerroksella, ylläpitää omaa ARP-väimuistia,  ARP-taulua, johon se kokoaa käyttämiään IP-osoite/MAC-osoite pareja. Taulussa on lisäksi jokaiselle osoiteparille oma voimassaoloaika, jonka kuluttua osoitemuunnoksen voi unohtaa. Tyypillinen voimassaoloaika on 20 minuuttia. Jos tietoa myöhemmin tarvitaan eikä muunnostieto enää ole ARP-taulussa, niin ARP-kysely on tehtävä uudelleen.

Huomaa, että laite selvittää vain samassa aliverkossa olevien laitteiden MAC-osoitteita, eli vain niitä osoitteita, jotka aliverkkopeitteen mukaan kuuluvat samaan aliverkkoon. Vain näille se voi lähettää viestejä suoraan linkkikerroksen avulla. Lähettäessään ARP-kyselyn se tietää, että laite, jonka osoitetta kysytään on samassa aliverkossa. Mieti miksi se voi tämän tietää!  (Vinkki: aliverkon peite).

ARP-protokollan mukaisesti kysely lähetetään linkkitason yleislähetysosoitteeseen, eli MAC-osoitteeseen FF-FF-FF-FF-FF-FF. Lähettäjä siis lähettää linkkikerroksen kehyksen, jossa vastaanottajana on yleislähetysosoite, lähettäjänä oma MAC-osoite ja datana kysytty IP-osoite ("Kenellä on tämä IP xx.yy.zz.vv?"). 

Kaikki verkon laitteet vastaanottavat tämän yleislähetysosoitteeseen saapuvan viestin. Jos viestissä on sisältönä laitteen oman IP-osoite, niin laite vastaa kyselyyn, jolloin lähettäjä saa vastauskehyksestä tietoonsa laitteen MAC-osoitteen.

Koska ARP-taulua käytetään väimuistina, niin kaikkien muiden välimuistien tapaan se on aluksi tyhjä. Tauluun siis lisätään tietoa sitä mukaan, kun laite saa näitä selville.

ARP-protokollaa käytetään vain IPv4-osoitteita vastaavien MAC-osoitteiden selvittämiseen. IPv6:lle määritelty Neighbour Discovery Protocol (NDP) tarjoaa vastaavan toiminnallisuuden IPv6-osoitteille.

ARP-protokolla on hyvä esimerkki siitä, että jotkut protokollat eivät oikein istu käyttämäämme protokollapinon mukaiseen jaotteluun. ARP-prokolla luokitellaan välillä verkkokerroksen ja välillä linkkikerroksen protokollaksi. Se on selkeästi näiden kerrosten rajapinnassa, koska sen avulla voidaan saada kuvaus verkkokerroksen IP-osoitteen ja linkkikerroksen MAC-osoitteen välille. Vastaavia protokollia on muitakin. Kerrosmallin tarkoitus on lähinnä helpottaa asioiden ja kokonaisuuden hahmottamista. Jotta malli on saatu pysymään yksinkertaisena on vain ollut hyväksyttävä, että osa toiminnallisuuksista voi olla vaikea sijoittaa tiettyyn kerrokseen. 



## Linkkikerroksen toteutuksesta

Linkkikerroksen toteutus on oltava jokaisessa laitteessa, joka on liitettynä internet-verkkoon. Yleensä linkkikerroksen toiminnallisuus on toteutettu suoraan laitteistolla. Tietokoneessa on tyypillisesti erillinen verkkosovitin, joka muun tietokoneen kannalta on I/O-laite (Näistä tarkemmin Tietokoneen toiminta -kurssilla). Verkkosovitin liitetään tietokoneen päässä koneen sisäiseen väylään kuten muutkin I/O-laitteet. Tietoliikennekaapeli liitetään sitten verkkosovittimella olevaan liittimeen. Nykyisin verkkosovittimet on usein integroitu osaksi tietokoneen emolevyä, mutta aiemmin ne olivat erillisiä verkkokortteja, joita voi poistaa ja lisätä laitteeseen.  Verkkosovittimessa tai verkkokortissa on oma laiteohjain (engl. device controller), joka on usein toteuttu laitteisto-ohjelmistona (engl. firmware). Se huolehtii kaikista viestien lähetykseen ja vastaanottoon liittyvistä linkkikerroksen toiminnoista. Käyttöjärjestelmässä puolestaan on laiteajuri (engl. device driver), joka huolehtii käyttöjärjestelmän ja laiteohjaimen välisestä kommunikoinnista.

Verkkosovittimen ja sen laiteohjaimen tehtävänä on siis huolehtia viestien lähettämisvaiheessa vähintään vuonvalvonnasta ja bittien koodaamisesta ja lähettämisestä fyysisen linkin edellyttämässä muodossa. Lisäksi sen tehtäviin kuuluu kuunnella kanavaa, tunnistaa itselle saapuvat viestit, vastaanottaa ne ja purkaa fyysisestä signaalista viestin bitit. Huomaa, että verkkosovitin ja sen laiteohjain kuulee kaiken kyseisessä johtimessa kulkevan liikenteen, mutta se suodattaa siitä vain itselle saapuvat viestit. Myös virhetarkistus kuuluu laiteohjaimen tehtäviin. 

Linkkikerroksella käytettävän siirtokehyksen (engl. frame) muodostaminen verkkokerrokselta saapuvan datagrammin ympärille voi olla joko laiteohjaimen tai laiteajurin tehtävä. Eli se voidaan tehdä joko laitteistolla tai ohjelmistolla. Tässä on vaihtelua eri toteutusten väilllä.
  


<img src="../img/linkkikerros.svg" alt="."/>

Kuva : Kaavakuva linkkikerroksen sijainnista



## Ethernet

Ethernet on tällä hetkellä yleisin lähiverkon toteutustekniikka. Se on tyypillinen kotiverkon teknologia, koska markkinoilla on tarjolla paljon monitoimireitittimiä, jotka tarjoavat ethernet-tekniikalla toteutettuja kaksipisteyhteyksiä reitittimen portin ja laitteen välille. Kaksipisteyhteys on yleenä toteutettu ns. ethernet-kaapelilla, joka nykyisin on tyypillisesti [parikaapeli](https://fi.wikipedia.org/wiki/Parikaapeli).

Ethernet on standardoitu. Itseasiassa sen toteutustekniikka ja nopeus on vuosien varrella muuttunut aina uuden standardin myötä. Tällä hetkellä tyypilliset verkot ovat 100 Mbit/s ja 1 Gbit/s. Wkipedian sivulla [Ethernet](https://fi.wikipedia.org/wiki/Ethernet) on hyvä tiivis kuvaus ethernetin eri versioista.

Ethernetin ensimmäiset versiot käyttivät koaksiaalikaapelia ja noudattivat väylätopologiaa. Näissä käytettiin liikenteen hallinnointiin Carrier Sense Media Access / Collision Detection (CSMA/CD) menetelmää, jossa lähettävän solmun piti ensin kuunnella (Carrier Sense), että väylä (Media Access) on vapaa ja sitten vielä lähetyksen aikana kuunnella, ettei mikään muu solmu lähettänyt samaan aikaan, ns yhteentörmäys (Collision Detection).  Tarkastellaan tämän menetelmän toimintaa tarkemmin osassa vuoronjakelu.

Tämä CSMA/CD on edelleen mukana myös myöhemmissä ethernet-toteutuksissa, joissa verkon topologia on tähti ja käytetään parikaapelia. Yhdessä parikaapelissa ei voi tapahtua yhteentörmäyksiä, koska kumpaankin suuntaan on oma johdipari, eikä samassa johdinparissa ole muita lähettäjiä. Tähtiverkossa yhteentörmäyksiä voi tapahtua, jos tähden keskipisteenä on [keskitin](https://fi.wikipedia.org/wiki/Keskitin) (engl. hub) eikä kytkin tai reititin. Toisin kuin kytkin, joka toimii linkkikerroksella ja osaa tarvittaessa tilapäisesti puskuroida kehyksiä, keskitin toimii fyysisellä tasolla ja on vain moniporttinen toistin (engl- repeater), joka toistaa saapuvan liikenteen samantien kaikkiin muihin suuntiin. Keskitin onkin vain usean toistimen muodostama kokonaisuus ja usein näitä termejä käytetäänkin jopa synonyymeina. 

Kaikki ethernetin versiot käyttävät samankokoista kehystä. Ethernet kehyksen alussa on ensin tahdistuskuvio, jolla vastaanottaja voi oman signaalinkäsittelynsä tahdistaa lähettäjän määräämään tahtiin. Siksi tahdistuskuvion 7 ensimmäistä tavua sisältävät vuorotellen bittejä 1 ja 0 eli yksi tavu on aina 10101010. Kuvion viimeistä 8. tavua voidaan kutsua kehyksen aloitukseksi (engl. start of frame, SOG) tai kehyksen alun rajoitteeksi (engl. start frame delimiter, SFD). 8. tavu on muuten kuin aiemmat 7 tavua, mutta sen lopussa on kaksi ykköstä, joka kertoo vastaanottajalle, että seuraavaksi tulee kehyksen varsinaista sisältöä, josta ensimmäisenä vastaanottajan MAC-osoite. Sen jälkeen vuorossa on lähettäjän oma MAC-osoite, jota seuraa kahden tavun pituuskenttä. Joissakin ethernetin versioissa tämän pituuskentän arvoa käytetään välitettävän protokollan tyypin kuvaamiseen. Tätä kenttää seuraa varsinainen data-alue. Ethernet-kehyksessä siirrettävällä data-alueella on minimipituus. Jos siirrettävä data on sitä lyhyempi, niin silloin datan loppuun lisätään täytetavuja (engl. pad byte). Vastaanottaja osaa sivuuttaa nämä täytetavut. Kehyksen lopussa data-alueen jälkeen on vielä erillinen lopuke, jossa on 4 tavua CRC-menetelmän mukaan laskettuja tarkistusbittejä.

<img src="../img/ethernet-kehys.svg" alt="Ethernet kehyksen rakenne: tahdistuskuvio (preamble 7 tavua ja SOF 1 tavu), vastaanottaja (destination MAC address, 6 tavua), lähettäjä (source MAC address, 6 tavua), pituus (length 2 tavua), data ja täyte (data and pad, 46-1500 tavua, lopuke (FSC, 4 tavua)"/>

KUVA: Ethernet kehys


<quiz id="a62c5c7d-8454-424c-a722-dbaa4342bb8c"> </quiz>




  










---
path: '/osa-5/2-virheidenhavaitseminen'
title: 'Virheiden havaitseminen ja korjaaminen'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata miksi tietoliikenteessä virheet ovat mahdollisia.
- Osaat kuvata virheen havaitsemisen ja korjaamisen periaatteet.
- Osaat mainita useita virheiden havaitsemiseen käytettyjä menetelmiä ja kuvata niiden tyypillisiä käyttötilanteita.
- Osaat kertoa UDP/Internet-tarkistussumman ja CRC:n toimintaperiaatteen ja jopa tarvittaessa toteuttaa pienen ohjelman, joka laskee tarkistussumman tällä periaatteella.

</text-box>

## Yleistä virheistä ja niiden havaitsemisesta

Koska tietoliikenteessä tietoa siirretään erilaisina signaaleina langallisesti tai langattomasti, niin signaalit voivat muuttua siirron aikana. Signaali saatta vaimentua niin paljon, että vastaanottaja ei enää kykene luotettavasti erottamaan nollia ja ykkösiä toisistaan. Kanavassa voi myös olla muuta taustakohinaa, joka häiritsee vastaanottoa, esimerkiksi kaksi samanaikaista lähettäjää. Myös magneettikenttien vaihtelut ja jopa avaruudesta saapuvat hiukkaset ja säteily voivat muuttaa signaalin tasoja. Nämä muutokset voivat kohdistua vain yhteen bittiin tai useampaan peräkkäiseen bittiin, jolloin niitä usein kutsutaan virheryöpyksi (engl. burst).

Virheiden havaitseminen on vastaanottajan vastuulla, mutta lähettäjän pitää antaa sille riittävä informaatio, jotta virheenhavaitseminen on mahdollista. Tätä varten lähettäjä lisää kehykseen tarkistustietoa tai tarkistusbittejä (engl. error detection and correction bits). Tämän tarkistustiedon avulla vastaanottaja voi tarkistaa, onko kehykseen tullut virheitä. Jos se havaitsee virheitä kehyksessä, niin se voi joko yrittää korjata virheen, hävittää kehyksen tai pyytää sitä uudelleen lähettäjältä. Nämä kaikki ovat aitoja vaihtoehtoja virheiden käsittelyssä, mutta tietoliikenteessä yleensä virheellinen kehys hävitetään. Lähettäjä joutuu lähettämään kehyksen uudelleen.

Virheen havaitsemiseen tarvitaan siis lisäbittejä, joita voidaan tarkistusbitti -nimityksen sijaan kutsua tarkistussummaksi. Tarkistussummaan tutustuimmekin jo TCP ja UDP -protokollien yhteydessä. Samaa tarkistussummaa käytetään myös IP-otsakkeessa. Ethernet-kehyksissä käytössä on [Cyclic Redundance Check (CRC)](https://fi.wikipedia.org/wiki/CRC), joka on tehokkaasti toteutettavissa laiteistolla.

Vaikka kuljetuskerroksella on oma segmenttejä ja paketteja koskeva virhetarkistus, niin linkkikerroksella, ainakin ethernet-verkoissa, on oma virhetarkitus. Miksi ihmeessä virhetarkistuksia tehdään useammalla kuin yhdellä kerroksella? Yksinkertainen vastaus, koska muut kerrokset eivät tiedä, missä muualla virhetarkistuksia tehdään. Monimutkaisempi vastaus, eri kerroksilla on käytössä eri menetelmiä, joista osa tekee virhetarkistuksia ja osa ei, joten jos kyseinen protokolla haluaa varmistua siitä, että virhetarkistus toimii kaikilla eri yhdistelmillä, niin se joutuu tekemään sen itse. Vaikka tällä kurssilla tutustutaankin vain linkkikerroksen osalta ethernet-verkon toimintaan, niin todellisuudessa linkkikerroksella voi olla käytössä joku muu menetelmä, jossa ei ole virhetarkistusta. Vastaavasti linkkikerrokselle saattaa saapua siirrettäväksi sellaista dataa, jossa ei ole ylempien kerroksien virhetarkistuksia.

Tietokoneen toiminta -kurssilla tutustuttiin jo pariteettibitin käyttämiseen bittivirheen havaitsemisessa ja Hamming-koodin käyttämiseen bittivirheen korjaamisessa. Tästä jo havaittiin, että virheen korjaamiseen tarvitaan paljon enemmän bittejä kuin pelkkään virheen havaitsemiseen. Jos uudelleenlähetys ei ole vaihtoehto, niin silloin lähetykseen pitää liittää vielä enemmän tarkistustietoa, jotta virheenkorjaaminen on mahdollista.

Teoreettisemmassa tarkastelussa virheen korjaaminen (engl. error correction) voidaan tehdä joko taaksepäin (backward) tai eteenpäin (forward). Uudelleenlähetys luokitellaan tässä taaksepäin tapahtuvaksi, koska järjestelmän toiminta tavallaan peruutetaan aiempaan toiminnallisuuteen. Vastaavasti sellaisen menetelmän käyttö, jossa paketti saadaan korjattua ja voidaan toimittaa edelleen kuuluu näihin eteenpäin tapahtuviin eli FEC-menetelmiin (engl. forward error correction).  Näitä menetelmiä ovat edellämainittu Hamming-koodi ja satelliittiyhteyksillä käytetty Reed-Solomon-koodi.

Tietoliikenteessä tyypillisesti, erikoistapauksia lukuunottamatta, tyydytään virheen havaitsemiseen ja tarvittaessa paketin hylkäämiseen / uudelleen lähetykseen. Näin tarvittavan tarkistustiedon määrä pysyy kohtuullisena. Ethernetissä noin 1500 tavua dataa sisältävän kehyksen tarkistustiedon koko on vain 4 tavua. Kun lisäksi valitaan laitteistolla tehokkaasti toteutettava koodaustapa, niin paketin siirron kokonaiskestoon ei tule kohtuutonta viivettä tarkistussumman laskennasta ja tarkistamisesta.

Koska virheet esiintyvät tyypillisesti ryöppyinä ja sekoittavat kehyksen sisällöstä enemmän kuin vain yhden bitin, eivät menetelmät, joilla havaitaan vain yksittäisen bitin vikaantuminen, toimi tietoliikenteessä. Esimerkiksi yksinkertaisella pariteettitarkistuksella on vain noin 50% todennäköisyys havaita viottunut paketti.  Vastaavasti se tulkitsee viallisen paketin samalla todennäköisyydellä oikeaksi. Jotta menetemä olisi käyttökelpoinen sen pitää havaita vioittunut paketti paljon luotettavammin.

Eri yhteyksillä virheiden esiintymistiheyksissä (engl. bit error rate, BER) on suuria eroja. Jos yhteydellä esiintyy paljon virheitä eli virheiden tiheys on suuri, niin lähetettävien kehysten kokoa kannattaa pienentää. Näin kasvatetaan todennäköisyyttä, että virhe ei osu kehykseen vaan ilmaantuu kanavalle joko ennen viestiä tai sen jälkeen. Suuri kehys on kauan siirtotiellä / kanavassa ja samalla kasvaa todennäköisyys, että kehykseen osuu bittivirhe tai virhepurske.

Linkkikerroksella ei käytetä kuljetuskerroksella käytettyä tarkistussummaa, jossa yhteenlasketaan 16 bitin kokonaisuuksia. Linkkikerroksen kannalta menetelmä ei ole kovin tehokas. Kyseinen menetelmä on kuvattuna kuljetuskerroksen yhteydessä eikä sitä siksi toisteta tässä.



## CRC

Ethernet käyttää polynomien avulla laskettua tiivistettä tarkistussummana kehyksen virheiden havaitsemiseen. Tämä [CRC-menetelmä](https://fi.wikipedia.org/wiki/CRC) (engl. cyclic redundancy check, CRC) on varsin luotettava menetelmä virheiden havaitsemiseen. Lisäksi se on helppo toteuttaa laitteistotasolla. CRC tunnetaan myös nimellä polynomikoodi (egl. polynomial code), koska se perustuu polynomien aritmetiikkaan.


CRC:ssä bittijono tulkitaan 2-kantaiseksi polynomiksi, jossa siis kertoimet ovat vain 0 tai 1. Eli bittijono 101110 voidaan kirjoittaa polynomina 1\*x^5 + 0\*x^4 + 1\*x^3 + 1\*x^2 + 1\*x^1 + 0\*x^0 eli lyhyemmin x^5 + x^3 + x^2 + x^1. Huomaa että \* on kertomerkki ja  ^ on potenssiin korotus. Itseasiassa olemme jo tottuneet käsittelemään bittijonoja polynomeina, koska jos laskemme tämän polynomin arvon arvolle x=2, niin samme binäärilukua 101110 vastaavan 10-järjestelmän luvun 2^5 + 2^3 + 2^2 + 2^1 = 32 + 8 + 4 +2 = 46.

Koska CRC käyttää polynomiaritmetiikkaa ja erityisesti polynomien jakolaskua, niin lähettäjän ja vastaanottajan täytyy sopia jakolaskussa käytettävästä jakajasta. Tästä jakajasta käytetään nimitystä virittäjäpolynomi (engl. generator polynomial), koska se toimii jakolaskussa jakajana. Tämän polynomien jakolaskun jakojäännös muodostostaa tarkistusbitit sanomalle. Lähettäjän pitää siis jakolaskussa selvittää tarkistusbittien arvo. Tarkistusbittejä laskettaessa jakajana on siis virittäjäpolynomi ja jaettavana on alkuperäinen data, jota on pidennetty tarkistusbittien verran lisäämällä (katenoimalla) datan loppuun oikea määrä nollia. Matemaattisena kaavana tämä voidaan ilmaista D\*2^r XOR R, missä D on alkuperäinen data, R on tarkistustieto ja r on tarkistustiedon bittien lukumäärä. Lähettäjällä tarkistusbitit R on siis nollia. Vastaanottajalla R on vastaavasti sanoman mukana saapuneet todellisest tarkistusbitit.

CRC:n tarkastusbittien lukumäärä riippuu käytettävästä virittäjäpolynomista. Virittäjäpolynomin aste on aina yhden suurempi kuin tarkistusbittien lukumäärä. Polyomin aste vastaa sitä kuvaavan bittijonon pituutta.

Laskennan tehostamiseksi CRC:ssä jätetään yhteen- ja vähennyslaskuista pois muistinumero (engl. carry) ja lainaus, jolloin binäärilukujen aritmetiikassa ne supistuvat yksinkertaiseksi XOR-operaatioksi.

<quiz id="a07cd207-7fcd-40db-982d-d4262d8545ff"> </quiz>

Tällä kurssilla ohitetaan matemaattiset perustelut sille, miksi CRC toimii hyvin virheiden havaitsemissa. Jos aihe kiinnostaa, niin wikipediasta löytyy artikkeli [Mathematics of CRC](http://en.wikipedia.org/wiki/Mathematics_of_CRC), jossa on kattavasti kerrottu menetelmän matemaattiset perusteet.

Erikseen on vielä sovittu, että virittäjäpolynomin merkitsevin bitti on aina 1 eli niissä ei koskaan ole etunollia. Näin virittäjäpolynomi on mahdollisimman lyhyt. Tarkistusbittien määrä on aina yhden pienempi kuin virittäjäpolynomin oma pituus. Näin on, koska tarkistusbitit ovat jakolaskun jakojäännös.

Esimerkiksi, jos meillä on käytössä virittäjäpolynomi G=x^3 + 1 eli bitteinä 1001, niin meillä on 3 tarkistusbittiä.
Jos data, johon tarkistusbitit liitetään on 101110, lähettäjä tekee jakolaskun 101110000 : 1001 ja saa jakojäännökseksi 011.

Lähettäjä lähettää siis vastaanottajalle bittijonon 101110011. Tätä kutsutaan usein koodiksi (engl. code), koska alkuperäinen data on koodattu jollain tavalla mukaan tähän lähetettävään koodiin. Samaa termiä ja toimintamallia käytetään myös salausalgoritmeissa. Lähettäjä siis tekee alkuperäiselle datalle jonkin operaation ja lähettää tämän operaation tuloksena syntynen koodin vastaanottajalle, joka puolestaan tekee koodille jonkin (saman tai eri) operaation, ja saa tulokseksi alkuperäisen datan.

Kun vastaanottaja vastaanottaa bittijonon 101110011, se laskee jakolaskun 101110011 : 1001 jakojäännöksen. Jos jakojäännös on pelkkiä nollia, kuten tässä, niin se tietää / olettaa, että kehyksessä ei ole virheitä ja antaa datan 101110 eteenpäin. Jos se on saanut jonkun muun bittikuvion, vaikkapa 010111011, niin jakolaskun lopputulos ei ole nollia, vaan 110, jolloin se tietää, että kehyksessä on virheitä ja hylkää sen.

<img src="../img/crc-esimerkki.png" alt="Kuvassa on skannattu esimerkki CRC-laskutoimituksista">

Laskutoimitus on yksityiskohtaisesti kuvattu englanninkielisellä wikipedian sivulla [Cyclic Redundancy Check](https://en.wikipedia.org/wiki/Cyclic_redundancy_check)

Koska lähettäjän ja vastaanottajan pitää käyttää samaa virittäjäpolynomia, niin niitä on standardoitu ja eri tilanteisiin on tarkasti määritelty mitä polynomia niissä käytetään.  Muistathan, että tämä virhetarkistus tehdään tyypillisesti laitteistotasolla, jolloin menetelmän vaihtaminen edellyttää laitteistoon tehtäviä muutoksia tai kokonaan uutta laitteistoa. Ethernet käyttää standardoitua virittäjäpolynomia CRC-32, joka on x^32+ x^26 + x^23 + x^22 + x^16 + x^12 + x^11 + x^10 + x^8 + x^7 +x^5 + x^4 + x^2 + x+1
eli bitteinä 1 0000 0100 1100 0001 0001 1101 1011 0111. Huomaa, että tässä on 33 bittiä, jolloin tarkistussumman pituus on 32.

Niille joita virheentarkistus kiinnostaa enemmänkin, niin muita stardardoituja virittäjäpolynomeja on lueteltu englanninkielisen wikipedian sivulla [CRC: Polynomial representations](https://en.wikipedia.org/wiki/Cyclic_redundancy_check#Polynomial_representations_of_cyclic_redundancy_checks). Pariteettibitti voidaan luokitella triviaaliksi 1-bittiseksi CRC:ksi.

CRC:ssä käytettävä polynomi kuvaa virheiden jakautumista. Hyvin valittu virittäjäpolynomi maksimoi virheiden havaitsemisen samalla, kun minimoidaan kaikki ylimääräinen tarkistus. Tietyllä virittäjäpolynomilla voidaan havaita virheryöpyt, joiden pituus on pienempi tai korkeintaan yhtäsuuri kuin virittäjän pituus. Tätä pidemmätkin virheryöpyt voidaan todennäköisesti havaita, mutta huonolla tuurilla osa niistä saattaa myös jäädä havaitsematta. Siksi edellä esimerkissä käyttämämme 4:n pituinen virittäjäpolynomi ei ole riittävän hyvä todelliseen käyttöön, vaan tarvitaan pidempiä polynomeja. Ethernet käyttää 33:n pituista virittäjäpolynomia, jolla havaitaan riittävän luotettavasti ethernet-kehysten virheet.



<quiz id='a7f4eab5-85bf-4b65-b403-de05c901a730'></quiz>




---
path: '/osa-5/3-vuorojen-jakelu'
title: 'Lähetysvuorojen jakelu'
hidden: false
---

<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata yleisellä tasolla, miten kanavan jakaminen ja lähetysvuorojen jakelu voidaan tehdä.
- Osaat esitellä erilaisia lähetysvuorojen jakeluun liittyviä periaatteellisia ongelmia sekä joitakin niihin liittyviä ratkaisuja
- Tunnistat mm. lyhenteet TDMA, FDMA, CDMA, CSMA/CD, CSMA/CA, jne.
- Osaat simuloida Ethernetin käyttämää lähetysvuorojen jakelumenetelmää erilaisissa tilanteissa.

</text-box>

## Yhteiskäyttöinen kanava ja lähetysvuorojen jakelu

Kanava, jolla lähettäjän ja vastaanottajan välinen viesti kulkee, voi olla joko oma tai jaettu. Omaa kanavaa kutsutaan kaksipisteyhteydeksi (engl. point-to-point), koska siinä on vain kaksi päätä lähettäjä ja vastaanottaja. Jos kanava on jaettu, niin silloin se on yleislähetysyhteys (engl. broadcast), jossa voi olla useita lähettäjiä ja vastaanottajia. Kaksipisteyhteys on esimerkiksi tähtiverkon yksi haara eli parikaapeli kytkimen ja isäntäkoneen (engl. host) välillä. Myös puhelinverkossa esimerkiksi kahden modeemin välinen yhteys on kaksipisteyhteys. [Point-to-Point Protocol (PPP)](https://fi.wikipedia.org/wiki/PPP_(tiedonsiirtoprotokolla)) on suunniteltu nimeomaan käytettäväksi tällaisilla yhteyksillä. Nykyisin ethernet on paljolti syrjäyttänyt sen, koska modeemien käyttö on vähentynyt ja ethernet-pohjaisten laajakaistayhteyksien käyttö lisääntynyt.

Langaton verkko, väylätopologia ja toisinaan myös tähtitopologia ovat yleislähetysyhteyksiä, koska kaikki voivat lähettää ja kaikki vastaaottajat kuulevat kaiken tai lähes kaiken kanavassa kulkevan liikenteen. Yleislähetysyhteydessä meillä on yksi jaettu kanava, jota kaikki kuuntelevat. Lähetys onnistuu virheettömäasti vain jos yksi lähettäjä lähettää kerrallaan. Jos useampi lähettäjä lähettää samanaikaisesti, niin syntyy yhteentörmäys, jolloin viestien signaalit sekoittuvat ja vastaanottajalle saapuu epämääräistä "bittimössöä". Vastaanottaja ei pysty tästä mössöstä enää erottamaan yhtään yksittäistä virheetöntä viestiä, vaan kaikki törmänneet viestit tuhoutuvat ja ne täytyy lähettää uudelleen. Meidän täytyy siis rakentaa mekanismi, jolla varmistetaan, että vain yksi lähettäjä kerrallaan lähettää.

Kanavan lähetysvuorojen jakelusta käytetään useita erilaisia englanninkielisiä termejä, ainakin channel access method, multiple-access protocol ja media access control (eli MAC). Niminä ne korostavat vuoronjaon eri ominaisuuksia. Suomen kielen termi 'lähetysvuorojen jakelu' on muuten kuvaava, mutta se ei valitettavsti ota kantaa siihen, että usein kyse on nimenomaan lähettäjällä tapahtuvasta päätöksenteosta. Englanninkieliset termit korostavat nimenomaan siitä, että kyse on lähettäjän tai viestin pääsystä (access) kanavalle.

Vuoronjakomenetelmää suunniteltaessa on siis päätettävä, miten solmu päättelee voiko se lähettää ja kuinka solmun on toimittava törmäystilanteessa. Huomaa, että tietoliikenteessä meillä on käytettävissä vain tämä yksi kanava, jolloin kaikki tarvittava neuvottelu lähetysvuoroista käydään tässä yhdessä ja samassa kanavassa, jossa myös dataviestit kulkevat. Neuvotteluissakin lähetetään ja vastaanotetaan viestejä, joiden lähetysvuoroista pitäisi sopia. Tässä siis sekä kontrolli (engl. control) että data kulkevat samassa kanavassa.

Yhteiskäyttöisen kanavan vuoronjakomenetelmä valitaan siten, että saamme mahdollisimman suuren osan kanavasta hyötykäyttöön. Tällöin menetelmän aiheuttama yleisrasite on pieni ja lähetysvuoroista sopiminen tehdään kustannustehokkaasti. Menetelmä on tällöin yleensä myös yksinkertainen ja halpa toteuttaa.

Kun kanavassa on vain yksi lähettäjä kerrallaan, se pystyy hyödyntämään kanavan koko siirtonopeuden eli siirtämään tietoa kanavan 'maksiminopeudella' R bittiä sekunnissa. Pidemmällä aikavälillä tarkasteltuna, kun meillä on M lähettäjää, niin jokainen niistä saa keskimäärin saman osuuden linjan siirtonopeudesta eli R/M bittiä sekunnissa.

Vuoronjakomenetelmän keskeinen ongelma onkin se, että miten voimme varmistaa, että yksi lähettäjä ei voi kaapata kanavaa itselleen, vaan että kaikilla lähettäjillä on tasapuolisesti mahdollisuus saada kanava käyttöön ja lähettää viesti sitä pitkin. Haluamme siis välttää yksittäisen lähettäjän nälkiintymisen (engl. starvation). Tietojenkäsittelytieteessä yleisesti nälkiintyminen tarkoittaa, että kyseinen entiteetti (tässä sanoman lähettäjä) ei saa koskaan tarvitsemaansa resurssia (tässä kanava). Jotta nälkiintymistä ei tapahdu, niin kanavanjako menetelmän täytyy olla tasapuolinen. Toisaalta myöskään lukkiutumista (engl. deadlock), eli että mikään lähettäjä ei voisi enää lähettää, ei saa esiintyä. Menetelmän pitää siis olla kaikilta ominaisuuksiltaan hyvin toimintavarma.


Lähetysvuorojen jakaminen yhdellä kanavalla voidaan tehdä usealla eri tavalla. Kanavanjakoprotokollilla (engl. channel partitioning protocols) voimme jakaa kanavan osiin ja antaa yhden osan yhden lähettäjän käyttöön. Vuorotteluprotokollilla (engl. taking-turns protocols) voimme jakaa käyttövuorot ennalta sovitun periaatteen mukaisesti vuoronperään eri lähettäjille. Kilpailuprotokollilla (engl. random access protocols) lähettäjät joutuvat kilpailemaan lähetysvuorosta. Vuorot jakautuvat niille satunnaisemmin ja lähetysvuoron odottamiseen kuluva aika on vaikeammin ennustettava.

### Kanavanjakoprotokollat

Kanavan jaolla annetaan jokaiselle lähettäjälle oma pala kanavasta. Lähettäjä saa tässä palasessa lähettää omia viestejä ilman, että muiden lähettäjien viestien signaalit häiritsevät lähetystä. Näin kukin solmu saa oman viipaleensa. Voimme jakaa kanavan paloihin ajan tai taajuuden perusteella. Lisäksi on mahdollista käyttää erilaisia bittien koodaustapoja, jolloin samassa kanavassa voidaan samanaikaisesti lähettää useita eri viestejä, jotka vastaanottaja pystyy edelleen erottamaan toisistaan.

Tässä siis oleellista on se, että lähettäjän käyttäessä sille varattua osaa kanavasta, ei yhteentörmäyksiä tapahdu, jolloin kyseinen osa kanavasta on aina lähettäjän käytettävissä. Näin kyseinen osa kanavasta on varattuna tälle lähettäjälle silloinkin, kun se ei sitä tarvitse.

Aikaviipaloidussa kanavassa, ns. [aikajakokanavointi](https://fi.wikipedia.org/wiki/TDMA) (engl. time-division multiple access, TDMA), jaetaan tietty aikajakso vakiokokoisiin aikaviipaleisiin siten, että aikaviipaleen pituus on yhden kehyksen lähetysaika ja jokainen lähettäjä saa (yhden) aikaviipaleen kerran tämän pidemmän aikajakson kuluessa.

<img src="../img/1-4-aikajako-vs-taajuusjako.svg" alt="">

KUVA:  Kanava jaettu aikaviipaleisiin ja niissä lähettäjät. Vieressä on sama kanava, mutta nyt taajuusjaoteltuna

[Taajuusjakokanavoinnissa](https://fi.wikipedia.org/wiki/FDMA) (eng. Frequency division multiple access, FDMA) jaetaan ajan sijasta käytettävää taajuusaluetta. Tämä muistuttaa esimerkiksi radio- tai tv-kanavien jakoperustetta, kun kyseessä on radiosignaalia käyttävä lähetys. Tässä jokaiselle lähettäjälle varataan kiinteä taajuusalue (fixed frequency band), joka on vain osa koko kanavan taajuusalueesta. Koska taajuusalue varataan yhdelle lähettäjälle, niin sitä eivät muut voi käyttää sinä aikana kun varaus on voimassa. Näin, jos lähetettävää ei kyseisellä lähettäjällä ole, niin se osa kanavan kapasiteetistä jää käyttämättä, vaikka muilla olisikin lähetettävää.

Sekä aikajaossa että taajuusjaossa lähettävä solmu (tai asema) saa käyttöönsä vain osan kanavan kapasiteetista. Jos kanavan kapasiteetti R bittiä sekunnissa jaetaan tasan kaikille M:lle lähettäjälle niin jokainen voi lähettää keskimäärin R/M bittiä sekunnissa, jos se käyttää kaikki sille varatut osat kanavasta.

[Koodijakokanavoinnissa](https://fi.wikipedia.org/wiki/CDMA) (engl. code division multiple access, CDMA) voidaan koko kanavan kapasiteetti antaa kaikkien lähettäjien käyttöön samanaikaisesti. Tätä käytetään lähinnä radiotiellä, jossa jokaisella asemalla on yksilöllinen (ja muiden kanssa ortogonaalinen) tapa koodata bitit 1 ja 0. Nyt kaikkien asemien lähettämät signaalit voivat vapaasti sekoittua radioaalloilla. Vastaanottajan pitää vain tietää, millä koodauksella sille tulevat viestit on koodattu ja se voi tämän avulla erotella saapuvasta yhteissignaalista itselleen kuuluvat bitit.


### Vuorotteluprotokollat

Vuorotteluprotokollia (engl. taking-turns protocols) kutsutaan myös vuoronantoprotokolliksi, koska niille on tyypillistä se, että kanavan käyttövuorot jaetaan jollakin etukäteen sovitulla tavalla (kuten vuorokysely tai vuoromerkki), mutta vain niille, joilla on jotain lähetettävää. Näin vältetään kanavan pitäminen turhaan varattuna. Toisaalta, kun lähettäjällä on lähetysvuoro, niin kaikki tietävät sen, eikä viestien yhteentörmäyksiä kanavassa pääse syntymään.

Vuorokyselyssä erityinen isäntäsolmu kyselee vuorotellen (engl. polling) jokaiselta solmulta, onko sillä lähetettävää. Jos solmulla on lähetettävää se voi kyselyn saatuaan lähettää yhden viestin. Isäntä kuuntelee signaalia ja osaa päätellä milloin lähetys loppui. Sitten se kysyy seuraavalta vuorossa olevalta solmulta, onko sillä lähetettävää. Näin lähetysvuoro kiertää solmulta toiselle.

Vuoromerkkiä (engl. token) voidaan käyttää vuoroja jakavan isäntäsolmun sijaan. Se soveltuu erityisesti rengastopologiaan. Kun solmulla on vuoromerkki, se saa lähettää viestin, jonka jälkeen se antaa vuoromerkin renkaassa seuraavana olevalle solmulle. Jos solmulla ei ole lähetettävää, kun se saa vuoromerkin, se antaa merkin välittömästä eteenpäin. Näin kanavan kapasiteetti tulee käyttöön tehokkaammin kuin kanavanjakoon perustuvissa menetelmissä.

Näistä on olemassa erilaisia versioita, joissa voidaan määritellä tarkemmin esimerkiksi, miten kauan vuoromerkkiä saa pitää, kuinka monta kehystä yhdessä vuorossa voi lähettää, jne. Esimerkiksi [Token Ring](https://fi.wikipedia.org/wiki/Token_Ring) on vuorottelua käyttävä verkko.

Näissä vuorottelumenetelmissä on yksi iso ongelma, ns. 'single point of failure'. Menetelmä toimii hyvin vain niin kauan kuin vuoromerkki tai kyselyjä hoitava isäntäkone ei katoa.  Jos tällainen vikaantuminen kuitenkin tapahtuu, niin mikään solmu ei voi lähettää kanavassa ja päädytään lukkiutuneeseen tilaan. Tästä voidaan toipua vain ensin havaitsemalla tilanne ja sitten joko valitsemalla uusi isäntäsolmu tai ottamalla käyttöön uusi vuoromerkki. Tällainen toipuminen on hidasta ja sen aikana viestit eivät kulje. Jätämme tällaisen hajautettujen järjstelmien yhteistoimintaan liittyvän asian tarkemman käsittelyn myöhemmille kursseille.



### Kilpailuprotokollat

Kilpailuprotokollista (engl. random access protocols) käytetään englanniksi myös termiä multiple access protocols. Lähettäjiä on useita ja ne kilpailevat lähetysvuoroista. Lähettäessään niiden pitää noudattaa tiettyjä sääntöjä, mutta etukäteen ei ole tiedossa milloin ja missä järjestyksessä lähettäjät voivat toimia. Periaatteena on siis yksinkertaisesti "kuka ensin ehtii".

Koska mitään keskitettyä jakoa tai vuorottelua ei ole, niin jokaisen solmun pitää itsenäisesti, pelkästään sen hetkisen paikallisen tiedon varassa, tehdä päätös viestin lähettämisestä tai lähetyksen viivästämisestä. Kun solmu haluaa lähettää, niin se ensin kuuntelee, onko joku muu solmu jo lähettämässä. Jos ei ole, niin solmu aloittaa oman lähetyksensä. Kaikki lähetykset tehdään aina kanavan täydellä nopeudella. Jos joku muu jo lähettää, niin solmu viivästää omaa lähetystään ja odottaa kanavan vapautumista.

Koska lähettäjät kilpailevat kanavasta, niin on mahdollista, että kaksi lähettäjää yrittää lähettää samaan aikaan ja tapahtuu yhteentörmäys. Mikäli kahden lähettäjän viestit ovat kanavassa samaan aikaan, niin kumpikin viesti tuhoutuu, koska niiden signaaleja ei voi sekoittumisen jälkeen enää erottaa. Kun tällainen viestien törmäys tapahtuu, niin molemmat lähettäjät joutuvat lähettämään omat viestinsä myöhemmin uudelleen.

Solmun pitää tavalla tai toisella havaita törmäys. Tässä suhteessa eri protokollat toimmivat eri tavalla. Niissä on myös eroja siinä, miten törmäyksestä toivutaan eli miten ja milloin uudelleenlähetys tapahtuu. Tyypillisesti törmäyksen jälkeen solmu odottaa satunnaisen (engl. random) ajan ja yrittää sitten uudelleen.


#### Aloha ja viipaloitu aloha

Aloitetaan historiasta ja ihan ensimmäisestä langattoman verkon lähetysvuorojen jakoprotokollasta, jonka nimi on [ALOHA](https://en.wikipedia.org/wiki/ALOHAnet). Vaikka ALOHA kehitettiin nimenomaan langatonta radioteitse tapahtuvaa viestintää varten 1971 Havaijilla, niin sitä käytettiin myös kaapeliyhteyksillä.

Alkuperäinen ALOHA ei ollut kovin tehokas, koska jokainen solmu sai lähettää viestin heti, kun sillä oli lähetettävää. Se ei siis  etukäteen kuunnellut onko radiotiellä jo viesti kulkemassa. Solmu kuunteli vasta lähetyksen jälkeen onnistuiko lähetys. Jos törmäys tapahtui, niin solmun piti odottaa satunnainen aika ja yrittää sitten uudelleen.

Koska solmut eivät kuunnelleet etukäteen ja koska viestien pituutta ei ollut rajoitettu, niin alkuperäisessä ALOHAssa törmäyksen todennäköisyys oli niin suuri, että vain noin 18% kanavan koko kapasiteetista saatiin käyttöön. Suurin osa kanavan kapasiteetista kului siis törmäysten vuoksi hukkaan. Katso tuolta englanninkielisestä wikipediasta kuvia, joista selviää miksi yhteentörmäykset vievät noin suuren osan kanavan kapasiteetista.

<quiz id="b56f937e-907b-492f-8314-efd73978c244"> </quiz>


ALOHAsta tehtiin paranneltu versio, jossa karsittiin osittain päällekkäiset yhteentörmäykset pois. Viipaloidussa ALOHAssa (engl. slotted ALOHA) kaikki siirrettävät kehykset ovat keskenään samankokoisia. Lisäksi kanava jaettiin aikaviipaleisiin siten, että yhdessä aikaviipaleessa voi lähettää yhden kehyksen. Nyt kaikki solmut aloittavat lähetyksensä aina aikaviipaleen alusta eikä kesken toisen solmun lähetystä. Tämä onnistui, kun solmut ja niiden kellot saatiin synkronoitua. Kaikki (lähettävät) solmut havaitsevat yhteentörmäykset.

Kun siirtokehys on valmis, niin solmu lähettää sen heti seuraavassa aikaviipaleessa. Jos ei tullut yhteenörmäystä, niin solmu voi lähettää seuraavan kehyksen heti seuraavassa aikaviipaleessa. Jos lähetyksessä tuli yhteentörmäys, niin solmu yrittää lähetystä uudelleen seuraavassa aikaviipaleessa jollakin todennäköisyydellä p.

Viipaloidulla ALOHAssa saadaan kanavan kapasiteetista käyttöön noin 37%, mikä on kaksinkertainen määrä alkuperäiseen ALOHAan verrattuna. Englanninkielisessä wikipediassa on hyvin kuvattu matemaattinen päättelyketju tämän tehokkuusluvun laskennassa.

Viipaloitua ALOHAa käytetään edelleen tietyissä erikoistilanteissa, koska se on toteutukseltaan ja toiminnaltaan hyvin yksinkertainen ja koska se sallii yhden lähettäjän lähettää täydellä nopeudella, jos muita lähettäjiä ei samanaikaisesti ole.

Wikipedian englanninkielisellä [ALOHAnet](https://en.wikipedia.org/wiki/ALOHAnet) sivulla on hyvä kuva viipaloidun ALOHAn toiminnasta useamman lähettäjän kanssa. Kuvassa on sekä yhteentörmäyksiä että onnistuneita lähetyksiä.

<quiz id="ac4463e7-892e-470d-bb03-e3b8788683be"> </quiz>




### Lähetyskanavan kuuntelu CSMA

[Lähetyskanavan kuuntelu](https://en.wikipedia.org/wiki/Carrier-sense_multiple_access) (engl. Carrier Sense Multiple Access, CSMA) on ALOHAn jälkeen kehitetty menetelmä, jossa keskeistä on, että lähettäjän täytyy ennen omaan lähetystään varmistaa, että kanava on tyhjä. Ajatus on siis, että solmu kuuntelee kanavaa ennen kuin lähettää ja lähettää vain, jos kanava on tyhjä. Jos kanava on tyhjä, niin voi lähettää samantien. Jos kanava on varattuna, niin solmun pitää odottaa hetki ja sitten voi yrittää uudelleen. Odotuksen kesto riippuu CSMAn toteutusvaihtoehdosta. Aika tavallista on odottaa satunnainen aika ja sitten tarkistaa, onko kanava vapaa. Odottaminen voi myös olla aktiivista, jolloin solmu aktiivisesti kuuntelee kanavan vapautumista ja lähettää heti, kun kanava on vapaa.

Etukäteen tapahtuvalla kanavan kuuntelulla ei kuitenkaan voi havaita kaikkia muiden lähetyksiä ainakaan riittävän nopeasti, joten yhteentörmäykset ovat edelleen mahdollisia. Esimerkiksi kaapelissa etenemisviiveen takia kaksi lähettäjää voivat molemmat havaita kanavan tyhjäksi ja aloittaa lähetyksen samaanaikaan. Langattomassa lähiverkossa lähettäjän ympäristön kuuntelu ei kerro, onko vastaanottaja saamassa sanomia muilta, joita lähettäjä ei voi etäisyyden takia kuulla. Vastaavasti satelliittikanavan kuuntelu ei paljasta, onko jonkin muu maa-asema jo aloittanut lähetyksen. Huomaathan, että sateelliittien kautta tapahtuvassa viestinnässä etenemisviiveet voivat olla hyvinkin suuria.

Mikäli yhteentörmäys tapahtuu, niin pakettien lähetykset epäonnistuvat ja ne joudutaan lähettämään uudelleen. Tällöin paketin lähettämiseen käytetty aika menee hukkaan. Solmujen väliset etäisyydet ja etenemisviiveet vaikuttavat yhteentörmäysten todennäköisyyteen, koska jos solmu ei voi havaita toisen solmun jo aloittamaa lähetystä, niin se voi aloittaa oman lähetyksensä samaan aikaan tuon toisen solmun kanssa.

CSMA:sta on useita erilaisia versioita esimerkiksi CSMA/CA (engl. Collision Avoidance, CA), jossa pyritään ensi sijaisesti välttämään törmäyksiä. Törmäysten välttämistä käytetään mm. WLANien käyttämässä standardissa [IEEE 802.11](https://fi.wikipedia.org/wiki/IEEE_802.11). Langattomassa liikennöinnissä solmun on vaikea samaan aikaan sekä lähettää että kuunnella mahdollista yhteentörmäystä. Sen takia siinä pyritään ensi sijaisesti välttämään törmäyksiä. Tämä voidaan tehdä esim. lähettämällä varaussignaali ennen varsinaista kehystä tai kuten IEEE 802.11:sta odottamalla satunnainen aika vapaata kanavaa seuraten ennen varsinaista lähetystä. Näin, jos kaksi solmua haluaa lähettää samaan aikaan, on todennäköistä, että toinen niistä aloittaa ensin ja toinen havaitsee lähetyksen eikä yritä lähettää päälle, vaan joutuu odottamaan pidempään.

Ethernetissä käytetään [CSMA/CD:tä](https://fi.wikipedia.org/wiki/CSMA/CD) (engl. Collision Detection). Siinä solmu voi aloittaa lähettämisen heti, kun se havaitsee kanavan olevan vapaana, mutta sen täytyy samanaikaisesti kuunnella kanavaa, jotta se voi havaita yhteentörmäyksen. Koska liikennöinti tapahtuu kaapelissa, niin voimme olla varmoja, että solmu voi havaita yhteentörmäyksen. Havaitseminen voidaan tehdä esimerkiksi signaalin voimakkuuden muutoksesta. Langattomassa verkossa törmäystä ei aina voida havaita, koska lähettäjät eivät välttämättä voi kuulla toisiaan esimerkiksi liian suuren etäisyyden aiheuttaman signaalin vaimenemisen vuoksi.

CSMA/CD:ssä solmun pitää keskeyttää kehyksen lähettäminen heti (minimipituuden jälkeen), jos se havaitsee törmäyksen. Tällä nopealla keskeytyksellä pienennetään törmäyksen aiheuttaa hukka-aikaa ja lyhennetään kanavan varauksen kestoa. Näin yhteentörmäyksestä toivutaan hiukan nopeammin, kuin jos solmut lähettäisivät kehyksen kokonaan. Tämä on CSMA/CD:n keskeinen ero perus-CSMA:han, jossa solmu saa lähettää koko kehyksen, vaikka se olisi havainnut törmäyksen.

Jos kehyksen lähetys epäonnistui törmäyksen vuoksi, niin solmu odottaa satunnaisen ajan ja yrittää lähettämistä sen jälkeen uudelleen. Tällöinkin se voi lähettää vasta, kun kanava on vapaa.

Iso kysymys erityisesti CSMA/CD:ssä on, että kuinka paljon pitää vähintään lähettää ja toisaalta, kuinka kauan on kuunneltava oman lähetyksen aloituksen jälkeen. Ajatellaan, että A:n ja B:n etäisyys on kyseisessä kaapelissa mahdollisimman suuri. Tällöin ne ovat kaapelin eri päissä. Vaikka A on jo aloittanut lähettämisen, niin B kuulee vielä hetken aikaa tyhjän kanavan ja voi aloittaa oman lähetyksensä. Tämä aika on etenemisviive A:lta B:lle. Jotta A voi havaita törmäyksen, niin sen pitää kuulla B:n lähetys, johon menee vielä toinen etenemisviive. Näin ollen pisin aika, jonka kuluessa mikä tahansa solmu voi havaita törmäyksen on 2 * etenemisviive solmujen välillä.  Varmistaakseen yhteentörmäyksen havaitsemisen solmu ei saa lopettaa omaa lähetystään ennen kuin törmäysignaali olisi ehtinut tulla. Näin ollen pienin sallittu lähetettävän kehyksen koko on se, jonka lähettäminen kestää vähintään 2 kertaa kaukaisimpien laitteiden välisen maksimietenemisviiveen verran. Näin ethernet-kehyksen minimikoko rajoittaa yhden linkkivälin ethernet-kaapelin pituutta.

Solmun, tai oikeammin sen verkkosovittimen (verkkokortti ja sen laiteohjain), toimenpiteet kehyksen lähetyksessä, kun noudatetaan CSMA/CD:tä:
1) Verkkosovitin saa kehyksen välitettäväksi.
2) Jos verkkosovitin havaitsee, että kanava on tyhjä, niin se aloittaa kehyksen lähetyksen samantien. Jos se havaitsee, että kanava on käytössä, niin se odottaa kunnes kanava on tyhjä ja aloittaa sitten kehyksen lähetyksen.
3) Kun kehyksen lähetys on käynnissä, verkkosovitin kuuntelee kanavaa ja pyrkii havaitsemaan jonkun muun lähettämän signaalin.
4) Jos verkkosovitin havaitsee signaalin, niin se lopettaa kehyksen lähettämisen (vaaditun minimikoon jälkeen).
5) Jos kehyksen lähetys päättyy, eikä muiden signaaleja ole kuultu, niin kehyksen lähetys on onnistunut.
6) Jos kehyksen lähetys päättyi keskeytykseen, niin verkkosovitin odottaa satunnaisen ajan ja jatkaa kohdasta 2.

Tuo verkkosovittimien satunnainen odotusaika kasvaa jokaisen peräkkäisen yhteentörmäyksen yhteydessä. Tästä käytetään englanninkielistä termiä binary exponential backoff. Odotusaika valitaan satunnaisesti kokonaislukujen joukosta {0,1,2,... (2^n)-1}, missä n on peräkkäisten yhteentörmäysten määrä.

Huomaathan, että verkkosovittimien toiminta on täysin riippumatonta aiempien viestien onnistumisesta ja muiden verkkosovittimien toiminnasta. Tällöin on täysin mahdollista, että verkkosovitin, joka juuri sai kehyksen välitettäväksi, saa kehyksensä välitettyä sillä aikaa, kun muut yhteentörmäysten jälkeen odottavat seuraavaa lähetysyritystä.

<quiz id="a349c4e9-8207-4fb2-82cb-d7d9ea386496"> </quiz>




---
path: '/osa-5/4-kytkin'
title: 'Kytkin'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata kytkimen toiminnan ja miten se eroaa reitittimen ja keskittimen/toistimen toiminnasta
- Osaat kertoa miten kytkin pitää kirjaa aliverkon laitteista ja miten se tietää missä osassa aliverkko laite sijaitsee.

</text-box>


## Keskitin, kytkin ja reititin

Kytkin, keskitin ja reititin on valitettavan helppo sekoittaa toisiinsa, koska niitä kaikkia käytetään yhdistämään tietoliikenneverkon eri osia toisiinsa. Muistathan, että reititin toimii verkkokerroksella. Tästä eri kerroksilla toimimisista on se seuraus, että kun reititin vastaanottaa paketin se purkaa siitä pois linkkikerroksen kehyksen ja tarkastelee esiin kuorittua IP-pakettia. Sen jälkeen se lähettää paketin edelleen haluttuun suuntaan. Tässä vaiheessa IP-paketti kääritään uuteen linkkikerroksen kehykseen, jossa on tämän uuden kehyksen lähettäjän ja vastaanottajan osoitteet.

[Kytkin](https://fi.wikipedia.org/wiki/Kytkin_(tietoliikenne)) toimii linkkikerroksella, joten se käsittelee aina linkkikerroksen kehystä. Se siis toimii kehyksen otsakkeesta saamiensa tietojen mukaan. Näin ollen kytkin osaa tunnistaa laitteiden MAC-osoitteita, mutta ei IP-osoitteita. Koska kytkin sanana suomenkielessä on käytössä sekä valokytkimissä että auton vaihteistossa, niin tarvittaessa voidaan käyttää termiä tietoliikennekytkin tai verkkokytkin erotuksena näistä sanan muista käyttöyhteyksistä. Tietoliikennealan sisällä kuitenkin puhutaan yksinkertaisesti kytkimistä.

[Keskitin](https://fi.wikipedia.org/wiki/Keskitin) on usemmasta toistimesta muodostettu fyysisen kerroksen laite, joka yksinkertaisimmillaan vain toistaa yhdestä portista saamansa tiedon kaikkiin muihin portteihin. Tällaista viestin toistamista tarvitaan, koska pitkillä siirtoyhteyksillä signaalit vaimenevat, eivätkä ne välttämättä olisi enää perillä tunnistettavia. Matkan varrelle sijoitetut toistimet (engl. repeater) generoivat saamansa signaalin uudelleen ja näin vahvistavat sen tasoja ja samalla poistavat häiritsevää taustakohinaa.

Keskitin siis toistaa saamansa signaalit sellaisenaan kaikkiin ulosmeneviin yhteyksiin. Se ei voi muuttaa signaalin nopeutta, joten se soveltuu yhdistämään vain saman teknologian samalla nopeudella toimivia verkon osia toisiinsa. Keskittimet eivät näy linkkikerrokselle, joten ne voivat pidentää viestin kulkuaikaa kyseisellä yhteydellä ja näin lisätä etenemisviivettä kahden ko. yhteyttä käyttävän solmun välillä.


## Kytkin

Kytkin voi suodattaa liikennettä linkkikerroksen MAC-osoitteiden perusteella. Toisin kuin keskitin, niin se voi suodattaa (engl. filter) sen läpi kulkevia viestejä ja lähettää viestin vain siihen porttiin, jossa se vastaanottajan MAC-osoitteen perusteella tietää vastaanottajan olevan. Lisäksi useimmat kytkimet osaavat myös tilapäisesti puskuroida viestejä, jolloin ne voivat liikennöidä eri solmujen kanssa eri nopeuksilla, mutta kuitenkin samaa teknologiaa käyttäen, koska kytkin ei muuta kehystä millään tavalla.

Verkkokerroksen (eli reitittimien ja verkon ulkoreunoilla olevien solmujen) kannalta kytkimen toiminta on ihan yhtä näkymätöntä kuin keskittimien ja toistimien toiminta on näkymätöntä kytkimelle.

Koska kytkin suodattaa kehyksiä ja ohjaa saapuvan kehyksen vain siihen porttiin, jossa kehyksen vastaanottaja on, se pitää kirjaa näistä.  Sillä on oma kytkintaulu (engl. switch table), jonka se voi katsoa, mihin porttiin kehys pitää ohjata. Kytkin käyttää kehyksen ohjaukseen vastaanottajan MAC-osoitetta. Sillä on siis omassa kytkintaulussaan (MAC-osoite, porttinumero) -pareja, joista se voi tarkistaa, mihin suuntaa kyseinen kehys pitää ohjata.

Koska kytkimen pitää välittää kehykset samantien, niin sillä ei ole aikaa kysyä, missä päin verkkoa tietty MAC-osoite sijaitsee. Jos se ei löydä tietoa kytkintaulusta, niin se toimii kuten keskitin ja lähettää kehyksen kaikkiin portteihin, paitsi sinne mistä kehys tuli. Näin se tulvittaa (engl. flooding) kyseisen kehyksen kaikkialle verkossa ja voi olla varma, että vastaanottaja saa sen.

Omaa kytkintauluaan se päivittää saapuvien kehysten tiedoilla. Aina, kun sille saapuu välitettävä kehys, se tarkistaa kytkintaulusta vastaanottajan osoitteen lisäksi myös lähettäjän MAC-osoitteen. Jos lähettäjän MAC-osoitetta ei löydy kytkintaulusta, niin kytkin lisää tauluun lähettäjän MAC-osoitteen ja sen portin numeron, josta kehys saapui. Näin se oppii liikennettä seuraamalla, minkä portin takana tietyt MAC-osoitteet ovat. Tästä käytetään joskus termiä 'takaperin oppiminen' (engl. backward learning) korostamaan sitä, että toisin kuin yleensä tässä tarkastellaan lähettäjän tietoja ja päivitetään taulua niiden perusteella. Yleensä tietoliikenteessä ollaan kiinnostuneita vain vastaanottajasta, mutta kytkintaulun päivityksessä kiinnostavaa on nimenomaan lähettäjä.

Tästä vaiheittaisesta kytkintaulun päivityksestä on se hyöty, että kytkimeen voidaan helposti liittää uusia laitteita ja kytkin oppii itsenäisesti, missä portissa laite on. Jotta kytkintaulu pysyisi riittävän pienenä, niin kytkin poistaa kytkitaulusta käyttämättömiä tietoja, eli jos tietystä MAC-osoitteesta ei ole vähään aikaan liikennöity, niin se poistetaan.

Kytkin siis käsittelee kytkintauluaan seuraavasti aina kun sille saapuu kehys
- Onko lähettäjän MAC-osoite taulussa?
    on: päivitä aikaleima
    ei: lisää tauluun (MAC, porttinumero, aikaleima)
- Onko vastaanottajan MAC-osoite taulussa?
    ei:  tulvita (eli lähetä kaikkialle muualle paitsi tuloporttiin)
    on: Jos portti eri kuin tuloportti, niin lähetä ko. porttiin. Jos portti sama kuin tuloportti, niin unohda.

 <img src="../img/5-4-tahti.svg" alt="Kuvassa on tähtitopologiaan perustuva verkko, jonka keskipisteessä on kytkin. Kytkimeen tulee ainakin neljä yhteyttä, joista kaksi tulee suoraan solmulta ja kahdessa kytkin on ensin liitetty keskittimeen, joista toiseen on liitetty 2 ja toiseen 3 solmua. Näin meillä on verkon reunoilla kaikkiaan 7 laitetta ja keskemmällä kaksi keskitintä ja yksi kytkin. A ja B on kiinni keskittimessä H1. H1 ja C on yhdistetty kytkimeen K, H1 porttiin 1 ja C porttiin 2. Toisella puolella kytkintä portissa 3 on H2, jossa on kiinni solmut E,F ja G. Lisäksi kytkimessä on vielä kiinni solmu I portissa 4.">

KUVA: Kuvassa on yksi aliverkko, jossa on 1 kytkin ja 2 keskitintä. Keskittimet välittävät kaiken liikenteen niiden läpi ja kaikkiin niihin liitettyihin laitteisiin. Kytkin osaa eristää liikennettä linkkikerroksella.


Käydään läpi esimerkki tähän kuvaan ja sen solmuihin liittyen. Oletetaan ensin, että kytkimen kytkentätaulu on tyhjä. Solmu A lähettää nyt kehyksen solmulle B. A:n lähettämä kehys päätyy ensin keskittimelle, joka välittää sen kaikkiin suuntiin. Näin kehys päätyy sekä B:lle että kytkimelle. Koska kehys tulee kytkimelle, niin kytkin lisää kytkentätauluunsa, että solmu A on kytkimen portin 1 takana. Näin kytkin osaa jatkossa välittää viestejä A:lle. Koska B:tä ei vielä löydy kytkimen kytkentätaulusta, niin kytkin välittää kyseisen kehyksen kaikkiin muihin suuntiin paitsi kytkimen porttiin 1, josta viesti tuli.  Kun B vastaa A:lle, niin viesti kulkee taas keskittimen H1 kautta ja päätyy sekä A:lle että kytkimelle. Nyt kytkin havaitsee omasta kytkentätaulustaan, että A on samassa portissa, josta viesti tuli, joten kytkin ei välitä viestiä minnekään.

Jos nyt seuraavaksi E lähettää kehyksen B:lle, niin kehys päätyy kytkimelle keskittimen H2 kautta. Kun kytkin saa viestin, se lisää E:n omaan kytkentätauluunsa ja havaitsee taulusta, että viesti B:lle pitää laittaa porttiin 1. Kytkin siis lähettää viestin vain porttiin 1, jolloin kehys päätyy B:lle keskittimen H1 kautta. Koska B löytyi kytkintaulusta, niin kehystä ei tulviteta, joten sitä ei lähetetä muihin portteihin.

<quiz id="ac60ec2c-8945-4296-be47-e3de30133428"> <quiz>

Kehysten tulvituksen liittyy aina riski siitä, että kehys jää ikuisesti kiertämään verkossa. Näin voi tapahtua, jos verkon rakenteessa on silmukka. Tehdään tuohon äskeiseen esimerkkiin silmukka esimerkiksi yhdistämällä keskittimet H1 ja H2 toisiinsa joko suoraan tai uuden kytkimen avulla. Nyt jos kytkin lähettää kehyksen A:lle porttiin 1, niin keskittimet toistavat viestin ja se päätyy takaisin kytkimelle portista 3. Kytkin siis lähettää viestin uudelleen porttiin 1 ja näin meillä on ikuisesti verkossa liikkuva viesti. Tällainen silmukka pudottaa tehokkaasti verkon tehokkuutta, kun suurin osa siirrettävistä kehyksistä on näitä turhia jo moneen kertaan lähetettyjä.

Voimme välttyä silmukoilta muodostamalla tällaiseen verkkoon virittävän puun, jota pitkin kytkimet voivat siirtää kehyksiä. Tämä voidaan tehdä esimerkiksi reitityksen yhteydessä käsitellyllä linkkitila-algoritmilla. Silmukka on ihan yhtä hankala, onpa se reitittimien muodostamassa verkossa tai kytkinten muodostamassa verkossa. Samat periaatteet pätevät niihin molempiin. Verkkoja tutkitaan myös hyvin teoreettisesti, jotta niiden tällaiset yleiset ominaisuudet voidaan havaita ja niiden ratkaisemiseen kehittää yleisiä algoritmeja.

Jos käytössä on puhdas tähtitopologiaan perustuva verkko, niin sellaisessa ei silmukoita voi olla. Usein kuitenkin verkkojen ylläpitäjät lisäävät verkkoihin varareitteja, jotta verkon vikaantuessa vaihtoehtoisten reittien käyttöönotto olisi nopeampaa. Väärin konfiguroituna näistä varareiteistä voi valitettavasti muodostua verkon toimintaa haittaavia silmukoita.

Kytkimien ohessa saatetaan joskus puhua myös [silloista](https://fi.wikipedia.org/wiki/Silta_(tietoliikenne)). Kytkin on internetiin ja erityisesti ethernet-verkkoihin liittyvä termi. Silta on mikä tahansa kahta verkkoa linkkikerroksella yhdistävä laite, mutta nykyisin kun käytetään lähinnä ethernet-verkkoja, niin silta on terminä jäämässä taustalle. Silta-termiä käytetään erityisesti silloin, kun yhdistetään eri teknologioilla toimivia verkkoja toisiinsa nimenomaan linkkikerroksella. Kytkin, joka osaa useita eri ethernet-versioita, on myös silta.

Tyypillisesti termiin silta tai oikeastaan sen muunnokseen siltaus tai siltaava saattaa törmätä ADSL-modeemin tai muun verkkolaitteen yhteydessä. Tällainen laite voi olla joko reitittävässä tai siltaavassa tilassa. Tällöin käytännössä otetaan kantaa millä protokollapinon kerroksella laitteen halutaan toimivan. Reitittävä tila tarkoittaa sitä, että laite toimii verkkokerroksen reitittimenä ja suorittaa verkkokerroksen tehtäviä. Siltaava tila puolestaan tarkoittaa, että laite toimii kuin linkkikerroksen kytkin eli että se ei käsittele IP-pakettia lainkaan vaan lähettää kaikki verkkokerroksen paketit suoraan laitteen läpi kuten kytkin. Toki siltaavassa tilassa se ohjaa linkkikerroksen kehyksiä kytkimen tavoin oikeaan suuntaan, mutta se ei koske lainkaan verkkokerroksen sisältöön.

<quiz id="ae548f5f-8ad3-409b-9d39-e672a90ddcbe"> <quiz>





---
path: '/osa-5/5-toiseen-verkkoon'
title: 'Lähettäminen toiseen verkkoon'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kertoa mitä IP-paketin eteenpäin lähetyksessä tapahtuu verkkokerroksen ja linkkikerroksen yhteistoimintana
- Osaat kuvata miten IP-paketin käsittely reitittimen linkkikerroksella tapahtuu. Verkkokerroksen käsittely oli jo aiemmin.

</text-box>


## Paketin lähettäminen toiseen verkkoon

Olemme jo useammassa kohdassa kurssia tutustuneet reitittimen toimintaan eri näkökulmista. Nyt kun myös linkkikerroksen toiminnallisuus on käsitelty, niin voimme katsoa tätä myös linkkikerroksen näkökulmasta. Samalla voimme yhdistää kaikki kurssilla käydyt teemat ja tarkastella yksityiskohtaisesti, mitä tapahtuu kun reitittimelle saapuu paketti ja se lähettää sen eteenpäin toiseen aliverkkoon.


<img src="../img/5-5-verkkojen-valilla.svg" alt="Kuvassa on kaksi aliverkkoa, jotka on yhdistetty kolmannella reitittimen välisellä aliverkolla. Ensimmäisessä on A ja B, jotka on yhdistetty reitittimeen R1 ja toisessa reititin R2 on yhdistetty C:hen ja D:hen. Reitittimet on yhdistetty toisiinsa. A:n IP-osoite on 192.68.12.4 ja MAC-osoite 11-22-33-44-55-66. B:n IP-osoite on 192.168.12.6 ja MAC-osoite 77-88-99-AA-BB-CC. Reitittimillä on kaksi rajapintaa, joten niillä on myös useampia IP- ja MAC-osoitteita. aliverkon suuntaan R1:n IP-osoite on 192.168.12.1 ja MAC 12-12-12-12-12-12. Toisen reitittimen suuntaan R1:n IP-osoite on 111.111.111.1 ja MAC 12-12-12-12-12-13. Reitittimet yhdistävässä aliverkossa R2:n IP-osoite on 111.111.111.2 ja MAC 23-23-23-23-23-01. Aliverkon suuntaan R2:n IP-osoite on 10.0.0.1 ja MAC 23-23-23-23-23-03. C:n IP-osoite on 10.0.0.2 ja MAC A1-A1-A1-A1-A1-A1. D:n IP-osoite on 10.0.0.3 ja MAC 12-13-14-15-16-17.">

KUVA: Kuvassa on kaksi aliverkkoa ja niitä yhdistävät reitittimet. Kummallakin aliverkolla on oma reititin. Tällöin reitittimien välinen yhteys muodostaa vielä kolmannen aliverkon. Huomaa, että kaikki IP- ja MAC-osoitteet ovat muodoltaan oikeita, mutta tätä esimerkkiä varten keksittyjä. Lisäksi IP-osoitteet ovat yksityisverkon osoitteita, joita ei voi yleisessä internetissä käyttää.


Oletetaan, nyt että A haluaa lähettää yhden paketin D:lle. Tämä voisi olla vaikkapa UDP-paketti tai TCP-yhteyden aloittava ACK, mutta koska viestin sisältö on vain A:n ja D:n kannalta merkityksellinen, niin jätetään se tästä tarkastelusta pois. A siis laittaa kuljetuskerroksen segmentin IP-pakettiin, jossa lähettäjänä on A:n oma IP eli 192.162.12.4 ja vastaanottajana D:n IP eli 10.0.0.3. A näkee omasta reititystaulustaan, että tämä paketti pitää ohjata R1:lle, joka osaa käsitellä 10.x verkkoon menevät viestit. IP-paketti laitetaan siis kehykseen, jossa vastaanottajana on R1:den MAC-osoite ja lähettäjänä A:n MAC-osoite. Jos A ei syystä tai toisesta tiedä vielä R1:n MAC-osoitetta, niin se kysyy tiedon ARP-protokollalla.


<img src="../img/5-5-kehys1.svg" alt="Kehys, jonka sisällä IP-paketti. Kehyksessä vastaanottajana R1:n MAC osoite, lähettäjänä A:n MAC osoite. Kehyksen sisällä olevassa IP-paketissa lähettäjänä A:n IP-osoite ja vastaanottajana D:n IP-osoite.">

KUVA: Kuvassa on A:n lähettämän kehyksen sisältöä. Tämän esimerkin kannalta meitä kiinnostavat erityisesti osoitteet sekä kehyksessä että IP-paketissa. Muut otsakkeen kentät ja data on jätetty tässä tyhjiksi.

Kun tämä A:n D:lle osoittama viesti saapuu reititin R1:lle, niin R1 on linkkikerroksen osoitteen mukaan kehyksen vastaanottaja, joten kehys otetaan vastaan ja annetaan kehyksen sisällä oleva IP-paketti reitittimen verkkokerroksen tarkasteltavaksi. Tästä IP-paketista reititin voi nähdä lopullisen vastaanottajan IP-osoitteen. Reititin katsoo omasta reititystaulusta, mihin suuntaan kyseiselle IP-osoitteelle lähetettävä paketti pitää ohjata. Tässä tapauksessa siis paketti pitää lähettää edelleen R2:lle, jonka takaa löytyy 10.x osoitteet.

R1 lisää nyt tämän IP-paketin, jossa lähettäjänä on A ja vastaanottajana D, ympärille uuden kehyksen. Kehyksessä vastaanottajan osoite on R2:n MAC-osoite ja lähettäjänä on R1:n MAC-osoite. Näin koska linkkikerroksella tämän kehyksen lähettäjä on R1 ja kehys on menossa R2:lle, joten ne ovat kehyksessä lähettäjänä ja vastaanottajana.

<img src="../img/5-5-kehys2.svg" alt="Kuvassa on kehys, jonka sisällä on IP-paketti. Kehyksessä vastaanottajana on R2:n MAC-osoite ja lähettäjänä R1:n MAC-osoite. Kehyksen sisällä olevassa IP-paketissa lähettäjän on edelleen A:n IP-osoite ja vastaanottajana D:n IP-osoite.">

KUVA: R1:n lähettämä kehys, joka on menossa R2:lle. Huomaa, että kehyksessä lähettäjänä on R1 ja vastaanottajana R2, mutta kehyksen sisällä olevassa IP-paketissa lähettäjänä on edelleen A ja vastaanottajana D.


Kun paketti aikanaan saavuttaa D:n, niin silloin kaikki kerrokset käsitellään vuorollaan alhaalta ylöspäin. Eli linkkikerros poistaa ensin oman kehyksensä, koska viesti oli tulossa tälle laitteelle. Verkkokerros tarkistaa vastaanottajan IP:n ja päättää että viesti on nyt perillä eikä sitä tarvitse enää lähettää eteenpäin. Se purkaa sitten IP-paketin ja antaa sisältä löytyvän segmentin kuljetuskerrokselle. Kuljetuskerros puolestaan välittää varsinaisen sovelluskerroksen viestin oikealle sovellukselle pistokkeen ja siihen liitetyn porttinumeron avulla.

<quiz id="abe1ee87-88e0-4090-8975-e336516dd15b"> </quiz>




---
path: '/osa-5/6-langaton'
title: 'Langaton verkko'
hidden: false
---


<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata langattomien verkkojen toimintaa ja ongelmia.
- Osaat kertoa, mikä on WLAN tai Wi-Fi ja miten viestit kulkevat sen ja langallisen verkon välillä.
- Tiedät mikä on tukiasema ja osaat kuvata sen perustoiminnan.

</text-box>

## Langaton verkko

Kaikille langattomille verkoille on yhteistä se, että käyttäjien laitteet (voidaan kutsua myös solmuiksi tai isäntäkoneiksi) ovat langattomasti yhteydessä verkon palvelut tarjoavaan tukiasemaan. Langaton linkki on tyypillisesti toteutettu radioaalloilla, jolloin kaikki tukiaseman läheisyydessä olevat laitteet voivat kuulla kaiken liikenteen. Toisaalta radioaallot vaimenevat etäisyyden kasvaessa, joten laitteen ja tukiaseman etäisyys on rajallinen. Tietoliikenteessä tästä puhutaan signaalin vaimenemisena. Signaalia (eli radioaaltoja) häiritsevät myös muiden laitteiden aiheuttamat häiriöt ja erilaisista pinnoista tapahtuvat heijastumiset. NÄiden seikkojen vuoksi kuuluvuus tukiaseman ja käyttäjän laitteen välillä voi vaihdella, vaikka molemmat laitteet olisivat paikallaan.

Langattomalle verkolle erityistä haastetta tuo kuitenkin käyttäjien laitteiden liikkuminen. Yhä useammin käytämme laitteita, joita kannetaan mukana ja jotka ovat yhdistettynä verkkoon myös liikkuessaan. Vaikka laite voi vaihtaa paikkaa myös langallisessa verkossa, niin se on siirtymisen aikana poissa verkosta. Langattomassa verkossa laite voi olla yhteydessä tukiasemaan myös silloin kun se liikkeessä.

Tällä hetkellä käytössä on kahden täysin erilaisen tekniikan avulla toteutettujan langattomia verkkoja. Ethernet-verkkoja mukailevia [WLAN](https://fi.wikipedia.org/wiki/WLAN)-verkkoja, jotka noudattavat jotain IEEE:n standardoimaa tiedonsiirtotapaa. [IEEE:n standardin 802.11](https://fi.wikipedia.org/wiki/IEEE_802.11) eri versiot määrittelevät erilaisia langattomia verkkotekniikoita langattoman lähiverkon toteuttamiseen. Osa laitteista ja tukiasemista tukee näistä vain yhtä ja osa tukee useampaa erilaista versiota. Nämä standardin eri versiot on nimetty kirjaimilla a-n.

Toinen yleinen langaton verkko on [matkapuhelinverkko](https://fi.wikipedia.org/wiki/Matkapuhelinverkko) ja erityisesti sen välityksellä käytettävä mobiilidata. Matkapuhelinverkkojen tekniikkakin on standardoitua. Koska nämä ovat puhelinverkkoja, niin niitä on alunperin standardoitu alueittain kuten langallisiakin puhelinverkkoja. Kaikenlaisia puhelinverkkoja standardoi [kansainvälinen televiestintäliitto ITU](https://fi.wikipedia.org/wiki/Kansainv%C3%A4linen_televiestint%C3%A4liitto). ITU keskittyy lähinnä eri operaattoreiden välisten asioiden säätelyyn. Operaattoreiden toiminta-alueilla on myös muita standardointiorganisaatioita, jotka vaikuttavat käytettäviin tekniikoihin. Nykyisessä globaalissa tilanteessa alueelliset standardointiorganisaatiot tekevät yhteistyötä [3GPP](https://fi.wikipedia.org/wiki/3GPP):ssä, jotta tulevat standardit olisivat mahdollisimman yhteensopivia eri puolilla maailmaa. Euroopassa näiden verkkojen standardoinnista vastaa [ETSI](https://fi.wikipedia.org/wiki/ETSI).

Matkapuhelinverkkojen, joita kutsutaan myös mobiiliverkoiksi, kehitystä on jaettu sukupolviin. Toisen sukupolven (2G) verkot käyttivät GSM-tekniikkaa. Sen jälkeen siirryttiin [3G](https://fi.wikipedia.org/wiki/3G)-verkkoihin. Nyt on jo käytössä [4G](https://fi.wikipedia.org/wiki/4G)-verkkoja, mutta ne eivät vielä ole käytettävissä kaikkialla. Tällä hetkellä standardointi kohdistuu tulevan 5G-verkon tekniikoihin. Tavoitteena on sekä nopeuttaa signaalin kulkua verkossa (pienentää etenemisviivettä) että samanaikaisesti lisätä siirrettävän datan määrää aikayksikköä kohti (eli kasvattaa verkon nopeutta).

Muita tunnettuja langattomia standardoituja verkkoja ovat [Bluetooth](https://fi.wikipedia.org/wiki/Bluetooth) ja [ZigBee](https://fi.wikipedia.org/wiki/ZigBee).

Tarkastelemme tällä kurssilla kuitenkin lähinnä WLAN-verkkojen toimintaa. Yleiset langattomaan liikennöintiin liittyvät seikat kuitenkin soveltuvat kaikille langattomille verkoille.


## Ad hoc -verkko

Langaton verkko voidaan rakentaa myös ilman tukiasemia. Tällöin puhutaan niin sanotuista ad hoc -verkoista, joiden toiminnallisuuden verkon rakentaja määrittelee täysin itsenäisesti. Tällaisen verkon ei tarvitse noudattaa mitään standardeja, mutta verkon toteuttajan on kuitenkin hyvä tietää kyseisen alueen radiotaajuuksien käyttösäännöt, jotta ei vahingossakaan syyllisty rikokseen.

Yksinkertaisimmillaan ad hoc -verkko on vain kahden laitteen välinen, jolloin laitteiden välinen liikennöinti tehdään langattomasti suoraan laitteelta toiselle.  Laajimmillaan tällaiset ad hoc -verkot voivat olla useiden satojen sensorien omia verkkoja. Näistä langattomista sensoriverkoista on hyvä kuvaus englanninkielisessä wikipediassa sivulla [wireless sensor networks](https://en.wikipedia.org/wiki/Wireless_sensor_network).

Ad hoc -verkon koneet voivat siis suoraan kommunikoida vain omalla kuuluvuusalueellaan olevien muiden koneiden kanssa, koska verkossa ei ole mitään palveluja suoraan tarjolla. Jos tällaisen verkon laitteen pitää kommunikoida kuuluvuusalueensa ulkopuolella olevien laitteiden kanssa, niin verkon pitää tarjota reititys näiden laitteiden välillä. Verkkoon voidaan toki toteuttaa myös vaikka oma nimipalvelu ja verkon laitteiden tunnisteiden jakelu. Jonkun on siis tuotettava nämä palvelun tällaisen satunnaisverkon käyttäjille.

Ad hoc -verkkojen käyttö tiettyihin spesifeihin tarkoituksiin on vuosien varrella selvitelty paljonkin. WLANin toteutuksessa käytetyllä tekniikalla toteutettujan ad hoc -verkkoja kutsutaan usein  [mobiileiksi ad hoc -verkoiksi](https://fi.wikipedia.org/wiki/Mobile_ad-hoc_network) (MANET). Autoja ajatellaan on myös pohdittu erityisten [vehicular ad hoc -verkkojen](https://en.wikipedia.org/wiki/Vehicular_ad-hoc_network) toiminnallisuutta. Näiden verkkojen erityispiirre on verkon solmujen suuri liikenopeus.

## Langattoman verkon ongelmia

Signaalin heijastuminen ja siitä aiheutuva viive voi pahimmillaan sekoittaa alkuperäisen suoraan menevän ja heijastunutta reittiä hiukan kauemmin kulkevan signaalin siten, että vastaanottaja ei pysty enää selvittämään viestin sisältöä tästä yhteissignaalista. Usein heijastunut signaali on kuitenkin vaimentunut sen verran, että alkuperäinen signaali erottuu vastaanottajan kannalta riittävästi.

Koska signaali kulkee ilmateitse, niin maaston muodot voivat jopa kokonaan estää signaalin kulkemisen vastaanottajalle. Langattoman verkon toimnnan kannalta signaalin esteetön kulku on välttämätöntä ainakin lähettäjän ja vastaanottajan välillä.

Langattomista verkoista on tunnistettu kaksi yleistä ongelmatilannetta, jota kutsutaan kätketyn aseman ja näkyvän aseman ongelmiksi.

Kätketyn aseman (engl. hidden terminal) ongelmassa kaksi laitetta yrittää samanaikaisesti viestiä kolmannelle. Nämä kaksi eivät kuitenkaan voi kuulla toistensa viestejä, koska ne eivät ole toistensa kuuluvuusalueella. Tämä voi johtua esimerkiksi maastoesteestä niiden välillä tai siitä, että ne ovat eri puolilla laitetta, jonka kanssa ne yrittävät kommunikoida.

<img src="../img/5-6-katketty-asema.svg" alt="Kuvassa on tukiasema ja kaksi sen kanssa kommunikoivaa laitetta A ja B. Kaikille laiteille on piirretty ympyränä niiden kuuluvuusalue.">

KUVA. Kuvassa havainnollistettu kätketyn aseman ongelmaa.

Näkyvän aseman (engl. exposed terminal) ongelmassa puolestaan laite kuulee toisen laitteen lähetyssignaalin ja jättää lähettämättä oman signaalinsa, vaikka signaalit eivät vastaanottajien kannalta mene sekaisin. Tällöin asemat ovat toistensa kuuluvuusalueella, mutta viestien vastaanottajat eivät kuulisi toisen aseman viestejä, joten niiden kannalta signaalien sekoittumista ei tapahtuisi.

<img src="../img/5-6-nakyva-asema.svg" alt="Kuvassa on kaksi tukiasemaa ja niiden välissä laitteet A ja B. A kommunikoi oman tukiasemansa kanssa ja B omansa. Tukiasemien kuuluvuus alueet eivät ole päällekkäin, mutta A ja B kuulevat oma tukiasemansa lisäksi myös toisensa.">

KUVA. Kuvassa havainnollistettu näkyvän aseman ongelmaa.

Molemmat ongelmat heikentävät verkon toimintaa. Kätketyn aseman tapauksessa molemmat lähetetyt viestit vaurioituvat ja ne pitää lähettää myöhemmin uudelleen. Näkyvän aseman tapauksessa taas kaistaa jää käyttämättä, vaikka viesti olisi mennyt virheettömästi perille.

Koska näitä ongelmia ei voi langattomista verkoista poistaa, niin useimmissa verkoissa edellytetään, että kaikki virheettömästi vastaanotetut viestit kuitataan jo linkkikerroksen kuittauksella. Muistathan, että kuljetuskerroksen TCP-protokollakin käytti kuittauksia viestien perillemenon varmistamiseen. Nyt kuittauksia käytetään linkkikerroksella varmistamaan, että viesti saatiin välitettyä onnistuneesti tämän yhden linkin yli. Kuittaukset lisäävät verkon liikennettä, mutta koska lähettäjällä ei langattomassa verkossa ole mahdollisuutta itse varmistua viestin perillemenosta, niin se joutuu turvautumaan vastaanottajan lähettämään kuittaukseen asian varmistamiseksi.


## WLAN / IEEE 802.11

IEEE 802.11 -tekniikalla toteutettu WLAN verkko on kotiverkoille tyypillinen langaton verkko. Myös yritysten omat sisäiset ja niiden asiakkailleen tarjoamat avoimet WLAN-verkot on toteutettu jollain IEEE 802.11 standardin versiolla.

Näistä verkoista ja niiden laitteista käytetään usein myös Wi-Fi nimitystä. Wi-Fi on rekisteröity tavaramerkki, jota hallinnoi Wi-Fi alliance (verkkosivu https://www.wi-fi.org/). Se myöntää yrityksille (maksua vastaan) oikeuden käyttää "Wi-Fi sertifioitu" -merkkiä yrityksen valmistamissa verkkolaitteissa.

IEEE 802.11 -verkkojen tukiasemat palvelevat kukin omaa erillistä joukkoa laitteita. Jokainen tukiasema on erikseen yhdistetty langalliseen verkkoon.  Jokainen laite kommunikoi vain yhden tukiaseman kanssa kerrallaan. Laite voi aika ajoin vaihtaa tukiasemaa. Jokaisella tukiasemalla on tunniste (Service Set ID, SSID) ja MAC-osoite. Tukiasema myös kommunikoi siihen liittyneiden laitteiden kanssa tietyllä kanavalla.

IEEE 802.11 jakaa käytettävän taajuusalueen (yleensä joko 2,4 gigahertsiä (GHz) tai 5 GHz) kanaviin, joita 2,4 GHx:n alueella on vähintään 11 (USA). Euroopassa kanavia on 13 ja Japanissa 14. Kanavilla varatut kapeat taajuuskaistat ovat limittäin (eli ne menevät osittain päällekkäin), jolloin vierekkäisillä kanavilla kommunikoivien laitteiden viestit voivat häiritä toisiaan. Kanavat 1, 6 ja 11 eivät ole keskenään päällekkäin, joten niitä voidaan käyttää vaikka laitteet kuulisivat toistensa viestejä.

Tukiaseman käyttämä kanava on konfiguroitavissa. Jos mahdollista, niin tukiaseman kanava kannattaa valita niin, että se on mahdollisimman kaukana sen kuulemien muiden tukiasemien kanavista. Näin kommunikointi tukiaseman ja siihen yhdistyneiden laitteiden välillä on mahdollisimman häiriötöntä.  Huomaa, että naapuritukiasemilla voi olla käytössä sama kanava. Tämä on yleisin syy siihen, että kotiverkon langaton tukiasema tuntuu pätkivän tai toimivan kovin hitaasti. Erityisesti kerrostaloissa tai kahviloissa tukiasema voi kuulla useiden muiden tukiasemien signaaleja. Jos niistä yksi tai useampia on samalla (tai hyvin läheisellä) kanavalla, niin ne eivät voi lähettää samaanaikaan, jolloin lähetyksiin tulee viiveitä. Ne voivat kyllä käyttää samaa kanavaa, mutta viestien lähetykset täytyy tehdä vuorotellen, jotta viestit voidaan vastaanottaa oikein. Jos siis havaitset ongelmia langattomassa liikenteessä, niin kannattaa tarkistaa, millä kanavilla kyseiseen kohtaan kuuluvat tukiasemat liikennöivät ja valita oman tukiaseman kanava mahdollisimman kauas muista sille kuuluvien tukiasemien kanavista.

Koska WLANissa ei ole mitään koordinointia, niin useiden tukiasemien samanaikaista kuulumista kutsutaan joskus Wi-Fi viidakoksi (engl. Wi-Fi jungle). Kun tällaisessa viidakossa yrittää yhdistää omaa tietokonettaan internetiin, niin valittavana voi olla useita langattomia lähiverkkoja ja niiden tukiasemia.

Kun laite haluaa tällaisessa usean tukiaseman viidakossa liittyä verkkoon, niin sen pitää kiinnittyä (engl. associate) yhteen tukiasemaan. Se siis rakentaa 'näkymättömän langan' itsensä ja tukiaseman välille. Kaikki laitteen liikennöinti tapahtuu vain ja ainoastaan tämän tukiaseman kanssa.

Ennen liittymistään laite voi vain passiivisesti hetken kuunnella liikennettä kaikilla kanavilla ja etsiä sieltä erityisiä merkkikehyksiä (engl. beacon frame). Niillä tukiasemat mainostavat itseään.  Merkkikehyksessä on tukiaseman tunniste (SSID, service set ID) ja MAC-osoite. Näiden perusteella laite voi sitten valita haluamansa tukiaseman.

Vaihtoehtoisesti laite voi ennen liittymistään aktiivisesti lähettää kyselykehyksen (engl. probe), johon tukiasemat sitten vastaavat. Kyselykehyksiä käytetään tyypillisesti silloin, kun laite on aiemmit jo käyttänyt jotain WiFi-verkkoa ja yrittää nyt liittyä uudelleen samaan verkkoon.

Standardit eivät millään tavalla määrittele kriteerejä, joiden mukaisesti laitteen pitäisi tukiasema valita. Laite saa tehdä valinnan haluallaan tavalla. Useimmiten laitevalmistajat käyttävät valintaperusteena signaalin voimakkuutta.

Kun laite on päättänyt, mihin tukiasemaan se haluaa kiinnittyä, niin se lähettää erityisen kiinnittymispyynnön (engl. association request frame), jonka tukiasema hyväksyy vastausviestillään. Nyt laite voi linkkikerroksen näkökulmasta liikennöidä muun verkon kanssa tukiaseman kautta, mutta ylempien kerrosten kannalta se ei vielä ole liittyneenä internetiin. Siltä puuttuu esimerkiksi vielä IP-osoite. Toki laitteen tarvitsemat varkkoyhteyteen liittyvät tiedot voi jo olla asetettuna laitteen konfigurointitietoihin, mutta yleensä langattomaan verkkoon liittyvä laite pyytää näitä tietoja DHCP-protokollalla.

Kuten monet avoimia Wi-Fi -verkkoja käyttäneet jo tietävätkin, niin monet palveluntarjoajat rajoittavat langattoman verkon käyttöä, jolloin tukiasemaan liittymisen yhteydessä voidaan edellyttää laitteen tai sen käyttäjän tunnistamista. Laitteen tunnistaminen voidaan tehdä käyttämällä ns. langattoman verkon salasanaa. Tällöin tukiasema hyväksyy kiinnittymispyynnön vain sellaisilta laitteilta, jotka osaavat antaa sille oikealla salausmenetelmällä salatun oikean salasanan. Useimmat intenet-palvelun tarjoajan (ISP) eli operaattorin välittämät Wi-Fi -tukiasemat on nykyisin oletuarvoisesti suojattu tällä menetelmällä. Tällöin tukiaseman tunniste ja salasana on usein valmiina tukiaseman pohjassa olevassa tarrassa. Tukiasema voi tunnistaa laitteen myös laitteen käyttämän MAC-osoitteen avulla. Tällöin tukiasemalle on etukäteen kerrottu sallittujen laitteiden MAC-osoitteet.  MAC-osoitteen käyttämistä tunnistuksessa ei pidetä turvallisena vaihtoehtona, koska pahantahtoinen toimija voi helposti verkkoa kuuntelemalla saada selville sallitun MAC-osoitteet. Koska nykyään laitteen MAC-osoite on helposti vaihdettavissa, pahantahtoisen toimijan on helppo kiinnittyä tällaiseen pelkästään MAC-osoitteilla suojattuun verkkoon.

Laitteen sijaan langattoman verkon haltija voi edellyttää käyttäjän tunnistamista. Tällöin tukiasema käyttää erillistä tunnistuspalvelua, johon käyttäjän pitää tunnistautua esimerkiksi käyttäjätunnuksella ja salasanalla. Tunnistautumisen jälkeen käyttäjän laitteella voi liikennöidä verkossa. Jätämme erilaisten käyttäjän tunnistuksen menetelmien tarkemman tarkastelun tietoturvakursseille, kuten Cyber security.

<quiz id="a6168f17-8442-4c82-b2b5-db8d712e034d"> </quiz>

### Lähetysvuorojen jakelu

IEEE 802.11 standardin mukaan toimivat verkot käyttävät kehysten yhteentörmäysten välttämiseen CSMA/CA menetelmää, johon jo tutustuimme lyhyesti aiemmin. Siinähän tavoitteena oli erityisesti välttää yhteentörmäyksiä.   Katsotaan nyt tarkemmin. miten tämä WLAN-verkoissa tehdään.

CSMA/CA:ssa edellytään, että lähettäjän pitää aina odottaa pieni hetki vapaata kanavaa kuunnellen ennenkuin lähetys voi alkaa. Näitä odotusaikoja on itseasiassa määritelty kaksi eri mittaista. SIFS (Short Inter-frame Spacing) on lyhyt ajanjakso, jota käytetään odotuksessa silloin, kun lähettäjä jo ennalta tietää, että seuraavan kehyksen lähetysvuoro on oikeastaan sillä. Esimerkiksi datan vastaanottokuittauksien lähetys käyttää tätä lyhyempää odotusta. Lyhyt odotus tarvitaan lähinnä siihen, että alkuperäisen datan lähettäjä ehtii vaihtaa omat antenninsa lähetystilasta vastaanottotilaan.  Jos lähettäjä pyrkii lähettämään uuden datakehyksen, niin silloin se käyttää odotuksen kestona pidempää DIFS:iä (Distributed Inter-frame Spacing), jolla siis erotellaan eri lähettäjien eri datakehykset toisistaan. Koska SIFS on lyhyempi kuin DIFS, niin erilaiset kuittausviestit yms. saavat prioriteetin, jolloin ne lähetetään ensin ja pidemmät datakehykset joutuvan odottamaan hiukan kauemmin.

WLAN-verkkojen käyttämässä CSMA/CA:ssa lähettäjä käyttää lisäksi kanavan varausta. Koska varauskehykset ja niiden kuittaukset ovat huomattavan paljon lyhyempiä kuin varsinaiset datakehykset, niin yhteentörmäykset varauskehysten kesken ovat nopeita selvittää. Lähettäjähän ei kuuntele tuliko yhteentörmäys, joten jos yhteentörmäys tulee pitkän datakehyksen aikana, niin lähettäjä kuitenkin lähettää kehyksen kokonaan. Kätketyn aseman ongelman vuoksi tällainen yhteentörmäys on mahdollinen. Nyt varausviestien kanssa lähettäjä, odotettuaan tuon DIFS aikaa, lähettääkin ensin pienen varauskehyksen (Request To Send, RTS), jossa se kertoo, kuinka ison kehyksen se haluaa lähettää ja kuinka kauan lähetys tulee kestämään. Vastaanottaja vahvistaa tämän varauksen erillisellä vahvistusviestillä (Clear To Send, CTS), jonka se lähettää heti SIFS ajan jälkeen, jolloin mikään muu asema ei vielä voi lähettää. Koska kuittaus tulee ison kehyksen vastaanottajalta, niin se tavoittaa kaikki ne laitteet, joiden mahdollinen lähetys voisi häiritä datakehyksen lähetystä. Ne osaavat nyt tämän kuittausviestin tietojen avulla odottaa koko datakehyksen lähetyksen ajan ennenkuin ne edes yrittävät omaa lähetystään. Näin alkuperäiseltä lähettäjältä kätkössä oleva asema saa tiedon lähetyksestä, jota se ei itse muuten pystyisi havaitsemaan.

<img src="../img/5-6-viestit.svg" alt="Kuvassa on viestien vaihdot yhden kehyksen lähettämiseen liittyen. Kuvassa on siis kaksi asemaa/laitetta ja niiden välissä tukiasema. Viestien vaihto alkaa tilanteesta, jossa tukiasema lähettää vastaanottokuittauksen edellisestä datakehyksestä. Tämä kuittaus menee molemmille laitteille. Sen jälkeen DIFS ajan kuluttua ensimmäinen asema lähettää varauskehyksen (Request to send 100 ) tukiasemalle, joka kuittaa sen SIFS ajan kuluttua vahvistusviestillä Clear to send 100 ). Tämä vahvistusviesti menee molemmille laitteille. Ensimmäinen laite aloittaa sitten SIFS ajan kuluttua oman dataviestinsä lähettämisen. Toinen laite kirjaa itselleen tiedoksi, että se ei voi lähettää niin kauaa kuin tuon datan siirto kestää (eli 100). Kun datan siirto päättyy, niin tukiasema lähettää taas kuittausviestin molemmille asemille.">

KUVA: Kuvassa on esitettynä yhden data kehyksen lähetykseen liittyvät viestit eli ensin varaus ja varauksen vahvistus ja sitten varsinainen datakahys ja lopuksi vielä sen kuittaus. Huomaa, että kuittaus- ja vahvistusviestit  kuuluvat kaikille vastaanottajan kuuluvuusalueella, vaikka varsinainen datansiirto ei kuuluisikaan.


### Langattoman verkon kehys


Langattoman verkon kehyksessä (katso kenttien selitykset englanninkielisestä wikipediasta [IEEE 802.11](https://en.wikipedia.org/wiki/IEEE_802.11#Layer_2_%E2%80%93_Datagrams) on neljä osoitetta. Muistathan, että langallisen ethernet-verkon kehyksessä oli vain kaksi osoitetta (vastaanottajan MAC ja lähettäjän MAC). Langattomassa verkossa kehykselle on määritelty neljä osoitekenttää, joista tosin yleensä ei käytetä kuin kolmea. Muista, että nämä kehykset ovat linkkikerroksella, jolloin kehysten osoitetiedot ovat MAC-osoitteita. Osoitekenttien tulkinnat vaihtelevat sen mukaan mille laitteelle (eli mihin suuntaan) kehys on menossa.

<img src="../img/5-6-802-11-kehysv2.svg">
KUVA: Langattoman verkon kehyksen otsake.

Kehyksen alussa on joukko kehyksen tulkintaan vaikuttavia kenttiä, joista kentät ToDS ja FromDS määrittävät näiden 4 osoitekentän tulkinnat. Tuo DS nimessä on lyhenne englanninkielen sanoista Distribution system ja tässä se tarkoittaa tämä langattoman yhteyden (eli lähettäjän ja vastaanottajan) ulkopuolista verkkoa kokonaisuudessaan. Muistathan, että tarkastelemme asioita linkkitasolla, ja kahden langattoman laitteen välinen viestintä ei vielä muodosta verkkokerroksen näkökulmasta yhtä ehjää linkkiväliä verkkokerroksen lähettäjältä seuraavalle verkkokerroksen vastaanottajalle, ellei tukiasema ole samalla myös reititin. Jos viesti on tulossa kauempaa, niin FromDS on 1 ja jos viesti on menossa kauemmas niin ToDS on 1. Näin saadaan 4 erilaista yhdistelmää. 00 - näiden kahden laitteen välinen viesti, tyypillisesti kontrolliviesti, 01- menossa eteenpäin, 10- tulossa kauempaa, 11 - tulossa kauempaa ja menossa eteenpäin.  Tätä luokkaa 11 käytetään lähinnä ad hod -verkoissa, jotka tekevät kehysten reititystä linkkikerroksella.


| ToDS  | FromDS  | Osoite 1  | Osoite 2  | Osoite 3  | Osoite 4  |
| ----- | --------- | ---------- | ---------------------- | ----------------------- | ---------------------- |
| 0   | 0     | vastaanottajan MAC  | lähettäjän MAC    | tukiaseman id        |  ei käytössä         |
| 0   | 1     | vastaanottajan MAC  | tukiaseman MAC  | lähettäjän MAC (esim. reititin)    | ei käytössä      |
| 1   | 0    |  tukiaseman MAC | lähettäjän MAC    | vastaanottajan MAC (esim. reititin)   | ei käytössä      |
| 1   | 1     | vastaanottavan tukiaseman MAC  | lähettävän tukiaseman MAC   | vastaanottajan MAC        | lähettäjän MAC    |


Taulukosta voi havaita, että osoitteet 1 ja 2 ovat tämän langattoman yhteyden lähettäjä ja vastaanottaja. Osoitteet 3 ja 4  kertovat sitten koko aliverkon osalta alkuperäisen lähettäjän tai vastaanottajan, joka siis on antanut kehyken linkkikerrokselle tai vastaavasti vastaanottovaiheessa saa kehyksen sisällön linkkikerrokselta verkkokerrokselle.
Koska kummankin kehyksen lopussa on kehykseen liittyvät tarkistusbitit (Frame Check Sequence, FCS), tukiasema joutuu otsaketietojen muunnoksen vuoksi laskemaan ne uudelleen.


<quiz id="b26eac43-8e17-4460-bc99-ebdecef70f2e"> </quiz>






---
path: '/osa-6/1-kaikki-yhteen'
title: 'Kaikki yhteen'
hidden: false
---

<text-box variant='learningObjectives' name='Oppimistavoitteet'>

- Osaat kuvata aiempien osien materiaalin yhteistoiminnan.

</text-box>

Tässä osassa käydään läpi yksi kokoava esimerkki, jossa käydään erityisesti läpi, miten kurssin kuluessa käsitellyt menetelmät toimivat yhdessä. Kun käyt tätä läpi, niin kertaa samalla kaikkien protokollien yksityiskohdat.


Käydään esimerkkinä läpi tilanne, jossa käyttäjä liittää oman koneensa aliverkkoon langallisella yhteydellä ja tekee sen jälkeen www-selaimella pyynnön lukea joku tietty sivu.  Tämä aliverkko voi olla kotiverkko tai esimerkiksi jonkun yrityksen hallinnoima oma sisäinen verkko.

Tämä esimerkki tiivistää suurimman osan kurssin sisällöstä yhteen tarinaan. Jotkut protokollat jäävät vielä pois tarinasta ja osasta ei tarvita kaikkia yksityiskohtia, mutta suurin osa kurssisisällöstä tulee kerrattua tällä hyvin yksinkertaisella tarinalla.

<img src="../img/kaikki-yhteen-verkko.svg"> </img>

## Verkkoon liittyminen

Verkkoon liitetty tietokone ei voi liikennöidä verkossa, jos sillä ei ole verkkoon sopivia tunnisteita, joilla muut voivat lähettää sille viestejä.

<quiz id="a69e0cef-84ae-4ad8-8c28-dc408c892e72"> </quiz>

Jotta sovelluskerroksella muodostetty pyyntö voidaan välittää verkkoon, niin sen pitää edetä protokollapinossa kerrokselta toiselle. Jätetään tuo kerrosten tarkastelu hetkiseksi ja mennään eteenpäin. Muista kuitenkin, että kaikki lähetetyt ja vastaanotetut viestit kulkevat aina protokollapinossa kerrokselta toiselle.

Kun tietokone on liittynyt verkkoon, se on valmiina lähettämään ja vastaanottamaan viestejä.

Seuraavaksi käyttäjä käynnistää www-selaimen ja kirjoittaa osoitekenttään sen www-palvelimen nimen, jonka pääsivun käyttäjä haluaa hakea. Oletamme tässä, että kyseisen palvelimen nimi on www.verkkotunnus.fi   (Tämä osoite vie itseasiassa Traficomin sivulle, joten tunnus on aidosti olemassa.)

Selain siis lähtee seuraavaksi hakemaan kyseistä www-sivua.

## Kyselyn alussa tietojen selvittäminen

Selaimen pitää muodostaa HTTP-pyyntö, mutta ennen kuin se saa pyynnön valmiiksi lähetystä varten, sen täytyy selvittää kyseistä verkkonimeä www.verkkotunnus.fi vastaava IP-osoite.

Niinpä selain tekee pyynnön nimipalvelijalle, jonka osoitteen se on jo saanut aiemmin. Sovelluskerrokselta nimipalvelukysely siirtyy kuljetuskerrokselle. Nimipalvelupyyntö käyttää UDP:tä kuljetuskerroksen protokollana, joten erillistä yhteydenmuodostusta ei tehdä.  Kuljetuskerros muodostaa pyynnöstä segementin ja antaa sen edelleen verkkokerrokselle välitettäväksi eteenpäin.
Verkkokerros paketoi segmentin omaan IP-datagrammiinsa ja antaa datagrammin linkkikerrokselle.

Verkkokerroksen datagrammissa on vastaanottajan IP-osoite. Koska vastaanottaja ei ole samassa aliverkossa täytyy verkkokerroksen ohjata viesti reititystaulun mukaisesti oletusyhdyskäytävälle. Oletusyhdyskäytävän IP-osoitteen laite on saanut verkkoon liittyessän. Näin ollen verkkokerros tietää sen, mutta linkkikerros tarvitsee IP-osoitetta vastaavan MAC-osoitteen. Joten ennenkuin verkkokerroksen datagrammi / IP-paketti voidaan sijoittaa linkkikerroksen kehykseen täytyy tuo MAC-osoite selvittää. IP-osoitteen perusteella MAC-osoitteen selvittävä protokolla määritellään välillä verkkokerrokselle ja välillä linkkikerrokselle kuuluvaksi.

<quiz id="a50903df-836c-422d-95ae-da29218e3448">  </quiz>

Nyt meillä on tarvittavat tiedot siihen, että linkkikerros voi sijoittaa saamansa IP-datagrammin Ethernet-kehykseen ja lähettää sen paikalliselle yhdyskäytäväreitittimelle.

Muistathan vielä, että kehyksen sisällä olevan datagrammin sisällä olevassa UDP-segmentissä on paikalliselle nimipalvelijalle menossa oleva kysely.

Nyt asiakaskone lähettää kehyksen verkkoon, josta se päätyy vastaanottajan MAC-osoitteen perusteella yhdyskäytäväreitittimelle.

Yhdyskäytäväreititin vastaanottaa verkkokerroksella sille linkkikerroksen kautta ohjatun nimipalvelukysely. Se tarkistaa datagrammista, mikä on vastaanottajan IP-osoite eli minne viesti on menossa ja välittää sen reititystaulunsa tietojen perusteella eteenpäin. Näin viesti liikkuu reitittimeltä toiselle, kunnes se saapuu nimipalvelijan kanssa samassa aliverkossa olevalle reitittimelle. Tämä reititin ohjaa viestin nimipalvelijalle.

Nimipalvelijalla linkkikerros vastaanottaa tälle laitteelle (=kehyksen vastaanottana on laitteen MAC-osoite) tulossa olevan viestin ja antaa sen verkkokerrokselle. Verkkokerros tarkistaa, että viesti on nyt perillä oikealla laitteella, eli että vastaanotetussa datagrammissa on vastaanottajana tämän laitteen IP-osoite. Verkkokerros antaa viestin kuljetuskerroksen UDP-protokollalle, joka segmentin porttinumeron perusteella osaa antaa viestin edelleen nimipalveluprosessille.

<quiz id="abb2ab02-88ba-465d-9d3b-e2f7d709d64b"> </quiz>

Nimipalveluprosessi selvittää ensin omasta välimuististaan tietääkö se jo valmiiksi vastauksen saamaansa kyselyyn.  Jos pyydettyä tietoa ei ole sen omassa välimuistissa, niin se lähtee kysymään tietoa virallisten nimipalvelijoiden hierarkialta. Ja saatuaan vastauksen lisää sen omaan välimuistiinsa. Oletetaan tässä yksinkertaisuuden vuoksi, että tieto löytyy suoraan välimuistista.

Nimipalvelija muodostaa niin nimipalveluprotokollan mukaisen viestin ja sijoittaa viestin vastauskentään tarvittavat nimipalvelutietueet. Sen jälkeen sovelluskerros antaa nimipaveluviestin kuljetuskerrokselle, jossa se sijoitetaan UDP-segmentin sisään ja annetaan verkkokerrokselle. Koska kyseessä on vastaus aiempaan viestiin, niin lähettäjällä (=tämä paikallinen nimipalvelija) on jo tiedossaan vastaanottajan (=alkuperäinen kysyjä) IP-osoite ja porttinumero. Ne tulivat kyselyn mukana otsakekentissä. Nyt lähettäjän ja vastaanottajan porttinumerot sijoitetan UDP-segmentin otsakkeeseen, jonka verkkokerros sijoittaa omaan IP-datagrammiinsa. Datagramissa on vastaavasti lähettäjän (=tämä nimipavelija) ja vastaanottajan (=alkuperäinen kysyjä) IP-osoitteet. Datagrammi etenee sitten seuraavaksi linkkikerrokselle, joka sijoittaa sen omaan kehykseensä. Linkkikerroksella tämän kehyksen vastaanottajana on nimipalvelijan aliverkon reitittimen MAC-osoite.

Ja näin vastaus viesti pääsee liikkelle ja etenee kuten kaikki muutkin viesti reititin kerrallaan vastaanottajalle, jossa taas protokollapinoa pitkin sovelluskerroksen nimipalvelukirjastolle ja sitä kautta tieto päätyy selaimelle.

## Itse kysely

Nyt selaimella on vihdoin tarvittavat tiedot, jotta se voi viimeistellä HTTP-pyynnön. Se tietää nyt mille laitteelle kysely pitää kohdistaa. Selain voi siis avata pistokkeen ja avamisen jälkeen sijoittaa pyynnön tähän pistokkeeseen, josta kuljetuskerros saa sen välitettäväksi eteenpäin.

Koska HTTP-protokolla käyttää TCP:tä kuljetuskerroksen palveluna, avaa TCP yhteyden vastaanottajaan jo pistokkeen luonnin yhteydessä. Siinä vaiheessa tehdään TCP:n SYN-ACK -kättely ja avataan yhteys, jota pitkin sitten myöhemmin sovelluskerroksen viestit voivat kulkea molempiin suuntiin. Asiakas siis aloittaa kättelyn siinä vaiheessa, kun selain suorittaa pistokkeen avaamiseen liittyvän kirjastofunktion. Osana funktion suoritusta kuljetuskerroksen TCP lähettää SYN-segmentin vastaanottajalle ja saa aikanaan SYNACK viestin vastauksena.  Tähän pitää asiakkaan vielä vastata ACK-kuittauksella, mutta TCP protokolla sallii kuittauksen kulkevan varsinaisen datasegmentin mukana, joten yhteydenmuodostuksen kolmivaiheisen kättelyn viimeinen kuittaus voidaan lähettää varsinaisen HTTP-pyynnön mukana.

Seuraavana on vihdoin vuorossa varsinaisen HTTP-pyynnön lähettäminen. Sovellus siis kirjoittaa sen pistokkeeseen, kun pistoke on ensin avattu. Kuljetuskerros saa pyynnön pistokkeesta ja muodostaa siitä segmentin. Yleensä HTTP-pyyntö mahtuu yhteen segmenttiin. Viesti kulkee sitten verkkokerroksen, linkkikerroksen ja verkon reitittimien välityksessä www-palvelimelle.

Palvelimella pyyntö kulkee protokollapino pitkin sovelluskerrokselle, jossa www-palvelinsovellus saa sen pistokkeen kautta käyttöönsä. Nyt palvelinsovellus analysoi pyynnön ja muodostaa vastauksen, jonka se sitten lähettää vastauksena asiakkaalle.  Koska vastaus saattaa olla hyvin suuri html-sivu, niin se ei enää välttämättä mahdu yhteen kuljetuskerroksen segmenttiin. Siinä tapauksessa kuljetuskeros jakaa sovelluskerroksen viestin useampaan segmenttiin. Itse asiassa TCP ei tunnista sovelluskerroksen viestien rajoja, joten sen ei tarvitse välittää siitä miten se pistokkeesta tulevan tavuvirran pilkkoo palasiksi. 

Nyt vihdoin palvelimelta tuleva hTTP-vastaus on asiakkaalla ja protokollapino voi välittää sen sovelluskerrolla toimivalla selaimelle. Kaiken tämän jälkeen selain vihdoin voi sivun kuvauksen mukaisesti näyttää sivun käyttäjälle. Sivulla voi olla lisäelementtejä, joita sovellus lähtee pyytämään seuraavaksi elementti kerrallaan. Elementit voivat tulla muilta palvelimilta, jolloin niille tehtäviin HTTP-pyyntöihin saatetaan tarvita ensin nimipalvelupyyntöä palvelimen IP-osoitteen selvittämiseen.

Tästä kuvauksesta jäi vielä pois kaikki otsakkeiden yksityiskohdat. Jos tuntuu, että ne eivät vielä ole täysin hallinnassa, niin kannattaa kerrata näiden protokollien toimintaa ja erityisesti otsakkeiden tietoja.


