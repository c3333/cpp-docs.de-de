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
ms.openlocfilehash: 0b61407920a0ce35a1c6a8466458736e983e271e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168563"
---
# <a name="support-for-unicode"></a>Unterstützung für Unicode

Unicode ist eine Spezifikation für die Unterstützung aller Zeichensätze, einschließlich derjenigen, die nicht in einem einzelnen Byte dargestellt werden können.  Wenn Sie für einen internationalen Markt programmieren, empfiehlt es sich, entweder Unicode oder einen [Multibytezeichen-Zeichensatz](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS) zu verwenden. Oder programmieren Sie Ihr Programm, damit Sie es für erstellen können, indem Sie einen Switch ändern.

Ein Breitzeichen ist ein mehrsprachiger 2-Byte-Zeichencode. Zehntausende von Zeichen, die fast alle in modernen Computing weltweit verwendeten Zeichen, einschließlich technischer Symbole und spezieller Veröffentlichungs Zeichen, umfassen, können gemäß der Unicode-Spezifikation als einzelnes breit Zeichen dargestellt werden, das von Verwenden von UTF-16. Zeichen, die nicht in nur einem breit Zeichen dargestellt werden können, können mithilfe der Unicode-Ersatz Zeichenpaar Funktion in einem Unicode-Paar dargestellt werden. Da fast jedes verwendete Zeichen in UTF-16 in einem einzelnen 16-Bit-breit Zeichen dargestellt wird, vereinfacht die Verwendung von breit Zeichen das Programmieren mit internationalen Zeichensätzen. Mithilfe von UTF-16LE (für Little-Endian) codierte breit Zeichen sind das Native Zeichenformat für Windows.

Eine Breitzeichenzeichenfolge wird als `wchar_t[]`-Array dargestellt, auf das mit einem `wchar_t*`-Zeiger gezeigt wird. Jedes ASCII-Zeichen kann als Breitzeichen dargestellt werden, indem der Buchstabe L dem Zeichen vorangestellt wird. L'\0' ist beispielsweise das abschließende (16-Bit) NULL-Breitzeichen. Auf ähnliche Weise kann jedes ASCII-Zeichenfolgenliteral als Breitzeichen-Zeichenfolgenliteral dargestellt werden, indem der Buchstabe L dem ASCII-Literal vorangestellt wird (L"Hello").

Im Allgemeinen benötigen Breitzeichen mehr Platz im Arbeitsspeicher als Multibytezeichen, werden aber schneller verarbeitet. Außerdem kann jeweils nur ein Gebiets Schema in einer multibytecodierung dargestellt werden, während alle Zeichensätze der Welt gleichzeitig von der Unicode-Darstellung dargestellt werden.

Das MFC-Framework ist komplett Unicode-fähig, und MFC erreicht die Unicode-Fähigkeit durch die Verwendung von portablen Makros, die in der folgenden Tabelle gezeigt sind.

## <a name="portable-data-types-in-mfc"></a>Portable Datentypen in MFC

|Nicht portable Datendatentypen|Ersetzt durch dieses Makro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*``LPSTR` (Win32-Datentyp), `LPWSTR`|`LPTSTR`|
|`const char*``LPCSTR` (Win32-Datentyp), `LPCWSTR`|`LPCTSTR`|

Class `CString` verwendet `_TCHAR` als Basis und stellt Konstruktoren und Operatoren für einfache Konvertierungen bereit. Die meisten Zeichenfolgenvorgänge für Unicode können durch dieselbe Logik geschrieben werden, die für die Verarbeitung des Windows-ANSI-Zeichensatzes verwendet wird, mit der Ausnahme, dass die grundlegende Einheit für Vorgänge ein 16-Bit-Zeichen anstelle eines 8-Bit-Zeichens ist. Im Gegensatz zur Arbeit mit Multibytezeichensätzen müssen (und sollten) Sie ein Unicode-Zeichen nicht behandeln, als bestünde es aus zwei unterschiedlichen Bytes. Sie müssen jedoch die Möglichkeit eines einzelnen Zeichens behandeln, das durch ein Ersatz Zeichenpaar von breit Zeichen dargestellt wird. Schreiben Sie im Allgemeinen keinen Code, der annimmt, dass die Länge einer Zeichenfolge mit der Anzahl der Zeichen übereinstimmt, die in der Zeichenfolge enthalten sind.

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [MFC-Unicode-und Multibyte-Zeichensatz Unterstützung (MBCS) verwenden](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Unicode in meinem Programm aktivieren](../text/international-enabling.md)

- [Aktivieren von Unicode und MBCS im Programm](../text/internationalization-strategies.md)

- [Verwenden von Unicode zum Erstellen eines internationalisierten Programms](../text/unicode-programming-summary.md)

- [Weitere Informationen zu den Vorteilen von Unicode](../text/benefits-of-character-set-portability.md)

- [Verwenden Sie wmain, damit ich breit Zeichen Argumente an mein Programm übergeben kann.](../text/support-for-using-wmain.md)

- [Siehe eine Zusammenfassung der Unicode-Programmierung.](../text/unicode-programming-summary.md)

- [Weitere Informationen zu generischen Text Zuordnungen für die Übertragbarkeit von Byte Breite](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Weitere Informationen

[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)<br/>
[Unterstützung für die Verwendung von wmain](../text/support-for-using-wmain.md)
