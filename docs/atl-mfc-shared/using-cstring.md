---
title: Verwenden von CString
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: 8ebf3441c7d8856fe412e2efed4c717b01ced362
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219013"
---
# <a name="using-cstring"></a>Verwenden von CString

In den Themen in diesem Abschnitt wird die Programmierung mit `CString` beschrieben. Eine Referenz Dokumentation zur- `CString` Klasse finden Sie in der Dokumentation zu [CStringT](../atl-mfc-shared/reference/cstringt-class.md).

Schließen Sie zum Verwenden von `CString` den `atlstr.h`-Header ein.

Die `CString` `CStringA` Klassen, und `CStringW` sind Spezialisierungs einer Klassen Vorlage namens [CStringT](../atl-mfc-shared/reference/cstringt-class.md) basierend auf dem Typ der Zeichendaten, die Sie unterstützen.

Ein `CStringW` -Objekt enthält den **`wchar_t`** -Typ und unterstützt Unicode-Zeichen folgen. Ein `CStringA` -Objekt enthält den **`char`** -Typ und unterstützt Einzel Byte-und Multibyte-Zeichen folgen (MBCS). Ein- `CString` Objekt unterstützt entweder den- **`char`** Typ oder den- **`wchar_t`** Typ, je nachdem, ob das MBCS-Symbol oder das Unicode-Symbol zur Kompilierzeit definiert ist.

Ein `CString`-Objekt hält Zeichendaten in einem `CStringData`-Objekt. `CString`akzeptiert NULL-terminierte Zeichen folgen im C-Stil. `CString`verfolgt die Zeichen folgen Länge für eine schnellere Leistung, behält aber auch das NULL-Zeichen in den gespeicherten Zeichendaten bei, um die Konvertierung in LPCWSTR zu unterstützen. `CString`schließt das NULL-Terminator beim Exportieren einer Zeichenfolge im C-Format ein. Sie können einen NULL-Wert an anderen Positionen in einem einfügen `CString` , dies kann jedoch zu unerwarteten Ergebnissen führen.

Die folgenden Zeichen folgen Klassen können ohne Verknüpfung einer MFC-Bibliothek mit oder ohne CRT-Unterstützung verwendet werden: `CAtlString` , `CAtlStringA` und `CAtlStringW` .

`CString`wird in systemeigenen Projekten verwendet. Verwenden Sie für Projekte mit verwaltetem Code (C++/CLI) `System::String`.

Um mehr Funktionen hinzuzufügen als `CString`, `CStringA` oder `CStringW` derzeit bieten, sollten Sie eine Unterklasse von `CStringT` erstellen, die die zusätzlichen Funktionen enthält.

Der folgende Code zeigt, wie Sie einen `CString` erstellen und als Standardausgabe drucken können:

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>In diesem Abschnitt

[Grundlegende CString-Vorgänge](../atl-mfc-shared/basic-cstring-operations.md)<br/>
Beschreibt grundlegende `CString`-Vorgänge, darunter das Erstellen von Objekten aus C-Literal-Zeichenfolgen, das Zugreifen auf einzelne Zeichen in einem `CString`, das Verketten von zwei Objekten und das Vergleichen von `CString`-Objekten.

[Zeichen folgen Datenverwaltung](../atl-mfc-shared/string-data-management.md)<br/>
Erläutert die Nutzung von Unicode und MBCS mit `CString`.

[CString-Semantik](../atl-mfc-shared/cstring-semantics.md)<br/>
Erläutert, wie `CString`-Objekte verwendet werden.

[CString-Vorgänge in Bezug auf Zeichen folgen im C-Stil](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
Beschreibt die Manipulation der Inhalte eines `CString`-Objekts wie eine mit Null abschließende Zeichenfolge im C-Format.

[Zuordnen und Freigeben von Arbeitsspeicher für einen BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
Erläutert die Verwendung von Arbeitsspeicher für ein BSTR-und COM-Objekt.

[CString-Ausnahme Bereinigung](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
Erklärt, dass eine explizite Bereinigung in MFC 3.0 und höher nicht mehr notwendig ist.

[CString-Argument Übergabe](../atl-mfc-shared/cstring-argument-passing.md)<br/>
Erläutert, wie Sie CString-Objekte an Funktionen übergeben und wie Sie `CString`-Objekte aus Funktionen zurückgeben können.

[Unterstützung für Unicode-und Multibyte-Zeichensätze (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
Beschreibt, wie MFC für Unicode- und MBCS-Unterstützung aktiviert wird.

## <a name="reference"></a>Verweis

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Bietet Referenzinformationen zur `CStringT`-Klasse.

[CSimpleStringT-Klasse](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
Bietet Referenzinformationen zur `CSimpleStringT`-Klasse.

## <a name="related-sections"></a>Verwandte Abschnitte

[Zeichen folgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
Enthält Links zu Themen, in denen verschiedene Methoden zum Verwalten von Zeichenfolgendaten beschrieben werden.

[Zeichen folgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
