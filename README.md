# Son Gokuren CV digitala

## 1. Proiektuaren deskribapena

Lan honetan Son Gokuren curriculum vitae digitala egin dut HTML eta CSS erabiliz.

CV bi zati nagusitan banatu dut:

* Ezkerreko zatia: argazkia, datu pertsonalak, gaitasunak, teknikak, hizkuntzak eta esaldi bat.
* Eskuineko zatia: profil profesionala, esperientzia, prestakuntza, lorpenak eta borrokak.

Helburua CV-a txukun antolatzea eta ordenagailuan zein mugikorrean ondo ikustea izan da.


## 2. CV egin aurretik egindako analisia

Programatzen hasi aurretik, irakasleak emandako Son Gokuren CV eredua begiratu nuen eta zatitan banatu nuen.

Nik honela banatu nuen:

1. **Alboko barra**

   * Argazkia
   * Datu pertsonalak
   * Gaitasunak
   * Teknika nagusiak
   * Hizkuntzak
   * Esaldia

2. **Goiburua**

   * Izen-abizenak
   * Lanbidea
   * Kokapena
   * Eskuragarritasuna

3. **Profil profesionala**

   * Profilaren izenburua
   * Deskribapen laburra

4. **Esperientzia**

   * Hiru esperientzia txartel desberdin

5. **Prestakuntza**

   * Lau entrenamendu txartel

6. **Lorpenak eta teknikak**

   * Bi zati, pantaila handietan bata bestearen ondoan

7. **Borroken taula**

   * Aurkaria
   * Emaitza
   * Testuingurua

Zati bakoitzean zer CSS erabili nezakeen ere pentsatu nuen. Adibidez, CV osoa antolatzeko Grid erabiltzea erabaki nuen eta barruko elementu batzuetan Flexbox erabiltzea.

Atal errepikatuak ere bilatu nituen. Adibidez, esperientzia guztiek antzeko itxura dutenez, `.experience-card` klasea erabiltzen dut. Gauza bera egiten dut `.card`, `.skill` eta `.tag` klaseekin.

### CV zatitan banatzea

CV diseinua zatitzeko, GIMP erabiliz atal desberdinak markatu nituen. Horrela, HTML egin aurretik gutxi gorabehera zein egitura izango zuen ikusi ahal izan nuen.


## 3. Diseinuaren planteamendua

**Mobile first** egitea aukeratu dut.

Lehenengo pantaila txikietan nola agertuko den pentsatu dut. Horregatik, `.cv-container` elementuak hasieran zutabe bakarra dauka:

```css
.cv-container {
  display: grid;
  grid-template-columns: 1fr;
}
```

Ondoren, pantaila handietan beste zutabe bat gehitzen dut. Horrela, alboko barra ezkerrean geratzen da eta CV-aren informazio nagusia eskuinean.

Nire ustez, modu honetan errazagoa da mugikorreko diseinutik pantaila handiagora egokitzea.


## 4. HTMLaren egitura

HTML elementu semantikoekin antolatu dut. Erabili ditudan elementu nagusiak hauek dira:

* `header`
* `main`
* `aside`
* `section`
* `article`
* `footer`
* `table`

`aside` elementuan alboko informazioa dago eta `main` elementuan CV informazio nagusia.

Adibidez, datu pertsonalak honela antolatu ditut:

```html
<div class="data-item">
  <span class="label">UBICACIÓN</span>
  <p class="label-value">Monte Paoz, Tierra</p>
</div>
```

Klaseak erabiltzen ditut antzeko elementuei estilo bera emateko.


## 5. CSSaren oinarrizko ezaugarriak

CSS-an aldagaiak erabili ditut `:root` barruan. Horrela, kolore batzuk eta beste balio batzuk behin definitu eta gero hainbat lekutan erabili ditzaket.

Adibidez:

```css
:root {
  --color-primary: #0a3663;
  --color-secondary: #0066cc;
  --color-bg-body: #eef2f5;
  --radius-card: 16px;
}
```

Ondoren:

```css
color: var(--color-primary);
border-radius: var(--radius-card);
```

Horrez gain, `rem` unitatea erabili dut letra tamainetan eta tarte batzuetan.

CSS hasieran ere `box-sizing: border-box` erabili dut:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

Horrela, elementuen tamainak kalkulatzea errazagoa da.


## 6. Grid eta Flexbox

CV egitura nagusia egiteko **CSS Grid** erabili dut.

Hasieran zutabe bakarra dauka:

```css
.cv-container {
  display: grid;
  gap: var(--spacing-lg);
  grid-template-columns: 1fr;
}
```

Pantaila handietan bi zutabe erabiltzen dira:

```css
@media (min-width: 900px) {
  .cv-container {
    grid-template-columns: 350px 1fr;
  }
}
```

Grid beste atal batzuetan ere erabili dut. Adibidez, esperientzia eta prestakuntza antolatzeko.

