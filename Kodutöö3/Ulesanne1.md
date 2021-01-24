# Kodutöö nr. 3


## Mis on mitmedimensiooniline massiiv? Too näide kasutades Javascripti.

Vihje: http://www.javascripttutorial.net/javascript-multidimensional-array/
Mitmedimensiooniline massiiv on andmekogu, mille elementideks on omakorda massiiv(id).
Näiteks massiiv, mille elementideks on teine massiiv on kahedimensiooniline massiiv e 2D massiiv.
Massiiv, mille elementideks on teine massiiv, mille elementideks on kolmas massiiv on kolmedimensiooniline massiiv e 3D massiiv.
Üks lihtsamaid näiteid on trips-traps-trull mängulaud, mis koosneb kolmest reast ja tulbast:
const BOARD = [
    ['X', '', ''],
    ['', 'X', ''],
    ['', '', 'X']
];
Ülaltoodud näide on 2D massiiv.
Saamaks teada, mis on esimese rea esimese tulba lahtri väärtus, on tarvis küsida element selle indeksi (või kui soovite - koordinaadi) järgi:
BOARD[0][0]; // Massiivi esimese elemendi (mis on ka massiiv) esimene väärtus: X tähemärk


## Kuidas püüda ja töödelda vigu Javascripti poolel? Too näide kasutades Javascripti.

Vihje: https://www.w3schools.com/jsref/jsref_try_catch.asp
Vigade ehk Error objektide püüdmine Javascripti poolel toimub try...catch ploki sees:
try {
    doSomething();
} catch (error) {
    // Kui doSomething funktsioon viskas vea/errori, siis selle saab turvaliselt kinni püüda catch plokis ja vastavalt töödelda.
    console.log('Oh no! Error happened while doSomething was called!');
}


## Kuidas tekitada erindeid (exceptions) Javascriptis. Too näide.

Vihje: https://www.w3schools.com/jsref/jsref_throw.asp
Erind (exception) on mingi eriolukord (mitte tingimata viga), mis programmi töö jooksul ilmneb.
Üldjuhul programmi töö seiskub erindi tõttu.
Selleks, et programmi töö ootamatult ei lõppeks, tuleb erindeid töödelda, ehk programmile öelda, mida erindi puhul ette võtta.
Javascriptis saab erindi (Errori) tekitada ka tahtlikult kasutades throw võtmesõna:
throw 'Number liiga väike!'; // Tekitab Error objekti, mis peatab programmi töö sõnumiga "Number liiga väike!"
throw võib edastada sõne, numbrit, boolean'i või objekti.


## Kirjuta näide, mis kombineerib kahte eelmist küsimust (erindi loomine ja püüdmine).

Nagu eelnevates vastustes selgitatud toimub erindite püüdmine try...catch ploki sees.
Piisab kui lisame throw eelnimetatud ploki sisse, et saada soovitud tulemus.
try {
    throw "Can't divide by zero!";
} catch (error) {
    console.log(error);
}


## Mida teeb finally plokk?

finally plokk on try...catch valikuline osa, mis käivitatakse sõltumata sellest kas error visati või mitte.
finally plokis olev kood käivitatakse alati!
try {
  // Koodiosa, mis võib lõppeda erroriga
}
catch(err) {
  // Koodiosa, mis töötleb errorit juhul kui see peaks juhtuma
}
finally {
  // Koodiosa, mis käivitatakse alati olenemata kas error on eelnevalt juhtunud või mitte
}


## Mis on HTML elemendi data atribuut?

Vihje: https://www.w3schools.com/tags/att_global_data.asp
data atribuudiga saab tavalistele HTML elementidele anda kaasa lisainfot, mida on mugav Javascripti poolel küsida ja töödelda.
HTML elementide data-* atribuudid on täielikult ignoreeritud veebilehitseja poolt ja mõeldud üksnes Javascripti ning CSS -ga kombineerimiseks.


## Kirjuta kood, mis eraldab data atribuudi coordinate elemendist ja prindib selle väärtuse konsooli:

<p data-coordinate-x="1234">Mingisuvatekst</p>
Vihje: https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes
const element = document.querySelector('p'); // <p> elemendi saamiseks DOM -st.
const xCoordinate = element.dataset.coordinateX; // Pane tähele, et kebab-case on asendatud camelCase -ga
console.log(xCoordinate);


## Kuidas Javascriptiga veebilehel andmeid salvestada?

Vihje: https://www.w3schools.com/jsref/obj_storage.asp
Javascriptiga saab talletada informatsiooni hilisemaks kasutamiseks kasutades localStorage või sessionStorage API -sid.
Mõlema API puhul salvestatakse andmed võti/vaste paaridena külastaja brauserisse (mitte veebiserverisse).
Seetõttu ei tohi kunagi eeldada, et informatsioon kasutaja brauseris on püsiv. Vähem kriitiliste andmete hoidmiseks sobiv.


## Mis vahe on localStorage VS sessionStorage?

localStorage salvestab andmed võti/vaste paarina brauserisse aegumistähtajata.
sessionStorage sarnane eelmisega selle erinevusega, et kui veebileht suletakse, siis salvestatud andmed kustuvad.


## Mis on "küpsised"?

Vihje: https://www.w3schools.com/js/js_cookies.asp
Küpsised on väikesed tekstifailid veebilehe külastaja arvutis, kus saab hoida informatsiooni veebilehe külastaja kohta.
Küpsistes saab hoida näiteks kasutaja sessiooni ID-d, et veebiserveril oleks lihtsam tuvastada kas sessioon on kehtiv ja vastavalt sellele nõuda kasutajalt sisselogimist.
Küpsistele saab omistada aegumistähtaja (vaikimisi aegub küpsis kohe kui leht suletakse, just nagu sessionStorage puhul).
Samuti saab öelda millise lehel asuva teekonna kohta küpsis kehtib.
Näiteks kui teil on leht example.com ja te soovite, et küpsis kehtiks vaid example.com/shopping-cart teekonnal, siis seda saab küpsises määratleda.

