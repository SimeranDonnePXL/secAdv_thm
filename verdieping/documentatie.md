# Documentatie
**Leden:** *Milan, Jarne Staal, Stefano, Simeran Donné en Su-zen Geurts* <br/>
**Learning paths:** *Red Team & Yellow Team*

### TODO
- Red Team
    - [ ] Room 1
    - [x] Sakura room
    - [ ] Room 3
- Yellow Team
    - [ ] Room 1
    - [ ] Room 2
    - [ ] Room 3

## Red Team: Sakura Room
| Taak   | Duur       |
|--------|------------|
| 1      | 2sec       |
| 2      | 30min      |
| 3      | 59min30sec |
| 4      | 58min      |
| 5      | 25min30sec |
| 5      | 35min30sec |
| TOTAAL | 3h18m32s   |

### Task 1  INTRODUCTION
**Are you ready to begin?**
Antwoord: `Let's Go!`

### Task 2  TIP-OFF
**What username does the attacker go by?**
Antwoord: `SakuraSnowAngelAiko`
  1. De naam "sakura" in de [URL](https://raw.githubusercontent.com/OsintDojo/public/3f178408909bc1aae7ea2f51126984a8813b0901/sakurapwnedletter.svg) &rarr; FAIL
  2. De hex code in de URL mbv [RapidTables](https://www.rapidtables.com/convert/number/binary-to-ascii.html) omzetten naar tekst &rarr; FAIL
  2. De binaire tekst op de achtergrond mbv RapidTables omzetten naar tekst &rarr; A picture is worth 1000 words but metadata is worth far more
  3. In de metadata van de afbeelding, de bestandsnaam "/home/SakuraSnowAngelAiko/Desktop/pwnedletter.png" &rarr; `SakuraSnowAngelAiko`

## Task 3  RECONNAISSANCE
**What is the full email address used by the attacker?**
Antwoord:
1. Google search: "SakuraSnowAngelAiko"
2. Open LinkedIn omdat in de TryHackMe tekst gepraat wordt over job hunting sites &rarr; Contactgegevens bevat enkel [een website](http://snowangelgames.com/) dat nietmeer bereikbaar is
3. Bij "People also viewed" staat "Aiko Abe" ("Aiko") komt voor in de username &rarr; bevat geen extra contactgegevens en verder niks nuttig &rarr; FAIL
4. Terug bij account van "Snow Angel" &rarr; bevat een website naar [zijn website](https://freegamest.com/) &rarr; Bij "Contact us" kijken voor een email
5. Een message gestuurd in de hoop dat ik een mail kreeg met het e-mail adres dat ik zoek &rarr; FAIL
6. Donorlijst bekijken via "Donate" &rarr; Klik op link om te doneren &rarr; FAIL
7. Open het [Facebook account](https://www.facebook.com/freegamest) van FreeGamest &rarr; snowangel@freegamest.com &rarr; FAIL
8. Het account is verder nutteloos. Ik vraag me af of de comments bij Donate later in de toekomst nuttig zijn &rarr; bekijk volgende vragen en er wordt verwacht dat ik een Github account bekijk
9. Opnieuw Google search: "sakurasnowangelaiko github"
10. Eerst optie is een Github met dezelfde usernaam 1
11. Bekijk alle repo's: cpuminer, IO, xmrig, Mailpile & PGP
12. De meest interessante repo is "Mailpile" want ik zoek een e-mail adres
13. Hun [demo website](https://www.mailpile.is/demos/) heeft een link "Try Mailpile in English (US) &rarr; ik heb geen wachtwoord
14. In de repo gaat het ook over PGP &rarr; er was een repo "PGP"
15. De repo "PGP" bevat een public key &rarr;
16. Google search: "convert PGP public key" &rarr; Eerste optie: [een github link](https://gist.github.com/mdellavo/f42b7841a3d8cd021c1bbe3962046c04)
17. In de github staat uitgelegd hoe de PK geconverteerd moet worden &rarr; pk moet in een asc-file nodig
18. public key van PGP repo in asc-file opslaan &rarr; gpg --import ../pk.asc &rarr; `SakuraSnowAngel83@protonmail.com`

### What is the attacker's full real name?
Antwoord: 
1. Account gelinkt aan het linkedIn account Snow Angel was `Aiko Abe`

## Task 4  UNVEIL
### What cryptocurrency does the attacker own a cryptocurrency wallet for?
Antwoord:
1. Repo "cpuminer" vermeld Litecoin and Bitcoin &rarr; FAIL
2. Repo "xmrig" nutteloos
3. Overige repos bekijken &rarr; Repo met miner voor `Ethereum`

### What is the attacker's cryptocurrency wallet address?
Antwoord:
1. Eerst opzoeken hoe een cryptocurrency wallet address eruit ziet &rarr; Google search: how does a cryptocurrency wallet address
2. In repo "ethminer" staat niks meer nuttig
3. In repo ETH staat één lijn &rarr; verdacht, ook maar 2 commits dus dubbel verdacht
4. Bekijk history zoals vermeld op TryHackMe &rarr; bevat "stratum://0xa102397dbeeBeFD8cD2F73A89122fCdB53abB6ef.Aiko:pswd@eu1.ethermine.org:4444" 
5. `0xa102397dbeeBeFD8cD2F73A89122fCdB53abB6ef`

### What mining pool did the attacker receive payments from on January 23, 2021 UTC?
Antwoord:
1. Google search: stratum://0xa102397dbeeBeFD8cD2F73A89122fCdB53abB6ef.Aiko:pswd@eu1.ethermine.org:4444
2. Open eerste [link](https://ethermine.org/) &rarr; geeft Ethereum miner address in &rarr; Klik op "Payouts"
3. Zoek specifieke datum 23 januari 2021 &rarr; Transactie komt van `Ethermine`

### What other cryptocurrency did the attacker exchange with using their cryptocurrency wallet?
Antwoord:
1. Ik vind niks onder "Dashboard", "Payouts", "Settings" of "Support"
2. Klik op "Start mining" &rarr; ga naar [GMiner Download](https://bitcointalk.org/index.php?topic=5034735) &rarr; ga naar [de officiele website](http://gminer.pro) &rarr; FAIL
3. Google search: etherium login &rarr; Open [Chainstack](https://chainstack.com/build-better-with-ethereum/?utm_term=ethereum%20mainnet&utm_campaign=global_tier3&utm_source=adwords&utm_medium=ppc&hsa_acc=7102112062&hsa_cam=18255849784&hsa_grp=142132552216&hsa_ad=650188287319&hsa_src=g&hsa_tgt=kwd-406453719480&hsa_kw=ethereum%20mainnet&hsa_mt=b&hsa_net=adwords&hsa_ver=3&gclid=Cj0KCQjww4-hBhCtARIsAC9gR3bbj7K_75cAFixhRP-NJXrx4d_KVo_8aCdWs2KOJ2w0bLUV_Q-IvtYaAkT3EALw_wcB)
4. Inloggen met "SakuraSnowAngel83@protonmail.com" (gevonden in repo PGP) en wachtwoord "pswd" (gevonden in repo ETH) &rarr; FAIL
5. Google search: 0xa102397dbeeBeFD8cD2F73A89122fCdB53abB6ef transactions %rarr; Eerste link is een [etherscan](https://etherscan.io/txs?a=0xa102397dbeeBeFD8cD2F73A89122fCdB53abB6ef) specifiek voor het miner adres 
6. Naast Ethereum staat tussen de transacties `Tether`

## Task 5  TAUNT
### What is the attacker's current Twitter handle?
Antwoord:
1. Google search: @AikoAbe3 $rarr; Huidige account staat tussen de zoekresultaten &rarr; `@SakuraLoverAiko`

### What is the URL for the location where the attacker saved their WiFi  SSIDs and passwords?
Antwoord:
1. Spot een foto op het twitter account over WiFi
2. Google search: 0a5c6e136a98a60b8a21643ce8c15a74 wifi Anon &rarr; enkel zoekresultaten van walkthrough's...
3. Bekijk hint &rarr; gebruik screenshot
4. Neemt URL en voegt "b2b37b3c106eb3f86e2340a3050968e2" toe &rarr; `http://deepv2w7p33xa4pwxzwi2ps4j62gfxpyp44ezjbmpttxz3owlsp4ljid.onion/show.php2md5=b2b37b3c106eb3f86e2340a3050968e2`

### What is the BSSID for the attacker's Home WiFi?
Antwoord:
1. Google search: What is BSSID &rarr; leer over BSSID en SSID
2. Bekijk hint &rarr; search for BSSID
3. De eerste [link](https://networkinghelp.datto.com/help/Content/2_AccessPoints/5-learn/KB115005592546.html) is nutteloos
4. De tweede [link](https://www.wigle.net/) is bruikbaar &rarr; Account registreren
5. Zoek View > Advanced search (Zoals aangegeven in de hint)
5. SSID "DK1F-G" invullen en klikken op "Query" &rarr;  MAC address: `84:af:ec:34:fc:f8`


## Task 6  HOMEBOUND
### What airport is closest to the location the attacker shared a photo from prior to getting on their flight?
Antwoord:
1. Zoek de tweet met foto vóór de vlucht &rarr; tweet over last minute cherry blossoms
2. Geolocate de foto met [GeoImgr](https://www.geoimgr.com/) &rarr; FAIL
3. Nog een (re)tweet over Cherry blossoms &rarr; de boom is in Bethesda, MD
4. Zoek dichtsbijzijnde vliegveld in de buurt van Bethesda mbv [TravelMath](https://www.travelmath.com/nearest-airport/Bethesda,+MD)
5. Eerste optie is in Washington, DC (21 miles) &rarr; DCA


### What airport did the attacker have their last layover in?
Antwoord:
1. Zoek de tweet over de laatste tussenstop &rarr; JAL Airlines
2. Google search: JAL Airlines First class lounge Sakura lounge &rarr; eerste link is [Japan Airlines](https://www.jal.co.jp/jp/en/inter/service/lounge/) &rarr; ook heel wazig zichtbaar op de foto
3. Volgens de site is de "First Class Lounge, Sakura Lounge list" bij Tokyo International Airport (Haneda)
4. Google search: Tokyo International Airport code &rarr; `HND`

### EXTRA: What airport did the attacker have their last layover in?
Om te verifiëren dat het deze is en geen wilde gok.
Antwoord:
1. Zoek zijn huis op &rarr; gebruik voorgaande gegevens van wigle &rarr; Est. Lat 40.60551453 en Est. Long 140.4606781 
2. Google Map search: 40.60551453, 140.4606781 &rarr; Mayacho, Hirosaki, Aomori 036-8357, Japan 
3. Zoek dichtsbijzijnde vliegveld in de buurt van Hirosaki mbv TravelMath &rarr; Aomori, Japan (29 km) &rarr; AOJ 
4. Google search: JAL airlines &rarr; [JAL Airlines site](https://www.jal.co.jp/jp/en/)
5. Zoek een vlucht van Bethesda naar Hirosaki (eerste klasse) &rarr; Vlucht gevonden &rarr; DCA > BOS > HND > AOJ 
6. Laaste tussenstop is `HND`

### What lake can be seen in the map shared by the attacker as they were on their final flight home?
Antwoord:
1. Zoek de tweet van de kaart
2. Zoek de woonplaats opnieuw &rarr; Google Map search: 40.60551453, 140.4606781 
3. Zoek het meer in de buurt van de woonplaats EN dat lijkt op de foto van de tweet
4. Lake Towada ligt in de buurt maar lijkt niet op de foto &rarr; zoom uit en zoek het meer
5. Meer gevonden: `Lake Inawashiro` 

### What city does the attacker likely consider "home"?
Antwoord:
1. Afgaand op de gevonden coordinaten &rarr; `Hirosaki`