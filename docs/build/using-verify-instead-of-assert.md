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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438609"
---
# <a name="using-verify-instead-of-assert"></a>Verwenden von VERIFY anstelle ASSERT

Angenommen, beim Ausführen der Debugversion Ihrer MFC-Anwendung sind keine Probleme aufgetreten. Die Releaseversion der gleichen Anwendung stürzt jedoch ab, gibt falsche Ergebnisse zurück und/oder weist ein anderes anormales Verhalten auf.

Dieses Problem kann verursacht werden, wenn Sie wichtigen Code in einer Assert-Anweisung platzieren, um sicherzustellen, dass er ordnungsgemäß ausgeführt wird. Da Assert-Anweisungen in einem Releasebuild eines MFC-Programms auskommentiert werden, wird der Code nicht in einem Releasebuild ausgeführt.

Wenn Sie Assert verwenden, um zu bestätigen, dass ein Funktions aufruferfolg erfolgreich war, sollten Sie stattdessen die [Überprüfung](../mfc/reference/diagnostic-services.md#verify) verwenden Das VERIFY-Makro wertet seine eigenen Argumente sowohl in Debug-als auch in Releasebuilds der Anwendung aus.

Eine weitere bevorzugte Methode besteht darin, den Rückgabewert der Funktion einer temporären Variablen zuzuweisen und dann die Variable in einer Assert-Anweisung zu testen.

Überprüfen Sie das folgende Code Fragment:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Dieser Code wird perfekt in einer Debugversion einer MFC-Anwendung ausgeführt. Wenn der `calloc( )`-Aufrufe fehlschlägt, wird eine Diagnose Meldung angezeigt, die die Datei und die Zeilennummer enthält. Allerdings in einem Einzelhandels Build einer MFC-Anwendung:

- der `calloc( )`-Aufrufe findet nie statt, `buf` nicht initialisiert, oder

- `strcpy_s( )` kopiert "`Hello, World`" in ein zufälliges Speicher Element, das möglicherweise die Anwendung abstürzt oder bewirkt, dass das System nicht mehr reagiert, oder

- `free()` versucht, Arbeitsspeicher freizugeben, der nie zugeordnet wurde.

Um Assert ordnungsgemäß zu verwenden, sollte das Codebeispiel wie folgt geändert werden:

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

Oder Sie können stattdessen überprüfen verwenden:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Weitere Informationen

[Beheben von Problemen mit dem Releasebuild](fixing-release-build-problems.md)
