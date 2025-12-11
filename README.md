<div align="center">
  <a href="#magyar" style="text-decoration:none; padding: 10px 20px; margin: 5px; background-color: #c00; color: white; border-radius: 5px; font-weight: bold;">🇭🇺</a>
  <a href="#english" style="text-decoration:none; padding: 10px 20px; margin: 5px; background-color: #0072c6; color: white; border-radius: 5px; font-weight: bold;">🇬🇧</a>
</div>
<br>

<a name="magyar"></a>

# Párizs 2024 Olimpiai Elemző Dashboard - Power BI

Ez a projekt egy interaktív Microsoft Power BI riport, amely a 2024-es Párizsi Olimpia részletes eredményeit és statisztikáit dolgozza fel. A dashboard célja, hogy egy többszintű, adatvezérelt betekintést nyújtson a globális trendektől kezdve egészen az egyedi sportolói és nemzeti teljesítményekig.

A riport több, egymással összekapcsolt oldalból áll, amelyek lehetővé teszik a felhasználó számára, hogy a globális áttekintéstől eljusson egészen egy adott sportág vagy nemzet mélyelemzéséig.

## A Riport Oldalai

A projekt négy fő nézetből épül fel, amelyek között gombokkal lehet navigálni.

### 1. Főoldal (Világáttekintés)

A projekt nyitóoldala egy "at-a-glance" (egy pillantással áttekinthető) felület, amely a legfontosabb globális mutatókat és trendeket összegzi.

**Főbb funkciók és vizualizációk:**

* **Központi Navigáció:** A Párizs 2024 logó alatt elhelyezett gombok ("Országok eredményei", "Sportág statisztikák", "Világtérkép") biztosítják a zökkenőmentes navigációt a riport különböző oldalai között.
* **Oldalszintű Szűrés (Slicers):** A "Gold", "Silver", és "Bronze" gombok segítségével a felhasználó az egész oldalt dinamikusan szűrheti éremtípus szerint.
* **Főbb KPI Kártyák:** Azonnali betekintés az érmesek teljes számába (2252) és a magyar érmek számába (25).
* **Top 10 éremtáblázat:** Halmozott sávdiagram a 10 legeredményesebb nemzetről, éremtípus (arany, ezüst, bronz) szerinti bontásban.
* **TOP 3 ország éremtáblázat alakulása:** Vonaldiagram, amely a három vezető nemzet éremszerzésének napi trendjét mutatja az olimpia ideje alatt.
* **Érmesek korfája:** Népességpiramis, amely az érmes sportolók demográfiai megoszlását mutatja kor és nem (Férfi/Nő) szerint.
* **Aranyérmek száma az érmek számához viszonyítva:** Pontdiagram, amely az összes érem és az aranyérmek arányát vizsgálja országonként, kiemelve a trendvonalat.
* **Dinamikus Infókártyák:** DAX mértékekkel azonosítja a legfiatalabb (TREW Arisa) és legidősebb (KRAUT Laura) érmest a teljes adatbázisban.

---

### 2. Országok Szereplése (Részletes Elemzés)

Ez az oldal egy "deep-dive" (mélyelemző) nézetet biztosít, ahol egy tetszőlegesen kiválasztott ország teljesítménye vizsgálható részletesen.

**Főbb funkciók és vizualizációk:**

* **Interaktív Kereső:** Egy szöveges keresőmező (slicer) lehetővé teszi, hogy a felhasználó bármelyik résztvevő országot kiválassza (a képen "Hungary" van szűrve). Az oldal összes vizualizációja dinamikusan frissül a kiválasztott országnak megfelelően.
* **Dinamikus KPI-ok:** A kártyák a kiválasztott ország érmeinek számát (25) és az éremtáblázaton elért hivatalos helyezését (18) mutatják.
* **Részletes Éremtáblázat:** Egy görgethető táblázat listázza a kiválasztott ország összes érmes sportolóját, nevet, kort, nemet, sportágat és versenyszámot is beleértve.
* **Dinamikus Infókártyák:** Az oldal automatikusan kiemeli a kiválasztott ország (pl. Magyarország) legeredményesebb sportágát (Canoe Sprint), legeredményesebb olimpikonját (CSIPES Tamara), valamint legfiatalabb (MARTON Viviana) és legidősebb (GEMESI Csanad) érmesét.

