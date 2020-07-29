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
ms.openlocfilehash: fa46e82f19d87c49f652779d0e86e78549935965
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220898"
---
# <a name="basic-cstring-operations"></a>Grundlegende CString-Vorgänge

In diesem Thema werden die folgenden grundlegenden [CString](../atl-mfc-shared/reference/cstringt-class.md) -Vorgänge erläutert:

- [Erstellen von CString-Objekten aus C-Standard Zeichenfolgen](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Zugreifen auf einzelne Zeichen in einer CString](#_core_accessing_individual_characters_in_a_cstring)

- [Verketten von zwei CString-Objekten](#_core_concatenating_two_cstring_objects)

- [Vergleichen von CString-Objekten](#_core_comparing_cstring_objects)

- [CString-Objekte werden umgerechnet](#_core_converting_cstring_objects)

`Class CString`basiert auf der Klassen Vorlage [CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md). `CString`ist ein **`typedef`** von `CStringT` . Genauer ist, `CString` ist eine einer **`typedef`** *expliziten Spezialisierung* von `CStringT` . Dies ist eine gängige Methode, eine Klassen Vorlage zum Definieren einer Klasse zu verwenden. Auf ähnliche Weise definierte Klassen sind `CStringA` und `CStringW` .

`CString`, `CStringA` und `CStringW` sind in "atlstr. h" definiert. `CStringT`wird in CStringT. h definiert.

`CString`, `CStringA` und `CStringW` erhalten jeweils eine Reihe von Methoden und Operatoren, die von `CStringT` für die Verwendung mit den von Ihnen unterstützten Zeichen folgen Daten definiert werden. Einige der Methoden sind doppelt vorhanden und überschreiten in einigen Fällen die Zeichen folgen Dienste der C-Laufzeitbibliotheken.

Hinweis: `CString` ist eine native Klasse. Verwenden Sie für eine Zeichen folgen Klasse, die zur Verwendung in einem C++/CLI Managed-Projekt verwendet werden soll `System.String` .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Erstellen von CString-Objekten aus C-Standard Zeichenfolgen

Sie können eine Literalzeichenfolge im C-Stil zu einem zuweisen, `CString` wie Sie ein Objekt einem anderen zuweisen können `CString` .

- Weisen Sie den Wert einer C-Literalzeichenfolge einem- `CString` Objekt zu.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Weisen Sie den Wert eines `CString` anderen `CString` Objekts zu.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Der Inhalt eines- `CString` Objekts wird kopiert, wenn ein- `CString` Objekt einem anderen zugewiesen wird. Daher haben die beiden Zeichen folgen keinen Verweis auf die eigentlichen Zeichen, die die Zeichenfolge bilden. Weitere Informationen zur Verwendung von `CString` Objekten als Werte finden Sie unter [CString-Semantik](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Wenn Sie Ihre Anwendung so schreiben möchten, dass Sie für Unicode oder ANSI kompiliert werden kann, codieren Sie Literale Zeichen folgen mithilfe des _T-Makros. Weitere Informationen finden Sie [unter Unterstützung für Unicode-und Multibyte-Zeichensätze (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Zugreifen auf einzelne Zeichen in einer CString

`CString`Mithilfe der `GetAt` -Methode und der-Methode können Sie auf einzelne Zeichen in einem-Objekt zugreifen `SetAt` . Sie können auch das Array-Element oder den Index Operator ([]) anstelle von verwenden, `GetAt` um einzelne Zeichen zu erhalten. (Dies ähnelt dem Zugriff auf Array Elemente nach Index, wie in standardmäßigen Zeichen folgen im C-Stil.) Index Werte für `CString` Zeichen sind NULL basiert.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Verketten von zwei CString-Objekten

Verwenden Sie zum Verketten von zwei `CString` Objekten die Verkettungs Operatoren (+ oder + =) wie folgt.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Mindestens ein Argument für die Verkettungs Operatoren (+ oder + =) muss ein- `CString` Objekt sein, Sie können jedoch eine Konstante Zeichenfolge (z. b. `"big"` ) oder eine-Zeichenfolge (z. b **`char`** . "x") für das andere Argument verwenden.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Vergleichen von CString-Objekten

Die `Compare` -Methode und der = =-Operator für `CString` sind gleichwertig. `Compare`, **Operator = =** und `CompareNoCase` sind MBCS und Unicode-fähig; `CompareNoCase` bei wird auch die Groß-/Kleinschreibung nicht beachtet. Die `Collate` -Methode von ist Gebiets Schema `CString` sensibel und häufig langsamer als `Compare` . Verwenden `Collate` Sie nur, wenn Sie die Sortierungsregeln wie im aktuellen Gebiets Schema angegeben einhalten müssen.

Die folgende Tabelle zeigt die verfügbaren [CString](../atl-mfc-shared/reference/cstringt-class.md) -Vergleichsfunktionen und ihre entsprechenden Unicode/MBCS-portablen Funktionen in der C-Lauf Zeit Bibliothek.

|CString-Funktion|MBCS-Funktion|Unicode-Funktion|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

Die `CStringT` Klassen Vorlage definiert die relationalen Operatoren (<, \<=, > =, >, = = und! =), die für die Verwendung durch verfügbar sind `CString` . Sie können zwei vergleichen `CStrings` , indem Sie diese Operatoren verwenden, wie im folgenden Beispiel gezeigt.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>CString-Objekte werden umgerechnet

Weitere Informationen zum Konvertieren von CString-Objekten in andere Zeichen folgen Typen finden Sie unter Gewusst [wie: Konvertieren zwischen verschiedenen Zeichen folgen Typen](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Verwenden von CString mit wcout

Um eine CString mit zu verwenden, `wcout` müssen Sie das-Objekt explizit in einen umwandeln, `const wchar_t*` wie im folgenden Beispiel gezeigt:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Ohne die Umwandlung `cs` wird als behandelt **`void*`** und `wcout` druckt die Adresse des Objekts. Dieses Verhalten wird durch feine Interaktionen zwischen Vorlagen Argument Ableitung und Überladungs Auflösung verursacht, die selbst korrekt und mit dem C++-standardkonform sind.

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Vorlagen Spezialisierung](../cpp/template-specialization-cpp.md)<br/>
[Gewusst wie: Konvertieren zwischen verschiedenen Zeichen folgen Typen](../text/how-to-convert-between-various-string-types.md)
