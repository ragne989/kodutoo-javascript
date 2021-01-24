# Kodutöö nr. 4

## Mis on CDN? Kirjuta näide, kus kasutad oma HTML lehel CDN'i mõne CSS ja/või JS faili importimiseks.

Content Delivery Network või Content Distribution Network on sisuedastusvõrk, millesse kuulub hulk servereid, mis serveerivad sama sisu, kuid erinevates geograafilistes asukohtades.
Selliselt tagatakse kasutajale kiirem ressursside laadimine ja seeläbi ka parem kasutajakogemus.
Mida lähemal on andmeid/faile serveeriv server füüsiliselt, seda vähem kulub aega päringule vastuse saamiseks.
Näiteks veebiarenduse kontekstis on vaja kasutada mõne teise osapoole ressursse, teeke - jQuery teeki või Bootstrap kaskaadlaadistikku.
Sellisel juhul on mõistlik kasutada CDN'i nende ressursside pärimiseks.
Näide:
<html>
    <head>
        <title>CDN kasutamise näide</title>
    </head>
   <body>
      Some content...
      
      <!-- jQuery importimine CDN'i abil -->
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
   </body>
</html>


## Mis on VCS (Version Control System) e versioonihaldus ja mis eesmärke see täidab tarkvaraarenduses? Too näiteid populaarseimatest VCS -dest.