---

### 3. Sportág Statisztikák (Összehasonlító Oldal)

Ezen az oldalon a felhasználó két különböző sportágat választhat ki és hasonlíthat össze közvetlenül, egymás mellett, demográfiai és teljesítménybeli szempontokból.

**Főbb funkciók és vizualizációk:**

* **Sportág Választók:** Két legördülő menü (slicer) szolgál a két sportág (a képen "Athletics" és "Fencing") kiválasztására.
* **Párhuzamos Elemzés:** A riport két hasábra van osztva, mindkét oldalon ugyanazokat a vizualizációkat mutatva a kiválasztott sportágra szűrve:
    * **KPI Kártya:** A sportágban elérhető versenyszámok száma.
    * **Sportág korfája (Népességpiramis):** A sportágra jellemző nemi és korbeli eloszlás.
    * **Korcsoportok szerinti érem táblázat:** Halmozott sávdiagram, amely az éremeloszlást mutatja korcsoportonként.
    * **Dinamikus kártyák:** Kiemelik a sportág legeredményesebb országát, olimpikonját és a kor-extrémumokat (legfiatalabb/legidősebb).

---

### 4. Világtérkép (Geografikus Elemzés)

Ez a nézet az érmek globális, földrajzi eloszlását mutatja be egy interaktív világtérképen (Choropleth Map).

**Főbb funkciók és vizualizációk:**

* **Choropleth Térkép (Shape Map):** Az országok az általuk szerzett összes érem darabszáma alapján vannak színezve.
* **Színlegenda:** A "MedalBin" (Érem kategória) alapján működik. **Minél sötétebb kék egy ország, annál több érmet szerzett** (a skála 0-5 éremtől 251-500 éremig terjed).

---

## Kiemelt Technikai Megoldások

A riport hatékonyságát és dinamizmusát komplex DAX mértékek és egy jól felépített adatmodell biztosítja.

### Egyedi Rangsorolási Logika (DAX)

Az "Országok Szereplése" oldalon látható "Helyezett" (Rank) nem egy egyszerű éremszámon alapul. A hivatalos olimpiai rangsorolási szabályoknak megfelelően egy egyedi, súlyozott pontszámot (`@OsszPontszam`) használ a rangsorolás alapjául, amely az aranyérmeket részesíti előnyben.

A pontszám DAX képlete a következő:

```dax
OsszPontszam = (Arany * 1000000) + (Ezüst * 1000) + Bronz
```
Ez a megközelítés biztosítja, hogy a rangsorolás (amelyet valószínűleg egy RANKX függvény használ ezzel a mértékkel) mindig a helyes sorrendet adja vissza: az aranyérmek száma az elsődleges, döntetlen esetén az ezüst, majd a bronz számít.


<a name="english"></a>

# Paris 2024 Olympic Analysis Dashboard - Power BI

This project is an interactive Microsoft Power BI report that analyzes the detailed results and statistics of the Paris 2024 Olympics. The dashboard aims to provide a multi-level, data-driven insight from global trends down to individual athlete and national performances.

The report consists of multiple interconnected pages, allowing the user to drill down from a global overview to a deep-dive analysis of a specific sport or nation.

## The Report's Pages

The project is built around four main views, with button-based navigation between them.

### 1. Main Page (World Overview)

The project's landing page is an "at-a-glance" dashboard summarizing the most important global metrics and trends.

**Key Features and Visualizations:**

