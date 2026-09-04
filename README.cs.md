# Strojové učení pro adaptaci autonomních agentů

[English](README.md) | **Česky**

Výzkumný úkol, Fakulta jaderná a fyzikálně inženýrská ČVUT v Praze, 2024.
Katedra softwarového inženýrství. Vedoucí práce: Ing. Josef Nový, Ph.D.

EN: *Machine Learning for the Adaptation of Autonomous Agents*

---

## O co jde

Rešerše a návrh: příprava pro stavbu herního AI protivníka, který se v reálném čase přizpůsobí
hráči místo toho, aby jel podle pevného stromu chování. Práce prochází, jak se herní AI reálně
staví ve vydaných hrách, probírá možnosti strojového učení a na závěr navrhuje konkrétní
architekturu agenta i způsob, jak ho hodnotit.

Jde o předchůdce mé [diplomové práce](../../DP), ve které byl agent implementován.

## Obsah

**1. AI ve hrách.** Historie od Turingovy úpravy algoritmu Minimax pro šachy přes Chinook, Deep
Blue, TD-Gammon až po AlphaGo. Následují techniky, které se ve hrách skutečně používají:
konečné automaty, stromy chování a AI založená na užitečnosti, včetně jejich kompromisů. Dvě
případové studie 3D akčních her s nadprůměrnou umělou inteligencí: automatizované plánování ve
hře F.E.A.R. (potomek systému STRIPS, kde každá akce nese předpoklady a účinky) a systém Nemesis
ze hry *Middle-Earth: Shadow of Mordor* a *Shadow of War*.

**2. Strojové učení.** Čtyři paradigmata s reprezentativními algoritmy: učení s učitelem (metoda
podpůrných vektorů, rozhodovací stromy), učení bez učitele (k-means, hierarchické shlukování,
Apriori a GSP pro těžbu častých vzorů), částečně řízené učení (generativní adverzní sítě)
a zpětnovazební učení.

**3. Návrh agenta.** Navržené prostředí, postavené jako střílečka z pohledu první osoby v Unreal
Engine, a dvoudílný agent: SARSA pro volbu výbavy vojáků, protože jde o malý kontrolovaný
prostor, kde se nic nemění náhodně, a Deep Q-Learning pro rozhodování na bojišti, kde je stavový
prostor velký a neustále se mění.

**4. Návrh hodnocení.** Tři způsoby hodnocení agenta, z nichž každý ho podle předpokladu
posunuje k jiné strategii: efektivita zabíjení (rychlí a křehcí útoční vojáci, nebo jeden těžce
obrněný a nepohyblivý), efektivita přežití (důraz na brnění, nebo mobilní odstřelovač) a
kombinace obojího.

## Jak to nakonec dopadlo

Stojí za to říct rovnou, protože navazující práce změnila směr: **implementovaný agent
nepoužívá SARSA ani Deep Q-Learning.** Diplomová práce ho postavila na Proximal Policy
Optimization.

Důvod byl praktický. Implementace využívá plugin NevarokML, který propojuje Unreal Engine se
Stable-Baselines3, a z algoritmů, které nabízí, se PPO ukázalo jako lepší kompromis mezi
stabilitou učení, implementační složitostí a použitelností v nestacionárním prostředí
s diskrétním akčním prostorem. Zde navržené rozdělení (jeden algoritmus na výbavu, druhý na boj)
nahradila jediná multi head politika, která řeší pohyb, rotaci, střelbu i volbu výbavy
dohromady.

Do implementace se naopak přenesl přístup k hodnocení z části 4, a to v podobě odměnové funkce,
která vyvažuje přesnost míření, udržování vzdálenosti a úspěšnou eliminaci.

## Obsah repozitáře

Zdrojový LaTeX a zkompilovaný text.

## Citace

```
JOCHEC, Martin. Strojové učení pro adaptaci autonomních agentů.
Výzkumný úkol. Praha: ČVUT, Fakulta jaderná a fyzikálně inženýrská, 2024.
Vedoucí práce Ing. Josef Nový, Ph.D.
```
