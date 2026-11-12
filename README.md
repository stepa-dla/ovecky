# Ovečky do Betléma – vánoční hra na televizi

Na televizi běží zasněžená louka se stádem. Kdo naskenuje vytištěný QR kód, stane se pastýřem: mobil je ovladač (joystick) a zároveň reproduktor. Hrát mohou až čtyři. Volné pastýře vede počítač. Když nikdo nehraje, běží ukázka.

## Soubory

| soubor | co to je |
|---|---|
| `index.html` | televize: hra přes celou obrazovku (16 : 9) |
| `hrac.html` | ovladač v mobilu (otevře se z QR kódu) |
| `tisk.html` | cedulka A4 s QR kódem k vytištění |

Stránky jsou samostatné, nepotřebují žádný server. Mobil a televize se spojí přes veřejný zprostředkovatel [PeerJS](https://peerjs.com) (zdarma, bez účtu). Data pak jdou přímo mezi mobilem a televizí.

## Nahrání na GitHub Pages

1. Na GitHubu založ nový veřejný repozitář, třeba `betlem`.
2. *Add file → Upload files*: přetáhni `index.html`, `hrac.html`, `tisk.html` a `README.md`. Potvrď *Commit changes*.
3. *Settings → Pages → Build and deployment*: Source **Deploy from a branch**, Branch **main**, složka **/ (root)**, *Save*.
4. Za minutu až dvě běží hra na `https://<tvé-jméno>.github.io/betlem/`.

## QR kód k vytištění

Otevři `https://<tvé-jméno>.github.io/betlem/tisk.html` a dej *Vytisknout* (A4, velikost 100 %). Kód vede na `hrac.html`. Televize má pevné ID zapsané přímo ve stránce, takže vytištěný kód platí trvale, i po restartu nebo na jiné televizi.

Hru nech běžet jen v jednom okně. Když je `index.html` otevřený současně na dvou místech (třeba na televizi a na počítači), druhé okno čeká, dokud se první nezavře.

## Spuštění na televizi

- V prohlížeči televize (nebo počítače připojeného k televizi) otevři adresu z bodu 4.
- **Celá obrazovka:** klávesa F nebo Enter (případně tlačítko OK na dálkovém ovladači).
- **Klávesy:** N noc/sníh · V chumelenice · W vlk · C hvězda · K konec kola · Z zvuk i z televize · H nápověda.
- **Světlo a stíny** počítá grafická karta (WebGL): měsíc od hvězdy, oheň, lucerny, světlo z chléva, lucerničky pastýřů a měkké vržené stíny. Klávesa L je vypne nebo zapne. Na slabém zařízení se samy vypnou a hra běží v plochém tisku.

## Průběh hry

1. Hráč naskenuje QR kód. Mobil ukáže, kterého pastýře řídí (barva a jméno). Kamkoli na displej položí prst, objeví se věneček pastýře a táhnutím ho vede.
2. Každý dá **Můžeme začít**. Kolo začne, až jsou připraveni všichni připojení. Pokud někdo nereaguje, začne se 25 s po prvním „připraven“.
3. Pastýři ženou stádo vrátky do ohrady s chlévem. Body má celý tým: ovečka 1, černá ovečka 3, zahnaný vlk 2. Překážky na louce (seno, balvany, sněhulák, sáně, studna, zídky) jsou v každém kole jinde.
4. Vlci se plíží k osamělým ovečkám, později v kole chodí ve dvojici. Pastýř musí dojít až k vlkovi, jinak odnese ovečku do lesa. Když vlk přijde, všechny mobily zavyjí a na Androidu zavibrují.
5. Kdo přijde během kola, převezme volného pastýře. Kdo se 12 s nedotkne ovladače, toho pastýře na chvíli vede počítač. Stačí se dotknout a řídí zase hráč.
6. Po kole dají hráči **Hrát znovu**. Když všichni odejdou, televize se vrátí k ukázce.

**Zvuk:** hudbu a společné zvuky hraje jeden mobil. Každý mobil navíc slyší „své“ ovečky a zvonek, když jeho ovečka vejde do ohrady. Zvuk se zapne prvním dotykem. Na Androidu mobil i vibruje.

## Volby v adrese televize

- `?cas=120`: délka kola v sekundách (výchozí 120).
- `?snih`: zasněžená paleta (jinak noc).
- `?bezvlku`: bez vlků.
- `?rychlost=250`: rychlost pastýřů hráčů v mm/s.
- `?zvuk`: zvuk i z televize.
- `?svetlo=0`: bez nasvícení (plochý tisk); `?svetlo=1`: nasvícení vždy, i na pomalém zařízení.
- `?id=betlem-nazev`: jiné ID (jen pro druhou, samostatnou hru). Cedulku pak tiskni přes `tisk.html?id=betlem-nazev`.

Volby jdou kombinovat: `index.html?cas=90&snih`.

## Autoři

Bečení oveček: reinsamba, [„110419-000_sheep_bleating.wav“](https://freesound.org/people/reinsamba/sounds/119161/), a HerbertBoland, [„Sheeheep.wav“](https://freesound.org/people/HerbertBoland/sounds/75190/). Obě nahrávky jsou pod licencí CC BY, výřezy pocházejí ze sady ESC-50 (K. J. Piczak).
Písma Alegreya a Alegreya SC (Juan Pablo del Peral, Huerta Tipográfica) jsou pod licencí SIL OFL. Spojení zajišťuje [PeerJS](https://github.com/peers/peerjs) (MIT), QR kód [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) (MIT).
