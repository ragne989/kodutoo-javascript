# Ülesanne 1

## Mis on regulaaravaldis (ingl. k. Regular expression aka regex)?

Vihje: https://www.w3schools.com/jsref/jsref_obj_regexp.asp
Regulaaravaldis on lihtsamalt öeldes otsingumuster.
Kasutatakse kontrollimiseks, kas sõne vastab kindlale mustrile või kas seal sisaldub otsitavat mustrit.
Regulaaravalise abil saab näiteks automatiseerida tekstitöötlust - kustutada, teha asendusi jms.


## Kirjuta regulaaravaldis, mis valideerub vaid juhul kui string on alfanumeeriline (sisaldab ainult tähemärke ja numbreid). NB! Tähemärgid tõstutundetud.

Vihje: regex'i katsetamiseks hea koht: https://regex101.com/
/[a-zA-Z0-9]/


## Kirjuta regulaaravaldis, mis kontrollib kas string algab ühe kuni kahekohalise numbriga.

Näide: "12kolm" ja "1kaks" valideeruks, "123neli" ei valideeruks.
/^[0-9]{1,2}[a-zA-Z]+$/

^ - sõne algus
[0-9] - numbrid 0...9
{1,2} - 1 kuni 2 korda
[a-zA-Z] - väike- või suurtähed
+ - kordab vahetult eelnevat avaldist vähemalt ühe korra
$ - sõne lõpp

## Kirjuta regulaaravaldis, mis kontrollib kas ainult numbritest koosnev string on täpselt kümnekohaline.

/^[0-9]{10}$/

^ - sõne algus
[0-9] - numbrid 0...9
{10} - 10 korda
$ - sõne lõpp


## Mis on JSONP ja kuidas ta erineb AJAX päringust?

Vihje: https://www.w3schools.com/js/js_json_jsonp.asp
JSONP (JSON with Padding) on meetod JSON andmete edastamiseks domeenide vaheliste piiranguteta (AJAXiga ei saa domeenide vahelisi päringuid teostada).
Kasutab <script> tage.
<script src="demo_jsonp.php"></script>
Dünaamiliselt lisatud (teisisõnu pärast DOMi laadimist) <script></script> tagides olevate skriptide laadimine on asünkroonne, mis tähendab seda, et teiste lehel olevate skriptide tööd ei takistata.


## Mis on rekursioon ja mis on rekursiivne funktsioon?

Rekursioon ehk iseennast väljakutsuv käitumine.
Rekursiivne funktsioon on funktsioon, mis kutsub ennast ise välja:
function recursiveFunction() {
  recursiveFunction(); // Kutsub iseennast välja
}
Rekurssivsete funktsioonidega tasub olla ettevaatlik, et ei tekiks lõpmatut ringsõltuvust. Funktsioonis peab sisalduma ka kontrollmehanism, mis rekursiooni peatab.


## Mis on Javascript setInterval vs setTimeout funktsioonide põhimõtteline erinevus?

Vihje: https://www.w3schools.com/js/js_timing.asp
setTimeout(function, milliseconds)
Käivitab funktsiooni peale defineeritud aja (millisekundites) möödumist
setInterval(function, milliseconds)
Sama, mis setTimeout(), kuid jääb funktsiooni väljakutsumist kordama defineeritud ajalise intervalli (millisekundites) tagant.


## Mis on "minified" kood? Mis on levinud hea praktika "minified" javascript failide nimekonventsioonis? Miks "minified" koodi kasutatakse?

Vihje: https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js VS https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.js - mis erinevust näete?
Minified ressurss on see, kust on eemaldatud kõikvõimalikud üleliigsed tähemärgid.
Tihti on minified Javascripti failides lisaks üleliigsete reavahetuste, tühikute eemaldamisele lühendatud ka muutujate, funktsioonide jms nimetusi.
Minifitseerimist kasutatakse peamiselt selleks, et failide suurus oleks võimalikult väike ja seega ka nende poole pöördumise ning sisu laadimise aeg võimalikult lühike.
Nimekonventsioon on tavaliselt selline, et enne faililaiendit lisatakse .min faili nimesse. Näiteks myScript.min.js.


## Nimeta erinevaid Javascripti DOM elementide selector funktsioone ja too välja nende peamised erinevused.

Vihje: näiteks document.getElementById('mingiId') - sarnaseid on mõned veel.
Vihje: https://www.w3schools.com/js/js_htmldom_elements.asp
getElementById('id') // HTML element ID attribuudi järgi (tagastab konkreetse elemendi)
getElementsByTagName('p') // Kõik HTML elemendid tag'i järgi (tagastab massiivi)
getElementsByClassName('small') // Kõik HTML elemendid, millel on CSS klass (tagastb massiivi)
querySelector('.small') // Esimene HTML element klassiga "small" (NB! tagastab esimene vaste)
querySelectorAll('p.small') // Kõik HTML <p> elemendid klassiga "small" (tagastab massiivi)
Kirjuta Javascript selector, mis tagastab ainult esimese(!) <p> elemendi.
const firstParagraph = document.querySelector('p');
Kirjuta Javascript selector, mis tagastab kõik(!) <p> elemendid massiivina, mis lehel leiduvad.
const paragraphs = document.querySelectorAll('p');


