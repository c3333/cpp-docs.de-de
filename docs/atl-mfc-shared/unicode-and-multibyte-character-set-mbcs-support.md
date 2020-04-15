---
title: Unterstützung für Unicode- und Multibyte-Zeichensätze (MBCS)
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317439"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unterstützung für Unicode- und Multibyte-Zeichensätze (MBCS)

Einige Sprachen wie Japanisch und Chinesisch haben große Zeichensätze. Um die Programmierung für diese Märkte zu unterstützen, ermöglicht die Microsoft Foundation-Klassenbibliothek (MFC) zwei verschiedene Ansätze für die Handhabung großer Zeichensätze:

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` , basierende Breitzeichen und Zeichenfolgen, die als UTF-16 kodiert sind.

- [Multibyte-Zeichensätze (MBCS),](#mfc-support-for-mbcs-strings) **zeichenbasierte** Einzel- oder Doppelbyte-Zeichen und Zeichenfolgen, die in einem gebietsschemaspezifischen Zeichensatz codiert sind.

Microsoft hat die MFC-Unicode-Bibliotheken für alle Neuentwicklungen empfohlen, und die MBCS-Bibliotheken waren in Visual Studio 2013 und Visual Studio 2015 veraltet. Das ist nicht mehr der Fall. Die MBCS-Veraltungswarnungen wurden in Visual Studio 2017 entfernt.

## <a name="mfc-support-for-unicode-strings"></a>MFC-Unterstützung für Unicode-Zeichenfolgen

Die gesamte MFC-Klassenbibliothek ist bedingt für Unicode-Zeichen und Zeichenfolgen aktiviert, die in breiten Zeichen als UTF-16 gespeichert sind. Insbesondere die Klasse [CString](../atl-mfc-shared/reference/cstringt-class.md) ist Unicode-fähig.

Diese Bibliotheks-, Debugger- und DLL-Dateien werden verwendet, um Unicode in MFC zu unterstützen:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|*MFC-Version*U.LIB|*MFC-Version*U.PDB|*MFC-Version*U.DLL|*MFC-Version*UD. Lib|
|*MFC-Version*UD. Pdb|*MFC-Version*UD. Dll|MFCS*version*U.LIB|*MFCS-Version*U.PDB|
|*MFCS-Version*UD. Lib|*MFCS-Version*UD. Pdb|*MFCM-Version*U.LIB|*MFCM-Version*U.PDB|
|*MFCM-Version*U.DLL|*MFCM-Version*UD. Lib|*MFCM-Version*UD. Pdb|*MFCM-Version*UD. Dll|

(*Version* stellt die Versionsnummer der Datei dar; z. B. "140" bedeutet Version 14.0.)

`CString`basiert auf dem TCHAR-Datentyp. Wenn das Symbol _UNICODE für einen Build Ihres Programms definiert `wchar_t`ist, wird TCHAR als Typ definiert, ein 16-Bit-Zeichencodierungstyp. Andernfalls wird TCHAR als **char**definiert, die normale 8-Bit-Zeichencodierung. Daher setzt sich ein `CString` unter Unicode aus 16-Bit-Zeichen zusammen. Ohne Unicode besteht es aus Zeichen vom Typ **char**.

Um Unicode-Programmierung der Anwendung durchzuführen, benötigen Sie auch Folgendes:

- Verwenden Sie das _T Makro, um Literalzeichenfolgen bedingt zu codieren, um in Unicode portierbar zu sein.

- Wenn Sie Zeichenfolgen übergeben, achten Sie darauf, ob für Funktionsargumente eine bestimmte Länge in Zeichen oder in Bytes erforderlich. Der Unterschied ist wichtig, wenn Sie Unicode-Zeichenfolgen verwenden.

- Verwenden Sie portable Versionen der C-Funktionen zur Behandlung von Zeichenfolgen zur Laufzeit.

- Verwenden Sie die folgenden Datentypen für Zeichen und Zeichenzeiger:

  - Verwenden Sie TCHAR dort, wo Sie **char**verwenden würden.

  - Verwenden Sie LPTSTR, wo Sie **char**<strong>\*</strong>verwenden würden.

  - Verwenden Sie LPCTSTR, wo Sie **const char**<strong>\*</strong>verwenden würden. `CString`stellt den Operator LPCTSTR `CString` zum Konvertieren zwischen und LPCTSTR bereit.

`CString` stellt außerdem Unicode-kompatible Konstruktoren, Zuweisungsoperatoren und Vergleichsoperatoren bereit.

Die [Laufzeitbibliotheksreferenz](../c-runtime-library/c-run-time-library-reference.md) definiert portable Versionen aller Zeichenfolgenbehandlungsfunktionen. Weitere Informationen finden Sie in der Kategorie [Internationalisierung](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>MFC-Unterstützung für MBCS-Zeichenfolgen

Die Klassenbibliothek wird auch für Multibyte-Zeichensätze, jedoch nur für Doppelbyte-Zeichensätze (DBCS) aktiviert.

In einem Multibyte-Zeichensatz kann ein Zeichen ein oder zwei Bytes breit sein. Wenn es zwei Bytes breit ist, ist sein erstes Byte ein spezielles "führendes Byte", das je nach verwendeter Codepage aus einem bestimmten Bereich ausgewählt wird. Zusammen angewendet, geben die führenden und die "nachfolgenden Bytes" eine eindeutige Zeichencodierung an.

Wenn das Symbol _MBCS für einen Build Ihres Programms definiert `CString` ist, geben Sie TCHAR, auf dem basiert, **char**zu. Sie bestimmen, welche Bytes in einer `CString` führende Bytes und welche nachfolgende Bytes sind. Die Zubehörfunktionen der C-Laufzeitbibliothek unterstützen Sie dabei.

Unter DBCS kann eine angegebene Zeichenfolge alle Einzelbyte-ANSI-Zeichen, alle Doppelbytezeichen oder eine Kombination der beiden enthalten. Diese Methoden erfordern besondere Sorgfalt beim Parsen von Zeichenfolgen. Hierzu gehören `CString`-Objekte.

> [!NOTE]
> Mit der Serialisierung von Unicode-Zeichenfolgen in MFC können sowohl Unicode als auch MBCS-Zeichenfolgen unabhängig von der Version der Anwendung, die Sie ausführen, gelesen werden. Die Datendateien sind zwischen Unicode- und MBCS-Versionen des Programms übertragbar.

`CString`-Memberfunktionen verwenden spezielle Versionen der C-Laufzeitfunktionen mit "generischem Text", die aufgerufen werden, oder sie verwenden Unicode-kompatible Funktionen. Wenn daher eine `CString`-Funktion normalerweise `strcmp` aufrufen würde, ruft sie stattdessen die entsprechende Funktion `_tcscmp` für generischen Text auf. Je nachdem, wie die Symbole `_tcscmp` _MBCS und _UNICODE definiert sind, werden folgende Karten:

|||
|-|-|
|_MBCS definiert|`_mbscmp`|
|_UNICODE definiert|`wcscmp`|
|Kein Symbol definiert|`strcmp`|

> [!NOTE]
> Die Symbole _MBCS und _UNICODE schließen sich gegenseitig aus.

Generic-Text-Funktionszuordnungen für alle Laufzeitzeichenfolgenbehandlungsroutinen werden in [C Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md)erläutert. Eine Liste finden Sie unter [Internationalisierung](../c-runtime-library/internationalization.md).

In `CString` ähnlicher Weise werden Methoden mithilfe generischer Datentypzuordnungen implementiert. Um MBCS und Unicode zu aktivieren, verwendet `wchar_t`MFC TCHAR für **char** oder , LPTSTR für **char** <strong>\*</strong> oder `wchar_t*`, und LPCTSTR für **const char** <strong>\*</strong> oder `const wchar_t*`. Diese stellen die richtigen Zuordnungen für Unicode oder MBCS sicher.

## <a name="see-also"></a>Siehe auch

[Zeichenfolgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[String-Manipulation](../c-runtime-library/string-manipulation-crt.md)
