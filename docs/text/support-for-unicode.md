---
title: Unterstützung für Unicode
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: 90c07874b61656a8bec0f9ef373f2ee8f339e994
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215373"
---
# <a name="support-for-unicode"></a>Unterstützung für Unicode

Unicode ist eine Spezifikation für die Unterstützung aller Zeichensätze, einschließlich derjenigen, die nicht in einem einzelnen Byte dargestellt werden können.  Wenn Sie für einen internationalen Markt programmieren, empfiehlt es sich, entweder Unicode oder einen [Multibytezeichen-Zeichensatz](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS) zu verwenden. Oder programmieren Sie Ihr Programm, damit Sie es für erstellen können, indem Sie einen Switch ändern.

Ein Breitzeichen ist ein mehrsprachiger 2-Byte-Zeichencode. Zehntausende von Zeichen, die fast alle in modernen Computing weltweit verwendeten Zeichen umfassen, einschließlich technischer Symbole und spezieller Veröffentlichungs Zeichen, können gemäß der Unicode-Spezifikation als einzelnes breit Zeichen dargestellt werden, das mithilfe von UTF-16 codiert wurde. Zeichen, die nicht in nur einem breit Zeichen dargestellt werden können, können mithilfe der Unicode-Ersatz Zeichenpaar Funktion in einem Unicode-Paar dargestellt werden. Da fast jedes verwendete Zeichen in UTF-16 in einem einzelnen 16-Bit-breit Zeichen dargestellt wird, vereinfacht die Verwendung von breit Zeichen das Programmieren mit internationalen Zeichensätzen. Mithilfe von UTF-16LE (für Little-Endian) codierte breit Zeichen sind das Native Zeichenformat für Windows.

Eine Breitzeichenzeichenfolge wird als `wchar_t[]`-Array dargestellt, auf das mit einem `wchar_t*`-Zeiger gezeigt wird. Jedes ASCII-Zeichen kann als Breitzeichen dargestellt werden, indem der Buchstabe L dem Zeichen vorangestellt wird. L'\0' ist beispielsweise das abschließende (16-Bit) NULL-Breitzeichen. Auf ähnliche Weise kann jedes ASCII-Zeichenfolgenliteral als Breitzeichen-Zeichenfolgenliteral dargestellt werden, indem der Buchstabe L dem ASCII-Literal vorangestellt wird (L"Hello").

Im Allgemeinen benötigen Breitzeichen mehr Platz im Arbeitsspeicher als Multibytezeichen, werden aber schneller verarbeitet. Außerdem kann jeweils nur ein Gebiets Schema in einer multibytecodierung dargestellt werden, während alle Zeichensätze der Welt gleichzeitig von der Unicode-Darstellung dargestellt werden.

Das MFC-Framework ist komplett Unicode-fähig, und MFC erreicht die Unicode-Fähigkeit durch die Verwendung von portablen Makros, die in der folgenden Tabelle gezeigt sind.

## <a name="portable-data-types-in-mfc"></a>Portable Datentypen in MFC

|Nicht portable Datendatentypen|Ersetzt durch dieses Makro|
|-----------------------------|----------------------------|
|**`char`**, **`wchar_t`**|`_TCHAR`|
|**`char*`**, `LPSTR` (Win32-Datentyp),`LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Win32-Datentyp),`LPCWSTR`|`LPCTSTR`|

`CString`Die Klasse verwendet `_TCHAR` als Basis und stellt Konstruktoren und Operatoren für einfache Konvertierungen bereit. Die meisten Zeichenfolgenvorgänge für Unicode können durch dieselbe Logik geschrieben werden, die für die Verarbeitung des Windows-ANSI-Zeichensatzes verwendet wird, mit der Ausnahme, dass die grundlegende Einheit für Vorgänge ein 16-Bit-Zeichen anstelle eines 8-Bit-Zeichens ist. Im Gegensatz zur Arbeit mit Multibytezeichensätzen müssen (und sollten) Sie ein Unicode-Zeichen nicht behandeln, als bestünde es aus zwei unterschiedlichen Bytes. Sie müssen jedoch die Möglichkeit eines einzelnen Zeichens behandeln, das durch ein Ersatz Zeichenpaar von breit Zeichen dargestellt wird. Schreiben Sie im Allgemeinen keinen Code, der annimmt, dass die Länge einer Zeichenfolge mit der Anzahl der Zeichen übereinstimmt, die in der Zeichenfolge enthalten sind.

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [MFC-Unicode-und Multibyte-Zeichensatz Unterstützung (MBCS) verwenden](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Aktivieren von Unicode im Programm](../text/international-enabling.md)

- [Sowohl Unicode als auch MBCS im Programm aktivieren](../text/internationalization-strategies.md)

- [Verwenden von Unicode zum Erstellen eines internationalen Programms](../text/unicode-programming-summary.md)

- [Weitere Informationen zu den Vorteilen von Unicode](../text/benefits-of-character-set-portability.md)

- [Verwenden von wmain zum Übergeben von Breitzeichenargumenten an ein Programm](../text/support-for-using-wmain.md)

- [Anzeigen einer Zusammenfassung zur Unicode-Programmierung](../text/unicode-programming-summary.md)

- [Etwas über die Zuordnungen generischer Texte bei Byte-breiter Portabilität erfahren](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Weitere Informationen

[Text und Zeichen folgen](../text/text-and-strings-in-visual-cpp.md)<br/>
[Unterstützung für die Verwendung von wmain](../text/support-for-using-wmain.md)