Prestakuntzan `auto-fit` eta `minmax()` erabili ditut txartelak espazioaren arabera egokitzeko:

```css
.training-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: var(--spacing-md);
}
```

Flexbox ere erabili dut. Adibidez, goiburuko datuak eta hizkuntzak lerrokatzeko:

```css
.header-details {
  display: flex;
  flex-wrap: wrap;
  gap: var(--spacing-sm) var(--spacing-md);
}
```


## 7. Txartelak

Atal desberdinak banatzeko `.card` klasea erabiltzen dut.

```css
.card {
  background-color: var(--color-bg-card);
  border-radius: var(--radius-card);
  padding: var(--spacing-md);
}
```

Txartelek atzeko kolorea, ertzak biribilduak eta barruko tartea dituzte.

Esperientzia eta prestakuntza txartel desberdinetan banatu ditut. Horri esker, informazioa ez da dena batera agertzen.


## 8. Atzeko irudia eta gradientea

Goiburuan atzeko irudi bat erabili dut:

```css
.header-card {
  background-image:
    linear-gradient(rgba(50, 98, 160, 0.1), rgba(50, 98, 160, 0.1)),
    url("../mountain.png");
}
```

Hemen bi gauza erabiltzen ditut: `mountain.png` irudia eta gradientea.

Gradientea irudiaren gainean jartzen da eta horrela goiburuko testua hobeto ikusten da.


## 9. Gaitasunak eta teknikak

Gaitasunak barra baten bidez erakusten ditut.

Adibidez, 5/5 mailak barra guztiz betetzen du:

```css
.level-5 {
  width: 100%;
}
```

4/5 mailak %80 betetzen du:

```css
.level-4 {
  width: 80%;
}
```

Teknikak berriz, etiketa txikiekin erakusten ditut:

```css
.tag {
  border: 1px solid rgb(165, 165, 240);
  padding: 4px 12px;
  border-radius: var(--radius-pill);
}
```

Adibidez, Kamehameha, Genkidama, Kaio-ken, Shunkan Idō eta Ultra Instinct agertzen dira.


## 10. Responsive diseinua

Webgunea responsive egiteko Media Query-ak erabili ditut.

900px-tik gora CV-a bi zutabetan jartzen da:

```css
@media (min-width: 900px) {
  .cv-container {
    grid-template-columns: 350px 1fr;
  }
}
```

Pantaila txikietan zutabe bakarra erabiltzen da.

Gainera, 420px baino txikiagoak diren pantaila batzuetan izenburuaren tamaina txikitzen dut:

```css
@media (max-width: 420px) {
  .header h1 {
    font-size: var(--font-xl);
  }
}
```

Horrela, izenburua ez da handiegia geratzen mugikorrean.

Taulari ere `overflow-x: auto` eman diot, pantaila txikian zabalera handiegia badauka horizontalki mugitu ahal izateko.


## 11. `calc()` eta `min()` erabilera

Ariketan eskatzen ziren `calc()` eta `min()` funtzioak ere erabili ditut.

`min()` erabiliz, edukiontziaren zabalera mugatzen dut:

```css
.cv-container {
  width: min(95%, 1200px);
}
```

Horrela, edukiontzia ez da 1200px baino handiagoa izango.

`calc()` ere erabili dut:

```css
.quote {
  margin-top: calc(var(--spacing-lg) + 1rem);
}
```

Kasu honetan, goiko marjinari `1rem` gehitzen zaio.


## 12. Taula

Azken zatian Son Gokuren aurkari batzuk erakusten dituen taula bat egin dut.

Taulak hiru zutabe ditu:

* Aurkaria
* Emaitza
* Testuingurua

Emaitzak koloreekin bereizten ditut:

```css
.green-color {
  color: green;
}

.red-color {
  color: red;
}

.yellow-color {
  color: rgb(222, 177, 44);
}
```

Berdea garaipenentzat erabiltzen dut, gorria porrotentzat eta horia emaitza erabakigarriarentzat.


## 13. Fitxategien antolaketa

Proiektua honela antolatuta dago:

```text
proiektua/
│
├── index.html
├── mountain.png
├── goku-avatar(1).jpg
│
└── css/
    └── styles.css
```

* `index.html`: CV-aren HTML egitura.
* `styles.css`: diseinuaren CSS.
* `mountain.png`: goiburuko atzeko irudia.
* `goku-avatar(1).jpg`: Son Gokuren argazkia.


## 14. Ondorioa

Lan honetan HTML eta CSS erabiliz CV digital bat egitea praktikatu dut.

Batez ere Grid, Flexbox, Media Query, CSS aldagaiak, `rem`, `calc()`, `min()`, txartelak eta taulak erabili ditut.

Nire helburua CV informazioa modu ordenatuan jartzea izan da eta, aldi berean, mugikorrean eta ordenagailuan ondo ikustea.

Azken emaitza Son Gokuren CV digital bat da.