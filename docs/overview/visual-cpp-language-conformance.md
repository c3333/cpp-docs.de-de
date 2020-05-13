---
title: 'Microsoft C++-Sprachkonformität: Tabelle'
description: Hier wird eine Tabelle mit Updates der Microsoft C++-Sprachkonformität je nach Visual Studio-Version angezeigt.
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 18f8db28fab83f795baced82a346f07d73256716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365237"
---
# <a name="microsoft-c-language-conformance-table"></a>Microsoft C++-Sprachkonformität: Tabelle

Die Standardkonformität für den Microsoft C++-Compiler in Visual Studio (MSVC) ist in Bearbeitung. Nachfolgend finden Sie eine Zusammenfassung der C++ ISO-Standardsprache und der Bibliothekskonformität geordnet nach Visual Studio-Version. Jeder Name eines Features im Compiler und in der Standardbibliothek verweist auf das C++ ISO-Standardvorschlagsdokument, in dem das Feature beschrieben ist, falls zum Zeitpunkt der Veröffentlichung ein solches Dokument verfügbar ist. Die Spalte **Unterstützt** gibt die Visual Studio-Version an, in der das Feature zum ersten Mal unterstützt wurde.

Weitere Informationen zu Verbesserungen der MSVC-Konformität in Visual Studio 2017 oder 2019 finden Sie in [Verbesserungen der C++-Konformität in Visual Studio](cpp-conformance-improvements.md). Eine Liste weiterer Änderungen finden Sie unter [Neuerungen bei Visual C++ in Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Kompatibilitätsänderungen in früheren Versionen finden Sie unter [Änderungsverlauf von Visual C++ von 2003 bis 2015](../porting/visual-cpp-change-history-2003-2015.md) und [Visual C++ What's New 2003 through 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md) (Visual C++ – Neuerungen von 2003 bis 2015). Aktuelle Nachrichten vom C++-Team finden Sie im [C++-Teamblog](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Es gibt keine binären Änderungen zwischen Visual Studio 2015, Visual Studio 2017 und Visual Studio 2019. Weitere Informationen finden Sie unter [Kompatibilität von C++-Binärdateien zwischen Visual Studio 2015, 2017 und 2019](../porting/binary-compat-2015-2017.md).

## <a name="compiler-features"></a>Compilerfeatures

|  |  |
|--|--|
| __Hauptsprachfeatures von C++03/11__ | __Unterstützt__ |
| &nbsp;&nbsp;Alles andere | VS 2015 <sup>[A](#note_A)</sup> |
| &nbsp;&nbsp;Zwei-Phasen Namenssuche | VS 2017 15.7 <sup>[B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 SFINAE für Ausdrücke](https://wg21.link/N2634) | VS 2017 15.7 |
| &nbsp;&nbsp;[N1653 C99-Präprozessor](https://wg21.link/N1653) | Teilweise <sup>[C](#note_C)</sup> |
| __Hauptsprachfeatures von C++14__ | __Unterstützt__ |
| &nbsp;&nbsp;[N3323 Optimierte Formulierungen für kontextbezogene Konvertierungen](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 Binäre Literale](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[N3638 Rückagebetypen „auto“ und „decltype(auto)“](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-captures](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 Generische Lambda-Ausdrücke](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[N3760: \[\[deprecated\]\]-Attribut](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[N3778 Zuordnungsaufhebung mit Größenangabe](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3781 Zahlentrennzeichen](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[N3651 Variablenvorlagen](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 Erweiterte constexpr](https://wg21.link/n3652) | VS 2017 15.0 |
| &nbsp;&nbsp;[N3653: Standardmemberinitialisierer für Aggregate](https://wg21.link/n3653) | VS 2017 15.0 |
| __Hauptsprachfeatures von C++17__ | __Unterstützt__ |
| &nbsp;&nbsp;[N4086 Entfernen von Trigraphen](https://wg21.link/n4086) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 Neue Regeln für „auto“ mit „braced-init-lists“](https://wg21.link/n3922) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4051 „typename“ in Vorlagen-Vorlagenparametern](https://wg21.link/n4051) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4266 Attribute für Namespaces und Enumeratoren](https://wg21.link/n4266) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267 u8-Zeichenliterale](https://wg21.link/n4267) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4230 Geschachtelte Namespacedefinitionen](https://wg21.link/n4230) | VS 2015.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 Knappes static_assert](https://wg21.link/n3928) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 Generalisierte bereichsbasierte for-Schleifen](https://wg21.link/p0184r0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0188R1: \[\[fallthrough\]\]-Attribut](https://wg21.link/p0188r1) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 Entfernen des register-Schlüsselworts](https://wg21.link/p0001r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 Entfernen von operator++ für bool](https://wg21.link/p0002r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 *dies nach Wert erfassen](https://wg21.link/p0018r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 Verwenden des Attribut Namespaces ohne Wiederholung](https://wg21.link/p0028r4) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1: \_\_has_include](https://wg21.link/p0061r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 Direct-Liste-Init von festen Enumerationen von Ganzzahlen](https://wg21.link/p0138r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 constexpr-Lambdas](https://wg21.link/p0170r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1: \[\[nodiscard\]\]-Attribut](https://wg21.link/p0189r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0212R1: \[\[maybe_unused\]\]-Attribut](https://wg21.link/p0212r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0217R3 Strukturierte Bindungen](https://wg21.link/p0217r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 constexpr if-Anweisung](https://wg21.link/p0292r2) | VS 2017 15.3 <sup>[D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 Auswahlanweisungen mit Initialisierern](https://wg21.link/p0305r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 Hexfloat-Literale](https://wg21.link/p0245r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268 Mehr Nicht-Typen-Vorlagenargumente erlauben](https://wg21.link/n4268) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4295 Fold-Ausdrücke](https://wg21.link/n4295) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Entfernen von dynamischen Ausnahmespezifikationen](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 noexcept zum Typsystem hinzufügen](https://wg21.link/p0012r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 Über-ausgerichtete dynamische Speicherbelegung](https://wg21.link/p0035r4) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 Inline-Variablen](https://wg21.link/p0386r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 Übereinstimmender template-Vorlagenparameter zu kompatiblen Argumenten](https://wg21.link/p0522r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 Entfernen einiger leerer unärer Folds](https://wg21.link/p0036r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 Qualifikationskonvertierungen beheben](https://wg21.link/n4261) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 Erweiterte ungültige Aggregatinitialisierung](https://wg21.link/p0017r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0091R3 Vorlagenargumentableitung für Klassenvorlagen](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0 Probleme mit der Argumentableitung für Klassenvorlagen](https://wg21.link/p0512r0) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 Deklarieren von Nichttyp-Vorlagenparameter mit auto](https://wg21.link/p0127r2) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 Garantierte copy elision](https://wg21.link/p0135r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0136R1 Umformulierung der Konstruktorvererbung](https://wg21.link/p0136r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std::launder](https://wg21.link/p0137r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 Reihenfolge der Ausdrucksauswertung optimieren](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 Auswertungsreihenfolge von Funktionsargumenten](https://wg21.link/p0400r0) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0195R2 Pack-Erweiterungen in der using-Deklarationen](https://wg21.link/p0195r2) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 Ignoriert nicht erkannte Attribute](https://wg21.link/p0283r2) | VS 2015 <sup>[14](#note_14)</sup> |
| __Hauptsprachfeatures von C++17 (Fehlerberichte)__ | __Unterstützt__ |
| &nbsp;&nbsp;[P0702R1 Beheben von Problemen mit der Argumentableitung für Klassenvorlagen für „initializer-list ctors“](https://wg21.link/p0702r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1: Lockern der Regeln für das Suchen von Anpassungspunkten von strukturierten Bindungen](https://wg21.link/p0961r1) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0: Zulassen strukturierter Bindungen an zugängliche Members](https://wg21.link/p0969r0) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1: Vereinfachen der Erfassung impliziter Lambdas](https://wg21.link/p0588r1) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[\[nodiscard\]\] für Konstruktoren](https://wg21.link/p1771r1) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0: Zusammengeführte Formulierungen für P0527R1 und P1155R3, ausführlichere Verschiebungen](https://wg21.link/p1825r0) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2: Überprüfen auf abstrakte Klassentypen](https://wg21.link/P0929R2) | Nein |
| &nbsp;&nbsp;[P0962R2: Lockern der Regeln für das Suchen von Anpassungspunkten von range-for-Schleifen](https://wg21.link/p0962r1) | Nein |
| &nbsp;&nbsp;[P0859R0 CWG 1581: Wann werden constexpr-Memberfunktionen definiert?](https://wg21.link/p0859r0) | Nein |
| &nbsp;&nbsp;[P1009R2: Arraygrößenableitung in neuen Ausdrücken](https://wg21.link/P1009R2) | Nein |
| &nbsp;&nbsp;[P1286R2: Contra CWG DR1778](https://wg21.link/P1286R2) | Nein |
| __Hauptsprachfeatures von C++20__ | __Unterstützt__ |
| &nbsp;&nbsp;[P0704R1 Beheben von „const lvalue ref“-qualifizierten Zeigern auf Member](https://wg21.link/p0704r1) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4: Konvertieren von char16_t/char32_t-Zeichenfolgenliteralen in UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0: Ändern des aktiven Members einer Union in constexpr](https://wg21.link/P1330R0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0: noexcept for \<chrono> zero(), min(), max()](https://wg21.link/P0972R0) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 Operator für Dreiwegevergleich <=> (Raumschiffoperator)](https://wg21.link/P0515R3) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2: Makros für Featuretest](https://wg21.link/P0941R2) | VS 2019 16.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1: Unterbindung von Aggregaten mit benutzerdeklarierten Konstruktoren](https://wg21.link/P1008R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 Designierte Initialisierung](https://wg21.link/p0329r4) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0: ADL und Funktionsvorlagen, die nicht sichtbar sind](https://wg21.link/P0846R0) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2: Zulassen von „lambda-capture \[=, this\]“](https://wg21.link/p0409r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 Bekannte Vorlagensyntax für generische Lambdas](https://wg21.link/p0428r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2: Konstruierbare und zuweisbare zustandslose Standard-Lambdas](https://wg21.link/P0624R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2: Zulassen der Paketerweiterung in Lambda „init-capture“](https://wg21.link/P0780R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2: Kennzeichnen der impliziten Erfassung als veraltet per \[=\]](https://wg21.link/P0806R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0: Konsistenzverbesserungen für <=> und andere Vergleichsoperatoren](https://wg21.link/P1120R0) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2: \<=\> != ==](https://wg21.link/P1185R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0734R0 Konzepte](https://wg21.link/P0734R0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0: Beheben von Funktionalitätslücken in Einschränkungen](https://wg21.link/P0857R0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2: Derzeitige Rückgabetypanforderungen sind unzureichend](https://wg21.link/P1084R2) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2: Bedingt explizit](https://wg21.link/P0892R2) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3: Erweitern von strukturierten Bindungen zur Annäherung an Variablendeklarationen](https://wg21.link/P1091R3) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5: Verwenden einer Aufzählung](https://wg21.link/P1099R5) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3: Wann wird \<=>](https://wg21.link/P1186R3) tatsächlich verwendet? | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1: Spaceship benötigt Überarbeitung](https://wg21.link/P1630R1) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 Hinzufügen von \_\_VA_OPT\_\_ für das Auslassen und Löschen von Kommas](https://wg21.link/P0306R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1: Bereichsbasierte for-Schleifen mit Initialisierern](https://wg21.link/P0614R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 Standardmemberinitialisierer für „bit-fields“](https://wg21.link/P0683R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1: try-catch-Blöcke in constexpr-Funktionen](https://wg21.link/P1002R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 Veraltete Verwendung des Kommaoperators bei Indizierungsausdrücken](https://wg21.link/P1161R3) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[\[nodiscard("message")\]\]](https://wg21.link/P1301R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 Erkennen von Headereinheitimporten erfordert vollständige Vorverarbeitung](https://wg21.link/P1703R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 Zulassen der Standardverwendung von Vergleichen nach Wert](https://wg21.link/P1946R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2: const-Konflikt mit Standardkopierkonstruktor](https://wg21.link/P0641R2) | Partial |
| &nbsp;&nbsp;[P0912R5: Coroutinen](https://wg21.link/P0912R5) | Partial |
| &nbsp;&nbsp;[P1103R3: Module](https://wg21.link/P1103R3) | Partial |
| &nbsp;&nbsp;[P0315R4: Zulassen von Lambdas in nicht ausgewerteten Kontexten](https://wg21.link/P0315R4) | Nein |
| &nbsp;&nbsp;[P0388R4 Zulassen von Konvertierungen in Arrays mit unbekannter Grenze](https://wg21.link/P0388R4) | Nein |
| &nbsp;&nbsp;[P0479R5: \[\[likely\]\]- und \[\[unlikely\]\]-Attribut](https://wg21.link/P0479R5) | Nein |
| &nbsp;&nbsp;[P0634R3: Gegen Typnamen!](https://wg21.link/P0634R3) | Nein |
| &nbsp;&nbsp;[P0692R1: Lockern der Zugriffsprüfung für Spezialisierungen](https://wg21.link/P0692R1) | Nein |
| &nbsp;&nbsp;[P0722R3: Löschen mit effizienter Größe für Klassen mit variabler Größe](https://wg21.link/P0722R3) | Nein |
| &nbsp;&nbsp;[P0732R2: Klassentypen in Vorlagenparametern ohne Typ](https://wg21.link/P0732R2) | Nein |
| &nbsp;&nbsp;[P0735R1 Interaktion von memory_order_consume mit Releasesequenzen](https://wg21.link/P0735R1) | Nein |
| &nbsp;&nbsp;[P0784R7 Weitere constexpr-Container](https://wg21.link/P0784R7) | Nein |
| &nbsp;&nbsp;[P0840R2: \[\[no_unique_address\]\]-Attribut](https://wg21.link/P0840R2) | Nein |
| &nbsp;&nbsp;[P0848R3 Bedingt triviale spezielle Memberfunktionen](https://wg21.link/P0848R3) | Nein |
| &nbsp;&nbsp;[P0960R3: Zulassen der Initialisierung von Aggregaten über eine in Klammern gesetzte Liste mit Werten](https://wg21.link/P0960R3) | Nein |
| &nbsp;&nbsp;[P1064R0: Zulassen von virtuellen Funktionsaufrufen in konstanten Ausdrücken](https://wg21.link/P1064R0) | Nein |
| &nbsp;&nbsp;[P1073R3: Direkte Funktionen](https://wg21.link/P1073R3) | Nein |
| &nbsp;&nbsp;[P1094R2: Geschachtelte Inlinenamespaces](https://wg21.link/P1094R2) | Nein |
| &nbsp;&nbsp;[P1139R2: Beheben von Wortlautproblemen in Bezug auf ISO 10646](https://wg21.link/P1139R2) | Nein |
| &nbsp;&nbsp;[P1141R2: Ein weiterer Ansatz für eingeschränkte Deklarationen](https://wg21.link/P1141R2) | Nein |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | Nein |
| &nbsp;&nbsp;[P1152R4 „volatil“ als veraltet markiert](https://wg21.link/P1152R4) | Nein |
| &nbsp;&nbsp;[P1236R1: Ganze Zahlen mit Vorzeichen sind Zweierkomplement](https://wg21.link/P1236R1) | Nein |
| &nbsp;&nbsp;[P1327R1: Zulassen von polymorpher dynamic_cast typeid in konstanten Ausdrücken](https://wg21.link/P1327R1) | Nein |
| &nbsp;&nbsp;[P1331R2 Zulassen der trivialen Standardinitialisierung in constexpr-Kontexten](https://wg21.link/P1331R2) | Nein |
| &nbsp;&nbsp;[P1353R0: Fehlende Makros für Featuretest](https://wg21.link/P1353R0) | Nein |
| &nbsp;&nbsp;[P1381R1: Verweiserfassung von strukturierten Bindungen](https://wg21.link/P1381R1) | Nein |
| &nbsp;&nbsp;[P1452R2 Über die nicht einheitliche Semantik von Rückgabetypanforderungen](https://wg21.link/P1452R2) | Nein |
| &nbsp;&nbsp;[P1616R1 Verwenden von nicht eingeschränkten TTPs mit eingeschränkten Vorlagen](https://wg21.link/P1616R1) | Nein |
| &nbsp;&nbsp;[P1668R1 Zulassen der nicht ausgewerteten Inlineassembly in constexpr-Funktionen](https://wg21.link/P1668R1) | Nein |
| &nbsp;&nbsp;[P1766R1 Beheben von kleineren Modulproblemen](https://wg21.link/P1766R1) | Nein |
| &nbsp;&nbsp;[P1811R0 Abschwächen der Neudefinitionsgseinschränkungen für die Neuexportierungsstabilität](https://wg21.link/P1811R0) | Nein |
| &nbsp;&nbsp;[P1814R0 Argumentableitung für Klassenvorlagen für Aliasvorlagen](https://wg21.link/P1814R0) | Nein |
| &nbsp;&nbsp;[P1816R0 Argumentableitung für Klassenvorlagen für Aggregate](https://wg21.link/P1816R0) | Nein |
| &nbsp;&nbsp;[P1874R1 Dynamische Initialisierungsreihenfolge von nicht lokalen Variablen in Modulen](https://wg21.link/P1874R1) | Nein |
| &nbsp;&nbsp;[P1907R1 Inkonsistenzen mit Nichttyp-Vorlagenparametern](https://wg21.link/P1907R1) | Nein |
| &nbsp;&nbsp;[P1971R0 Wesentliche Änderungen für NB-Kommentare vom Treffen im November 2019 (Belfast)](https://wg21.link/P1971R0) | Nein |
| &nbsp;&nbsp;[P1972R0 US105 Überprüfen der Einschränkungszufriedenheit für Nicht-Vorlagen beim Bilden eines Zeigers auf eine Funktion](https://wg21.link/P1972R0) | Nein |
| &nbsp;&nbsp;[P1975R0 Verbessern der Formulierung der in Klammern gesetzten Aggregatinitialisierung](https://wg21.link/P1975R0) | Nein |
| &nbsp;&nbsp;[P1979R0 Auflösung zu US086](https://wg21.link/P1979R0) | Nein |
| &nbsp;&nbsp;[P1980R0 CA096: Deklarationsübereinstimmung bei nicht abhängigen requires-Klauseln](https://wg21.link/P1980R0) | Nein |

## <a name="standard-library-features"></a>Standardbibliotheksfeatures

|  |  |
|--|--|
| __Standardbibliotheksfeatures von C++20__ | __Unterstützt__ |
| &nbsp;&nbsp;[P0809R0: Vergleichen unsortierter Container](https://wg21.link/p0809r0) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0: Anforderungen des Constexpr-Iterators](https://wg21.link/p0858r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1: Vermeiden unnötigen Verfalls](https://wg21.link/p0777r1) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1: Erhöhen der Intuitivität für create_directory()](https://wg21.link/P1164R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2: remove_cvref](https://wg21.link/p0550r2) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1: unwrap_reference, unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2: starts_with()/ends_with() für basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 contains() für sortierte und unsortierte assoziative Container](https://wg21.link/p0458r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1: list/forward_list remove()/remove_if()/unique() Return size_type](https://wg21.link/p0646r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2: shift_left(), shift_right()](https://wg21.link/p0769r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1: type_identity](https://wg21.link/p0887r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6: atomic\<float>, atomic\<double>, atomic\<long double>](https://wg21.link/p0020r6) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 Endian](https://wg21.link/p0463r1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: Ein Typ für UTF-8-Zeichen und -Zeichenfolgen](https://wg21.link/P0482R6) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1: \[\[nodiscard\]\] Für STL, Teil 1](https://wg21.link/p0600r1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2: to_address()](https://wg21.link/p0653r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2: \<version>](https://wg21.link/p0754r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1: noexcept für Bewegungskonstruktor von std::function](https://wg21.link/P0771R1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1: Behebung von operator>>(basic_istream&, CharT*)](https://wg21.link/P0487R1) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0: Verwenden von move() in \<numeric>](https://wg21.link/p0616r0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1: is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0898R3: Standardbibliothekskonzepte](https://wg21.link/P0898R3) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3: Heterogenes Nachschlagen für unsortierte Container](https://wg21.link/P0919R3) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1: Umbenennung in standard_case](https://wg21.link/P1754R1) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array aus LFTS mit Updates](https://wg21.link/P0325R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3: SFINAE-freundliches underlying_type-Element](https://wg21.link/P0340R3) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5: bind_front()](https://wg21.link/P0356R5) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0: memory_order für Enumerationsklasse](https://wg21.link/p0439r0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bit> Rotations- und Zählfunktionen](https://wg21.link/P0553R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<numbers> Math-Konstanten](https://wg21.link/P0631R8) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2: istream_iterator-Bereinigung](https://wg21.link/P0738R2) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1: Unterstützung für is_pod wird eingestellt](https://wg21.link/P0767R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1: string::reserve() sollte sich nicht verkleinern](https://wg21.link/P0966R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0: erase_if(), erase()](https://wg21.link/P1209R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2: std::ssize() mit Vorzeichen, span::size() ohne Vorzeichen](https://wg21.link/P1227R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 Schmaler Vertrag für ceil2()](https://wg21.link/P1355R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1: is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 Verschieben von endian zu \<bit>](https://wg21.link/P1612R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front() sollte nicht den Umbruch bei reference_wrapper aufheben](https://wg21.link/P1651R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 Optimieren des heterogenen Nachschlagens für unsortierte Container](https://wg21.link/P1690R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 Fehlende Makros für Featuretest 2017-2019](https://wg21.link/P1902R1) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8: atomic_ref](https://wg21.link/P0019R8) | Nein |
| &nbsp;&nbsp;[P0053R7: \<syncstream>](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[P0753R2: osyncstream-Manipulatoren](https://wg21.link/p0753r2) | Nein |
| &nbsp;&nbsp;[P0122R7: \<span>](https://wg21.link/p0122r7) | Nein |
| &nbsp;&nbsp;[P0202R3: constexpr für \<algorithm> und exchange()](https://wg21.link/p0202r3) | Nein |
| &nbsp;&nbsp;[P0339R6: polymorphic_allocator<>](https://wg21.link/P0339R6) | Nein |
| &nbsp;&nbsp;[P0355R7: \<chrono> Kalender und Zeitzonen](https://wg21.link/p0355r7) | Nein |
| &nbsp;&nbsp;[P0357R3: Unterstützung von unvollständigen Typen in reference_wrapper](https://wg21.link/P0357R3) | Nein |
| &nbsp;&nbsp;[P0415R1: constexpr für \<complex> (noch einmal)](https://wg21.link/p0415r1) | Nein |
| &nbsp;&nbsp;[P0475R1: Garantierte Auslassung von „copy“ für stückweise Konstruktion](https://wg21.link/P0475R1) | Nein |
| &nbsp;&nbsp;[P0476R2 \<bit> bit_cast](https://wg21.link/P0476R2) | Nein |
| &nbsp;&nbsp;[P0528R3: Atomisches Vergleichen und Austauschen mit Auffüll-Bits](https://wg21.link/P0528R3) | Nein |
| &nbsp;&nbsp;[P0591R4: Hilfsfunktionen für Uses-Allocator-Konstruktion](https://wg21.link/P0591R4) | Nein |
| &nbsp;&nbsp;[P0608R3: Verbessern des Konvertierungskonstruktors/der Zuweisung der Variante](https://wg21.link/P0608R3) | Nein |
| &nbsp;&nbsp;[P0619R4: Entfernen von veralteten C++17-Features in C++20](https://wg21.link/P0619R4) | Nein |
| &nbsp;&nbsp;[P0653R2: to_address()](https://wg21.link/p0653r2) | Nein |
| &nbsp;&nbsp;[P0655R1 visit\<R>()](https://wg21.link/P0655R1) | Nein |
| &nbsp;&nbsp;[P0674R1 „make_shared()“ für Arrays](https://wg21.link/p0674r1) | Nein |
| &nbsp;&nbsp;[P0718R2: atomic\<shared_ptr\<T>>, atomic\<weak_ptr\<T>>](https://wg21.link/p0718r2) | Nein |
| &nbsp;&nbsp;[P0768R1: Bibliotheksunterstützung für den Spaceship-Vergleichsoperator \<=>](https://wg21.link/p0768r1) | Nein |
| &nbsp;&nbsp;[P0811R3: midpoint(), lerp()](https://wg21.link/P0811R3) | Nein |
| &nbsp;&nbsp;[P0879R0: constexpr für Austauschfunktionen](https://wg21.link/P0879R0) | Nein |
| &nbsp;&nbsp;[P0896R4: \<ranges\>](https://wg21.link/P0896R4) | Nein |
| &nbsp;&nbsp;[P0912R5: Bibliotheksunterstützung für Coroutinen](https://wg21.link/P0912R5) | Nein |
| &nbsp;&nbsp;[P0920R2: Nachschlagen mit vorausberechnetem Hashwert](https://wg21.link/P0920R2) | Nein |
| &nbsp;&nbsp;[P0935R0: Beseitigen von unnötig expliziten Standardkonstruktoren](https://wg21.link/P0935R0) | Nein |
| &nbsp;&nbsp;[P1001R2: execution::unseq](https://wg21.link/P1001R2) | Nein |
| &nbsp;&nbsp;[P1006R1: constexpr für pointer_traits<T*>::pointer_to()](https://wg21.link/P1006R1) | Nein |
| &nbsp;&nbsp;[P1007R3: assume_aligned()](https://wg21.link/P1007R3) | Nein |
| &nbsp;&nbsp;[P1020R1: Erstellung eines intelligenten Zeigers mit Standardinitialisierung](https://wg21.link/P1020R1) | Nein |
| &nbsp;&nbsp;[P1023R0: constexpr für std::array-Vergleiche](https://wg21.link/P1023R0) | Nein |
| &nbsp;&nbsp;[P1032R1: constexpr – Verschiedenes](https://wg21.link/P1032R1) | Nein |
| &nbsp;&nbsp;[P1165R1: Einheitliches Weitergeben von zustandsbehafteten Zuweisungen in operator+() von basic_string](https://wg21.link/P1165R1) | Nein |
| &nbsp;&nbsp;[P1285R0: Verbessern der Vollständigkeitsanforderungen für Typmerkmale](https://wg21.link/P1285R0) | Nein |
| __Standardbibliotheksfeatures von C++17__ | __Unterstützt__ |
| &nbsp;&nbsp;[LWG 2221: Formatierter Ausgabeoperator für nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16.1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 Sichere Konvertierungen in unique_ptr\<T[]>](https://wg21.link/n4089) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 invoke()](https://wg21.link/n4169) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 Entfernen von auto_ptr, random_shuffle(), und altem \<functional> Stuff](https://wg21.link/n4190) | VS 2015 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 noexcept-Bereinigungen](https://wg21.link/n4258) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions()](https://wg21.link/n4259) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 Einfach kopierbare reference_wrapper](https://wg21.link/n4277) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() für map/unordered_map](https://wg21.link/n4279) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 size(), empty(), data()](https://wg21.link/n4280) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 Exakt eingeschränkte unique_ptr-Zuweisungen](https://wg21.link/n4366) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 Verbessern von pair und tuple](https://wg21.link/n4387) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (nicht zeitgesteuert)](https://wg21.link/n4508) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 Unterstützung von unvollständigen Typen in vector/list/forward_list](https://wg21.link/n4510) | VS 2013 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: \<algorithm> sample()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: \<any>](https://wg21.link/n4562#any) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: \<memory_resource >](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 Löschen der polymorphic_allocator-Zuweisung](https://wg21.link/p0337r0) | VS 2017 15.6 |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: \<optional>](https://wg21.link/n4562#optional) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: \<string_view>](https://wg21.link/n4562#string.view) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: \<tuple> apply()](https://wg21.link/n4562#tuple) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Bibliotheksgrundlagen: Boyer-Moore search()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Beheben der Suchprogramm-Rückgabetypen](https://wg21.link/p0253r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Entfernen von dynamischen Ausnahmespezifikationen](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 Veraltete Iostreams-Aliase entfernen](https://wg21.link/p0004r1) | VS 2015.2 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 Korrekturen für not_fn()](https://wg21.link/p0358r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0006R0 Variable Vorlagen für Typmerkmale (is_same_v, usw.).](https://wg21.link/p0006r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const()](https://wg21.link/p0007r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0013R1 Typmerkmale von logischen Operatoren (conjunction, usw.).](https://wg21.link/p0013r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0024R2 Parallele Algorithmen](https://wg21.link/p0024r2)<br/>&nbsp;&nbsp;[P0336R1 Umbenennen der Richtlinien für parallele Ausführung](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 Parallele Algorithmen müssen bei Ausnahmefehlern „terminate()“ aufrufen](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 Vereinheitlichen von parallelen \<numeric>-Algorithmen](https://wg21.link/p0452r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0025R1 clamp()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot(x, y, z)](https://wg21.link/p0030r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0031R0 constexpr für \<array> (erneut) und \<iterator>](https://wg21.link/p0031r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 Homogene Schnittstelle für variant/any/optional](https://wg21.link/p0032r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0033R1 enable_shared_from_this umformulieren](https://wg21.link/p0033r1) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 Erweitern von Speicher-Verwaltungstools](https://wg21.link/p0040r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0063R3 C11-Standardbibliothek](https://wg21.link/p0063r3) | VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0067R5 Elementare Zeichenfolgenkonvertierungen](https://wg21.link/p0067r5) | VS 2019 16.4 <sup>[charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0083R3 Zusammenführen von Zuordnungen und Festlegungen](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 insert_return_type klarstellen](https://wg21.link/p0508r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 Emplace-Rückgabetyp](https://wg21.link/p0084r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0088R3 \<variant>](https://wg21.link/p0088r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](https://wg21.link/p0092r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, usw.](https://wg21.link/p0154r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 Variadic lock_guard](https://wg21.link/p0156r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 Umbenennen von „Variadic lock\_guard“ in „scoped\_lock“](https://wg21.link/p0156r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](https://wg21.link/p0163r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0174R2 Veraltete rudimentäre Bibliotheksteile](https://wg21.link/p0174r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple()](https://wg21.link/p0209r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0218R1 \<filesystem>](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[P0219R1 Relative Pfade für Dateisystem](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[P0317R1 Zwischenspeichern von Verzeichniseinträgen für Dateisystem](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 Unterstützung von string_view in Dateisystempfaden](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 Unterstützung von Nicht-POSIX-Dateisystemen](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 Auflösen von NB-Kommentaren für Dateisystem](https://wg21.link/p0492r2) | VS 2017 15.7 <sup>[E](#note_E)</sup> |
| &nbsp;&nbsp;[P0220R1 Bibliotheksgrundlagen V1](https://wg21.link/p0220r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0226R1 Mathematische spezielle Funktionen](https://wg21.link/p0226r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0254R2 string_view und std::string integrieren](https://wg21.link/p0254r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15.3 <sup>[G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 gcd(), lcm()](https://wg21.link/p0295r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std::byte](https://wg21.link/p0298r3) | VS 2017 15.3 <sup>[17](#note_17),&nbsp;[byte](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 Entfernen der Unterstützung für Zuweisung in std::function](https://wg21.link/p0302r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 Optional wieder größer gleich machen](https://wg21.link/p0307r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0393R3 Variant größer gleich machen](https://wg21.link/p0393r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0403R1 UDLs für \<string_view> ("meow"sv, usw.)](https://wg21.link/p0403r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 Beheben von shared_ptr für Arrays](https://wg21.link/p0497r0) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 atomic compare_exchange memory_order-Anforderungen](https://wg21.link/p0418r2) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr für char_traits](https://wg21.link/p0426r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0433R2 Integrieren der Vorlagenableitung für Klassenvorlagen in die Standardbibliothek](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 Verbessern der Integration der Argumentableitung für Klassenvorlagen in die Standardbibliothek](https://wg21.link/p0739r0) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0435R1 common_type überholen](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 Anpassung von „common\_type“ und „duration“](https://wg21.link/p0548r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 Erneute Betrachtung von in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](https://wg21.link/p0504r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0505R0 constexpr für \<chrono> (erneut)](https://wg21.link/p0505r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 Ablehnen von Varianten von Nothing, Arrays, Verweisen und unvollständigen Typen](https://wg21.link/p0510r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0513R0 Hashwerte verfälschen](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 noexcept-Hash](https://wg21.link/p0599r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 Kopieren von shared_future als noexcept markieren](https://wg21.link/p0516r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 future_error aus future_errc erstellen](https://wg21.link/p0517r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 Veraltete shared_ptr::unique()](https://wg21.link/p0521r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1: Auflösen von Inkonsistenzen in benannten atomic\<T>-Basisklassen](https://wg21.link/p0558r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2: std::is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4: Weitergeben von Copy/Move-Trivialität in variant/optional](https://wg21.link/P0602R4) | VS 2017 15.3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 Ändern von „is\_callable/result\_of“ in „invoke\_result“, „is\_invocable“, „is\_nothrow\_invocable“](https://wg21.link/p0604r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0607R0 Inlinevariablen für die Standardbibliothek](https://wg21.link/p0607r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 Kennzeichnen von „\<codecvt>“ als veraltet](https://wg21.link/p0618r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1: Reparieren von elementaren Zeichenfolgenkonvertierungen](https://wg21.link/P0682R1) | VS 2015 15.7 <sup>[17](#note_17)</sup> |
| __Standardbibliotheksfeatures von C++14__ | __Unterstützt__ |
| &nbsp;&nbsp;[N3462 SFINAE-freundliche result_of](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr für \<complex>](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr für \<chrono>](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr für \<array>](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr für \<initializer_list>, \<tuple>, \<utility>](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant::operator()()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 UDLs für \<chrono>, \<string> (1729ms, „meow“s, usw.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 NULL-Forward-Iteratoren](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 quoted()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 Heterogenes assoziatives Nachschlagen](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (zeitgesteuert)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 exchange()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 constexpr-Memberfunktionen ohne const beheben](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670 get\<T>()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 Zweibereich equal(), is_permutation(), mismatch()](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[N3778 Zuordnungsaufhebung mit Größenangabe](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 UDLs für \<complex> (3.14i, usw.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr für \<functional>](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 Umbenennen von shared_mutex (zeitgesteuert) in shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 Minimale Containerelement-Anforderungen](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 Transparente Operatorfunktionselemente (less\<>, usw.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[N3655 Alias-Vorlagen für \<type_traits> (decay_t, usw.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique()](https://wg21.link/n3656) | VS 2013 |

Eine Gruppe von Dokumenten, die zusammen aufgelistet sind, gibt ein Standardfeature zusammen mit mindestens einer genehmigten Verbesserung oder Erweiterung an. Diese Funktionen werden zusammen implementiert.

### <a name="supported-values"></a>Unterstützte Werte

__Nein__ bedeutet noch nicht implementiert.\
__Partiell__ bedeutet, dass die Implementierung unvollständig ist. Weitere Informationen finden Sie im Abschnitt „Hinweise“.\
__VS 2010__ gibt Features an, die in Visual Studio 2010 unterstützt werden.\
__VS 2013__ gibt Features an, die in Visual Studio 2013 unterstützt werden.\
__VS 2015__ gibt Features an, die in Visual Studio 2015 (RTW) unterstützt werden.\
__VS 2015.2__ und __VS 2015.3__ geben Features an, die in Visual Studio 2015 Update 2 und Visual Studio 2015 Update 3 unterstützt werden.\
__VS 2017 15.0__ gibt Features an, die in Visual Studio 2017 Version 15.0 (RTW) unterstützt werden.\
__VS 2017 15.3__ gibt Features an, die in Visual Studio 2017 Version 15.3 unterstützt werden.\
__VS 2017 15.5__ gibt Features an, die in Visual Studio 2017 Version 15.5 unterstützt werden.\
__VS 2017 15.7__ gibt Features an, die in Visual Studio 2017 Version 15.7 unterstützt werden.\
__VS 2019 16.0__ gibt Features an, die in Visual Studio 2019 Version 16.0 (RTW) unterstützt werden.\
__VS 2019 16.1__ gibt Features an, die in Visual Studio 2019 Version 16.1 unterstützt werden.\
__VS 2019 16.2__ gibt Features an, die in Visual Studio 2019 Version 16.2 unterstützt werden.\
__VS 2019 16.3__ gibt Features an, die in Visual Studio 2019 Version 16.3 unterstützt werden.\
__VS 2019 16.4__ gibt Features an, die in Visual Studio 2019 Version 16.4 unterstützt werden.\
__VS 2019 16.5__ gibt Features an, die in Visual Studio 2019 Version 16.5 unterstützt werden.

### <a name="notes"></a>Hinweise

<a name="note_A"></a> __A__ Im Modus [/std:c++14](../build/reference/std-specify-language-standard-version.md) werden dynamische Ausnahmespezifikationen nicht implementiert, und `throw()` wird weiterhin als Synonym von `__declspec(nothrow)` behandelt. In C++17 wurden dynamische Ausnahmespezifikationen hauptsächlich durch P0003R5 entfernt. Nur `throw()` wurde noch nicht entfernt, weshalb es nun als veraltet markiert wird und als Synonym von `noexcept` behandelt werden muss. Im Modus [/std:c++17](../build/reference/std-specify-language-standard-version.md) entspricht MSVC nun dem Standard, da `throw()` das gleiche Verhalten wie `noexcept` aufweist (d. h. Erzwingung durch Beenden).

Die Compileroption [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) fordert das alte Verhalten von `__declspec(nothrow)` an. Wahrscheinlich wird `throw()` in C++20 entfernt. Es wurden neue Compilerwarnungen für Probleme mit Ausnahmespezifikationen unter [/std:c++17](../build/reference/std-specify-language-standard-version.md) und [/permissive-](../build/reference/permissive-standards-conformance.md) hinzugefügt, um die Codemigration aufgrund dieser Änderungen im Standard und unserer Implementierung zu erleichtern.

<a name="note_B"></a> __B__ Wird im Modus [/permissive-](../build/reference/permissive-standards-conformance.md) in Visual Studio 2017 Version 15.7 unterstützt. Weitere Informationen finden Sie im Blogbeitrag [Two-phase name lookup support comes to MSVC](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/) (Unterstützung der Namenssuche in zwei Phasen in MSVC).

<a name="note_C"></a> __C__ Der Support des Compilers für die C99-Präprozessorregeln ist in Visual Studio 2017 unvollständig. Wir haben den Präprozessor überarbeitet und die Auslieferung der Änderungen in Visual Studio 2017, Version 15.8, mit der Compileroption [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) gestartet.

<a name="note_D"></a> __D__ Unterstützt unter [/std:c++14](../build/reference/std-specify-language-standard-version.md) mit einer unterdrückbaren Warnung ([C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md)).

<a name="note_E"></a> __E__ Dies ist eine völlig neue Implementierung, die nicht mit der vorherigen `std::experimental`-Version kompatibel ist. Sie ist aufgrund von Symlink-Unterstützung, Fehlerbehebungen und Änderungen des erforderlichen Standardverhaltens erforderlich. Wenn \<filesystem> verwendet wird, schließt dies aktuell das neue `std::filesystem`- und das vorherige `std::experimental::filesystem`-Element ein, und wenn \<experimental/filesystem> verwendet wird, schließt dies nur die alte experimentelle Implementierung ein. Die experimentelle Implementierung wird mit dem nächsten ABI unterbrechenden Release der Bibliotheken entfernt.

<a name="note_G"></a> __G__ Unterstützt durch eine intrinsische Compilerfunktion.

<a name="note_14"></a> __14__ Diese C++17/20-Features sind immer aktiviert, auch wenn [/std:c++14](../build/reference/std-specify-language-standard-version.md) (Standard) angegeben ist. Grund dafür ist, dass das Feature vor der Einführung der **/std**-Optionen implementiert wurde, oder dass die bedingte Implementierung unerwünscht komplex war.

<a name="note_17"></a> __17__ Diese Features werden durch die Compileroption [/std:c++17](../build/reference/std-specify-language-standard-version.md) (oder [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) aktiviert.

<a name="note_20"></a> __20__ Diese Features werden durch die Compileroption [/std:c++latest](../build/reference/std-specify-language-standard-version.md) aktiviert. Wenn die C++ 20-Implementierung abgeschlossen ist, wird die neue Compileroption **/std:c++20** hinzugefügt. Unter dieser sind dieses Features ebenfalls verfügbar.

<a name="note_byte"></a> __byte__ `std::byte` wird durch [/std:c++17](../build/reference/std-specify-language-standard-version.md) (oder [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) aktiviert, da jedoch in einigen Fällen Konflikte mit den Windows SDK-Headern auftreten können, ist ein differenziertes Makro für die Abwahl vorhanden. Die Deaktivierung erfolgt durch Definieren von `_HAS_STD_BYTE` als `0`.

<a name="note_C11"></a> __C11__ Die Universal CRT implementierte die Teile der C11-Standardbibliothek, die für C++17 erforderlich sind, mit Ausnahme der `strftime()`-Bezeichner in C99 für die alternative E/O-Konvertierung, dem exklusiven `fopen()`-Modus in C11 und der `aligned_alloc()`-Funktion in C11. Die Implementierung der letztgenannten Funktion ist unwahrscheinlich, da C11 `aligned_alloc()` auf eine Weise angibt, die mit der Microsoft-Implementierung von `free()` nicht kompatibel ist. Insbesondere muss `free()` in der Lage sein, hochgradig ausgerichtete Zuweisungen zu verarbeiten.

<a name="note_rem"></a> __rem__ Diese Features wurden entfernt, als die Compileroption [/std:c++17](../build/reference/std-specify-language-standard-version.md) (oder [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) angegeben wurde. Diese Features können erneut aktiviert werden, um die Umstellung auf neuere Sprachmodi zu vereinfachen, indem diese Makros verwendet werden: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS` und `_HAS_UNEXPECTED`.

<a name="note_charconv"></a> __charconv__ `from_chars()` und `to_chars()` sind für ganze Zahlen verfügbar. Die Zeitachse für `from_chars()` (Gleitkomma) und `to_chars()` (Gleitkomma) lautet wie folgt:

- VS 2017 15.7: `from_chars()` (ganze Zahl) und `to_chars()`.
- VS 2017 15.8: `from_chars()` (Gleitkomma).
- VS 2017 15.9: `to_chars()`-Überladungen (Gleitkomma) für kürzeste Dezimalzahl.
- VS 2019 16.0: `to_chars()`-Überladungen (Gleitkomma) für kürzesten und genauen Hexadezimalwert.
- VS 2019 16.2: `to_chars()`-Überladungen (Gleitkomma) für Genauigkeit (feststehend und wissenschaftlich).
- VS 2019 16.4: `to_chars()`-Überladung (Gleitkomma) für Genauigkeit (allgemein).

<a name ="note_parallel"></a> __parallel__ Die Bibliothek mit parallelen Algorithmen von C++17 ist vollständig. „Vollständig“ bedeutet nicht, dass jeder Algorithmus in jedem Fall parallelisiert wird. Die wichtigsten Algorithmen wurden parallelisiert, und Ausführungsrichtliniensignaturen werden auch dann angegeben, wenn Algorithmen nicht parallelisiert sind. Der zentrale interne Header der Implementierung (yvals_core.h) enthält folgende Anmerkungen zu parallelen Algorithmen: In C++ kann eine Implementierung parallele Algorithmen aus Aufrufe von seriellen Algorithmen implementieren. Diese Implementierung parallelisiert einige aber nicht alle gängigen Algorithmusaufrufe.

Die folgenden Algorithmen werden parallelisiert:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Die folgenden Algorithmen sind aktuell nicht parallelisiert:

- Keine nennenswerte Verbesserung der Leistung durch Parallelität auf der Zielhardware. Alle Algorithmen, die Elemente ohne Branches nur kopieren oder verschieben, verfügen normalerweise über eine Begrenzung der Arbeitsspeicherbandbreite:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Benutzerparallelitätsanforderungen können unklar sein. Können vermutlich der oben stehenden Kategorie zugeordnet werden:
  - `generate`, `generate_n`
- Effektive Parallelität kann wahrscheinlich nicht erreicht werden:
  - `partial_sort`, `partial_sort_copy`
- Noch nicht ausgewertet. Möglicherweise wird die Parallelität in einem kommenden Release implementiert, vermutlich positive Auswirkungen:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Siehe auch

[C++ Language Reference (C++-Programmiersprachenreferenz)](../cpp/cpp-language-reference.md)\
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)\
[Verbesserungen der C++-Konformität in Visual Studio 2015](cpp-conformance-improvements.md)\
[Neuerungen bei Visual C++ in Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Änderungsverlauf von Visual C++ von 2003 bis 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Visual C++: Neuerungen von 2003 bis 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[C++-Teamblog](https://devblogs.microsoft.com/cppblog/)
