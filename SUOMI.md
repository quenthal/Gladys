# Gladys Assistant suomeksi

Tämä forkki lisää suomenkielisen käyttöliittymän Gladys Assistant 5.3.1:een.
Valitse käyttöönotossa tai käyttäjäprofiilissa kieleksi **Suomi**.
Suomenkielinen selain valitsee suomen automaattisesti, kun aiempaa kielivalintaa ei ole.

## Mitä on suomennettu?

- Ydinprojektin käyttöliittymän käännöstiedosto ja kuvakkeiden hakusanat: yhteensä 6 836 tekstiä.
- Käyttöönotto, valikot, kojelaudat, käyttäjäasetukset, automaatioeditori ja integraatioiden ydinnäkymät.
- Kalenterien, päivämäärävalitsimien ja kaavioiden kieliasetukset.
- Suomen hyväksyminen käyttäjän kieleksi palvelimella.

Käännös on koneavusteinen. Keskeisiä näkymiä, laiteohjauksia ja sanastoa on tarkistettu ja korjattu erikseen. Kaikkia integraatioiden pitkiä ohjetekstejä ei ole vielä kielentarkistettu rivi riviltä. Korjaukset ovat tervetulleita.

## Asentaminen

Tavallinen Gladysin virallinen Docker-kuva ei sisällä tämän forkin muutoksia.
Käytä tämän repositorion lähdekoodia ja projektin [kehitysohjetta](https://gladysassistant.com/docs/dev/developing-a-service/).
Projekti määrittelee ympäristöksi Node.js 24.x:n ja npm 11.x:n.
Pelkkä `fi.json`-tiedoston kopiointi ei riitä, sillä myös kielten rekisteröinti on muuttunut.

Älä aseta itse rakennetulle versiolle `GLADYS_OFFICIAL_RELEASE_IMAGE`-muuttujaa.

## Rajaukset ja testaus

Tämä muutos lisää käyttöliittymän kielituen. Se ei lisää paikallista puheentunnistusta, kielimallia tai puhesynteesiä. Ulkoisten integraatioiden omat tekstit, dokumentaatio ja palvelimen keskusteluvastaukset voivat edelleen olla englanniksi.

Käyttöliittymän koonti, käännösavainten vertailu, muuttujien ja HTML-merkintöjen säilyminen sekä kielenvaihdon selainkokeet on tarkistettu. Selainkokeissa käytettiin simuloituja palvelinvastauksia. Oikeilla kotiautomaatiolaitteilla tehtävää hyväksymistestausta ei ole vielä tehty.

Ensimmäinen paikallinen koonti tehtiin Windowsissa Node.js 22.23.2:lla ja npm 10.9.8:lla. Projektin määrittelemä Node.js 24 / npm 11 -ympäristö sekä koko palvelimen testisarja on varmistettava ennen tuotantojulkaisua.

## Käännösten ylläpito

Käyttöliittymä: `front/src/config/i18n/fi.json`.
Kuvakkeet: `front/src/config/i18n/icon-keywords/fi.json`.

Säilytä avaimet, `{{muuttujat}}`, HTML-tagit, linkit ja tekniset koodikatkelmat. Vertaa englanninkielisiin tiedostoihin ja aja käyttöliittymän hakemistossa `npm run compare-translations` sekä projektin muut tarkistukset.

Käännös käyttää muun muassa termejä **kojelauta**, **automaatio**, **laukaisin**, **toiminto** ja **ehto**.
