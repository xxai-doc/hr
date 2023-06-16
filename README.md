<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Preporuča se prvo instalirati nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , a zatim `direnv allow` nakon ulaska u direktorij ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) će se automatski izvršiti nakon ulaska u direktorij).

Značenje je: kineski prijevod na japanski, korejski, engleski, engleski prijevod na sve ostale jezike. Ako želite podržati samo kineski i engleski, možete samo napisati `zh: en` .

Značenje je: kineski prijevod na japanski, korejski, engleski, engleski prijevod na sve ostale jezike. Ako želite podržati samo kineski i engleski, možete samo napisati `zh: en` .

* [front-end kod](https://github.com/xxai-art/web)
* [Jezični paketi za web mjesto u cjelini](https://github.com/xxai-art/web/tree/main/i18n)
* [Jezični paketi za module za prijavu](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Višejezična dokumentacija web stranice](https://github.com/xxai-doc)

Prednji programski jezik je [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , koji dodaje neke značajke temeljene na sintaksi coffeescripta, pogledajte [./coffee_plus.md](./coffee_plus.md) .

## Internacionalizacija web stranica i dokumenata

Nadogradite na sljedeća 3 projekta

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Sufiks je `.mdt` , možete koristiti sintaksu sličnu `<+ ./coffee_plus/import.js>` za upućivanje na vanjske datoteke i generirati markdown sa sufiksom `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown prijevod neće prevoditi kodove i veze, te će predmemorirati prevedene rečenice. Ako je prijevod izmijenjen, ali izvorni tekst nije izmijenjen, njegovo ponovno izvođenje neće prebrisati izmjenu prijevoda.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Jezične datoteke za prevođenje `yaml` generiranih web stranica.

### Upute za automatizaciju prijevoda dokumenata

Vidi repozitorij kodova [xxai-art/doc](https://github.com/xxai-art/doc)

Preporuča se prvo instalirati nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , a zatim `direnv allow` nakon ulaska u direktorij ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) će se automatski izvršiti nakon ulaska u direktorij).

Kako bih izbjegao veliku bazu koda prevedenu na stotine jezika, stvorio sam zasebnu bazu koda za svaki jezik i stvorio organizaciju za pohranjivanje baze koda

Postavljanjem varijable okoline `GITHUB_ACCESS_TOKEN` i pokretanjem [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) automatski će se stvoriti spremište koda.

Naravno, možete ga staviti i u bazu kodova.

Referenca skripte prijevoda [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Kod skripte tumači se na sljedeći način:

[bunx](https://bun.sh/docs/cli/bunx) je zamjena za npx, koji je brži. Naravno, ako nemate instaliran bun, umjesto njega možete koristiti `npx` .

`bunx mdt zh` prikazuje `.mdt` u direktoriju zh kao `.md` , pogledajte 2 povezane datoteke u nastavku

* [kava_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [kava_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` je osnovni kod za prevođenje (ako imate instaliran samo `nodejs` , ali `bun` i `direnv` nisu instalirani, također možete pokrenuti `npx i18n` za prevođenje).

Analizirat će [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfiguracija `i18n.yml` u ovom dokumentu je sljedeća:

```
en:
zh: ja ko en
```

Značenje je: kineski prijevod na japanski, korejski, engleski, engleski prijevod na sve ostale jezike. Ako želite podržati samo kineski i engleski, možete samo napisati `zh: en` .

Posljednji je [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , koji izvlači sadržaj između glavnog naslova i prvog podnaslova `README.md` svakog jezika kako bi generirao unos `README.md` . Kod je vrlo jednostavan, možete ga sami pogledati.

Za besplatno prevođenje koristi se Google API. Ako ne možete pristupiti Googleu, konfigurirajte i postavite proxy, kao što je:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Skripta za prijevod će generirati prevedenu predmemoriju u direktoriju `.i18n` , molimo provjerite je s `git status` i dodajte je u repozitorij koda kako biste izbjegli ponavljanje prijevoda.

Molimo pokrenite `bunx i18n` svaki put kada izmijenite prijevod da ažurirate predmemoriju.

Ako se originalni tekst i prijevod modificiraju u isto vrijeme, predmemorija će biti zbunjena, pa ako želite modificirati, možete modificirati samo jedan, a zatim pokrenuti `bunx i18n` da ažurirate predmemoriju.
