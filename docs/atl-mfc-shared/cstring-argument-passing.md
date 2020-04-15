---
title: CString-Argumentenübergabe
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317932"
---
# <a name="cstring-argument-passing"></a>CString-Argumentenübergabe

In diesem Artikel wird erläutert, wie [CString-Objekte](../atl-mfc-shared/reference/cstringt-class.md) an Funktionen übergeben und Objekte aus Funktionen zurückgegeben `CString` werden.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>CString-Argument-Passing-Konventionen

Wenn Sie eine Klassenschnittstelle definieren, müssen Sie die Argumentübergabekonvention für Ihre Memberfunktionen bestimmen. Es gibt einige Standardregeln `CString` für das Übergeben und Zurückgeben von Objekten. Wenn Sie die in Strings beschriebenen Regeln [als Funktionseingaben](#_core_strings_as_function_inputs) und [Zeichenfolgen als Funktionsausgaben](#_core_strings_as_function_outputs)befolgen, haben Sie effizienten, korrekten Code.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>Strings als Funktionseingänge

Die effizienteste und sicherste `CString` Methode zur Verwendung eines `CString` Objekts in aufgerufenen Funktionen besteht darin, ein Objekt an die Funktion zu übergeben. Trotz des Namens `CString` speichert ein Objekt eine Zeichenfolge intern nicht als Zeichenfolge im C-Stil, die über einen Nullabschluss verfügt. Stattdessen verfolgt `CString` ein Objekt sorgfältig die Anzahl der Zeichen, die es hat. Die `CString` Bereitstellung eines LPCTSTR-Zeigers auf eine null-terminierte Zeichenfolge ist eine kleine Menge an Arbeit, die erheblich werden kann, wenn Ihr Code dies ständig tun muss. Das Ergebnis ist temporär, da jede Änderung am `CString` Inhalt alte Kopien des LPCTSTR-Zeigers ungültig macht.

In einigen Fällen ist es sinnvoll, eine Zeichenfolge im C-Stil bereitzustellen. Es kann z. B. eine Situation geben, in der eine aufgerufene Funktion in C geschrieben wird und keine Objekte unterstützt. In diesem Fall wird `CString` der Parameter zu LPCTSTR genötigt, und die Funktion erhält eine Null-Termin-Zeichenfolge im C-Stil. Sie können auch in die `CString` andere Richtung `CString` gehen und ein Objekt erstellen, indem Sie den Konstruktor verwenden, der einen Zeichenfolgenparameter im C-Stil akzeptiert.

Wenn der Zeichenfolgeninhalt durch eine Funktion geändert werden soll, deklarieren Sie den Parameter als nicht konstanten `CString` Verweis (`CString&`).

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>Zeichenfolgen als Funktionsausgänge

In der `CString` Regel können `CString` Sie Objekte aus Funktionen zurückgeben, da Objekte Wertsemantik wie primitive Typen folgen. Um eine schreibgeschützte Zeichenfolge zurückzugeben, `CString` verwenden`const CString&`Sie einen konstanten Verweis ( ). Das folgende Beispiel veranschaulicht `CString` die Verwendung von Parametern und Rückgabetypen:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Siehe auch

[Zeichenfolgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
