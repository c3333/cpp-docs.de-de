---
title: Verwenden von VERIFY anstelle ASSERT
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: bfc0847677ae232fef67ab6200c626472f042bdb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438609"
---
# <a name="using-verify-instead-of-assert"></a>Verwenden von VERIFY anstelle ASSERT

Angenommen, beim Ausführen der Debugversion Ihrer MFC-Anwendung sind keine Probleme aufgetreten. Die Releaseversion derselben Anwendung stürzt jedoch ab, gibt falsche Ergebnisse zurück und/oder weist ein anderes anormales Verhalten auf.

Dieses Problem kann verursacht werden, wenn Sie wichtigen Code in einer ASSERT-Anweisung platzieren, um zu überprüfen, ob er ordnungsgemäß ausgeführt wird. Da ASSERT-Anweisungen in einem Releasebuild eines MFC-Programms auskommentiert werden, wird der Code in einem Releasebuild nicht ausgeführt.

Wenn Sie ASSERT verwenden, um zu bestätigen, dass ein Funktionsaufruf erfolgreich war, sollten Sie stattdessen [VERIFY](../mfc/reference/diagnostic-services.md#verify) verwenden. Das VERIFY-Makro wertet seine eigenen Argumente sowohl in Debug- als auch in Releasebuilds der Anwendung aus.

Eine weitere bevorzugte Methode besteht darin, den Rückgabewert der Funktion einer temporären Variablen zuzuweisen und dann die Variable in einer ASSERT-Anweisung zu testen.

Sehen Sie sich das folgende Codefragment an:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Dieser Code wird in einer Debugversion einer MFC-Anwendung problemlos ausgeführt. Wenn der `calloc( )`-Aufruf fehlschlägt, wird eine Diagnosemeldung angezeigt, die die Datei und die Zeilennummer enthält. In einem Einzelhandelsbuild einer MFC-Anwendung passiert jedoch Folgendes:

- Der `calloc( )`-Aufruf findet nie statt, sodass `buf` nicht initialisiert wird, oder

- `strcpy_s( )` kopiert "`Hello, World`" in einen zufälligen Speicherbereich, was möglicherweise die Anwendung abstürzen lässt oder bewirkt, dass das System nicht mehr reagiert, oder

- `free()` versucht, Arbeitsspeicher freizugeben, der nie zugeordnet wurde.

Um ASSERT ordnungsgemäß zu verwenden, sollte das Codebeispiel wie folgt geändert werden:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Oder Sie können stattdessen VERIFY verwenden:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Siehe auch

[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