## Mis on Javascripti keyword "this"?

Vihje: https://www.w3schools.com/js/js_this.asp
this viitab objektile, millele ta kuulub.
Näiteks <button> elemendi click eventListener funktsiooni sees viitab this nupu objektile.


## Mida teeb "async" antud HTML-s: <script src="myscript.js" async></script>

Vihje: https://www.w3schools.com/tags/att_script_async.asp
async skript laetakse taustal, ning lehe kuvamist ei takistata.
Skript käivitatakse kohe kui ta on laetud, teisisõnu ta ei ole sõltuv sellest kas DOM on täielikult laetud ja kas mõni teine skript veel lehel laeb.


## Mida teeb "defer" antud HTML-s: <script src="myscript.js" defer></script>

Vihje: https://www.w3schools.com/tags/att_script_defer.asp
defer skriptid, nagu ka async skriptid laetakse taustal nii, et lehe kuvamist ei takistata, kuid defer ootab ära DOM'i täieliku laadimise, ning ootab ära ka teised skriptid, mis on järjekorras enne teda ja alles siis käivitab oma sisu.
##Mõnikord brauser/veebilehitseja salvestab veebilehe komponendid (CSS, JS failid jne) lehe kiiremaks kuvamiseks (cache kasutamine). Kuidas saab arendaja sundida HTML poolelt veebilehitsejat CSS või JS faile uuesti alla laadima nii, et veebilehitseja caches leiduvat sisu ei kasutaks?
Vihje: https://developer.dynamsoft.com/dwt/kb/2878 <-- Aegunud viide
Veebilehitsejad salvestavad tihti külastatud lehe ressursse (näit. CSS'i, Javascripti) vahemällu (cache'i) lehe kiiremaks laadimiseks.
Veebiarendajad võivad lehel midagi muuta, näiteks lisada uusi stiile või muuta javaskripti käitumist.
Kui veebilehe külastajal on aga vanad väärtused vahemälus, siis ei pruugi uuendused kasutaja brauseris kajastuda.
Kasutaja saab ka ise cache'i invalideerida tehes hard refresh'i: https://www.getfilecloud.com/blog/2015/03/tech-tip-how-to-do-hard-refresh-in-browsers/#.X9_X0NgzZPZ
Tihti kasutajad ei oska seda teha või ei tea, et nad peaksid seda tegema.
Et sellist situatsiooni ei tekiks, siis ressursid versioneeritakse, mis sunnib brauseri vastavat ressurssi uuesti alla laadima.
<!-- Pane tähele GET parameetrit v=1 -->
<script src="http://example.com/script.js?v=1"></script>
Muidugi see GET parameeter võib olla ükskõik millise nimega, nimetus v ja väärtus 1 oli lihtsalt näide.


## Kuidas dünaamiliselt luua veebilehele uusi elemente? Kirjuta näide Javascriptis, kus lood uue <textarea> elemendi, paned sisuks: "Tere tulemast tore telemast!" ning lisad readonly attribuudi. ##Lõpetuseks lisad selle vastloodud elemendi HTML <body> viimaseks elemendiks.

Vihje: https://www.w3schools.com/jsref/met_document_createelement.asp
const textarea = document.createElement('textarea');
textarea.value = 'Tere tulemast tore telemast!';
textarea.readOnly = true;
document.body.appendChild(textarea);


## Mis on anonüümne funktsioon?

Vihje: https://www.w3schools.com/js/js_function_definition.asp
Tavaliselt on funktsioonidel nimed:
function doSomething() {
  // Doing something
}
Antud juhul on funktsiooni nimeks doSomething.
Anonüümne funktsioon on funktsioon millele pole antud nime.
Näiteks kui muutujale omistatakse väärtus, mis on funktsioon:
const doSomething = function() {
  // Doing something
};

doSomething(); // Kutsutakse välja muutuja nime järgi. Sulud "()" tähendavad, et "käivita" muutuja ja kuna muutuja väärtuseks on funktsioon, siis seda saab käivitada


## Mis on Javascript substring? Kasutades substringi kirjuta skript, mis eraldab sõna "lennu" sõnast "kuulilennuteetunneliluuk".

substring on olemuselt ühe sõne alam-sõne ehk mingi fragment sõnest.
Sõne on olemuselt tähemärkide massiiv. Seega igal tähemärgil on sõnes indeks.
Tuletan meelde, et elemendi indeksid algavad massiivis 0'ga!
const lennu = 'kuulilennuteetunneliluuk'.substring(5, 10); // Alusta tähemärgiga indeksil 5 ja lõpeta tähemärgiga indeksil 10 = "lennu"