Versioonihaldus võimaldab säiitada tarkvara muudatusi (versioone) selliselt, et igal ajal on võimalik taastada mingi versiooni hetkeseis, vaadata millised muutused on tehtud jne. Lisaks võimaldab versioonihaldus töötada projektiga nii (branch'id), et teisi sama projektiga töötavaid arendajaid muudatustega ei segata.
Populaarsemad versioonihaldustarkvarad: Git, SVN, Mercurial


## Mis on code-review? Miks seda tehakse? Kes seda tegema peaks?

Code-review on protsess, mida teostatakse tarvaaraarenduse meeskondades lähtekoodi kvaliteedi ja nõuetele vastavuse tagamiseks.
Selle käigus kontrollitakse näiteks kas lähtekood vastab meeskonnas kokku lepitud koodistiilile, standarditele ja üldistele tarkvaraarenduse headele praktikatele.
Kontrollitakse kas muudatused vastavad ülesande püstitusele. Otsitakse võimalikke vigu, turvanõrkusi. Sealhulgas antakse edasi ka teadmisi.
Code-review'd teostab keegi teine peale koodi autori. Üldjuhul teostavad ülevaatuse mõned meeskonna kogenumad arendajad.
Praktika on näidanud, et need arendajad, kelle meeskonnas on code-review üheks arendusprotsessi osaks, arenevad erialaselt kiiremini ja suudavad luua ka kvaliteetsemaid lahendusi.


## Mis on event delegation ja mis juhtudel ta hea on?

Javascriptis saab lisada HTML elementidele teatud sündmuste kuulamise, mille esinemisel rakendatakse soovitud toiming.
Näiteks click sündmus elemendil klikkimise registreerimiseks.
Kui elemente, millele sündmuste kuulaja lisatakse, on dokumendis(veebileht) väga palju, siis võib dokument muutuda liigse ressurssikasutuse tõttu aeglaseks.
Kujutage ette, et teil on HTML tabel, kus on 10 000 lahtrit ja igal lahtril peab olema click sündmuse kuulaja.
Sellisel juhul oleks mõistlik panna click sündmuse kuulamine tervele tabelile ja sündmust protsessiva koodi sees kontrollida kas ja millisele lahtrile vajutati.
Näide:
// Üks event listener kogu tabelile, delegeerime <td> elementide click sündmuste kuulamise ühele <table> elemendile, 
// mille alla antud <td> elemendid kuuluvad
someTableElement.addEventListener('click', (event) => {
    const target = event.target; // Sündmuse target (element, millele klikiti)
    if (target && target.tagName !== 'TD') { // Kontrolli kas klikitud element oli tabeli lahter
        return; // Oleme huvitatud vaid <td> elementidele vajutustest, välju funktsioonist
    }
    // ... protsessi <td> elemendile vajutust
});


## Mis on closure?

Closure ehk sulund on viis kuidas kasutada pesastatud (nested) funktsiooni sees selle skoobist välja jäävaid muutujaid.
Selgitav näide:
function greeting() {
    const message = 'Hi';
    
    // Pesastatud funktsioon
    function sayHi() {
        console.log(message); // Pääseb ligi "message" muutujale
    }
    sayHi();
}

greeting();


## Mis on throttling? Milleks see hea on?

Throttling on viis kuidas protsessida suurt hulka identseid päringuid nii, et neile ei vastata, mitte iga päringu peale, vaid korra määratud aja jooksul.
Nõnda saab ressursiahnete arvutuste puhul oluliselt arvutusi ja seeläbi ka ressursse kokku hoida.
Kujutage ette, et nupuvajutuse peale tehakse AJAX päring serverisse mingi suure hulga andmete protsessimiseks vms.
Mõni kärsitu või pahatahtlik kasutaja võib teie serveri korduvate nupuvajutuste peale tõsiselt üle koormata. Throttling kaitseb teid selle eest.
Näite lähtekood (Live demo):
<!DOCTYPE html>
<html lang="et">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>JavaScript | Throttling</title>
</head>

<body>
<button id="throttle">Paina mind!</button>
<p>Nupuvajutusele regeeritakse üks kord 1.5s jooksul. Vaata konsooli ...</p>
<script>
  document.getElementById('throttle').addEventListener('click', throttle(() => {
    console.log('Nupuvajutus')
  }, 1500));

  function throttle(callback, delay) {
    let prev = 0;
    return (...args) => {
      const now = new Date().getTime();
      if (now - prev > delay) {
        prev = now;
        return callback(...args);
      }
    }
  }
</script>
</body>
</html>


## Mis on debouncing? Milleks see hea on?

Debouncing on väga sarnane throttling meetodiga, kuid väikese erinevusega.
Erinevus seisneb selles, et toimingut tehakse alles siis kui määratud aeg viimasest kasutaja tegevusest on möödunud.
Näiteks situatsioon kus teil on veebilehel otsingu tekstikast, mis klahvivajutuste peale automaatselt tulemusi otsib/kuvab.
Tundub mugav?
Paraku võivad otsingud ja filtreerimised olla kulukad operatsioonid, seega pole mõistlik iga klahvivajutuse peale kohe otsingu koodi käivitada vaid oodata hetkeni, mil kasutaja on lõpetanud trükkimise.
Kui klahvivajutuste vahele jääb murdosa sekundist, siis järelikult kasutaja veel trükib oma otsingusõna ja otsingu koodi ei ole mõistlik käivitada.
Näite lähtekood (Live demo):
<!DOCTYPE html>
<html lang="et">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>JavaScript | Debouncing</title>
</head>
<body>
<p>Kirjuta tekstikasti kiirest ja siis aeglaselt, et näha debounce efekti.</p>
<input id="debounce" type="text" placeholder="Sisesta otsingusõna">
<p id="search-input"></p>
<script>
  const input = document.getElementById('debounce');
  input.addEventListener('keyup', debounce(handleSearchInput, 500));

  function handleSearchInput() {
    document.getElementById('search-input').textContent = `Otsisid fraasi "${input.value}"`;
  }

  function debounce(callback, wait) {
    let timeout;
    return function executedFunction(...args) {
      const later = () => {
        clearTimeout(timeout);
        callback(...args);
      };
      clearTimeout(timeout);
      timeout = setTimeout(later, wait);
    };
  }
</script>
</body>
</html>


## Mis on üks kõige enam kasutatud javascripti teek jQuery?

Teek, mis lihtsustab ja kiirendab veebilehtedel kasutatava koodi kirjutamist.
jQuery slogan on: "write less, do more".
Laialdaste võimalustega teek, mis sobib hästi HTML elementide DOM'st pärimiseks, animeerimiseks, sündmuste manageerimiseks jne.


## Too välja jQuery head küljed võrreldes VanillaJS'ga.

Lihtsustab DOMi muudatuste tegemist läbi väiksema hulga koodiridade.


## Too välja ka mõned miinused jQuery kasutamisel.

jQuery negatiivsed mõjud veebilehele võivad olla:
•	Veebileht on sõltuv jQuery teegist.
Näiteks jQuery CDN ei tööta. Veebilehe funktsionaalsus kannatab.
•	jQuery teek on mahukas - võib aeglustada lehe laadimist.
•	jQuery on aeglasem kui vanilla-js.
•	jQuery kasutamine pärsib vanilla-js oskuste õppimist.
Oleks õigem teha selgeks vanilla-js enne kui kasutada jQueryt.
•	jQuery versioonide konfliktid.
Võib juhtuda, et lehel vajavad erinevad imporditud teegid/raamistikud erinevaid jQuery versioone, mis tekitab veebilehel konflikte.

