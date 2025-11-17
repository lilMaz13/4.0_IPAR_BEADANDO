# 4.0_IPAR_BEADANDO
MQTT-alapú jelzőrendszer hardening laptopon: TLS/mTLS, ACL, rate-limit és „retained” higiénia hatása a késleltetésre, átviteli teljesítményre és DoS-állóképességre

A dolgozat célja egy könnyen reprodukálható, kizárólag laptopon futtatható „mini-labor”
kidolgozása és kiértékelése, amely az MQTT-alapú üzenetközvetítés biztonságos
üzemeltetését vizsgálja ipari/IoT kontextusban.
A fókusz az MQTT hardening gyakorlatain van: TLS/mTLS titkosítás és hitelesítés,
felhasználó- és topikalapú hozzáférés-szabályozás (ACL), üzenet-„higiénia” (retained/LWT,
topic-névkonvenciók), valamint egyszerű forgalom-korlátozás és anomália-szűrés. A
módszertan Docker-komponensekre épül (Mosquitto broker és mérőszkriptek), így külső
eszköz nélkül, determinisztikusan futtatható és mérhető a három konfigurációs mód:
(1) baseline – titkosítás és erős ACL nélkül
(2) TLS + jelszavas hitelesítés szűk ACL-lel
(3) kölcsönös TLS (mTLS) + ACL + „higiéniai” szabályok
Mindhárom módban azonos mérési forgatókönyveket hajtunk végre Python alapú
publisher/subscriber eszközökkel: késleltetés és átviteli jellemzők (QoS0/1, payload-méret),
hozzáférési tesztek (engedélyezett/tiltott műveletek aránya), broker erőforrás-terhelés
(CPU/RAM) és opcionális zaj/DoS-szerű terhelés hatása.
A mérések CSV-be gyűjtve grafikonokká alakíthatók, így a biztonsági kontrollok költséghaszon elemzése számszerűsíthető (teljesítmény–biztonság kompromisszumok). A dolgozat
tartalmazni fogja az MQTT fenyegetésképet és a releváns ellenintézkedéseket, a labor
topológiát és konfigurációkat, a mérési eredmények ábráit és összehasonlítását.
Az elkészült anyag célja, hogy reprodukálható példán mutassa be, miként javítható érdemben
egy MQTT broker biztonsága kézzelfogható teljesítményáron.
