# Systém Face_Rec 

Aplikace slouží pro tvorbu databáze fotografií osob s nástroji pro stažení a labelování dat. Následně je možné v aplikaci tyto data otestovat na metody strojového učení, zaměřené na detekci obličeje, rozpoznání osob a jejich pohlaví, věku a emocí.

## Analýza cílové skupiny

- Machine Learning Researcher
- Data analytik

**Předpokládané vzdělaní:** vysokoškolské <br/>
**Zaměření:** IT, strojové učení <br/>

# Struktura dokumentace

## 1. Úvod do projektu
Tato práce se skládá ze 3 hlavních komponent:
  - Databáze
  - Aplikace
  - Analýza testování
  
Před začátkem je velmi doporučena instalace veškerých knihoven. Je přiložen import virtuálního prostředí v adresáři /virtual_env/env_data_science.yml.Tento soubor lze importovat v prostředí Anaconda (spustit Anaconda -> prostředí -> import -> zvolit .yml soubor. Bohužel knihovny DLIB a face_recognition vyžadují samostatnou instalaci (včetně Visual studia).
 
## 2. Databáze

Databáze obsahuje 100 slavných osobností zastoupena 50 různými snímky. Ohraničení oblasti obličeje probíhalo poloautomatickou formou s využitím algoritmu HOG, zbylé kategorie byly stanoveny prostřednictvím vytvořené aplikace. Databáze je uložena /data/data.json s následující strukturou:
- "name": jméno
- "age": 10 | 20 | 30 | 40 | 50 | 60 | 70
- "gender": "F" | "M"
- "emotion": "S" | "H" | "N"  | "A" |
- "faceloc" = [x1, y1, y2, x2] ((levý horní roh), (pravý spodní roh))
- "path" = "osobnost/jmeno/img"

Příklad uložení 1 osoby:

![](json_example.png)


## 3. Použité metody
### Metody detekce osob
- Segmentace (vlastní implementace)
- Viola-Jones (OpenCV)
- MTCNN (OpenCV)
- HOG (DLIB)
### Metody rozpoznání osob
- PCA (vlasní implementace + Scipy)
- Korelační filtr MACE (vlastní implementace)
- Deep metric learning (knihovna Face_recognition implementující resnet-34 architekturu DLIB)
### Metody rozpoznání emocí, pohlaví a věku
- YOLO v7 (použita [implementace](https://github.com/WongKinYiu/yolov7))
- Vlastní neuronové sítě
  - MLP
  - 2x konvoluční vrstva
  - modifikace Resnet-8
  - modifikace VGG7BN
## 4. Aplikace Face_Rec

Aplikaci lze spustit napsáním příkazu python3 main.py v přikazovém řádku.

### Vývojový diagram
 ![](window_flow.png)
### Funkcionalita

- Stažení snímků do databáze

Zadáním jména osobnosti do textového pole je staženo $n$ fotografií dané osoby s možností zvolit, které snímky si uživatel přeje uložit do své databáze.

![](dataset_download.png)

- Anotace dat

Tato část se dělí na tři samostatná podokna. V prvním podokně je možnost volby osobnosti, kterou si uživatel přeje upravit. Následně jsou zobrazeny všechny fotografie dané osoby včetně anotací, pokud jsou již přiřazeny. Poslední podokno je věnováno samotnému upravení anotací snímku (věku, pohlaví a emoci), včetně zobrazení plochy ohraničující obličej.

![](one_people.png)

- Vizuální testování na libovolné fotografii

Umožňuje vybrat libovolnou fotografii z adresářové struktury a stejně jako v okně s webkamerou je možné vizuálně otestovat vybrané algoritmy.

![](testing.png)


- Vizuální testování webkamerou

V případě připojené videokamery je možné otestovat vybrané metody v reálném čase. Obraz je aktualizován s obnovovací frekvencí 30 snímků za vteřinu. Pro zrychlení chodu aplikace probíhá, v případě aktivace jedné z rozpoznávacích metod, identifikace každé tři vteřiny.

## 5. Popis zbývajících souborů

- kivy_screens: obsahuje front-end soubory pro tvorbu github
- plotting_methos: pomocné programy, které byly využity při tvorbě dokumentace
- data: je zde uložena struktura JSON s databázi a detekční soubory
- data_analysis: soubory s výsledky testování
- yolo: v yolo/yolov7 se nachází implementace yolov7, v yolo/weights jsou natrénované váhy detektoru
- own_cnn.ipynb: Zde je vytvořený program v jupyter notebooku pro testování neuronových sítí na databázi




