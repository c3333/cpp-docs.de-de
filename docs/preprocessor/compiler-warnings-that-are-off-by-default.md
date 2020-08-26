---
title: Standardmäßig deaktivierte Compilerwarnungen
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: 3727777c6abd3ae5ba19f147e2b6fbe559251813
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836608"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Standardmäßig deaktivierte Compilerwarnungen

Der Compiler unterstützt Warnungen, die standardmäßig deaktiviert sind, da die meisten Entwickler diese nicht als nützlich finden. In einigen Fällen warnen Sie über eine stilwahl oder über allgemeine Ausdrücke in älteren Code. Andere Warnungen sind die Verwendung einer Microsoft-Erweiterung in der Sprache. Einige Warnungen geben einen Bereich an, in dem Programmierer häufig falsche Annahmen treffen, was zu unerwartetem oder undefiniertem Verhalten führen kann. Wenn alle diese Warnungen aktiviert sind, können einige davon in Bibliotheks Headern mehrmals vorkommen. Die C-Laufzeitbibliotheken und die C++-Standardbibliotheken sind darauf ausgerichtet, keine Warnungen nur auf Warnstufe [/W4](../build/reference/compiler-option-warning-level.md)auszugeben.

## <a name="enable-warnings-that-are-off-by-default"></a>Standardmäßig deaktivierte Warnungen aktivieren

Sie können Warnungen, die normalerweise standardmäßig deaktiviert sind, mithilfe einer der folgenden Optionen aktivieren:

- **#pragma Warnung (Standard:** *Warning_number* **)**

   Die angegebene Warnung (*Warning_number*) wird auf der Standard Ebene aktiviert. Dokumentation für die Warnung enthält die Standardebene der Warnung.