* **Central Navigation:** Buttons located under the Paris 2024 logo ("Országok eredményei" [Country Results], "Sportág statisztikák" [Sport Statistics], "Világtérkép" [World Map]) provide seamless navigation between the report pages.
* **Page-Level Slicers:** "Gold", "Silver", and "Bronze" buttons allow the user to dynamically filter the entire page by medal type.
* **Main KPI Cards:** Provides instant insight into the total number of medalists (2252) and the number of Hungarian medals (25).
* **Top 10 Medal Table:** A stacked bar chart showing the 10 most successful nations, broken down by medal type (gold, silver, bronze).
* **TOP 3 Countries Medal Trend:** A line chart that displays the daily medal acquisition trend for the three leading nations throughout the Olympics.
* **Athlete Age Pyramid:** A population pyramid illustrating the demographic distribution of medal-winning athletes by age and gender (Male/Female).
* **Gold Medals vs. Total Medals:** A scatter plot that examines the ratio of total medals to gold medals by country, highlighting the trendline.
* **Dynamic Info Cards:** Uses DAX measures to identify the youngest (TREW Arisa) and oldest (KRAUT Laura) medalists in the entire database.

---

### 2. Country Performance (Detailed Analysis)

This page provides a "deep-dive" view where the performance of any selected country can be examined in detail.

**Key Features and Visualizations:**

* **Interactive Search:** A text search box (slicer) allows the user to select any participating country (the image is filtered for "Hungary"). All visualizations on the page update dynamically based on the selected country.
* **Dynamic KPIs:** The cards display the selected country's total medal count (25) and its official rank on the medal table (18).
* **Detailed Medal Table:** A scrollable table lists all medal-winning athletes from the selected country, including their name, age, gender, sport, and event.
* **Dynamic Info Cards:** The page automatically highlights the selected country's (e.g., Hungary's) most successful sport (Canoe Sprint), most successful Olympian (CSIPES Tamara), and its youngest (MARTON Viviana) and oldest (GEMESI Csanad) medalists.

---

### 3. Sport Statistics (Comparison Page)

On this page, the user can select and directly compare two different sports based on demographics and performance.

**Key Features and Visualizations:**

* **Sport Slicers:** Two dropdown menus (slicers) are used to select the two sports for comparison (in the picture: "Athletics" and "Fencing").
* **Side-by-Side Analysis:** The report is split into two columns, showing the same set of visualizations for each selected sport, allowing for direct comparison of:
    * **KPI Card:** The number of events available in the sport.
    * **Sport Age Pyramid:** The typical gender and age distribution for the sport.
    * **Medal Table by Age Group:** A stacked bar chart showing medal distribution by age group.
    * **Dynamic Cards:** Highlight the sport's most successful country, Olympian, and age extremes (youngest/oldest).

---

### 4. World Map (Geographic Analysis)

This view presents the global, geographical distribution of medals on an interactive world map (Choropleth Map).

**Key Features and Visualizations:**

* **Choropleth Map (Shape Map):** Countries are colored based on the total number of medals they have won.
* **Color Legend:** The coloring is based on "MedalBin" (Medal Bins). **The darker blue a country is, the more medals it has won** (the scale ranges from 0-5 medals up to 251-500).

---

## Featured Technical Solutions

The report's effectiveness and dynamism are powered by complex DAX measures and a well-structured data model.

### Custom Ranking Logic (DAX)

The "Helyezett" (Rank) shown on the "Country Performance" page is not based on a simple medal count. Following official Olympic ranking rules, it uses a custom, weighted score (`@OsszPontszam`) as the basis for ranking, which prioritizes gold medals.

The DAX formula for the score is as follows:

```dax
OsszPontszam = (Arany * 1000000) + (Ezüst * 1000) + Bronz
```
This approach ensures that the ranking (likely using a RANKX function with this measure) always returns the correct order: the number of gold medals is primary, followed by silver, and then bronze in case of a tie.
