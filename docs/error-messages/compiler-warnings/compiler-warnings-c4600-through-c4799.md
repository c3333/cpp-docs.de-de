---
title: Compilerwarnungen C4600 bis C4799
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 638af32b27f8d66086f3a39b74ecd46fdbb4649d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438172"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Compilerwarnungen C4600 bis C4799

In den Artikeln in diesem Abschnitt der Dokumentation wird eine Teilmenge der Warnmeldungen erläutert, die vom Compiler generiert werden.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Warnmeldungen

|Warnung|`Message`|
|-------------|-------------|
|[Compilerwarnung (Stufe 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#Pragma "Makro Name": Es wurde eine gültige nicht leere Zeichenfolge erwartet.|
|[Compilerwarnung (Stufe 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: "Makro Name" kein vorheriger #Pragma push_macro für diesen Bezeichner.|
|[Compilerwarnung (Stufe 1) C4603](compiler-warning-level-1-c4603.md)|"*Bezeichner*": das Makro ist nicht definiert, oder die Definition ist nach Verwendung des vorkompilierten Headers anders.|
|Compilerwarnung (Stufe 1) C4604|"*Typ*": das Übergeben eines Arguments nach Wert über die systemeigene und verwaltete Grenze erfordert einen gültigen Kopierkonstruktor. Andernfalls ist das Laufzeitverhalten nicht definiert.|
|Compilerwarnung (Stufe 1) C4605|"/D*Macro*" wurde in der aktuellen Befehlszeile angegeben, wurde jedoch beim Erstellen des vorkompilierten Headers nicht angegeben.|
|[Compilerwarnung (Stufe 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma Warnung: "Warnungs Nummer" wird ignoriert. Code Analyse Warnungen sind keinen Warn Stufen zugeordnet.|
|[Compilerwarnung (Stufe 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|"union_member" wurde bereits von einem anderen Union-Member in der Initialisierungsliste initialisiert, "union_member"|
|Compilerwarnung (Ebene 3, Fehler) C4609|"*Typ1*" wird von der Standardschnittstelle "*Interface*" für den Typ "*Typ2*" abgeleitet. Verwenden Sie eine andere Standardschnittstelle für "*Typ1*", oder unterbrechen Sie die Basis/abgeleitete Beziehung.|
|[Compilerwarnung (Stufe 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|Objekt "Klasse" kann nie instanziiert werden-benutzerdefinierter Konstruktor erforderlich|
|[Compilerwarnung (Stufe 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|die Interaktion zwischen "Function" C++ und der Objekt Zerstörung ist nicht portabel.|
|[Compilerwarnung (Stufe 1) C4612](compiler-warning-level-1-c4612.md)|Fehler im Namen der Includedatei|
|[Compilerwarnung (Stufe 1) C4613](compiler-warning-level-1-c4613.md)|'*Symbol*': die Klasse des Segments kann nicht geändert werden.|
|[Compilerwarnung (Stufe 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma Warnung: Unbekannter Benutzer Warnungstyp.|
|[Compilerwarnung (Stufe 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma Warnung: die Warnungs Nummer ' Number ' ist keine gültige Compilerwarnung.|
|[Compilerwarnung (Stufe 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|Pragma-Parameter enthalten eine leere Zeichenfolge. Pragma wird ignoriert.|
|[Compilerwarnung (Stufe 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma-Warnung: Keine Warnungsnummer 'number' vorhanden|
|[Compilerwarnung (Stufe 1) C4620](compiler-warning-level-1-c4620.md)|Keine Postfix-Form von 'Operator ++' für den Typ 'Typ' gefunden, Präfix-Form verwendet|
|[Compilerwarnung (Stufe 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|Es wurde keine Postfix-Form "Operator--" für den Typ "Type" gefunden, Präfix-Formular verwendet.|
|[Compilerwarnung (Stufe 3) C4622](compiler-warning-level-3-c4622.md)|Überschreiben von Debuginformationen, die beim Erstellen des vorkompilierten Headers in der Objektdatei erstellt wurden: "file"|
|[Compilerwarnung (Stufe 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|' abgeleitete Klasse ': der Standardkonstruktor wurde implizit als gelöscht definiert, da der Standardkonstruktor der Basisklasse nicht zugänglich ist oder gelöscht wird.|
|[Compilerwarnung (Stufe 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|' abgeleitete Klasse ': der Dekonstruktor wurde implizit als gelöscht definiert, da auf einen basisklassendekonstruktor nicht zugegriffen werden kann|
|[Compilerwarnung (Stufe 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|' abgeleitete Klasse ': der Kopierkonstruktor wurde implizit als gelöscht definiert, da auf einen basisklassenkopierkonstruktor nicht zugegriffen werden kann.|
|[Compilerwarnung (Stufe 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|' abgeleitete Klasse ': der Zuweisungs Operator wurde implizit als gelöscht definiert, da ein Basisklassen Zuweisungs Operator nicht verfügbar oder gelöscht ist.|
|[Compilerwarnung (Stufe 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<Identifier > ': beim Suchen der Verwendung vorkompilierter Header übersprungen|
|[Compilerwarnung (Stufe 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|'digraphs' werden mit '-Ze' nicht unterstützt. Die Zeichenfolge "Digraph" wird nicht als alternatives Token für "% s" interpretiert.|
|[Compilerwarnung (Stufe 4) C4629](compiler-warning-level-4-c4629.md)|"Digraph" wurde verwendet, Zeichensequenz "Digraph" wurde als Token "Zeichen" interpretiert (Fügen Sie zwischen den beiden Zeichen ein Leerzeichen ein, wenn Sie etwas anderes beabsichtigt haben)|
|[Compilerwarnung (Stufe 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|"Symbol": der Speicherklassenspezifizierer "extern" ist für die Element Definition unzulässig.|
|Compilerwarnung (Stufe 2) C4631|MSXML oder XPath ist nicht verfügbar. XML-Dokumentkommentare werden nicht verarbeitet. reason|
|[Compilerwarnung (Stufe 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML-Dokument Kommentar: Dateizugriff verweigert: Grund|
|[Compilerwarnung (Stufe 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML-Dokument Kommentar Ziel: Fehler: Grund|
|[Compilerwarnung (Stufe 4) C4634](compiler-warning-level-4-c4634.md)|XML-Dokument Kommentar Ziel: kann nicht angewendet werden: Grund|
|[Compilerwarnung (Stufe 3) C4635](compiler-warning-level-3-c4635.md)|XML-Dokumentkommentarziel: Ungültige XML: Grund|
|[Compilerwarnung (Stufe 3) C4636](compiler-warning-level-3-c4636.md)|Auf das Konstrukt angewendeter XML-Dokument Kommentar: für das Tag ist ein nicht leeres Attribut Attribut erforderlich.|
|[Compilerwarnung (Ebene 3 und Ebene 4) C4637](compiler-warning-level-3-c4637.md)|XML-Dokument Kommentar Ziel: \<> Tag enthalten, das verworfen wurde. `Reason`|
|[Compilerwarnung (Stufe 3) C4638](compiler-warning-level-3-c4638.md)|XML-Dokument Kommentar Ziel: Verweis auf unbekanntes Symbol ' Symbol '.|
|[Compilerwarnung (Stufe 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML-Fehler: XML-Dokument Kommentare werden nicht verarbeitet. `Reason`|
|[Compilerwarnung (Stufe 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|„Instanz“: Erstellen eines lokalen static-Objekts ist nicht threadsicher|
|[Compilerwarnung (Stufe 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML-Dokument Kommentar enthält einen mehrdeutigen Querverweis:|
|[Compilerwarnung (Stufe 3) C4645](compiler-warning-level-3-c4645.md)|Eine Funktion, die mit "__declspec(noreturn)" deklariert wurde, hat eine Rückgabeanweisung|
|[Compilerwarnung (Stufe 3) C4646](compiler-warning-level-3-c4646.md)|Eine Funktion, die mit "__declspec(noreturn)" deklariert wurde, hat einen nicht leeren Rückgabetyp|
|Compilerwarnung (Stufe 3) C4647|Behavior Change: __is_pod (*Typ*) hat in früheren Versionen einen anderen Wert.|
|Compilerwarnung (Stufe 3) C4648|Das Standard Attribut "carries_dependency" wird ignoriert.|
|Compilerwarnung (Stufe 3) C4649|Attribute werden in diesem Kontext ignoriert.|
|[Compilerwarnung (Stufe 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|Debuginformationen nicht in vorkompiliertem Header; Es sind nur globale Symbole aus dem Header verfügbar.|
|[Compilerwarnung (Stufe 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|"Definition" für den vorkompilierten Header, aber nicht für die aktuelle Kompilierung angegeben|
|[Compilerwarnung (Stufe 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|die Compileroption "Option" ist inkonsistent mit dem vorkompilierten Header die aktuelle Befehlszeilenoption überschreibt, die im vorkompilierten Header definiert ist.|
|[Compilerwarnung (Stufe 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|die Compileroption "Option" ist inkonsistent mit dem vorkompilierten Header aktuelle Befehlszeilenoption wird ignoriert.|
|Compilerwarnung (Stufe 4) C4654|Der Code, der vor dem einschließen der vorkompilierten Kopfzeile eingefügt wurde, wird ignoriert. Fügen Sie dem vorkompilierten Header Code hinzu.|
|[Compilerwarnung (Stufe 1) C4655](compiler-warning-level-1-c4655.md)|' Symbol ': der Variablentyp ist neu seit dem letzten Build oder wurde an anderer Stelle unterschiedlich definiert.|
|[Compilerwarnung (Stufe 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|' Symbol ': der Datentyp ist neu oder wurde seit dem letzten Build geändert, oder er wurde an anderer Stelle unterschiedlich definiert.|
|[Compilerwarnung (Stufe 1) C4657](compiler-warning-level-1-c4657.md)|der Ausdruck enthält einen Datentyp, der seit dem letzten Build neu ist.|
|Compilerwarnung (Stufe 1) C4658|"Function": der Funktionsprototyp ist neu seit dem letzten Build oder wurde an anderer Stelle unterschiedlich deklariert.|
|[Compilerwarnung (Stufe 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma ' pragma ': die Verwendung des reservierten Segments ' Segment ' weist ein undefiniertes Verhalten auf. verwenden Sie #pragma Kommentar (linker,...).|
|[Compilerwarnung (Stufe 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|"Bezeichner": für die explizite Vorlagen Instanziierung-Anforderung wurde keine passende Definition bereitgestellt.|
|[Compilerwarnung (Stufe 1) C4662](compiler-warning-level-1-c4662.md)|Explizite Instanziierung; Vorlagenklasse "Bezeichner1" besitzt keine Definition, von der "Bezeichner2" spezialisiert werden kann.|
|[Compilerwarnung (Stufe 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|"Function": Es ist keine Funktions Vorlage definiert, die der erzwungenen Instanziierung entspricht.|
|[Compilerwarnung (Stufe 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|' Symbol ' ist nicht als Präprozessormakro definiert und wird durch ' 0 ' für ' Direktive ' ersetzt|
|[Compilerwarnung (Stufe 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|"Cast": unsichere Konvertierung: "Class" ist ein Objekt mit verwaltetem Typ.|
|[Compilerwarnung (Stufe 4) C4670](compiler-warning-level-4-c4670.md)|"Bezeichner": auf diese Basisklasse kann nicht zugegriffen werden.|
|Compilerwarnung (Stufe 4) C4671|' Identifier ': auf den Kopierkonstruktor kann nicht zugegriffen werden.|
|[Compilerwarnung (Stufe 4) C4672](compiler-warning-level-4-c4672.md)|' Bezeichner1 ': mehrdeutig. Zuerst als 'identifier2' aufgetreten|
|[Compilerwarnung (Stufe 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|das Auslösen von "Identifier" der folgenden Typen wird auf der catch-Site nicht berücksichtigt.|
|[Compilerwarnung (Stufe 1) C4674](compiler-warning-level-1-c4674.md)|"Methode" sollte als "static" deklariert werden und nur einen Parameter haben|
|Compilerwarnung (Stufe 4) C4676|"% s": auf den Dekonstruktor kann nicht zugegriffen werden.|
|[Compilerwarnung (Stufe 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|"Funktion": die Signatur des nicht privaten Members enthält den privaten Assemblytyp "private_type".|
|[Compilerwarnung (Stufe 1) C4678](compiler-warning-level-1-c4678.md)|Die Basisklasse 'base_type' hat eine stärkere Zugriffsbeschränkung als 'derived_type'|
|[Compilerwarnung (Stufe 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|"Member": der Member konnte nicht importiert werden.|
|[Compilerwarnung (Stufe 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|"Class": die Co-Klasse gibt keine Standardschnittstelle an.|
|[Compilerwarnung (Stufe 4) C4681](compiler-warning-level-4-c4681.md)|"Class": die Co-Klasse gibt keine Standardschnittstelle an, die eine Ereignis Quelle ist.|
|[Compilerwarnung (Stufe 4) C4682](compiler-warning-level-4-c4682.md)|"Parameter": Es wurde kein direktionales Parameter Attribut angegeben, standardmäßig [in]|
|[Compilerwarnung (Stufe 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|' function ': die Ereignis Quelle hat einen ' out'-Parameter; Vorsicht beim Einbinden mehrerer Ereignishandler|
|[Compilerwarnung (Stufe 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' Attribut ': Warnung! das Attribut kann eine ungültige Codegenerierung verursachen: Verwendung mit Vorsicht.|
|[Compilerwarnung (Stufe 1) C4685](compiler-warning-level-1-c4685.md)|"> >" erwartet. ">>" wurde beim Verarbeiten der Vorlagenparameter gefunden|
|[Compilerwarnung (Stufe 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'benutzerdefinierter Typ': mögliche Verhaltensänderung, Änderung in der UDT gibt Aufrufkonvention zurück|
|[Compilerwarnung (Fehler) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|"Class": eine versiegelte abstrakte Klasse kann keine Schnittstelle "Schnittstelle" implementieren.|
|[Compilerwarnung (Stufe 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|"constraint": Die Einschränkungsliste enthält den privaten Assemblytyp "type".|
|Compilerwarnung (Stufe 1) C4689|"% c": nicht unterstütztes Zeichen in #pragma detect_mismatch; #pragma ignoriert|
|[Compilerwarnung (Stufe 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (Pop)]: mehr POPs als Pushvorgänge|
|[Compilerwarnung (Stufe 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|"Typ": der Typ, auf den verwiesen wird, wurde in einer nicht referenzierten Assembly "file" erwartet, die in der aktuellen Übersetzungseinheit definiert ist.|
|[Compilerwarnung (Stufe 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'Funktion': Die Signatur des nicht privaten Members enthält den privaten systemeigenen Assemblytyp 'systemeigener_Typ'|
|[Compilerwarnung (Stufe 1, Fehler) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|' Klasse ': eine versiegelte abstrakte Klasse kann keine Instanzmember ' Instanzmember ' aufweisen.|
|[Compilerwarnung (Stufe 1, Fehler) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|' class ': eine versiegelte abstrakte Klasse kann keine Basisklasse ' BASE_CLASS ' aufweisen.|
|Compilerwarnung (Stufe 1) C4695|#pragma execution_character_set: "Zeichensatz" ist kein unterstütztes Argument: Derzeit wird nur "UTF-8" unterstützt.|
|Compilerwarnung (Stufe 1) C4696|Die/ZBvalue1-Option liegt außerhalb des zulässigen Bereichs. angenommen, "Value2"|
|[Compilerwarnung (Ebene 1 und Ebene 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|die nicht initialisierte lokale Variable "Name" wurde verwendet.|
|[Compilerwarnung (Stufe 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|Möglicherweise wurde die nicht initialisierte lokale Variable "Name" verwendet.|
|[Compilerwarnung (Stufe 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|nicht erreichbarer Code|
|[Compilerwarnung (Stufe 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|die möglicherweise nicht initialisierte lokale Zeiger Variable "% s" wurde verwendet.|
|[Compilerwarnung (Stufe 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|Zuweisung in bedingtem Ausdruck|
|[Compilerwarnung (Stufe 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|Komma-Operator innerhalb des Array Index Ausdrucks|
|[Compilerwarnung (Stufe 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'Funktion': Funktion ist nicht inline|
|[Compilerwarnung (Stufe 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|Funktion "Function" ausgewählt für automatische Inline Erweiterung|
|[Compilerwarnung (Stufe 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|die Funktion "Function" ist als __forceinline nicht Inline gekennzeichnet.|
|[Compilerwarnung (Stufe 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|"Function": nicht alle Steuerelement Pfade geben einen Wert zurück.|
|[Compilerwarnung (Stufe 1, Fehler) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|"Function": muss einen Wert zurückgeben.|
|[Compilerwarnung (Stufe 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|"Function": rekursiv für alle Steuerelement Pfade, Funktion führt zu einem Lauf Zeit Stapelüberlauf|
|[Compilerwarnung (Stufe 4) C4718](compiler-warning-level-4-c4718.md)|' Funktionsaufrufe ': der rekursive aufrufsvorgang hat keine Nebeneffekte, wird gelöscht|
|Compilerwarnung (Stufe 1) C4719|Doppelte Konstante gefunden, wenn Qfast angegeben ist. verwenden Sie "f" als Suffix, um eine einzelne Genauigkeit anzugeben.|
|Compilerwarnung (Stufe 2) C4720|in-line-Assembler-Berichte: "Message"|
|Compilerwarnung (Stufe 1) C4721|"Funktion": nicht als systeminterne Funktion verfügbar|
|[Compilerwarnung (Stufe 1) C4722](compiler-warning-level-1-c4722.md)|"Function": der Dekonstruktor gibt nie zurück, potenzieller Speicherplatz.|
|[Compilerwarnung (Stufe 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|mögliche Teilung durch 0|
|[Compilerwarnung (Stufe 3) C4724](compiler-warning-level-3-c4724.md)|Mögliches Modulo durch 0 (Null)|
|Compilerwarnung (Stufe 3) C4725|Anweisung kann auf einigen Pentium-Prozessoren ungenau sein|
|[Compilerwarnung (Stufe 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH mit dem Namen Pch_file mit demselben Zeitstempel, der in obj_file_1 und obj_file_2 gefunden wurde.  Verwenden des ersten PCH.|
|Compilerwarnung (Stufe 1) C4728|Die/yl-Option wird-Option wird ignoriert, da ein PCH-Verweis erforderlich|
|Compilerwarnung (Stufe 4) C4729|Die Funktion ist zu groß für auf Verlaufdiagrammen basierende Warnungen.|
|[Compilerwarnung (Stufe 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md) Compilerwarnung (Stufe 1) C4730|"Main": das Mischen von _m64 und Gleit Komma Ausdrücken kann zu fehlerhaftem Code führen.|
|[Compilerwarnung (Stufe 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|"Pointer": Frame Zeiger Register "Register" geändert durch Inline-Assemblycode|
|Compilerwarnung (Stufe 1) C4732|die systeminterne Funktion "% s" wird in dieser Architektur nicht unterstützt.|
|[Compilerwarnung (Stufe 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Inline-ASM weist "FS: 0" zu: der Handler ist nicht als sicherer Handler registriert.|
|[Compilerwarnung (Stufe 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|Das 32-Bit-Gleitkommaergebnis wird im Speicher gespeichert. Möglicherweise kommt es zu einem Leistungsverlust|
|[Compilerwarnung (Stufe 1) C4739](compiler-warning-level-1-c4739.md)|Für den Verweis auf die Variable 'var' ist nicht genügend Speicherplatz vorhanden.|
|[Compilerwarnung (Stufe 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|Flow in oder aus Inline-ASM-Code unterdrückt globale Optimierung|
|[Compilerwarnung (Stufe 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|"var" hat eine unterschiedliche Ausrichtung in "file1" und "file2": Anzahl und Zahl|
|[Compilerwarnung (Stufe 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|"Type" hat eine unterschiedliche Größe in "file1" und "file2": Anzahl und Anzahl von Bytes|
|[Compilerwarnung (Stufe 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|"var" weist einen anderen Typ in "file1" und "file2" auf: "Typ1" und "Typ2".|
|[Compilerwarnung C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|flüchtiger Zugriff auf "*Expression*" unterliegt/volatile:\<ISO&#124;MS > Einstellung; Verwenden Sie __iso_volatile_load intrinsischen/Store-Funktionen.|
|[Compilerwarnung (Stufe 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Der verwaltete "EntryPoint" wird aufgerufen: verwalteter Code darf nicht unter der Loadersperre ausgeführt werden, einschließlich des dll-Einstiegs Punkts und der Aufrufe, die vom DLL-Einstiegspunkt aus erreicht werden.|
|Compilerwarnung (Stufe 4) C4749|bedingt unterstützt: OffsetOf angewendet auf den Typ "*Typ*", der nicht dem Standardlayout entspricht.|
|[Compilerwarnung (Stufe 1) C4750](compiler-warning-level-1-c4750.md)|'Bezeichner': Funktion mit „_alloca()“ „inline“ in einer Schleife|
|Compilerwarnung (Stufe 4) C4751|/Arch: AVX gilt nicht für Intel (R)-Streaming SIMD Extensions, die sich innerhalb von Inline-ASM befinden.|
|Compilerwarnung (Stufe 4) C4752|Intel (R) Advanced Vector Extensions gefunden; Verwenden Sie ggf./Arch: AVX|
|[Compilerwarnung (Stufe 4) C4754](compiler-warning-level-4-c4754.md)|Die Konvertierungsregeln für arithmetische Vorgänge im Vergleich bei% s (% d) bedeuten, dass eine Verzweigung nicht ausgeführt werden kann. "% S" wird in "% s" umgewandelt (oder in einen ähnlichen Typ von% d Bytes).|
|Compilerwarnung C4755|Die Konvertierungsregeln für arithmetische Vorgänge im Vergleich bei% s (% d) bedeuten, dass eine Verzweigung nicht in einer Inline Funktion ausgeführt werden kann. "% S" wird in "% s" umgewandelt (oder in einen ähnlichen Typ von% d Bytes).|
|[Compilerwarnung (Stufe 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|Überlauf bei konstanter Arithmetik|
|Compilerwarnung (Stufe 4) C4757|der Index ist ein großer unsignierter Wert, haben Sie eine negative Konstante beabsichtigt?|
|[Compilerwarnung (Stufe 4) C4764](compiler-warning-level-4-c4764.md)|Catch-Objekte können nicht mehr als 16 Bytes ausgerichtet werden.|
|Compilerwarnung (Stufe 4) C4767|der Abschnitts Name "% s" ist länger als 8 Zeichen und wird vom Linker abgeschnitten.|
|Compilerwarnung (Stufe 3) C4768|__declspec Attribute, bevor die Verknüpfungs Angabe ignoriert wird|
|Compilerwarnung C4770|der teilweise validierte Enumeration "*Name*" wird als Index verwendet.|
|Compilerwarnung C4771|Grenzen müssen mit einem einfachen Zeiger erstellt werden. Systeminterne MPX-Funktion wird ignoriert|
|[Compilerwarnung (Stufe 1, Fehler) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#Import auf einen Typ aus einer fehlenden Typbibliothek verwiesen; "Missing_type" als Platzhalter verwendet|
|Compilerwarnung (Stufe 4) C4774|"*String*": die in der Argument *Nummer* erwartete Format Zeichenfolge ist kein Zeichenfolgenliteral|
|Compilerwarnung (Stufe 3) C4775|nicht dem Standard entsprechende Erweiterung in der Format Zeichenfolge "*String*" der Funktion "*Function*" verwendet.|
|Compilerwarnung (Stufe 1) C4776|"%*Character*" ist in der Format Zeichenfolge der Funktion "*Function*" nicht zulässig.|
|Compilerwarnung (Stufe 4) C4777|"*Function*": die Format Zeichenfolge "*String*" erfordert ein Argument vom Typ "*Typ1*", die Variadic-Argument *Nummer* weist jedoch den Typ "*Typ2*" auf.|
|Compilerwarnung (Stufe 3) C4778|"*Function*": nicht abgeschlossener Format Zeichenfolge "*String*"|
|[Compilerwarnung (Stufe 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|"Bezeichner": der Bezeichner wurde auf "Number"-Zeichen gekürzt.|
|[Compilerwarnung (Stufe 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|Der Puffer 'Bezeichner' mit der Größe von N-Bytes wird überlaufen; M-Bytes werden ab Offset L geschrieben.|
|Compilerwarnung (Stufe 2) C4792|die Funktion "% s" wurde mithilfe von "sysimport" deklariert und aus System eigenem Code referenziert. Import Bibliothek ist zum Verknüpfen erforderlich.|
|[Compilerwarnung (Stufe 1 und 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|"Function": als System eigen kompilierte Funktion: \ n\t "Reason"|
|[Compilerwarnung (Stufe 1) C4794](compiler-warning-level-1-c4794.md)|Das Segment der lokalen Thread Speicher Variable "% s" wurde von "% s" in "% s" geändert.|
|[Compilerwarnung (Stufe 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|die Funktion "Function" hat keine EMMS-Anweisung.|

## <a name="see-also"></a>Weitere Informationen

[Fehler undC++ Warnungen für C/Compiler und Buildtools](../compiler-errors-1/c-cpp-build-errors.md) \
[Compilerwarnungen C4000-C5999](compiler-warnings-c4000-c5999.md)
