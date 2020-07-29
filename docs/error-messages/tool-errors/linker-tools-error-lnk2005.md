---
title: Linkertoolfehler LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 278f05b8338ac4238d6862fd7b9bd7744f6c8ee5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225214"
---
# <a name="linker-tools-error-lnk2005"></a>Linkertoolfehler LNK2005

> Das *Symbol* ist bereits im Objekt definiert.

Das Symbol *Symbol* wurde mehrmals definiert.

Auf diesen Fehler folgt ein schwerwiegender Fehler [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Mögliche Ursachen und Lösungen

Im Allgemeinen bedeutet dieser Fehler, dass Sie die *eine Definitions Regel*beschädigt haben, die nur eine Definition für beliebige Vorlagen, Funktionen, Typen oder Objekte in einer bestimmten Objektdatei und nur eine Definition für die gesamte ausführbare Datei für extern sichtbare Objekte oder Funktionen zulässt.

Im folgenden finden Sie einige häufige Gründe für diesen Fehler.

- Dieser Fehler kann auftreten, wenn eine Header Datei eine Variable definiert. Wenn Sie diese Header Datei z. b. in mehr als eine Quelldatei in Ihrem Projekt einschließen, wird ein Fehler ausgegeben:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Folgende Lösungen sind möglich:

  - Deklarieren Sie die Variable **`extern`** in der Header Datei: `extern int global_int;` , definieren Sie Sie, und initialisieren Sie Sie optional nur in einer einzigen Quelldatei: `int global_int = 17;` . Diese Variable ist jetzt ein globaler, das Sie in jeder beliebigen Quelldatei verwenden können, indem Sie sie deklariert **`extern`** , z. b. durch einschließen der Header Datei. Wir empfehlen diese Lösung für Variablen, die Global sein müssen, aber eine gute Software Entwicklungs Übung minimiert globale Variablen.

  - Deklarieren Sie die Variable [static](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;` . Dadurch wird der Gültigkeitsbereich der Definition auf die aktuelle Objektdatei beschränkt, und mehrere Objektdateien können über eine eigene Kopie der Variablen verfügen. Es wird nicht empfohlen, statische Variablen in Header Dateien zu definieren, da es möglicherweise Verwirrung mit globalen Variablen gibt. Ziehen Sie es vor, statische Variablen Definitionen in die Quelldateien zu verschieben, die Sie verwenden.

  - Deklarieren Sie die Variable [Selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;` . Dadurch wird der Linker aufgefordert, eine Definition zur Verwendung durch alle externen Verweise auszuwählen und den Rest zu verwerfen. Diese Lösung ist manchmal nützlich, wenn Import Bibliotheken kombiniert werden. Andernfalls empfiehlt es sich nicht, Linkerfehler zu vermeiden.

- Dieser Fehler kann auftreten, wenn eine Header Datei eine Funktion definiert, die nicht ist **`inline`** . Wenn Sie diese Header Datei in mehr als eine Quelldatei einschließen, erhalten Sie mehrere Definitionen der Funktion in der ausführbaren Datei.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Folgende Lösungen sind möglich:

  - Fügen Sie das- **`inline`** Schlüsselwort der-Funktion hinzu:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Entfernen Sie den Funktions Text aus der Header Datei, und lassen Sie nur die-Deklaration zu, und implementieren Sie dann die-Funktion nur in einer einzigen Quelldatei:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Dieser Fehler kann auch auftreten, wenn Sie Element Funktionen außerhalb der Klassen Deklaration in einer Header Datei definieren:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Um dieses Problem zu beheben, verschieben Sie die Member-Funktionsdefinitionen in die-Klasse. Member-Funktionen, die innerhalb einer Klassen Deklaration definiert sind, sind implizit Inline.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Dieser Fehler kann auftreten, wenn Sie mehr als eine Version der Standardbibliothek oder CRT verknüpfen. Wenn Sie z. b. versuchen, sowohl die Retail-als auch die Debug-CRT-Bibliotheken oder sowohl die statische als auch die dynamische Version einer Bibliothek oder zwei verschiedene Versionen einer Standardbibliothek mit Ihrer ausführbaren Datei zu verknüpfen, wird dieser Fehler möglicherweise mehrmals gemeldet. Um dieses Problem zu beheben, entfernen Sie alle Kopien der einzelnen Bibliotheken aus dem Link-Befehl. Es wird nicht empfohlen, Einzelhandels-und Debugbibliotheken oder andere Versionen einer Bibliothek in derselben ausführbaren Datei zu mischen.

   Um dem Linker mitzuteilen, dass andere Bibliotheken als die Standardwerte verwendet werden sollen, geben Sie in der Befehlszeile die zu verwendenden Bibliotheken an, und verwenden Sie die Option [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) , um die Standardbibliotheken zu deaktivieren. Fügen Sie in der IDE Verweise auf das Projekt hinzu, um die zu verwendenden Bibliotheken anzugeben, öffnen Sie dann das Dialogfeld Eigenschaften **Seiten** für das Projekt, und legen Sie auf der Seite **Linker**, **Eingabe** Eigenschaft entweder **alle Standardbibliotheken ignorieren**fest, oder **bestimmte Standard Bibliotheks Eigenschaften ignorieren** , um die Standardbibliotheken zu deaktivieren.

- Dieser Fehler kann auftreten, wenn Sie die Verwendung statischer und dynamischer Bibliotheken bei Verwendung der [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Option mischen. Dieser Fehler kann z. b. auftreten, wenn Sie eine DLL für die Verwendung in der ausführbaren Datei erstellen, die mit der statischen CRT verknüpft ist. Um dieses Problem zu beheben, verwenden Sie nur statische Bibliotheken oder nur dynamische Bibliotheken für die gesamte ausführbare Datei und für alle Bibliotheken, die Sie für die Verwendung in der ausführbaren Datei erstellen.

- Dieser Fehler kann auftreten, wenn das Symbol eine Paket Funktion ist (erstellt durch Kompilieren mit [/Gy](../../build/reference/gy-enable-function-level-linking.md)) und in mehr als einer Datei enthalten war, jedoch zwischen Kompilierungen geändert wurde. Um dieses Problem zu beheben, kompilieren Sie alle Dateien neu, die die gepackte Funktion enthalten.

- Dieser Fehler kann auftreten, wenn das Symbol in zwei Element Objekten in verschiedenen Bibliotheken anders definiert ist und beide Member-Objekte verwendet werden. Eine Möglichkeit, dieses Problem zu beheben, wenn die Bibliotheken statisch verknüpft sind, besteht darin, das Member-Objekt nur aus einer Bibliothek zu verwenden und diese Bibliothek zuerst in der Linkerbefehlszeile einzuschließen. Um beide Symbole verwenden zu können, müssen Sie eine Möglichkeit zum unterscheiden der Symbole erstellen. Wenn Sie z. b. die Bibliotheken aus der Quelle erstellen können, können Sie jede Bibliothek in einem eindeutigen Namespace einschließen. Alternativ können Sie eine neue Wrapper Bibliothek erstellen, die eindeutige Namen verwendet, um Verweise auf eine der ursprünglichen Bibliotheken zu umschließen, die neue Bibliothek mit der ursprünglichen Bibliothek zu verknüpfen und dann die ausführbare Datei mit der neuen Bibliothek anstatt mit der ursprünglichen Bibliothek zu verknüpfen.

- Dieser Fehler kann auftreten, wenn eine `extern const` Variable zweimal definiert wird und in jeder Definition ein anderer Wert vorhanden ist. Um dieses Problem zu beheben, definieren Sie die Konstante nur einmal, oder verwenden Sie Namespaces oder **`enum class`** Definitionen, um die Konstanten zu unterscheiden.

- Dieser Fehler kann auftreten, wenn UUID. lib in Kombination mit anderen lib-Dateien verwendet wird, die GUIDs definieren (z. b. "OleDb. lib" und "adsiid. lib"). Beispiel:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Um dieses Problem zu beheben, fügen Sie den linkerbefehlszeilenoptionen [/Force: Multiple](../../build/reference/force-force-file-output.md) hinzu, und stellen Sie sicher, dass uuid. lib die erste Bibliothek ist, auf die verwiesen wird
