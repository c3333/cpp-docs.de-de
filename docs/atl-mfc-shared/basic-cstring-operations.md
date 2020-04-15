---
title: Grundlegende CString-Vorgänge
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317963"
---
# <a name="basic-cstring-operations"></a>Grundlegende CString-Vorgänge

In diesem Thema werden die folgenden grundlegenden [CString-Vorgänge](../atl-mfc-shared/reference/cstringt-class.md) erläutert:

- [Erstellen von CString-Objekten aus Standard-C-Literalzeichenfolgen](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Zugriff auf einzelne Zeichen in einem CString](#_core_accessing_individual_characters_in_a_cstring)

- [Verketten von zwei CString-Objekten](#_core_concatenating_two_cstring_objects)

- [Vergleichen von CString-Objekten](#_core_comparing_cstring_objects)

- [Konvertieren von CString-Objekten](#_core_converting_cstring_objects)

`Class CString`basiert auf der Klassenvorlage [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md). `CString`ist ein **typedef** von `CStringT`. Genauer `CString` gesagt, ist ein **typedef** einer *expliziten Spezialisierung* von `CStringT`, die eine übliche Möglichkeit ist, eine Klassenvorlage zu verwenden, um eine Klasse zu definieren. Ähnlich definierte `CStringA` Klassen `CStringW`sind und .

`CString`, `CStringA`und `CStringW` sind in atlstr.h definiert. `CStringT`ist in cstringt.h definiert.

`CString`, `CStringA`und `CStringW` jeder erhält einen Satz der `CStringT` Methoden und Operatoren, die für die Verwendung mit den von ihnen unterstützten Zeichenfolgendaten definiert sind. Einige der Methoden duplizieren und übertreffen in einigen Fällen die Zeichenfolgendienste der C-Laufzeitbibliotheken.

Hinweis: `CString` ist eine native Klasse. Verwenden Sie `System.String`für eine Zeichenfolgenklasse, die für die Verwendung in einem von C++/CLI verwalteten Projekt verwendet wird.

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Erstellen von CString-Objekten aus Standard-C-Literalzeichenfolgen

Sie können einem ebenso wie `CString` einem `CString` anderen Objekt ein Objekt zuweisen.

- Weisen Sie einem `CString` Objekt den Wert einer C-Literalzeichenfolge zu.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Weisen Sie den `CString` Wert `CString` eines Objekts einem anderen Objekt zu.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Der Inhalt `CString` eines Objekts `CString` wird kopiert, wenn ein Objekt einem anderen Objekt zugewiesen wird. Daher haben die beiden Zeichenfolgen keinen Verweis auf die tatsächlichen Zeichen, aus denen die Zeichenfolge besteht. Weitere Informationen zur Verwendung `CString` von Objekten als Werte finden Sie unter [CString Semantics](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Um Ihre Anwendung so zu schreiben, dass sie für Unicode oder ANSI kompiliert werden kann, codieren Sie Literalzeichenfolgen mithilfe des _T-Makros. Weitere Informationen finden Sie unter [Unicode- und Multibyte-Zeichensatz-Unterstützung (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Zugreifen auf einzelne Zeichen in einem CString

Sie können auf einzelne `CString` Zeichen in `GetAt` `SetAt` einem Objekt zugreifen, indem Sie die und Methoden verwenden. Sie können auch das Arrayelement oder den Subskriptoperator `GetAt` ( [ ] ) verwenden, anstatt einzelne Zeichen abzurufen. (Dies ähnelt dem Zugriff auf Arrayelemente nach Index, wie in Standardzeichenfolgen im C-Stil.) Indexwerte `CString` für Zeichen sind nullbasiert.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Verketten von zwei CString-Objekten

Um zwei `CString` Objekte zu verketten, verwenden Sie die Verkettungsoperatoren (+ oder +=) wie folgt.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Mindestens ein Argument für die Verkettungsoperatoren (+ `CString` oder +=) muss ein Objekt sein, aber Sie können eine konstante Zeichenfolge (z. B. `"big"`) oder ein **Zeichen** (z. B. 'x') für das andere Argument verwenden.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Vergleichen von CString-Objekten

Die `Compare` Methode und der `CString` == Operator für sind äquivalent. `Compare`, **Operator==** `CompareNoCase` , und sind MBCS und Unicode-bekannt; `CompareNoCase` wird auch die Groß-/Kleinschreibung nicht berücksichtigt. Die `Collate` Methode `CString` von ist gebietsschemaempfindlich und `Compare`ist oft langsamer als . Verwenden `Collate` Sie diese nur dort, wo Sie sich an die Sortierregeln halten müssen, die vom aktuellen Gebietsschema angegeben sind.

Die folgende Tabelle [CString](../atl-mfc-shared/reference/cstringt-class.md) zeigt die verfügbaren CString-Vergleichsfunktionen und ihre entsprechenden Unicode/MBCS-portablen Funktionen in der C-Laufzeitbibliothek.

|CString-Funktion|MBCS-Funktion|Unicode-Funktion|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

Die `CStringT` Klassenvorlage definiert die relationalen \<Operatoren (<, =, >=, >, `CString`==und !=), die für die Verwendung durch verfügbar sind. Sie können `CStrings` zwei vergleichen, indem Sie diese Operatoren verwenden, wie im folgenden Beispiel gezeigt.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Konvertieren von CString-Objekten

Informationen zum Konvertieren von CString-Objekten in andere Zeichenfolgentypen finden Sie unter [Gewusst wie: Konvertieren zwischen verschiedenen Zeichenfolgentypen](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Verwenden von CString mit wcout

Um einen CString `wcout` mit zu verwenden, `const wchar_t*` müssen Sie das Objekt explizit in ein umsetzen, wie im folgenden Beispiel gezeigt:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Ohne die `cs` Umwandlung wird `void*` als `wcout` a behandelt und die Adresse des Objekts gedruckt. Dieses Verhalten wird durch subtile Interaktionen zwischen Vorlagenargumentabzug und Überlastauflösung verursacht, die an sich korrekt und mit dem C++-Standard übereinstimmen.

## <a name="see-also"></a>Siehe auch

[Zeichenfolgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Vorlagenspezialisierung](../cpp/template-specialization-cpp.md)<br/>
[Gewusst wie: Konvertieren zwischen verschiedenen Zeichenfolgentypen](../text/how-to-convert-between-various-string-types.md)
