---
title: Compilerfehler C3400 bis C3499
ms.date: 04/21/2019
f1_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
helpviewer_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
ms.assetid: a5651dfb-c402-4e01-b3ae-28f371e51d6a
ms.openlocfilehash: f4aff80178033d34cf051a14d89736b2b8347dd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446836"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Compilerfehler C3400 bis C3499

In den Artikeln in diesem Abschnitt der Dokumentation wird eine Teilmenge der Fehlermeldungen erläutert, die vom Compiler generiert werden.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Fehlermeldungen

|Fehler|`Message`|
|-----------|-------------|
|[Compilerfehler C3400](compiler-error-c3400.md)|zirkuläre Einschränkungs Abhängigkeit mit "*einschränkung1*" und "*einschränkung2*"|
|Compilerfehler C3401|"*Spezifizierer*": Ungültiger Assemblyzugriffsspezifizierer-nur "private" ist für Klassen Vorlagen zulässig.|
|Compilerfehler C3402|"*Funktion*": die Überladung kann nicht im aktuellen Gültigkeitsbereich aufgelöst werden.|
|Compilerfehler C3403|thread_local kann nicht mit/CLR: pure oder/CLR: Safe verwendet werden.|
|Compilerfehler C3404|'*Construct*': Unerwarteter Syntax Fehler|
|Compilerfehler C3405|"*Funktion*": Überladung kann nicht ohne vervollständigen-Deskriptor aufgelöst werden.|
|Compilerfehler C3406|'*Schlüsselwort*': kann nicht in einem ausführlichen Typspezifizierer verwendet werden.|
|Compilerfehler C3407|"*Type*" kann in diesem Kontext nicht verwendet werden.|
|[Compilerfehler C3408](compiler-error-c3408.md)|"*Attribut*": das Attribut ist für Vorlagen Definitionen nicht zulässig.|
|[Compilerfehler C3409](compiler-error-c3409.md)|ein leerer Attribut Block ist nicht zulässig.|
|Compilerfehler C3410|'*Identifier*': der Typ der expliziten Instanziierung '*Type*' stimmt nicht mit dem Typ der Variablen Vorlage '*Type*' identisch.|
|Compilerfehler C3411|'*Type*' ist nicht als Größe eines Arrays gültig, da es sich nicht um einen ganzzahligen Typ handelt.|
|[Compilerfehler C3412](compiler-error-c3412.md)|"*Spezialisierung*": die Vorlage kann im aktuellen Bereich nicht spezialisiert werden.|
|[Compilerfehler C3413](compiler-error-c3413.md)|"*Template*": Ungültige explizite Instanziierung.|
|[Compilerfehler C3414](compiler-error-c3414.md)|"*Funktion*": die importierte Member-Funktion kann nicht definiert werden.|
|[Compilerfehler C3415](compiler-error-c3415.md)|mehrere "*section*"-Abschnitte mit unterschiedlichen Attributen gefunden ("0x-*Wert*")|
|Compilerfehler C3416 generiert|Veraltet.|
|[Compilerfehler C3417](compiler-error-c3417.md)|"*Deklarator*": Werttypen können keine benutzerdefinierten speziellen Member-Funktionen enthalten.|
|[Compilerfehler C3418](compiler-error-c3418.md)|Zugriffsspezifizierer "*Spezifizierer*" wird nicht unterstützt|
|Compilerfehler C3419|Veraltet.|
|[Compilerfehler C3420](compiler-error-c3420.md)|"*Funktion*": ein Finalizer kann nicht virtuell sein.|
|[Compilerfehler C3421](compiler-error-c3421.md)|"*Funktion*": Sie können den Finalizer für diese Klasse nicht aufzurufen, da er entweder nicht verfügbar oder nicht vorhanden ist.|
|Compilerfehler C3422|'*Deklaration*': nicht übereinstimmende Typen '*Type*' und '*Type*'.|
|Compilerfehler C3423|Veraltet.|
|Compilerfehler C3424|"Type": eine*Typumwandlung*in einen Arraytyp ist nicht zulässig.|
|Compilerfehler C3425|Ein Zeiger auf ein Objekt des unvollständigen Typs "*Typ*" kann nicht ausgelöst werden|
|Compilerfehler C3426|ein Objekt vom unvollständigen Typ "*Type*" kann nicht ausgelöst werden.|
|Compilerfehler C3427|'*context*': '*Schlüsselwort*' kann nicht mit layout_version (*Zahl*) verwendet werden.|
|Compilerfehler C3428|'*context*': '*Schlüsselwort*' kann nur auf Klassen Deklarationen oder Definitionen angewendet werden.|
|Compilerfehler C3429|'*context*': '*Schlüsselwort*' kann nicht auf eine Union angewendet werden.|
|Compilerfehler C3430|eine Bereichs bezogene Enumeration muss einen Namen haben.|
|Compilerfehler C3431|"*Bezeichner*": *Typ1* kann nicht erneut als *Typ2* deklariert werden.|
|Compilerfehler C3432|"*Bezeichner*": eine vorwärts Deklaration einer Enumeration ohne Bereichs Einschränkung muss über einen zugrunde liegenden Typ verfügen.|
|Compilerfehler C3433|'*Bezeichner*': alle Deklarationen einer Enumeration müssen denselben zugrunde liegenden Typ aufweisen, was '*Typ1*' jetzt '*Typ2*' ist.|
|Compilerfehler C3434|'*context*': der Enumeratorwert '*Number*' kann nicht als '*Type*' dargestellt werden, der Wert ist '*Number*'.|
|Compilerfehler C3435|der Zeichensatz "*Name*" wird nicht unterstützt.|
|Compilerfehler C3436|#pragma setlocale wird nicht unterstützt, wenn "/Source-charset", "/Execution-charset" oder "/UTF-8" angegeben wurde.|
|Compilerfehler C3437|#pragma execution_character_set wird nicht unterstützt, wenn "/Source-charset", "/Execution-charset" oder "/UTF-8" angegeben wurde.|
|Compilerfehler C3438|'*context*': '*value*' kann nicht auf eine verwaltete/WinRT-Klasse angewendet werden.|
|Compilerfehler C3439|layout_version (*Zahl*): Ungültige Versionsnummer.|
|Compilerfehler C3440|'*Deklaration*': layout_version (*Zahl*) ist mit einer vorherigen Deklaration nicht kompatibel.|
|Compilerfehler C3441|'*Deklaration*': '*Schlüsselwort*' kann nicht angewendet werden, nachdem die Klasse definiert wurde.|
|Compilerfehler C3442|Initialisieren mehrerer Member der Union: "*Member1*" und "*member2*"|
|Compilerfehler C3443|Der Standardmember-Initialisierer für "*Class*" ist rekursiv.|
|Compilerfehler C3444|Die leere Aggregat Klasse "*Class*" muss mit "{}" initialisiert werden.|
|[Compilerfehler C3445](compiler-error-c3445.md)|die Copy-List-Initialisierung von "*Type*" kann keinen expliziten Konstruktor verwenden.|
|[Compilerfehler C3446](compiler-error-c3446.md)|"*Klasse*": ein Standardmember-Initialisierer ist für einen Member einer Wert Klasse nicht zulässig.|
|Compilerfehler C3447|Veraltet.|
|Compilerfehler C3448|Veraltet.|
|Compilerfehler C3449|Veraltet.|
|[Compilerfehler C3450](compiler-error-c3450.md)|'*Typ*': kein Attribut; [System:: AttributeUsageAttribute]/[Windows:: Foundation:: Metadata:: AttributeUsageAttribute] kann nicht angegeben werden.|
|[Compilerfehler C3451](compiler-error-c3451.md)|'*Attribut*': das nicht verwaltete Attribut kann nicht auf '*Type*' angewendet werden.|
|[Compilerfehler C3452](compiler-error-c3452.md)|Der Listenargumentmember ist keine Konstante.|
|[Compilerfehler C3453](compiler-error-c3453.md)|"*Attribut*": das Attribut wurde nicht angewendet, da der Qualifizierer "*Qualifizierer*" nicht entsprach|
|[Compilerfehler C3454](compiler-error-c3454.md)|[attribut] ist in der Klassendeklaration nicht zulässig|
|[Compilerfehler C3455](compiler-error-c3455.md)|'*Attribut*': keiner der Attributkonstruktoren stimmte mit den Argumenten überein.|
|[Compilerfehler C3456](compiler-error-c3456.md)|[Quelle\_annotation_attribute] nicht zulässig für verwaltete/WinRT-Klassen Deklaration.|
|[Compilerfehler C3457](compiler-error-c3457.md)|"*Attribut*": das Attribut unterstützt keine unbenannten Argumente.|
|[Compilerfehler C3458](compiler-error-c3458.md)|"[*Attribute*]": das Attribut "[*Attribute*]" wurde bereits für "*Identifier*" angegeben.|
|[Compilerfehler C3459](compiler-error-c3459.md)|"[*Attribute*]": das Attribut ist nur für den Klassenindexer (indizierte Standard Eigenschaft) zulässig.|
|[Compilerfehler C3460](compiler-error-c3460.md)|"*Typ*": nur ein benutzerdefinierter Typ kann weitergeleitet werden.|
|[Compilerfehler C3461](compiler-error-c3461.md)|"*Typ*": nur ein verwalteter/WinRT-Typ kann weitergeleitet werden.|
|[Compilerfehler C3462](compiler-error-c3462.md)|"*Typ*": nur ein importierter Typ kann weitergeleitet werden.|
|[Compilerfehler C3463](compiler-error-c3463.md)|"*Typ*": der Typ ist im Attribut "implementiert" nicht zulässig.|
|[Compilerfehler C3464](compiler-error-c3464.md)|der*Typ "Type*" kann nicht weitergeleitet werden.|
|[Compilerfehler C3465](compiler-error-c3465.md)|um den Typ "*Typ*" zu verwenden, müssen Sie auf die Assembly "*Assembly*" verweisen.|
|[Compilerfehler C3466](compiler-error-c3466.md)|"*Typ*": eine Spezialisierung einer generischen Klasse kann nicht weitergeleitet werden.|
|[Compilerfehler C3467](compiler-error-c3467.md)|'*Typ*': dieser Typ wurde bereits weitergeleitet.|
|[Compilerfehler C3468](compiler-error-c3468.md)|"*Typ*": Sie können einen Typ nur an eine Assembly weiterleiten: "*Bezeichner*" ist keine Assembly.|
|[Compilerfehler C3469](compiler-error-c3469.md)|'*Typ*': eine generische Klasse kann nicht weitergeleitet werden.|
|[Compilerfehler C3470](compiler-error-c3470.md)|"*Klasse*": eine Klasse kann nicht gleichzeitig einen Indexer (indizierte Standard Eigenschaft) und einen []-Operator aufweisen.|
|Compilerfehler C3471|neuer *Name des Modul namens (fest* gelegt in der Befehlszeile) verursacht einen Konflikt mit dem vorherigen namens *Namen*|
|Compilerfehler C3472|neuer Name der Ausgabe *Datei (fest* gelegt in der Befehlszeile) verursacht einen Konflikt mit dem vorherigen Dateinamen *Dateiname*|
|Compilerfehler C3473|Es wurde kein Ausgabe Pfadname oder Modulname angegeben.|
|Compilerfehler C3474|Ausgabedatei "*Dateiname*" konnte nicht geöffnet werden.|
|Compilerfehler C3475|Syntax Fehler in der Eingabedatei "*Dateiname*".|
|Compilerfehler C3476|die Datei "*filename*" konnte nicht für die Eingabe geöffnet werden.|
|Compilerfehler C3477|ein Lambda kann nicht in einem nicht ausgewerteten Kontext angezeigt werden.|
|Compilerfehler C3478|"*Bezeichner*": ein Array kann nicht per Kopie aufgezeichnet werden.|
|Compilerfehler C3479|SAL-Anmerkungen in Lambdas werden nicht unterstützt.|
|[Compilerfehler C3480](compiler-error-c3480.md)|"*Variable*": eine Lambda Erfassungs Variable muss aus einem einschließenden Funktionsbereich bestehen.|
|[Compilerfehler C3481](compiler-error-c3481.md)|"*Bezeichner*": Lambda Erfassungs Variable wurde nicht gefunden.|
|[Compilerfehler C3482](compiler-error-c3482.md)|"this" kann nur als Lambdaerfassung innerhalb einer nicht statischen Memberfunktion verwendet werden.|
|[Compilerfehler C3483](compiler-error-c3483.md)|"*Identifier*" ist bereits Teil der Lambda Erfassungs Liste.|
|[Compilerfehler C3484](compiler-error-c3484.md)|Syntax Fehler: "->" vor dem Rückgabetyp erwartet.|
|[Compilerfehler C3485](compiler-error-c3485.md)|Eine Lambdadefinition kann keine CV-Qualifizierer aufweisen.|
|Compilerfehler C3486|Veraltet.|
|[Compilerfehler C3487](compiler-error-c3487.md)|'*Typ*': alle Rückgabe Ausdrücke müssen in denselben Typ hergeleitet werden: zuvor war es '*Type*'.|
|[Compilerfehler C3488](compiler-error-c3488.md)|"&*Identifier*" ist nicht zulässig, wenn der Standard Erfassungs Modus ein nach Verweis ist.|
|[Compilerfehler C3489](compiler-error-c3489.md)|"&*Identifier*" ist erforderlich, wenn der Standard Erfassungs Modus nach Kopie ist.|
|[Compilerfehler C3490](compiler-error-c3490.md)|"*Bezeichner*" kann nicht geändert werden, da über ein konstantenobjekt darauf zugegriffen wird.|
|[Compilerfehler C3491](compiler-error-c3491.md)|"*Bezeichner*": eine nach Kopier Erfassung kann in einem nicht änderbaren Lambda nicht geändert werden.|
|[Compilerfehler C3492](compiler-error-c3492.md)|"*Bezeichner*": ein Member einer anonymen Union kann nicht erfasst werden.|
|[Compilerfehler C3493](compiler-error-c3493.md)|'*Identifier*' kann nicht implizit erfasst werden, da kein Standard Erfassungs Modus angegeben wurde.|
|Compilerfehler C3494|"This" kann nicht explizit erfasst werden, da es von einem einschließenden Erfassungs Modus nicht zugelassen wird.|
|[Compilerfehler C3495](compiler-error-c3495.md)|"*Bezeichner*": der Bezeichner bei der Erfassung muss eine Variable mit automatischer Speicherdauer sein, die im Gültigkeitsbereich des Lambda-Ausdrucks deklariert ist.|
|[Compilerfehler C3496](compiler-error-c3496.md)|"this" wird immer nach Wert erfasst: "&" wird ignoriert.|
|Compilerfehler C3497|Sie können keine Instanz eines Lambda-Ausdrucks erstellen.|
|[Compilerfehler C3498](compiler-error-c3498.md)|"*Bezeichner*": Sie können keine Variable erfassen, die über einen verwalteten/WinRT-Typ verfügt.|
|[Compilerfehler C3499](compiler-error-c3499.md)|Ein Lambda, für das ein Void-Rückgabetyp angegeben wurde, kann keinen Wert zurückgeben.|

## <a name="see-also"></a>Weitere Informationen

[Fehler undC++ Warnungen für C/Compiler und Buildtools](../compiler-errors-1/c-cpp-build-errors.md) \
[Compilerfehler C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
