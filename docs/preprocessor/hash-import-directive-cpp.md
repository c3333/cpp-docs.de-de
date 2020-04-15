---
title: '##import-Anweisung (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332067"
---
# <a name="import-directive-c"></a>#import -Direktive (C++)

**C++-spezifisch**

Wird verwendet, um Informationen aus einer Typbibliothek zu integrieren. Der Inhalt der Typbibliothek wird in C++-Klassen konvertiert, die größtenteils die COM-Schnittstellen beschreiben.

## <a name="syntax"></a>Syntax

> **#import** "*Dateiname*" \[ *Attribute*]"
> > \[*Dateiname-Attribute* **#import** \< *filename*]

### <a name="parameters"></a>Parameter

*Dateiname*\
Gibt die zu importierende Typbibliothek an. Der *Dateiname* kann eine der folgenden Arten sein:

- Der Name einer Datei, die eine Typbibliothek enthält, z. B. eine OLB-, TLB- oder DLL-Datei. Das Schlüsselwort `file:`, kann jedem Dateinamen vorantreten.

- Die ProgID eines Steuerelements in der Typbibliothek. Das Schlüsselwort `progid:`, kann jedem progid vorantreten. Beispiel:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Weitere Informationen zu progids finden Sie unter [Angeben der Lokalisierungs-ID und versionsnummer](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Wenn Sie einen 32-Bit-Kreuzcompiler auf einem 64-Bit-Betriebssystem verwenden, kann der Compiler nur die 32-Bit-Registrierungsstruktur lesen. Sie sollten den systemeigenen 64-Bit-Compiler verwenden, um eine 64-Bit-Typbibliothek zu erstellen und zu registrieren.

- Die Bibliotheks-ID der Typbibliothek. Das Schlüsselwort `libid:`, kann jeder Bibliotheks-ID vorantreten. Beispiel:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Wenn Sie die `version` angewendeten `lcid` `progid:` [Regeln](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) nicht angeben oder `libid:`angeben, werden sie auch auf angewendet.

- Ein ausführbare Datei (EXE-Datei).

- Eine Bibliotheksdatei (.dll), die eine Typbibliotheksressource (z. B. eine .ocx) enthält.

- Ein Verbunddokument, das eine Typbibliothek enthält.

- Jedes andere Dateiformat, das von der **LoadTypeLib-API** verstanden werden kann.

*Attribute*\
Ein oder mehrere [#import Attribute](#_predir_the_23import_directive_import_attributes). Trennen Sie Attribute entweder mit einem Komma oder einem Leerzeichen. Beispiel:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- oder -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Bemerkungen

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>Suchreihenfolge nach Dateinamen

*Dateiname* wird optional eine Verzeichnisspezifikation vorangestellt. Der Dateiname muss eine vorhandene Datei benennen. Der Unterschied zwischen den beiden Syntaxformen liegt in der Reihenfolge, in der der Präprozessor nach den Typbibliotheksdateien sucht, wenn der Pfad unvollständig angegeben wird.

|Syntaxformat|Aktion|
|-----------------|------------|
|Format mit Anführungszeichen|Weist den Präprozessor an, zuerst im Verzeichnis der Datei, die die **#import-Anweisung** enthält, und dann`#include`in den Verzeichnissen der Dateien, die diese Datei enthalten, nach Typbibliotheksdateien zu suchen. Der Präprozessor sucht dann in den unten aufgeführten Verzeichnissen.|
|Format mit spitzer Klammer|Weist den Präprozessor an, nach Typbibliotheksdateien in den folgenden Verzeichnissen zu suchen:<br /><br /> 1. `PATH` Die Pfadliste der Umgebungsvariablen<br />2. `LIB` Die Pfadliste der Umgebungsvariablen<br />3. Der pfad, der von der [/I-Compileroption](../build/reference/i-additional-include-directories.md) angegeben wird, mit der Ausnahme, dass der Compiler nach einer Typbibliothek sucht, auf die von einer anderen Typbibliothek mit dem [Attribut no_registry](../preprocessor/no-registry.md) verwiesen wurde.|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Angeben der Lokalisierungs-ID und Versionsnummer

Wenn Sie eine ProgID angeben, können Sie auch die Lokalisierungs-ID und die Versionsnummer der ProgID angeben. Beispiel:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Wenn Sie keine Lokalisierungs-ID angeben, wird ein Progid nach den folgenden Regeln ausgewählt:

- Wenn es nur eine Lokalisierungs-ID gibt, wird diese verwendet.

- Wenn mehr als eine Lokalisierungs-ID vorhanden ist, wird die erste mit der Versionsnummer 0, 9 oder 409 verwendet.

- Wenn mehr als eine Lokalisierungs-ID vorhanden ist und keine von ihnen 0, 9 oder 409 ist, wird die letzte verwendet.

- Wenn Sie keine Versionsnummer angeben, wird die neueste Version verwendet.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>Headerdateien, die durch Import erstellt werden

**#import** erstellt zwei Headerdateien, die den Inhalt der Typbibliothek im C++-Quellcode rekonstruieren. Die primäre Headerdatei ähnelt der, die vom MIDL-Compiler (Microsoft Interface Definition Language) erstellt wurde, jedoch mit zusätzlichem vom Compiler generiertem Code und Daten. Die [primäre Headerdatei](#_predir_the_primary_type_library_header_file) hat denselben Basisnamen wie die Typbibliothek sowie eine . TLH-Erweiterung. Die sekundäre Headerdatei weist den gleichen Basisnamen wie die Typbibliothek auf, mit einer TLI-Erweiterung. Sie enthält die Implementierungen für vom Compiler generierte Memberfunktionen und wird in die primäre Headerdatei eingefügt (`#include`).

Beim Importieren einer dispinterface-Eigenschaft, die Parameter verwendet, `byref` generiert **#import** keine [__declspec(Eigenschaft)-Anweisung](../cpp/property-cpp.md) für die Funktion.

Beide Headerdateien werden in dem Ausgabeverzeichnis platziert, das durch die Option [/Fo (Name-Objektdatei)](../build/reference/fo-object-file-name.md) angegeben wird. Sie werden dann vom Compiler gelesen und kompiliert, als `#include` ob die primäre Headerdatei von einer Direktive benannt wurde.

Die folgenden Compileroptimierungen **#import** werden mit der #import-Direktive bereitgestellt:

- Wenn sie erstellt wird, wird der Headerdatei der gleiche Zeitstempel gegeben wie der Typbibliothek.

- Wenn **#import** verarbeitet wird, überprüft der Compiler zuerst, ob der Header vorhanden ist und ist aktuell. Wenn ja, dann muss es nicht neu erstellt werden.

Die **#import** #import-Direktive beteiligt sich ebenfalls an einem minimalen Neuaufbau und kann in einer vorkompilierten Headerdatei platziert werden.  Weitere Informationen finden Sie unter [Erstellen vorkompilierter Headerdateien](../build/creating-precompiled-header-files.md).

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>Primäre Typbibliotheksheaderdatei

Die primäre Headerdatei der Typbibliothek umfasst sieben Abschnitte:

- Textbaustein für Überschrift: Besteht aus Kommentaren, der `#include`-Anweisung für COMDEF.H (das mehrere Standardmakros definiert, die im Header verwendet werden) und weiteren verschiedenen Setupinformationen.

- Vorwärtsverweise und Typdefinitionen: Bestehen aus Strukturdeklarationen wie `struct IMyInterface` und Typdefinitionen.

- Intelligente Zeigerdeklarationen: `_com_ptr_t` Die Vorlagenklasse ist ein intelligenter Zeiger. Es kapselt Schnittstellenzeiger und eliminiert die Notwendigkeit, , `AddRef` `Release`, `QueryInterface` und Funktionen aufzurufen. Außerdem wird der `CoCreateInstance` Aufruf beim Erstellen eines neuen COM-Objekts ausgeblendet. In diesem Abschnitt `_COM_SMARTPTR_TYPEDEF` wird die Makroanweisung verwendet, um typedefs von COM-Schnittstellen als Vorlagenspezialisierungen der [_com_ptr_t-Vorlagenklasse](../cpp/com-ptr-t-class.md) einzurichten. Zum Beispiel für `IMyInterface`Schnittstelle , die . TLH-Datei enthält:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   Dies wird vom Compiler zu Folgendem erweitert:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` kann dann anstelle des nicht formatierten Schnittstellenzeigers `IMyInterface*` verwendet werden. Daher müssen die verschiedenen `IUnknown` Memberfunktionen nicht

- Typinfo-Deklarationen: Besteht in erster Linie aus Klassendefinitionen `ITypeLib:GetTypeInfo`und anderen Elementen, die die einzelnen typinfo-Elemente freisetzen, die von zurückgegeben werden. In diesem Abschnitt wird jede Typinformation aus der Typbibliothek im Header in einem Format wiedergegeben, das von den `TYPEKIND`-Informationen abhängt.

- Definition der optionalen GUID im alten Format: Enthält Initialisierungen der benannten GUID-Konstanten. Diese Namen haben `CLSID_CoClass` `IID_Interface`die Form und , ähnlich denen, die vom MIDL-Compiler generiert werden.

- `#include`-Anweisung für den sekundären Header der Typbibliothek.

- Textbaustein für Footer: Schließt aktuell `#pragma pack(pop)` ein.

Alle Abschnitte, mit Ausnahme des Abschnitts "Überschrift Boilerplate" und "Footer Boilerplate", sind in einen Namespace mit seinem Namen eingeschlossen, der durch die `library` Anweisung in der ursprünglichen IDL-Datei angegeben ist. Sie können die Namen aus dem Typbibliotheksheader durch eine explizite Qualifizierung mithilfe des Namespacenamens verwenden. Sie können auch die folgende Anweisung einschließen:

```cpp
using namespace MyLib;
```

unmittelbar nach der **#import-Anweisung** im Quellcode.

Der Namespace kann mithilfe des [Attributs no_namespace](no-namespace.md)) der **#import-Direktive** unterdrückt werden. Allerdings kann das Unterdrücken des Namespace zu Namenskonflikten führen. Der Namespace kann auch durch das [Attribut rename_namespace](rename-namespace.md) umbenannt werden.

Der Compiler stellt den vollständigen Pfad zu jeder Typbibliotheksabhängigkeit bereit, die für die Derzeit verarbeitete Typbibliothek erforderlich ist. Der Pfad wird in Form von Kommentaren in den Header der Typbibliothek (.TLH) geschrieben, den der Compiler für jede verarbeitete Typbibliothek erstellt.

Wenn eine Typbibliothek Verweise auf Typen enthält, die in anderen Typbibliotheken definiert sind, dann enthält die TLH-Datei Kommentare folgender Art:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Der tatsächliche Dateiname im **#import** Kommentar ist der vollständige Pfad der referenzierten Typbibliothek, wie er in der Registrierung gespeichert ist. Wenn Fehler auftreten, die durch fehlende Typdefinitionen verursacht werden, überprüfen Sie die Kommentare an der Spitze des . TLH, um zu sehen, welche abhängigen Typbibliotheken möglicherweise zuerst importiert werden müssen. Wahrscheinliche Fehler sind Syntaxfehler (z. B. C2143, C2146, C2321), C2501 (fehlende decl-Spezifizierer) oder C2433 ("inline" bei Datendeklaration nicht zulässig) beim Kompilieren der TLI-Datei.

Um Abhängigkeitsfehler zu beheben, bestimmen Sie, welche der Abhängigkeitskommentare sonst nicht von Systemheadern bereitgestellt werden, und stellen Sie dann irgendwann vor der **#import** Direktive der abhängigen Typbibliothek eine **#import-Direktive** bereit.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import-Attribute

**#import** können optional ein oder mehrere Attribute enthalten. Diese Attribute weisen den Compiler an, den Inhalt der Typbibliotheksheader zu ändern. Ein umgekehrter**\\**Schrägstrich ( ) kann verwendet werden, um zusätzliche Zeilen in eine einzelne **#import-Anweisung** einzuschließen. Beispiel:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Weitere Informationen finden Sie [unter #import Attribute](../preprocessor/hash-import-attributes-cpp.md).

**Ende C++-spezifisch**

## <a name="see-also"></a>Siehe auch

[Präprozessordirektiven](../preprocessor/preprocessor-directives.md)\
[Compiler-COM-Unterstützung](../cpp/compiler-com-support.md)
