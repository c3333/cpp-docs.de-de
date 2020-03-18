---
title: Compilerwarnungen C4800 bis C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
ms.openlocfilehash: 4d349ba8a51b324b5262e3e38506015ea198d5e3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438274"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Compilerwarnungen C4800 bis C5999

In den Artikeln in diesem Abschnitt der Dokumentation wird eine Teilmenge der Warnmeldungen erläutert, die vom Compiler generiert werden.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Warnmeldungen

|Warnung|`Message`|
|-------------|------------|
|[Compilerwarnung (Stufe 4) C4800](compiler-warning-level-3-c4800.md)| Implizite Konvertierung von '*Type*' in bool. Möglicher Informationsverlust |
|[Compilerwarnung (Stufe 1) C4803](compiler-warning-level-1-c4803.md)|'*Methode*': die Raise-Methode hat eine andere Speicher Klasse als die des Ereignisses '*Event*'.|
|[Compilerwarnung (Stufe 1) C4804](compiler-warning-level-1-c4804.md)|"*Operation*": unsichere Verwendung des Typs "bool" in Vorgang|
|[Compilerwarnung (Stufe 1) C4805](compiler-warning-level-1-c4805.md)|'*Operation*': unsichere Mischung aus Typ '*Typ1*' und Typ '*Typ2*' in Vorgang|
|[Compilerwarnung (Stufe 1) C4806](compiler-warning-level-1-c4806.md)|"*Operation*": unsichere Operation: kein Wert vom Typ "*Typ1*", der auf den Typ "*Typ2*" herauf gestuft wurde, kann der angegebenen Konstante entsprechen.|
|[Compilerwarnung (Stufe 1) C4807](compiler-warning-level-1-c4807.md)|"*Operation*": unsichere Mischung aus Typ "*Typ1*" und signiertem Bitfeld vom Typ "*Typ2*"|
|Compilerwarnung (Stufe 1) C4808|der Case *-Wert ist*kein gültiger Wert für eine Switch-Bedingung vom Typ "bool".|
|Compilerwarnung (Stufe 1) C4809|Switch-Anweisung hat redundante "Default"-Bezeichnung; alle möglichen Case-Bezeichnungen werden angegeben.|
|[Compilerwarnung (Stufe 1) C4810](compiler-warning-level-1-c4810.md)|Wert von pragma pack(show) == n|
|[Compilerwarnung (Stufe 1) C4811](compiler-warning-level-1-c4811.md)|Wert von 'pragma conform(forScope, show) == Wert'|
|[Compilerwarnung (Stufe 1) C4812](compiler-warning-level-1-c4812.md)|veralteter Deklarations Stil: Verwenden Sie stattdessen "*new_syntax*".|
|[Compilerwarnung (Stufe 1) C4813](compiler-warning-level-1-c4813.md)|"*Function*": eine Friend-Funktion einer lokalen Klasse muss bereits deklariert sein.|
|[Compilerwarnung (Stufe 4) C4816](compiler-warning-level-4-c4816.md)|'*param*': Parameter hat ein Array der Größenangabe, das abgeschnitten wird (sofern das Objekt nicht als Verweis übergeben wird).|
|[Compilerwarnung (Stufe 1) C4817](compiler-warning-level-1-c4817.md)|"*Member*": Unzulässige Verwendung von "." für den Zugriff auf diesen Member. der Compiler wurde durch "->" ersetzt.|
|[Compilerwarnung (Stufe 1) C4819](compiler-warning-level-1-c4819.md)|Die Datei enthält ein Zeichen, das in der aktuellen Codepage (Nummer) nicht dargestellt werden kann. Speichern Sie die Datei im Unicode-Format, um Datenverluste zu verhindern.|
|[Compilerwarnung (Stufe 4) C4820](compiler-warning-level-4-c4820.md)|Byte *-* Auffüll Zeichen werden nach dem Erstellen von "*MEMBER_NAME*" hinzugefügt.|
|[Compilerwarnung (Stufe 1) C4821](compiler-warning-level-1-c4821.md)|Der Unicode-Codierungstyp kann nicht bestimmt werden. speichern Sie die Datei mit der Signatur (BOM).|
|[Compilerwarnung (Stufe 1) C4822](compiler-warning-level-1-c4822.md)|' Member-Funktion ': die Member-Funktion der lokalen Klasse weist keinen Text auf.|
|[Compilerwarnung (Stufe 3) C4823](compiler-warning-level-3-c4823.md)|"*Function*": verwendet anheften-Zeiger, aber die Entlade Semantik ist nicht aktiviert. Verwenden Sie/EHA.|
|Compilerwarnung (Stufe 2) C4826|Die Konvertierung von '*Typ1*' in '*Typ2*' ist mit der Signatur erweitert. Dies kann zu unerwartetem Laufzeitverhalten führen.|
|Compilerwarnung (Stufe 3) C4827|Eine öffentliche "ToString"-Methode mit 0 Parametern muss als "Virtual" und "override" markiert werden.|
|[Compilerwarnung (Stufe 1) C4829](compiler-warning-level-1-c4829.md)|Möglicherweise falsche Parameter für Main-Funktion. "Int main (Platform:: Array\<Platform:: String ^ > ^ argv)" in Erwägung gezogen|
|[Compilerwarnung (Stufe 1) C4835](compiler-warning-level-1-c4835.md)|'*Variable*': der Initialisierer für exportierte Daten wird erst ausgeführt, wenn der verwaltete Code zuerst in der Hostassembly ausgeführt wird.|
|Compilerwarnung (Stufe 4) C4837|'?? ' gefunden? *Zeichen*"ersetzt durch"*Zeichen*"|
|[Compilerwarnung (Stufe 1) C4838](compiler-warning-level-1-c4838.md)|die Konvertierung von '*TYPE_1*' in '*TYPE_2*' erfordert eine einschränkende Konvertierung.|
|[Compilerwarnung (Stufe 3) C4839](compiler-warning-level-3-c4839.md)|nicht standardmäßige Verwendung der '*Type*'-Klasse als Argument für eine Variadic-Funktion|
|[Compilerwarnung (Stufe 4) C4840](compiler-warning-level-4-c4840.md)|nicht Portier Bare Verwendung der '*Type*'-Klasse als Argument für eine Variadic-Funktion|
|Compilerwarnung (Stufe 4) C4841|nicht standardmäßige Erweiterung verwendet: in offsetof verwendeter Verbund Element Kenn Zeichner|
|Compilerwarnung (Stufe 4) C4842|Das Ergebnis von "offsetof", das mithilfe mehrerer Vererbung auf einen Typ angewendet wird, ist nicht garantiert zwischen den compilerreleases konsistent.|
|Compilerwarnung C4843|"*Typ1*": ein Ausnahmehandler des Verweises auf ein Array oder einen Funktionstyp ist nicht erreichbar, verwenden Sie stattdessen "*Typ2*".|
|Compilerwarnung C4844|"Export Module *module_name*;" ist jetzt die bevorzugte Syntax zum Deklarieren einer Modulschnittstelle.|
| Compilerwarnung (Stufe 4) C4845 | '\_\_declspec (No\_init\_all) ' wird ignoriert, wenn '/d1initall\[0\|1\|2\|3] ' nicht in der Befehlszeile angegeben wurde. |
| Compilerwarnung (Stufe 4) C4846 | "*value*" ist kein gültiges Argument für "/d1initall": das befehlszeilenflag wird ignoriert. |
| Compilerwarnung (Stufe 4) C4847 | '\_\_declspec (No\_init\_all) ' kann nur auf eine Funktion, einen Klassentyp oder eine lokale Variable angewendet werden: wird ignoriert. |
| Compilerwarnung (Stufe 1) C4848 | Unterstützung für das Standard Attribut "No\_Unique\_Address" in c++ 17 und früher ist eine Hersteller Erweiterung. |
|[Compilerwarnung (Stufe 4) C4866](c4866.md)| der Compiler kann die Auswertungs Reihenfolge von links nach rechts nicht erzwingen, um aufzurufen *operator_name*|
|[Compilerwarnung (Fehler) C4867](compiler-warning-c4867.md)|"*Function*": Funktionsaufrufe fehlen Argumentliste; Verwenden Sie "*rufen*", um einen Zeiger auf den Member zu erstellen.|
|[Compilerwarnung (Stufe 4) C4868](compiler-warning-c4868.md)|der Compiler '_File_(*LINE_NUMBER*) ' kann die Auswertungs Reihenfolge von links nach rechts in der Initialisierungs Liste mit geschweiftem Klammern nicht erzwingen.|
|Compilerwarnung (Stufe 2) C4872|beim Kompilieren des Aufruf Diagramms für die Parallelität wurde eine Gleit Komma Division durch 0 (null) erkannt::p arallel_for_each an: '*Location*'|
|Compilerwarnung (Stufe 1) C4880|Umwandlung von ' const *TYPE_1*' in '*TYPE_2*': das Umwandeln von constness aus einem Zeiger oder Verweis kann zu einem nicht definierten Verhalten in einer eingeschränkten amp-Funktion führen.|
|Compilerwarnung (Stufe 4) C4881|der Konstruktor und/oder der Dekonstruktor werden nicht für die tile_static Variable "*Variable*" aufgerufen.|
|Compilerwarnung (Stufe 1) C4882|übergeben von Funktoren mit nicht konstanten Ansichts Operatoren an Parallelität::p arallel_for_each ist veraltet|
|[Compilerwarnung C4900](compiler-warning-level-1-c4900.md)|Il-Konflikt zwischen "*Tool1*", Version "*Version1*" und "*Tool2*", Version "*Version2*"|
|[Compilerwarnung (Stufe 1) C4905](compiler-warning-level-1-c4905.md)|{1}Breites Zeichenfolgenliteral umgewandelt zu "{2}{3}{4}LPSTR{5}{6}{7}"{8}|
|[Compilerwarnung (Stufe 1) C4906](compiler-warning-level-1-c4906.md)|{1}Zeichenfolgenliteral umgewandelt zu "{2}{3}{4}LPWSTR{5}{6}{7}"{8}|
|[Compilerwarnung (Stufe 1) C4910](compiler-warning-level-1-c4910.md)|"\<Identifier >: ' __declspec (dllexport)" und "extern" sind bei einer expliziten Instanziierung nicht kompatibel.|
|[Compilerwarnung (Stufe 1) C4912](compiler-warning-level-1-c4912.md)|"*Attribut*": das Attribut hat ein nicht definiertes Verhalten für einen in einem netsted UDT|
|[Compilerwarnung (Stufe 4) C4913](compiler-warning-level-4-c4913.md)|Benutzerdefinierter binärer Operator "," ist vorhanden, die Überladung konnte aber alle Operanden nicht konvertieren. Es wurde der standardmäßig enthaltene binäre Operator "," verwendet.|
|Compilerwarnung (Stufe 1) C4916|um eine "DISPID" zu haben, "*Description*": muss von einer Schnittstelle eingeführt werden.|
|[Compilerwarnung (Stufe 1) C4917](compiler-warning-level-1-c4917.md)|"*Deklarator*": eine GUID kann nur einer Klasse, einer Schnittstelle oder einem Namespace zugeordnet werden.|
|[Compilerwarnung (Stufe 4) C4918](compiler-warning-level-4-c4918.md)|'*Character*': Ungültiges Zeichen in der pragma-Optimierungs Liste|
|[Compilerwarnung (Stufe 1) C4920](compiler-warning-level-1-c4920.md)|Enumeration-Enumerationsmember member_1 = value_1 in enumerationsenumeration bereits als member_2 = angezeigt value_2|
|Compilerwarnung (Stufe 3) C4921|'*Beschreibung*': der Attribut Wert '*Attribut*' sollte nicht multipliziert angegeben werden.|
|[Compilerwarnung (Stufe 1) C4925](compiler-warning-level-1-c4925.md)|"*method*": die dispinterface-Methode kann nicht aus dem Skript aufgerufen werden.|
|[Compilerwarnung (Stufe 1) C4926](compiler-warning-level-1-c4926.md)|'*Identifier*': das Symbol ist bereits definiert: Attribute werden ignoriert.|
|[Compilerwarnung (Stufe 1) C4927](compiler-warning-level-1-c4927.md)|Ungültige Konvertierung; Es wurden mehrere benutzerdefinierte Konvertierungen implizit angewendet.|
|[Compilerwarnung (Stufe 1) C4928](compiler-warning-level-1-c4928.md)|Unzulässige Kopierinitialisierung. Mehrere benutzerdefinierte Konvertierungen wurden implizit übernommen|
|[Compilerwarnung (Stufe 1) C4929](compiler-warning-level-1-c4929.md)|"*File*": Typbibliothek enthält eine Union. der Qualifizierer "embedded_idl" wird ignoriert.|
|[Compilerwarnung (Stufe 1) C4930](compiler-warning-level-1-c4930.md)|"*Prototyp*": eine prototypisierte Funktion wird nicht aufgerufen (war eine Variablen Definition beabsichtigt?)|
|[Compilerwarnung (Stufe 4) C4931](compiler-warning-level-4-c4931.md)|Es wird angenommen, dass die Typbibliothek für Anzahl-Bit-Pointer erstellt wurde|
|[Compilerwarnung (Stufe 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*Bezeichner*) und \__identifier (*Bezeichner*) sind nicht unterscheidbar.|
|Compilerwarnung (Stufe 1) C4934|"__delegate (Multicast)" ist veraltet, verwenden Sie stattdessen "\__Delegate".|
|[Compilerwarnung (Stufe 1) C4935](compiler-warning-level-1-c4935.md)|Assemblyzugriffsspezifizierer geändert von "*Access*"|
|[Compilerwarnung (Stufe 1, Fehler) C4936](compiler-warning-c4936.md)|__declspec wird nur bei einer Kompilierung mit /clr oder /clr:pure unterstützt.|
|[Compilerwarnung (Stufe 4) C4937](compiler-warning-level-4-c4937.md)|'*text1*' und '*Text2*' sind als Argumente für '*Direktive*' nicht unterscheidbar.|
|[Compilerwarnung (Stufe 4) C4938](compiler-warning-level-4-c4938.md)|"*var*": die Variable für die Gleit Komma Reduzierung kann zu inkonsistenten Ergebnissen unter/fp: strict oder #pragma führen fenv_access|
|[Compilerwarnung C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp ist veraltet und wird in einer der nächsten Versionen von Visual C++ entfernt.|
|[Compilerwarnung (Stufe 1) C4944](compiler-warning-level-1-c4944.md)|'*Symbol*': das Symbol kann nicht aus '*Assembly1*' importiert werden: '*Symbol*' ist bereits im aktuellen Gültigkeitsbereich vorhanden.|
|[Compilerwarnung (Stufe 1) C4945](compiler-warning-level-1-c4945.md)|'*Symbol*': das Symbol kann nicht aus '*Assembly1*' importiert werden: da '*Symbol*' bereits aus einer anderen Assembly '*Assembly2*' importiert wurde.|
|[Compilerwarnung (Stufe 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast zwischen verknüpften Klassen verwendet: "*Class1*" und "*Klasse2*"|
|[Compilerwarnung (Stufe 1) C4947](compiler-warning-level-1-c4947.md)|'*type_or_member*': als veraltet markiert|
|[Compilerwarnung (Stufe 2) C4948](compiler-warning-level-2-c4948.md)|der Rückgabetyp von "*Accessor*" stimmt nicht mit dem letzten Parametertyp des entsprechenden Setters überein.|
|[Compilerwarnung (Ebene 1 und Ebene 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|die Pragmas "Managed" und "unmanaged" sind nur sinnvoll, wenn Sie mit "/CLR [: Option]" kompiliert werden.|
|[Compilerwarnung (Stufe 1, Fehler) C4950](compiler-warning-c4950.md)|'*type_or_member*': als veraltet markiert|
|[Compilerwarnung (Stufe 1) C4951](compiler-warning-level-1-c4951.md)|"*Funktion*" wurde bearbeitet, seit die Profildaten erfasst wurden. die Funktions Profildaten werden nicht verwendet.|
|[Compilerwarnung (Stufe 1) C4952](compiler-warning-level-1-c4952.md)|"*Funktion*": in der Programmdatenbank "*pgd_file*" wurden keine Profildaten gefunden.|
|[Compilerwarnung (Stufe 1) C4953](compiler-warning-level-1-c4953.md)|Inlinee "*Function*" wurde bearbeitet, seit die Profildaten erfasst wurden. die Profildaten werden nicht verwendet.|
|Compilerwarnung C4954|"*Funktion*": keine Profilerstellung (enthält __int64 Switch-Ausdruck)|
|Compilerwarnung C4955|"*import2*": der Import wird ignoriert. wurde bereits aus '*Import1*' importiert.|
|[Compilerwarnung (Stufe 1, Fehler) C4956](compiler-warning-c4956.md)|'*Typ*': dieser Typ ist nicht überprüfbar.|
|[Compilerwarnung (Stufe 1, Fehler) C4957](compiler-warning-c4957.md)|'*Cast*': die explizite Umwandlung von '*cast_from*' in '*cast_to*' ist nicht überprüfbar.|
|[Compilerwarnung (Stufe 1, Fehler) C4958](compiler-warning-c4958.md)|'*Operation*': die Zeigerarithmetik ist nicht überprüfbar.|
|[Compilerwarnung (Stufe 1, Fehler) C4959](compiler-warning-c4959.md)|der nicht verwaltete Typ '*Type*' in/CLR: Safe kann nicht definiert werden, da der Zugriff auf seine Member nicht überprüfbaren Code ergibt.|
|[Compilerwarnung (Stufe 4) C4960](compiler-warning-level-4-c4960.md)|"*Function*" ist zu groß für die Profilerstellung.|
|[Compilerwarnung (Stufe 1) C4961](compiler-warning-c4961.md)|In 'PGD-Datei' wurden keine Profildaten zusammengeführt, profilgesteuerte Optimierungen werden deaktiviert.|
|[Compilerwarnung (Stufe 4) C4962](compiler-warning-c4962.md)|"*Funktion*": Profil gesteuerte Optimierungen wurden deaktiviert, da durch Optimierungen das inkonsistente Profildaten verursacht wurde.|
|Compilerwarnung (Stufe 1) C4963|'*Beschreibung*': Es wurden keine Profildaten gefunden. in instrumentierter Build wurden verschiedene Compileroptionen verwendet.|
|[Compilerwarnung (Stufe 1) C4964](compiler-warning-level-1-c4964.md)|Es wurden keine Optimierungs Optionen angegeben. Profilinformationen werden nicht erfasst.|
|[Compilerwarnung (Stufe 1) C4965](compiler-warning-level-1-c4965.md)|Implizites Feld der Ganzzahl 0; Verwenden von nullptr oder expliziter Umwandlung|
|Compilerwarnung (Stufe 1) C4966|"*Function*" hat __code_seg Anmerkung mit nicht unterstützter Segment Name, Anmerkung wird ignoriert.|
|Compilerwarnung C4970|Delegatkonstruktor: das Zielobjekt wird ignoriert, da "*Type*" statisch ist.|
|Compilerwarnung (Stufe 1) C4971|Argument Reihenfolge: \<Zielobjekt >, \<Zielfunktion > für den Delegatkonstruktor ist veraltet, verwenden Sie \<Zielfunktion > \<target object = "" >|
|[Compilerwarnung (Stufe 1, Fehler) C4972](compiler-warning-c4972.md)|Das direkte Ändern oder Behandeln des Ergebnisses eines Unboxing-Vorgangs als L-Wert kann nicht überprüft werden.|
|Compilerwarnung (Stufe 1) C4973|'*Symbol*': als veraltet markiert|
|Compilerwarnung (Stufe 1) C4974|'*Symbol*': als veraltet markiert|
|Compilerwarnung (Stufe 3) C4981|Warbird: die Funktion "*Function*" ist als __forceinline nicht Inline gekennzeichnet, da Sie eine Ausnahme Semantik enthält.|
|[Compilerwarnung C4984](compiler-warning-c4984.md)|"if constexpr" ist eine c++ 17-Spracherweiterung|
|[Compilerwarnung (Stufe 4) C4985](compiler-warning-level-4-c4985.md)|'*symbol_name*': Attribute sind in vorheriger Deklaration nicht vorhanden.|
|[Compilerwarnung C4986](compiler-warning-c4986.md)|'*Deklaration*': die Ausnahme Spezifikation stimmt nicht mit der vorherigen Deklaration.|
|Compilerwarnung (Stufe 4) C4987|Es wurde eine nicht standardmäßige Erweiterung verwendet: 'throw (...)'|
|Compilerwarnung (Stufe 4) C4988|'*Variable*': Variable wurde außerhalb des Klassen-/Funktionsbereichs deklariert.|
|Compilerwarnung (Stufe 4) C4989|"*Typ*": der Typ weist in Konflikt stehende Definitionen auf.|
|Compilerwarnung (Stufe 3) C4990|Warbird: *Meldung*|
|Compilerwarnung (Stufe 3) C4991|Warbird: die Funktion "*Function*" ist als __forceinline nicht Inline gekennzeichnet, weil die Schutz Ebene von inlinees größer als das übergeordnete Element ist.|
|Compilerwarnung (Stufe 3) C4992|Warbird: die Funktion "*Funktion*" ist als __forceinline nicht Inline gekennzeichnet, weil Sie eine Inlineassembly enthält, die nicht geschützt werden kann.|
|[Compilerwarnung (Stufe 3) C4995](compiler-warning-level-3-c4995.md)|"*Function*": der Name wurde als veraltet markiert #Pragma|
|[Compilerwarnung (Stufe 3) C4996](compiler-warning-level-3-c4996.md)|"*deprecated-Declaration*": *depreation-Message* (oder "wurde als veraltet deklariert")|
|[Compilerwarnung (Stufe 1) C4997](compiler-warning-level-1-c4997.md)|"*Class*": die Co-Klasse implementiert keine COM-Schnittstelle oder Pseudo Schnittstelle.|
|Compilerwarnung (Stufe 1) C4998|Erwartung fehlgeschlagen: *Erwartung*(*Wert*)|
|[Compilerwarnung C4999](compiler-warning-level-1-c4999.md)|Unbekannte Warnung wählen Sie im Menü "visuelle C++ Hilfe" den Befehl "technischer Support", oder öffnen Sie die Hilfedatei für technischen Support, um weitere Informationen zu erhalten.|
|Compilerwarnung C5022|'*Type*': Es wurden mehrere bewegungskonstruktoren angegeben.|
|Compilerwarnung C5023|"*Typ*": mehrere Verschiebungs Zuweisungs Operatoren angegeben|
|Compilerwarnung (Stufe 4) C5024|"*Type*": der bewegungskonstruktor wurde implizit als gelöscht definiert.|
|Compilerwarnung (Stufe 4) C5025|"*Type*": der Bewegungs Zuweisungs Operator wurde implizit als gelöscht definiert.|
|Compilerwarnung (Ebene 1 und Ebene 4) C5026|"*Type*": der bewegungskonstruktor wurde implizit als gelöscht definiert.|
|Compilerwarnung (Ebene 1 und Ebene 4) C5027|"*Type*": der Bewegungs Zuweisungs Operator wurde implizit als gelöscht definiert.|
|Compilerwarnung (Stufe 1) C5028|'*Name*': die in vorheriger Deklaration (*Zahl*) angegebene Ausrichtung wurde in der Definition nicht angegeben.|
|Compilerwarnung (Stufe 4) C5029|nicht dem Standard entsprechende Erweiterung: Ausrichtungs C++ Attribute in gelten nur für Variablen, Datenmember und Tagtypen.|
|Compilerwarnung (Stufe 3) C5030|das Attribut '*Attribut*' wurde nicht erkannt.|
|Compilerwarnung (Stufe 4) C5031|#pragma Warnung (Pop): wahrscheinliche fehl Übereinstimmung, pping-Warn Status in anderer Datei übermittelt|
|Compilerwarnung (Stufe 4) C5032|#pragma Warnung (Push) ohne entsprechende #pragma Warnung (Pop) erkannt.|
|Compilerwarnung (Stufe 1) C5033|"*Storage-Class*" ist keine unterstützte Speicher Klasse mehr.|
|Compilerwarnung C5034|die Verwendung der systeminternen '*intrinsischen*' bewirkt, dass die Funktions *Funktion* als gastcode kompiliert wird.|
|Compilerwarnung C5035|die Verwendung der Funktion "*Feature*" bewirkt, dass die Funktions *Funktion* als gastcode kompiliert wird.|
|Compilerwarnung (Stufe 1) C5036|VarArgs-Funktionszeiger Konvertierung beim Kompilieren mit/Hybrid: x86arm64 '*Typ1*' in '*Typ2*'|
|Compilerwarnung (Fehler) C5037|"*Member-Function*": eine Out-of-Line-Definition eines Members einer Klassen Vorlage kann keine Standardargumente aufweisen.|
|[Compilerwarnung (Stufe 4) C5038](c5038.md)|der Datenmember "*Member1*" wird nach dem Datenmember "*member2*" initialisiert.|
|Compilerwarnung (Stufe 4) C5039|"*Function*": ein Zeiger oder Verweis auf eine potenziell auslösende Funktion, die an die externe C-Funktion unter "-EHC" Ein nicht definiertes Verhalten kann auftreten, wenn diese Funktion eine Ausnahme auslöst.|
|Compilerwarnung (Stufe 3) C5040|dynamische Ausnahme Spezifikationen sind nur in c++ 14 und früheren Versionen gültig. Behandeln von als "noaußer" (false)|
|Compilerwarnung (Stufe 1) C5041|"*Definition*": Out-of-Line-Definition für statisches constexpr-Datenmember ist nicht erforderlich und ist in c++ 17 veraltet.|
|Compilerwarnung (Stufe 3) C5042|'*Deklaration*': Funktions Deklarationen im Block Bereich können nicht ' Inline ' in C++Standard angegeben werden; Inline-Spezifizierer entfernen|
|Compilerwarnung (Stufe 2) C5043|"*Specification*": die Ausnahme Spezifikation stimmt nicht mit der vorherigen Deklaration.|
|Compilerwarnung (Stufe 4) C5044|Ein Argument für die Befehls *Zeilen Option-Option verweist auf* *einen Pfad,* der nicht vorhanden ist.|
| [Compilerwarnung C5045](c5045.md) | Der Compiler fügt eine Spectre-Entschärfung für die Speicherauslastung ein, wenn/Qspectre Switch angegeben |
| [Compilerwarnung (Stufe 2) C5046](c5046.md) | "*Function*": ein Symbol für den Typ mit interner Verknüpfung ist nicht definiert. |
| Compilerwarnung (Stufe 1) C5047 | Verwendung von nicht standardmäßigen \_\_wenn\_mit Modulen nicht unterstützt wird |
| Compilerwarnung (Stufe 1) C5048 | Die Verwendung des Makros "*macroname*" kann eine nicht deterministische Ausgabe zur Folge haben. |
| Compilerwarnung (Stufe 1) C5049 | "*String*": das Einbetten eines vollständigen Pfads kann zu einer Computer abhängigen Ausgabe führen. |
| Compilerwarnung (Stufe 1) C5050 | Mögliche inkompatible Umgebung beim Importieren des Moduls "*module_name*": *Problem* |
| Compilerwarnung (Stufe 1) C5100 | \_\_VA\_args\_\_ für die Verwendung in Variadic-Makros reserviert. |
| Compilerwarnung (Stufe 1) C5101 | die Verwendung der Präprozessordirektive in einer Funktions ähnlichen Makro Argumentliste ist nicht definiertes Verhalten. |
| Compilerwarnung (Stufe 1) C5102 | Ungültige Befehlszeilen-Makro Definition '*Wert*' wird ignoriert. |
| Compilerwarnung (Stufe 1) C5103 | das Einfügen von "*ttoken1*" und "*Token2*" führt nicht zu einem gültigen Vorverarbeitungs Token. |
| Compilerwarnung (Stufe 1) C5104 | "*Zeichenfolge1*#*Zeichenfolge2*" in der Liste "Makro Ersetzung" gefunden, meinten Sie "*Zeichenfolge1*" "#*Zeichenfolge2*"? |
| [Compilerwarnung (Stufe 1) C5105](c5105.md) | Makro Erweiterung beim Erzeugen von "Defined" hat ein nicht definiertes Verhalten |
| Compilerwarnung (Stufe 1) C5106 | Makro neu definiert mit unterschiedlichen Parameternamen |
| Compilerwarnung (Stufe 1) C5107 | Fehlendes abschließende Zeichen "*char*" |

## <a name="see-also"></a>Weitere Informationen

[Fehler undC++ Warnungen für C/Compiler und Buildtools](../compiler-errors-1/c-cpp-build-errors.md) \
[Compilerwarnungen C4000-C5999](compiler-warnings-c4000-c5999.md)
