# IoT kamera za ulazna vrata

Sustav se sastoji od 3 međusobno povezane komponente unutar iste Wi-Fi mreže:

- Vanjska jedinica
- Unutarnja jedinica
- Mobilna aplikacija

## Vanjska jedinica

Vanjska jedinica sastoji se od kamere, PIR senzora, tipke za zvono i buzzera. ESP32-CAM služi kao server koji clientima prenosi video s kamere, obavještava cliente kada netko pozvoni pritiskom na tipku ili kada se aktivira PIR senzor, aktivira vanjski buzzer i omogućuje clientima da odluče hoće li otključati bravu. Umjesto prave brave u ovom prototipu koristit će se LED dioda koja svijetli pri otključavanju. Na server može biti povezano više clienata te se svakom clientu šalje obavijest. Kod vanjske jedinice biti će napisan u C++ programskom jeziku koristeći ESP-IDF i FreeRTOS.

## Unutarnja jedinica

Unutarnja jedinica sastoji se od ESP32 mikrokontrolera, ekrana povezanog SPI protokolom, tipkom za uključivanje i isključivanje, tipkom za otključavanje brave te buzzerom koji se oglasi na zahtjev vanjske jedinice. ESP32 povezuje se na ESP32-CAM server, na ekranu prikazuje video, obavještava korisnika o zvonu na vratima te šalje naredbu da se brava otključa ako korisnik tako odluči. Za programiranje ESP32 koristit će se ESP-IDF, FreeRTOS i C++.

## Mobilna aplikacija

Mobilna aplikacija pruža istu funkcionalnost kao i unutarnja jedinica kada je mobitel spojen na isti Wi-Fi. Aplikacija će biti razvijena koristeći React Native i Expo.

## Podjela rada
Dino:
- Vanjska jedinica
- 3D printanje kućišta

Damjan:
- Unutarnja jedinica
- Mobilna aplikacija

## Oprema

| Stavka bodovanja             | Predložena komponenta                                       | Napomena                                                                          |
| ---------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Mikrokontroler (15 bodova)   | ESP32-CAM, ESP32                                            | Mikrokontroleri vanjske i unutarnje jedinice                                      |
| SPI komunikacija (20 bodova) | SPI TFT zaslon (ILI9341)                                    | Komunikacija između ESP32 i ILI9341                                               |
| Senzori (15 bodova)          | ESP32-CAM, HC-SR501 PIR                                     | Kamera dolazi ugrađena na ESP32-CAM                                               |
| Zaslon (15 bodova)           | SPI TFT zaslon (ILI9341)                                    | Prikaz video streama s vanjske jedinice                                           |
| Audio (5 bodova)             | Piezo buzzer (2)                                            | Oglašava se kada netko pozvoni                                                    |
| IoT mogućnost (20 bodova)    | Wi-Fi povezivanje, mobilna aplikacija                       | Video stream, obavijest o zvonu i otključavanje na daljinu                        |
| 3D print (10 bodova)         | Kućišta za vanjsku i unutarnju jedinicu                     | Zaštita elektronike                                                               |




