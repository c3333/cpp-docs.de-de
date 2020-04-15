---
title: Linkertoolfehler LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353241"
---
# <a name="linker-tools-error-lnk2005"></a>Linkertoolfehler LNK2005

> *Symbol,* das bereits im Objekt definiert ist

Das *Symbolsymbol* wurde mehr als einmal definiert.

Auf diesen Fehler folgt der schwerwiegende Fehler [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Mögliche Ursachen und Lösungen

Im Allgemeinen bedeutet dieser Fehler, dass Sie die *eine Definitionsregel*gebrochen haben, die nur eine Definition für jede verwendete Vorlage, Funktion, einen Typ oder ein Objekt in einer bestimmten Objektdatei und nur eine Definition in der gesamten ausführbaren Datei für extern sichtbare Objekte oder Funktionen zulässt.

Hier sind einige häufige Ursachen für diesen Fehler.

- Dieser Fehler kann auftreten, wenn eine Headerdatei eine Variable definiert. Wenn Sie diese Headerdatei beispielsweise in mehr als eine Quelldatei in Ihr Projekt einschließen, führt dies zu einem Fehler:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Folgende Lösungen sind möglich:

  - Deklarieren `extern` Sie die `extern int global_int;`Variable in der Headerdatei: , definieren Sie sie `int global_int = 17;`dann und initialisieren Sie sie optional in einer und nur einer Quelldatei: . Diese Variable ist jetzt eine globale Variable, die Sie `extern`in jeder Quelldatei verwenden können, indem Sie sie deklarieren, z. B. durch Einschließen der Headerdatei. Wir empfehlen diese Lösung für Variablen, die global sein müssen, aber eine gute Software-Engineering-Praxis minimiert globale Variablen.

  - Deklarieren [static](../../cpp/storage-classes-cpp.md#static)Sie `static int static_int = 17;`die Variable static : . Dadurch wird der Bereich der Definition auf die aktuelle Objektdatei beschränkt und es mehreren Objektdateien ermöglicht, eine eigene Kopie der Variablen zu erhalten. Es wird nicht empfohlen, statische Variablen in Headerdateien zu definieren, da dies zu Verwechslungen mit globalen Variablen führen kann. Ziehen Sie es vor, statische Variablendefinitionen in die Quelldateien zu verschieben, die sie verwenden.

  - Deklarieren Sie `__declspec(selectany) int global_int = 17;`die Variable [selectany](../../cpp/selectany.md): . Dadurch wird der Linker aufgefordert, eine Definition für die Verwendung durch alle externen Verweise auszuwählen und den Rest zu verwerfen. Diese Lösung ist manchmal nützlich, wenn Importbibliotheken kombiniert werden. Andernfalls empfehlen wir es nicht, um Linkerfehler zu vermeiden.

- Dieser Fehler kann auftreten, wenn eine Headerdatei eine `inline`Funktion definiert, die nicht ist. Wenn Sie diese Headerdatei in mehr als eine Quelldatei einschließen, erhalten Sie mehrere Definitionen der Funktion in der ausführbaren Datei.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Folgende Lösungen sind möglich:

  - Fügen `inline` Sie das Schlüsselwort zur Funktion hinzu:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Entfernen Sie den Funktionstext aus der Headerdatei, und lassen Sie nur die Deklaration, und implementieren Sie die Funktion dann in einer und nur einer Quelldatei:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Dieser Fehler kann auch auftreten, wenn Sie Memberfunktionen außerhalb der Klassendeklaration in einer Headerdatei definieren:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Um dieses Problem zu beheben, verschieben Sie die Memberfunktionsdefinitionen innerhalb der Klasse. Memberfunktionen, die in einer Klassendeklaration definiert sind, werden implizit eingefüttert.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Dieser Fehler kann auftreten, wenn Sie mehr als eine Version der Standardbibliothek oder CRT verknüpfen. Wenn Sie beispielsweise versuchen, sowohl die Retail- als auch die Debug-CRT-Bibliotheken oder sowohl die statischen als auch die dynamischen Versionen einer Bibliothek oder zwei verschiedene Versionen einer Standardbibliothek mit Ihrer ausführbaren Datei zu verknüpfen, kann dieser Fehler häufig gemeldet werden. Um dieses Problem zu beheben, entfernen Sie alle bis auf eine Kopie jeder Bibliothek aus dem Linkbefehl. Es wird nicht empfohlen, Einzelhandels- und Debugbibliotheken oder verschiedene Versionen einer Bibliothek in derselben ausführbaren Datei zu mischen.

   Um den Linker anzuweisen, andere Bibliotheken als die Standardeinstellungen zu verwenden, geben Sie in der Befehlszeile die zu verwendenden Bibliotheken an, und verwenden Sie die Option [/NODEFAULTLIB,](../../build/reference/nodefaultlib-ignore-libraries.md) um die Standardbibliotheken zu deaktivieren. Fügen Sie in der IDE Verweise auf Ihr Projekt hinzu, um die zu verwendenden Bibliotheken anzugeben, und öffnen Sie dann das Dialogfeld **Eigenschaftenseiten** für Ihr Projekt, und legen Sie in der Eigenschaftenseite **Linker**, **Eingabe** entweder **Alle Standardbibliotheken**ignorieren oder **bestimmte Standardbibliotheken** ignorieren fest, um die Standardbibliotheken zu deaktivieren.

- Dieser Fehler kann auftreten, wenn Sie die Verwendung statischer und dynamischer Bibliotheken mischen, wenn Sie die Option [/clr](../../build/reference/clr-common-language-runtime-compilation.md) verwenden. Dieser Fehler kann z. B. auftreten, wenn Sie eine DLL für die Verwendung in Ihrer ausführbaren Datei erstellen, die in der statischen CRT verknüpft ist. Um dieses Problem zu beheben, verwenden Sie nur statische Bibliotheken oder nur dynamische Bibliotheken für die gesamte ausführbare Datei und für alle Bibliotheken, die Sie für die Verwendung in der ausführbaren Datei erstellen.

- Dieser Fehler kann auftreten, wenn es sich bei dem Symbol um eine verpackte Funktion handelt (erstellt durch Kompilieren mit [/Gy](../../build/reference/gy-enable-function-level-linking.md)) und es in mehr als einer Datei enthalten war, aber zwischen Kompilierungen geändert wurde. Um dieses Problem zu beheben, kompilieren Sie alle Dateien neu, die die paketierte Funktion enthalten.

- Dieser Fehler kann auftreten, wenn das Symbol in zwei Elementobjekten in verschiedenen Bibliotheken unterschiedlich definiert ist und beide Memberobjekte verwendet werden. Eine Möglichkeit, dieses Problem zu beheben, wenn die Bibliotheken statisch verknüpft sind, besteht darin, das Memberobjekt nur aus einer Bibliothek zu verwenden und diese Bibliothek zuerst in die Linker-Befehlszeile einzuschließen. Um beide Symbole zu verwenden, müssen Sie eine Möglichkeit erstellen, sie zu unterscheiden. Wenn Sie beispielsweise die Bibliotheken aus der Quelle erstellen können, können Sie jede Bibliothek in einem eindeutigen Namespace umschließen. Alternativ können Sie eine neue Wrapperbibliothek erstellen, die eindeutige Namen verwendet, um Verweise auf eine der ursprünglichen Bibliotheken zu umschließen, die neue Bibliothek mit der ursprünglichen Bibliothek zu verknüpfen und dann die ausführbare Datei mit der neuen Bibliothek anstelle der ursprünglichen Bibliothek zu verknüpfen.

- Dieser Fehler kann `extern const` auftreten, wenn eine Variable zweimal definiert wird und in jeder Definition einen anderen Wert aufweist. Um dieses Problem zu beheben, definieren Sie die `enum class` Konstante nur einmal, oder verwenden Sie Namespaces oder Definitionen, um die Konstanten zu unterscheiden.

- Dieser Fehler kann auftreten, wenn Sie uuid.lib in Kombination mit anderen .lib-Dateien verwenden, die GUIDs definieren (z. B. oledb.lib und adsiid.lib). Beispiel:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Um dieses Problem zu beheben, fügen Sie [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) zu den Linker-Befehlszeilenoptionen hinzu, und stellen Sie sicher, dass uuid.lib die erste Bibliothek ist, auf die verwiesen wird.
