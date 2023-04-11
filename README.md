# Systém Face_Rec 

Aplikace slouží pro tvorbu databáze fotografií osob s nástroji pro stažení a labelování dat. Následně je možné v aplikaci tyto data otestovat na metody strojového učení, zaměřené na detekci obličeje, rozpoznání osob a jejich pohlaví, věku a emocí.

## Analýza cílové skupiny

- Machine Learning Researcher
- Data analytik

**Předpokládané vzdělaní:** vysokoškolské <br/>
**Zaměření:** IT, strojové učení <br/>

# Struktura dokumentace

## 1. Úvod do projektu
 - představení projektu
 - knihovny potřebné pro spuštění
## 2. Databáze
databáze obsahuje 100 slavných osobností zastoupena 50 různými snímky. Ohraničení oblasti obličeje probíhalo poloautomatickou formou s využitím algoritmu HOG, zbylé kategorie byly stanoveny prostřednictvím vytvořené aplikace. Pro uložení anotací k snímkům byl zvolen formát JSON s následující strukturou:
- "name": jméno
- "age": 10 | 20 | 30 | 40 | 50 | 60 | 70
- "gender": "F" | "M"
- "emotion": "S" | "H" | "N"  | "A" |
- "faceloc" = [x1, y1, y2, x2] ((levý horní roh), (pravý spodní roh))

## 3. Použité metody
### metody detekce osob
- Segmentace (vlastní implementace)
- Viola-Jones (OpenCV)
- MTCNN (OpenCV)
- HOG (DLIB)
### metody rozpoznání osob
- PCA (vlasní implementace + Scipy)
- Korelační filtr MACE (vlastní implementace)
- Deep metric learning (knihovna Face_recognition implementující resnet-34 architekturu DLIB)
### metody rozpoznání emocí, pohlaví a věku
- YOLO v7 (použita [implementace](https://github.com/WongKinYiu/yolov7))
- Vlastní neuronové sítě
  - test
  - test
  - test
## 4. Aplikace Face_Rec
### vývojový diagram
### funkcionalita
### návod ke spuštění

## 5. Programy pro analýzu dat
- soupis jednotlivých scriptů
  - popis funkcionality
  - souhrn použitých metod
  - ovládací proměnné
## 6. Data a výsledky analýzy testování
- strukturované odkazy k výsledkům testování včetně použitých dat

# Pivo

## 1) Koncept

Otvírak slouží k otevření nápojů s kovovými zátkami.

## 2) Pracovní postup

+ Pevně uchopte láhev svou slabší rukou těšně pod uzávěrem
+ Do druhé ruky si vezměte otvírák
+ Konec otvíráku zapřete mezi ukazováček a zátku
+ Poté pákou zatlačte otvírákem směrem dolů
+ Tímto by mělo dojít k otevření láhve

## 3) Reference

### Otvírák
kovový otvírák střední velikost

### Kroužek

slouží pro připojení úchytného zařízení

###  kovová svorka

svorka sloužící na připojení ke kusu oblečení, zabraňující ztrátě

## 4) Katalogový list


rozměry: 5, 4 × 1 cm
hmotnost (kg): 0,01
materiál: hliník
údržba: vhodný do myčky
záruka: 2 roky

## 5) Tuturiál

Při prvním užití je vhodné připojení otvíráku ke svorce. Následně je možné přistoupit k prvnímu otevření láhve. Poté uchopíme otvírák do ruky a přiložíme pod úhlem 45 stupňů k láhvy. Páčivým pohybem směrem dolů od láhve lze oddělit uzávěr od láhve.
