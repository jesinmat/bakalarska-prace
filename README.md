# Automatický provisioning herních serverů pomocí cloudové image

Bakalářská práce. Fakulta informačních technologií ČVUT, 2020.

Autor: Matyáš Ješina

Vedoucí práce: Ing. Tomáš Vondra, Ph.D.

## Zadání

Některé počítačové hry hrané po síti vyžadují pro každou hru mít spuštěný zvláštní server. To je předurčuje
k nasazení v cloudu, kde je velmi snadné takové servery snadno vytvářet a rušit. V cloudu je zákazník zvyklý
software neinstalovat, ale vybrat si již hotový image operačního systému s předinstalovaným softwarem.
1. Analyzujte možnosti automatického sestavování obrazů operačních systémů a automatizované instalace
herních serverů.
2. Opakovatelným skriptovaným způsobem vytvořte image, který bude podporovat instalaci několika
populárních her a bude použitelný laickým uživatelem virtualizace/cloudu.
3. Image na cloud musí splňovat několik podmínek, aby byl bezpečný, například si po startu nastavit
náhodné heslo a přegenerovat všechny klíče a identifikátory, aby nebyly sdíleny s jinými virtuálními stroji.
Popište tyto bezpečnostní prvky Vašeho řešení.
4. Celé řešení dobře zdokumentujte a otestujte.
5. Zhodnoťte výsledek práce a diskutujte další možná rozšíření.

## Abstrakt

Tato práce se zabývá problematikou automatického nasazování herních serverů a jejich provozu v cloudovém prostředí.
Zkoumá možnosti nasazování aplikací v cloudu za účelem nalezení nejefektivnějšího způsobu
a popisuje vytvoření obrazu systému, který je pro dané využití vhodný. Tento systém je schopný podporovat množství herních serverů
bez nutnosti jeho časté změny a je snadno rozšiřitelný i pro další hry v budoucnosti.

Výsledkem je obraz systému určeného pro provoz herních serverů, který je bezpečný, obsahuje jen nezbytně nutné součásti a dá se jednoduše nasadit v cloudovém prostředí.
Celý proces jeho sestavení a následné instalace serveru je plně automatizovaný.

## Stažení

Zdrojové kódy vypracovaného systému jsou ke stažení v samostatných repozitářích. Jedná se o systém [GameServer Appliance](https://github.com/jesinmat/tkl-gameserver) a správce herních serverů [Linux GameServers](https://github.com/jesinmat/linux-gameservers). Repozitáře obsahují popis jednotlivých součástí včetně návodu k použití.

Výsledná podoba bakalářské práce včetně sestaveného obrazu systému je k dispozici v tomto repozitáři v záložce [Releases](https://github.com/jesinmat/bakalarska-prace/releases).

## Sestavení

Návod k sestavení obrazu systému a zkompilování PDF bakalářské práce najdete v [docs/README.md](https://github.com/jesinmat/bakalarska-prace/tree/master/docs).