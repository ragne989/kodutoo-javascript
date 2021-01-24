
# Ülesanne 1

## 1. Vasta küsimustele:Mis on HTML tag "<noscript>"? Milleks seda kasutatakse ja mis on sellel seost Javascriptiga?

Html'is kasutatakse <noscript> märgist alternatiiv teksti lisamiseks veebidokumenti. Seda juhuks kui külastaja brauser ei toeta skripti. Selle asemel kuvatakse tekst, mis jääb <noscript> ja </noscript> märgiste vahele.

## 2. Mis on Vanilla Javascript (kirjapilt tihti ka VanillaJS)?

Vanilla JS on kiire, kerge ja platvormidevaheline raamistik uskumatute ja võimsate JavaScripti rakenduste loomiseks.Vanilla JS meeskond hoiab raamistikus iga baidi koodi ja töötab iga päev kõvasti, et veenduda, et see on väike ja intuitiivne. Seda kasutavad näiteks Facebook, Google, YouTube, Yahoo, Wikipedia, Twitter, Amazon, LinkedIn, MSN,eBay, Microsoft, Tumblr, Apple, Pinterest, PayPal, Reddit, Netflix jne

## #. Mis on DOM?

DOM: Document Object Model
DOM on eeskiri selle kohta, kuidas objekte (tekst, pildid, pealkirjad, lingid jne.) veebilehel esitada. DOM määrab ära, millised atribuudid kuuluvad millise objekti juurde ning kuidas objekte ja atribuute käsitleda.


## 3. Mis on skoop (ingl.k "scope") programmeerimise mõistes?Vihje: https://www.w3schools.com/js/js_scope.asp

Skoop on muutujate kehtivuspiirkond. Osa programmist, kus muutuja deklaratsioon kehtib, ehk muutuja on nähtav. Saavad olla lokaalsed või globaalsed. Muutujad funktsiooni sees ei ole väliselt nähtavad ja kui muutuja defineeritakse väljaspool funktsiooni, on see juurdepääsetav igale scriptile ja veebilehele.Mis vahe on muutujate defineerimisel kasutatavatel Javascripti keywordidel nagu let ja var?
Vihje: https://javascript.info/var

Esiteks on var vana ja ei kasutata enam uutes scriptides, kuid vanemates võid seda siiski veel leida.
Miinused let´i ees: Kuna var ignoreerib koodiplokke, on ta põhimõtteliselt alati globaalne muutuja. Sama asi kehtib ka loopimise (silmustamise) kohta- var on globaalne. Var on sisemine muutuja vaid juhul, kui koodiplokk on funktsiooni sees. Lisaks on variga muutujat deklareerides võimalik sama nime mitu korda kasutada, see ei anna errorit, kuid samas ei muuda ka midagi, sest var on juba varem deklareeritud. Vari puhul ei ole ka vahet, kas see realselt defineeritakse funktsiooni alguses või lõpus, töödeldakse see siiki funktsiooni alguses.

## 6. Mis on ECMAScript ja mis seos on sellel Javascriptiga?

 Vihje 1: https://www.w3schools.com/js/js_versions.asp
ECMAScript on Javascripti ametlik nimi.

## 7.Mis on JSON? Kirjuta lihtne JSON formaadis string, mis sisaldab 5 kursusekaaslase nime
Vihje 1: https://www.w3schools.com/js/js_json.asp
Vihje 2: JSON stringi saab ka kui Javascript objekt stringiks teha: https://www.w3schools.com/js/js_json_stringify.asp

JSON on andmete salvestamise ja transportimise vorming. Kasutatakse tihti andmete saatmisel serverist veebilehele.

let obj = { name:[ "Airika", "Ingrid", "Kevin", "Taive", "Vaire"] };let myJSON = JSON.stringify(obj);


## 8. Mis on AJAX? Mis on peamine piirang AJAX päringu teostamisel?
Vihje: Vastuse piirangu osas leiab siit: https://www.w3schools.com/js/js_ajax_http.asp

Ajax päring on läbi JavaScripti välja kutsutud asünkroonne HTTP päring, millega võib kaasa anda GET ja POST parameetreid ning mille tulemus (serverist väljastatud vastus) antakse kindlaks määratud JavaScript funktsioonile töötlemiseks. Asünkroonsus annab võimaluse päringu töötlemise ajal tegeleda millegi muuga. Kui päring õnnestub ja vastus on käes, teeb programm andmetega vajaliku töö ära ning näitab kasutajale tulemust. Päringute teostamine on nii kiirem kui tervet lehte uuesti laadides. Peamiseks piiranguks on see, et turvakaalutlustel ei luba modernsed browserid juurdepääsu üle domeenide. See tähendab, et mõlemad, nii veebileht, kui HML fail, mida see proovib laadida, peavad asuma samas serveris.

## 9. Mis vahe on kui javascript pannakse HTML-s <head> tagide vahele vs <body> tagide vahle vahetult enne </body> tagi?
Vihje: https://www.w3schools.com/js/js_whereto.asp

Kui panna tagide vahele vahetult enne tagi, siis see kiirendab lehe kuvamise kiirust, sest script interpreteerimine aeglustab lehe laadimist.

## 10. Võta lahti mõni veebileht Google Chromega. Ava konsool (CTRL + Shift + j) ja trüki konsooli järgnev:
document.designMode = 'on';
Mis selle tagajärjel juhtus? Mida veebilehega nüüd teha saab?

Saab kõike muuta. Kohe veebilehel. Teksti kustutada ja juurde lisada. Väga hea teadmine.