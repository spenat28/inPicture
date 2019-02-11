## Databáze

### Majitel

Majitelem je myšlena osoba či organizace, která vlastní a provozuje databázi a její API.
Jediná úloha majitele - udržet server v chodu.
A dočasně: ověření identity redaktora. V budoucnu by ověření mělo být nahrazeno.


### Principy hlavní databáze

Zámek:
	hlasování je po půl roce od vložení informace uzamčeno
	uzamčené informace nelze dále měnit
	
Hlasování lze měnit, dokud není hlasování uzamčeno. Změna hlasu se zvlášť nezaznamenává.

#### Ověřený uživatel

Může zasílat návrhy do redakce a tvořit vlastní obrazy, které také může zasílat jako návrhy.
Může hlasovat pro existující obrazy.

#### Redakce

Redakce

##### Redaktor

* přidává informace
* přidává spojení
* hlasuje o informacích které sám nevytvořil a jsou odemčené
* vytváří pohledy (obrázky)

###### Získání členství v redakci

Ověřený uživatel.
Na počátku: Osobním setkáním s majitelem databáze nebo již ověřeným redaktorem.
Budoucnost: Ověření přes Czechpoint nebo jinou státní či jinou nezávislou autoritu jako OpenID, ...

* určení počtu redaktorů z množství ověřených uživatelů: 10% a zároveň více než 2 a méně nebo rovno 500
* každý půlrok hlasování (v aplikaci)
	* nikdo nemůže hlasovat pro sebe (ošetřeno aplikací)
* průběh hlasování
	* 1. kolo - redakce hlasuje sama mezi současnými členy koho by ráda v radě ponechala
		* 50% méně úspěšných míst je uvolněno - zaokrouhleno dolů na celá čísla
		* kolo trvá 14 dnů
	* 2. kolo - všichni ověření uživatelé hlasují pro obsazení uvolněných míst mezi všemi existujícími uživateli, kteří mají zašktnuto, že chtějí být redaktory
		* kolo trvá 14 dnů

##### Rada

* práva rady
	+ diskvalifikovat redakatora - s možností:
		- diskvalifikovat všechna jeho zaznamenaná hlasování
		- zpochybnit jím zadané neuzamčené informace
	+ odemknout (hlasováním) hlasování u již zamčené informace
	+ hlasovat o uzamčení informace

##### diskvalifikace probíhá

* návrh jedním z členů rady (kliknutím v aplikaci)
* hlasováním
* 2/3 hlasů z počtu hlasujících jsou potřeba pro diskvalifikaci
* hlasování probíhá 1 týden nebo do vyčerpání počtu hlasujících členů

###### Členství v radě

* určení počtu křesel z množství redaktorů: 10% a zároveň více než 2 a méně nebo rovno 50
* každý půlrok hlasování (v aplikaci)
	* nikdo nemůže hlasovat pro sebe (ošetřeno aplikací)
* průběh hlasování
	* 1. kolo - rada hlasuje sama mezi současnými členy koho by ráda v radě ponechala
		* 50% méně úspěšných křesel je uvolněno - zaokrouhleno dolů na celá čísla
		* kolo trvá 14 dnů
	* 2. kolo - všichni redaktoři hlasují pro obsazení uvolněných křesel mezi všemi existujícími redaktory, kteří mají zaškrtnuto, že chtějí být v radě
		* kolo trvá 14 dnů