- **#pragma Warnung (** *warning_level* **:** *Warning_number* **)**

   Die angegebene Warnung (*Warning_number*) wird auf der angegebenen Ebene (*warning_level*) aktiviert.

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` aktiviert alle Warnungen, die standardmäßig deaktiviert sind. Wenn Sie diese Option verwenden, können Sie einzelne Warnungen mithilfe der [/WD](../build/reference/compiler-option-warning-level.md) -Option deaktivieren.

- [/w*lnnnn*](../build/reference/compiler-option-warning-level.md)

   Diese Option aktiviert die Warnung *nnnn* auf Ebene *L*.

## <a name="warnings-that-are-off-by-default"></a>Standardmäßig deaktivierte Warnungen

Die folgenden Warnungen sind in Visual Studio 2015 und höheren Versionen standardmäßig deaktiviert:

|Warnung|`Message`|
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (Stufe 4)|der Enumerator '*Identifier*' in einem Schalter der*Enumeration ' Enumeration*' wird nicht explizit von einer Case-Bezeichnung behandelt.|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (Stufe 4)|der Enumerator '*Identifier*' in einem Schalter der*Enumeration ' Enumeration*' wird nicht behandelt.|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (Stufe 1) | "HRESULT" wird in "bool" konvertiert. sind Sie sicher, was Sie möchten? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (Stufe 3)|"*Operator*": unsichere Konvertierung von "*type_of_expression*" in "*type_required*"|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (Stufe 4)|'*Identifier*': Konvertierung von '*Typ1*' in '*Typ2*', möglicher Datenverlust|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (Stufe 4)|'*Operator*': Konvertierung von '*Typ1*' in '*Typ2*', möglicher Datenverlust|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (Stufe 4)|"*Function*": kein Funktionsprototyp angegeben: "()" wird in "(void)" umgerechnet.|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (Stufe 4)|"*Function*": die Member-Funktion überschreibt keine virtuelle Member-Funktion der Basisklasse.|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (Stufe 1)|'*Virtual_function*': für die Funktion eines virtuellen Members von der Basis*Klasse*' ' ist keine Überschreibung verfügbar. die Funktion ist ausgeblendet.|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (Stufe 3)|"*Class*": die Klasse besitzt virtuelle Funktionen, aber der debugtor ist nicht virtuell.|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (Stufe 4)|"*Function*": Es ist keine Überschreibung für die virtuelle Element Funktion aus Basis "*Typ*" verfügbar. die Funktion ist ausgeblendet.|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (Stufe 3)|"*Operator*": nicht signierte/negative Konstante stimmen nicht überein.|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (Stufe 4)|nicht dem Standard entsprechende Erweiterung: "*var*": die Schleifen Steuerungs Variable, die in der for-Schleife deklariert wurde, wird außerhalb des for-Schleifen Bereichs verwendet.|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (Stufe 4)|"*Operator*": der Ausdruck ist immer "false".|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (Stufe 4)|'*Typ*': die Verwendung eines undefinierten Typs wurde in CLR-Meta-Data erkannt. die Verwendung dieses Typs kann zu einer Lauf Zeit Ausnahme führen.|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (Stufe 1)|Behavior Change: "*Function*" aufgerufen, aber in früheren Versionen wurde ein Member-Operator aufgerufen.|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (Stufe 1)|Behavior Change: "*Member1*" wird anstelle von "*member2*" aufgerufen.|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|"this": Wird in der Basisliste für den Memberinitialisierer verwendet|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (Stufe 4)|"*Action*": Konvertierung von "*TYPE_1*" in "*TYPE_2*", nicht übereinstimmende/nicht signierte Konvertierung|
|C4370 (Stufe 3)|Durch bessere Verpackung wurde das Klassenlayout geändert, das vorher eine andere Compilerversion hatte|
|[C4371](../error-messages/compiler-warnings/c4371.md) (Stufe 3)|"*className*": das Layout der Klasse wurde möglicherweise von einer früheren Version des Compilers geändert, weil der Member "*Member*" besser verpackt wurde.|
|C4388 (Stufe 4)|Konflikt zwischen 'signed' und 'unsigned'|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (Stufe 2)|'*Function*': die Funktions Signatur enthält den Typ '*Type*'; C++-Objekte sind unsicher, um zwischen reinem und gemischtem oder nativem Code zu übergeben|
|C4426 (Stufe 1)|die Optimierungs Flags wurden nach dem einschließen des Headers geändert, möglicherweise #Pragma Optimieren () <sup>14,1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (Stufe 4)|'*Class1*': das Objekt Layout unter "/vd2" wird aufgrund der virtuellen Basis '*Klasse2*' geändert.|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (Stufe 4)|die dynamic_cast von der virtuellen Basis "*Class1*" zu "*Klasse2*" kann in einigen Kontexten fehlschlagen.|
|C4444 (Stufe 3)|Höchste Ebene '__unaligned' ist in diesem Kontext nicht implementiert|
|[C4464](../error-messages/compiler-warnings/c4464.md) (Stufe 4)|relativer Includepfad enthält '.. '|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (Stufe 4)|eine vorwärts Deklaration einer Enumeration ohne Bereichs Einschränkung muss über einen zugrunde liegenden Typ verfügen (int wird <sup>angenommen).</sup>|
|C4472 generiert (Stufe 1)|'*Identifier*' ist eine systemeigene Enumeration: Fügen Sie einen Zugriffsspezifizierer (privat/öffentlich) hinzu, um eine verwaltete Enumeration zu deklarieren|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (Stufe 4)|"*Funktion*": nicht referenzierte Inline Funktion wurde entfernt.|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (Stufe 4)|' Typname ': der Typname überschreitet das Metadatenlimit von '*Limit*'-Zeichen.|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (Stufe 1)|Ausdruck vor dem Komma wird als Funktion ausgewertet, der eine Argumentliste fehlt|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (Stufe 1)|Funktionsaufruf vor dem Komma ohne Argumentliste|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (Stufe 1)|"*Operator*": der Operator vor dem Komma hat keine Auswirkungen. Operator mit Nebeneffekt erwartet|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (Stufe 1)|Ausdruck vor dem Komma hat keine Auswirkung; es wurde ein Ausdruck mit Nebeneffekt erwartet|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (Stufe 1)|"*Operator1*": der Operator vor dem Komma hat keine Auswirkungen. haben Sie "*Operator2*" beabsichtigt?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (Stufe 1)|Der Ausdruck hat keine Auswirkungen; Ausdruck mit Nebeneffekten erwartet|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (Stufe 3)|"__assume" enthält Auswirkung "*Auswirkung*".|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (Stufe 4)|Information: die catch (...)-Semantik wurde seit Visual C++ 7,1 geändert. strukturierte Ausnahmen (SEH) werden nicht mehr abgefangen.|
|C4574 (Stufe 4)|"*Identifier*" ist als "0" definiert: wollten Sie "#If *Identifier*" verwenden?|
|C4577 (Stufe 1)|"noaußer" wird verwendet, ohne dass der Ausnahme Behandlungs Modus angegeben wurde. Beendigung bei Ausnahme ist nicht gewährleistet. /EHsc angeben|
|C4582 (Stufe 4)|"*Type*": der Konstruktor wird nicht implizit aufgerufen|
|C4583 (Stufe 4)|"*Type*": der Dekonstruktor wird nicht implizit aufgerufen|
|C4587 (Stufe 1)|'*anonymous_structure*': Behavior Change: der Konstruktor wird nicht mehr implizit aufgerufen.|
|C4588 (Stufe 1)|'*anonymous_structure*': Behavior Change: Dekonstruktor wird nicht mehr implizit aufgerufen|
|[C4596](../error-messages/compiler-warnings/c4596.md) (Stufe 4)|'*Identifier*': Ungültiger qualifizierter Name in der Mitglieds Deklaration <sup>14,3</sup> <sup>Perm</sup>|
|C4598 (Ebene 1 und Ebene 3)|' #include '-*Header*' ': Header Nummer *-Header-Nummer* im vorkompilierten Header stimmt nicht mit der aktuellen Kompilierung an dieser Position <sup>14,3</sup>|
|C4599 (Stufe 3)|'*options* *Pfad*': die Nummer der Befehlszeilenargument- *Nummer stimmt nicht* mit dem vorkompilierten Header <sup>14,3</sup> überein.|
|C4605 (Stufe 1)|"/D*Macro*" wurde in der aktuellen Befehlszeile angegeben, wurde jedoch beim Erstellen des vorkompilierten Headers nicht angegeben.|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (Stufe 3)|'*union_member*' wurde bereits von einem anderen Union-Member in der Initialisiererliste initialisiert, '*union_member*' <sup>Perm</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (Stufe 3)|#pragma Warnung: die Warnungs Nummer '*Number*' ist nicht vorhanden.|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (Stufe 4)|'Abgeleitete Klasse': Der Standardkonstruktor konnte nicht generiert werden, da auf einen Basisklassen-Standardkonstruktor nicht zugegriffen werden kann|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (Stufe 4)|'Abgeleitete Klasse': Der Kopierkonstruktor konnte nicht generiert werden, da auf einen Basisklassen-Kopierkonstruktor nicht zugegriffen werden kann|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (Stufe 4)|'Abgeleitete Klasse': Der Zuweisungsoperator konnte nicht generiert werden, da auf einen Basisklassen-Zuweisungsoperator nicht zugegriffen werden kann|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (Stufe 1)|'digraphs' werden mit '-Ze' nicht unterstützt. Die Zeichenfolge '*Digraph*' wird nicht als alternatives Token für '*char*' interpretiert.|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (Stufe 3)|'*instance*': die Konstruktion des lokalen statischen Objekts ist nicht Thread sicher.|
| C4643 (Stufe 4) | Die vorwärts Deklaration von '*Identifier*' in Namespace Std ist durch den C++-Standard nicht zulässig. <sup>15.8</sup> |
|C4647 (Stufe 3)|Behavior Change: __is_pod (*Typ*) hat in früheren Versionen einen anderen Wert.|
|C4654 (Stufe 4)|Der Code, der vor dem einschließen der vorkompilierten Kopfzeile eingefügt wurde, wird ignoriert. Fügen Sie dem vorkompilierten Header Code hinzu. <sup>14,1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (Stufe 4)|'*Symbol*' ist nicht als Präprozessormakro definiert und wird durch ' 0 ' für '*Direktiven*' ersetzt|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (Stufe 4)|'*Symbol*': Es wurde kein direktionales Parameter Attribut angegeben, standardmäßig [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (Stufe 3)|'*benutzerdefinierter Typ*': mögliche Änderung im Verhalten, Änderung in der UDT gibt Aufruf Konvention zurück|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (Stufe 1)|"*Funktion*": die Signatur des nicht privaten Members enthält den privaten systemeigenen Assemblytyp "*NATIVE_TYPE*".|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (Stufe 4)|"*Function*": Funktion nicht Inline|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (Stufe 3)|Das 32-Bit-Gleitkommaergebnis wird im Speicher gespeichert. Möglicherweise kommt es zu einem Leistungsverlust|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|flüchtiger Zugriff auf "*Expression*" unterliegt/volatile: \<iso&#124;ms> Setting; verwenden Sie ggf. __iso_volatile_load intrinsische Funktionen von/Store.|
|C4749 (Stufe 4)|bedingt unterstützt: OffsetOf angewendet auf den Typ "*Typ*", der nicht dem Standardlayout entspricht.|
|C4767 (Stufe 4)|der Abschnitts Name '*Symbol*' ist länger als 8 Zeichen und wird vom Linker abgeschnitten.|
|C4768 (Stufe 3)|__declspec Attribute, bevor die Verknüpfungs Angabe ignoriert wird|
|C4774 (Stufe 4)|"*String*": die in der Argument *Nummer* erwartete Format Zeichenfolge ist kein Zeichenfolgenliteral|
|C4777 (Stufe 4)|"*Function*": die Format Zeichenfolge "*String*" erfordert ein Argument vom Typ "*Typ1*", die Variadic-Argument *Nummer* weist jedoch den Typ "*Typ2*" auf.|
|C4786 (Stufe 3)|'*Symbol*': der Objektname wurde in den Debuginformationen auf '*Number*'-Zeichen gekürzt.|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (Stufe 4) | Implizite Konvertierung von '*Type*' in bool. Möglicher Informationsverlust <sup>16,0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (Stufe 4)|Byte *-* Auffüll Zeichen werden nach dem Erstellen von "*MEMBER_NAME*" hinzugefügt.|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (Stufe 1) | "*Member*": die Member-Funktion der lokalen Klasse weist keinen Text auf. |
|C4826 (Stufe 2)|Die Konvertierung von '*Typ1*' in '*Typ2*' ist mit der Signatur erweitert. Dies kann zu unerwartetem Laufzeitverhalten führen.|
|C4837 (Stufe 4)|'?? ' gefunden? *Zeichen*"ersetzt durch"*Zeichen*"|
|C4841 (Stufe 4)|nicht standardmäßige Erweiterung verwendet: in offsetof verwendeter Verbund Element Kenn Zeichner|
|C4842 (Stufe 4)|Das Ergebnis von "offsetof", das mithilfe mehrerer Vererbung auf einen Typ angewendet wird, ist nicht garantiert zwischen den compilerreleases konsistent.|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (Stufe 4)|der Compiler '_File_(*LINE_NUMBER*) ' kann die Auswertungs Reihenfolge von links nach rechts in der Initialisierungs Liste mit geschweiftem Klammern nicht erzwingen.|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (Stufe 1)|Breites Zeichenfolgenliteral umgewandelt zu "LPSTR"|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (Stufe 1)|Zeichenfolgenliteral umgewandelt zu "LPWSTR"|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (Stufe 1)|"*Deklarator*": eine GUID kann nur einer Klasse, einer Schnittstelle oder einem Namespace zugeordnet werden.|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (Stufe 1)|Unzulässige Kopierinitialisierung. Mehrere benutzerdefinierte Konvertierungen wurden implizit übernommen|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (Stufe 4)|Es wird angenommen, dass die Typbibliothek für Anzahl-Bit-Pointer erstellt wurde|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (Stufe 1)|reinterpret_cast zwischen verknüpften Klassen verwendet: "*Class1*" und "*Klasse2*"|
|C4962|"*Funktion*": Profil gesteuerte Optimierungen wurden deaktiviert, da durch Optimierungen das inkonsistente Profildaten verursacht wurde.|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (Stufe 4)|'*Symbol*': die Ausnahme Spezifikation stimmt nicht mit der vorherigen Deklaration.|
|C4987 (Stufe 4)|Es wurde eine nicht standardmäßige Erweiterung verwendet: 'throw (...)'|
|C4988 (Stufe 4)|'*Symbol*': Variable wurde außerhalb des Klassen-/Funktionsbereichs deklariert.|
|C5022|'*Type*': Es wurden mehrere bewegungskonstruktoren angegeben.|
|C5023|"*Typ*": mehrere Verschiebungs Zuweisungs Operatoren angegeben|
|C5024 (Stufe 4)|"*Type*": der bewegungskonstruktor wurde implizit als gelöscht definiert.|
|C5025 (Stufe 4)|"*Type*": der Bewegungs Zuweisungs Operator wurde implizit als gelöscht definiert.|
|C5026 (Ebene 1 und Ebene 4)|"*Type*": der bewegungskonstruktor wurde implizit als gelöscht definiert.|
|C5027 (Ebene 1 und Ebene 4)|"*Type*": der Bewegungs Zuweisungs Operator wurde implizit als gelöscht definiert.|
|C5029 (Stufe 4)|nicht dem Standard entsprechende Erweiterung: Ausrichtungs Attribute in C++ gelten nur für Variablen, Datenmember und Tagtypen.|
|C5031 (Stufe 4)|#pragma Warnung (Pop): wahrscheinliche fehl Übereinstimmung, pping-Warn Status in anderer Datei <sup>14,1</sup>|
|C5032 (Stufe 4)|#pragma Warnung (Push) ohne entsprechende #pragma Warnung (Pop) <sup>14,1</sup> erkannt|
|C5034|die Verwendung der systeminternen '*intrinsischen*' bewirkt, dass Funktions *Funktionsname* als gastcode <sup>15,3</sup> kompiliert wird.|
|C5035|die Verwendung der Funktion "*Feature*" bewirkt, dass Funktions *Funktionsname* als gastcode <sup>15,3</sup> kompiliert wird.|
|C5036 (Stufe 1)|VarArgs-Funktionszeiger Konvertierung bei der Kompilierung mit/Hybrid: x86arm64 '*Typ1*' in '*Typ2*' <sup>15,3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (Stufe 4)|der Datenmember "*Member1*" wird nach dem Datenmember "*member2* <sup>15,3</sup> " initialisiert.|
|C5039 (Stufe 4)|"*Function*": ein Zeiger oder Verweis auf eine potenziell auslösende Funktion, die an die externe C-Funktion unter "-EHC" Ein nicht definiertes Verhalten kann auftreten, wenn diese Funktion eine Ausnahme auslöst. <sup>15,5</sup>|
|C5042 (Stufe 3)|"*Function*": Funktions Deklarationen im Block Bereich können in Standard C++ nicht "Inline" angegeben werden; Inline-Spezifizierer <sup>15,5</sup> entfernen|
|[C5045](../error-messages/compiler-warnings/c5045.md)|Der Compiler fügt eine Spectre-Entschärfung für die Speicherauslastung ein, wenn/Qspectre Switch <sup>15,7</sup>|

<sup>14,1</sup> diese Warnung ist ab Visual Studio 2015 Update 1 verfügbar. \
<sup>14,3</sup> diese Warnung ist ab Visual Studio 2015 Update 3 verfügbar.
<sup>15,3</sup> diese Warnung ist ab Visual Studio 2017 Version 15,3 verfügbar.
<sup>15,5</sup> diese Warnung ist ab Visual Studio 2017 Version 15,5 verfügbar.
<sup>15,7</sup> diese Warnung ist ab Visual Studio 2017 Version 15,7 verfügbar.
<sup>15,8</sup> diese Warnung ist ab Visual Studio 2017 Version 15,8 verfügbar.
<sup>16,0</sup> diese Warnung ist ab Visual Studio 2019 RTM verfügbar. \
<sup>Perm</sup> Diese Warnung ist deaktiviert, sofern die [/permissive-](../build/reference/permissive-standards-conformance.md) -Compileroption nicht festgelegt ist.

## <a name="warnings-off-by-default-in-earlier-versions"></a>Warnungen werden in früheren Versionen standardmäßig deaktiviert.

Diese Warnungen waren in Compilerversionen vor Visual Studio 2015 standardmäßig deaktiviert:

|Warnung|`Message`|
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (Stufe 2)|'*Konvertierung*': Abschneiden von '*Typ1*' in '*Typ2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (Stufe 1)|'*Variable*': Zeiger Verkürzung von '*Typ*' in '*Typ*'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (Stufe 1)|'*Operation*': Konvertierung von '*Typ1*' in '*Typ2*' mit größerer Größe|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (Stufe 1)|"*Operator*": NULL Erweiterung von "*Typ1*" auf "*Typ2*" mit größerer Größe|

Diese Warnung war in Compilerversionen vor Visual Studio 2012 standardmäßig deaktiviert:

|Warnung|`Message`|
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (Stufe 4)|Fehlender Typspezifizierer - int wird angenommen. Hinweis: default-int wird von C++ nicht unterstützt|

## <a name="see-also"></a>Weitere Informationen

[warning](../preprocessor/warning.md)
