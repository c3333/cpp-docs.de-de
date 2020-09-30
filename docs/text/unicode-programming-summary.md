---
title: Zusammenfassung der Unicode-Programmierung
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 5095e1c58db3e5c35eb9215367f2fbb064bc228a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504701"
---
# <a name="unicode-programming-summary"></a>Zusammenfassung der Unicode-Programmierung

Wenn Sie von MFC- und C-Laufzeitunterstützung für Unicode profitieren möchten, müssen Sie folgende Schritte ausführen:

- Definieren Sie `_UNICODE` .

   Definieren Sie das Symbol, `_UNICODE` bevor Sie das Programm erstellen.

- Geben Sie den Einstiegspunkt an.

   Legen Sie **auf der Seite** **erweitert** des linkerordners im Dialogfeld [Eigenschaften Seiten](../build/reference/property-pages-visual-cpp.md) des Projekts das Symbol für den **Einstiegspunkt** auf fest `wWinMainCRTStartup` .

- Verwenden Sie portable Laufzeitfunktionen und Typen.

   Verwenden Sie für die Behandlung von Unicode-Zeichenfolgen die richtigen C-Laufzeitfunktionen. Sie können die- `wcs` Funktions Familie verwenden, aber Sie bevorzugen möglicherweise die vollständig portablen (International aktivierten) `_TCHAR` Makros. Diese Makros verfügen alle über das Präfix `_tcs` . Sie ersetzen, eines für die `str` Funktions Familie. Diese Funktionen werden im Abschnitt [Internationalisierung](../c-runtime-library/internationalization.md) der *Lauf Zeit Bibliotheks Referenz*ausführlich beschrieben. Weitere Informationen finden Sie unter Zuordnungen für [generischen Text in Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

   Verwenden Sie `_TCHAR` und die zugehörigen portablen Datentypen, die [unter Unterstützung für Unicode](../text/support-for-unicode.md)beschrieben werden.

- Bearbeiten Sie Zeichenfolgenliterale vorschriftsmäßig.

   Vom Visual C++-Compiler wird ein Zeichenfolgenliteral der Form

    ```cpp
    L"this is a literal string"
    ```

   als Unicode-Zeichenfolge interpretiert. Sie können dasselbe Präfix für Literalzeichen verwenden. Verwenden Sie das- `_T` Makro, um Literalzeichenfolgen generisch zu codieren, sodass Sie als Unicode-Zeichen folgen unter Unicode oder als ANSI-Zeichen folgen (einschließlich MBCS) ohne Unicode Verwenden Sie anstelle von

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   sondern:

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   Wenn `_UNICODE` definiert ist, `_T` übersetzt die Literalzeichenfolge in das l-Präfix-Formular; andernfalls `_T` übersetzt die Zeichenfolge ohne das l-Präfix.

    > [!TIP]
    >  Das- `_T` Makro ist identisch mit dem- `_TEXT` Makro.

- Gehen Sie beim Übergeben von Zeichenfolgenlängen an Funktionen mit Bedacht vor.

   Bei einigen Funktionen muss die Anzahl der Zeichen in einer Zeichenfolge angegeben werden, bei anderen Funktionen die Anzahl der Bytes. Wenn z. b. `_UNICODE` definiert ist, funktioniert der folgende- `CArchive` Objekt Vorgang nicht ( `str` ist ein `CString` ):

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   In einer Unicode-Anwendung gibt die Länge die Zeichenanzahl, aber nicht die richtige Byte-Anzahl an, da jedes Zeichen zwei Bytes breit ist. Sie müssen also den obigen Funktionsaufruf wie folgt ändern:

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   Dieser Aufruf gibt fehlerfrei an, wie viele Bytes geschrieben werden sollen.

   Zeichenorientierte MFC-Memberfunktionen arbeiten jedoch im Gegensatz zu Byte-orientierten Memberfunktionen ohne diese zusätzliche Codierung:

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   Für `CDC::TextOut` ist eine Anzahl von Zeichen, nicht eine Anzahl von Bytes erforderlich.

- Verwenden Sie [fopen_s _wfopen_s,](../c-runtime-library/reference/fopen-s-wfopen-s.md) um Unicode-Dateien zu öffnen.

Zusammenfassend bietet MFC und die Lauf Zeit Bibliothek die folgende Unterstützung für die Unicode-Programmierung:

- Mit Ausnahme der Memberfunktionen für Datenbankklassen sind alle MFC-Funktionen, einschließlich `CString`. `CString` stellt darüber hinaus Unicode/ANSI-Konvertierungsfunktionen bereit.

- Die Laufzeitbibliothek stellt Unicode-Versionen aller Funktionen zur Behandlung von Zeichenfolgen zur Verfügung. (Die Laufzeitbibliothek enthält mit den _tcs-Makros auch portable, für Unicode Dies sind die `_tcs` Makros.)

- Tchar. h liefert portable Datentypen und das `_T` Makro zum Übersetzen von Literalzeichenfolgen und Zeichen. Weitere Informationen finden Sie unter Zuordnungen für [generischen Text in Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

- Die Lauf Zeit Bibliothek stellt eine breit Zeichen Version von bereit `main` . Verwenden Sie `wmain` , um die Anwendung Unicode-kompatibel zu machen.

## <a name="see-also"></a>Weitere Informationen

[Unterstützung für Unicode](../text/support-for-unicode.md)
