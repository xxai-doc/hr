<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Dio koda web stranice je otvorenog koda, dobrodošli da pomognete optimizirati prijevod.

## front-end kod

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
