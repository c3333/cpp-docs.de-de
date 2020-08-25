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
ms.openlocfilehash: efa90acd169aeb8739b0bf97a5ab27026cc80cc6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831982"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unterstützung für Unicode- und Multibyte-Zeichensätze (MBCS)

Einige Sprachen wie Japanisch und Chinesisch haben große Zeichensätze. Um die Programmierung für diese Märkte zu unterstützen, ermöglicht die Microsoft Foundation Class-Bibliothek (MFC) zwei unterschiedliche Ansätze für die Handhabung von großen Zeichensätzen:

- [Unicode](#mfc-support-for-unicode-strings), **`wchar_t`** basierende breit Zeichen und Zeichen folgen, die als UTF-16 codiert sind.

- [Multibyte-Zeichensätze (MBCS)](#mfc-support-for-mbcs-strings), **`char`** basierte Einzel-oder Doppelbyte Zeichen und Zeichen folgen, die in einem Gebiets Schema spezifischen Zeichensatz codiert sind.

Microsoft hat die MFC-Unicode-Bibliotheken für alle neuen Entwicklungen empfohlen, und die MBCS-Bibliotheken wurden in Visual Studio 2013 und Visual Studio 2015 als veraltet eingestuft. Dies ist nun nicht mehr der Fall. Die MBCS-veralnungs Warnungen wurden in Visual Studio 2017 entfernt.

## <a name="mfc-support-for-unicode-strings"></a>MFC-Unterstützung für Unicode-Zeichenfolgen

Die gesamte MFC-Klassenbibliothek ist für Unicode-Zeichen und Zeichen folgen, die in breit Zeichen als UTF-16 gespeichert sind, bedingt aktiviert. Insbesondere die Klasse [CString](../atl-mfc-shared/reference/cstringt-class.md) ist Unicode-aktiviert.

Diese Bibliothek-, Debugger-und dll-Dateien werden verwendet, um Unicode in MFC zu unterstützen:

:::row:::
   :::column span="":::
      MFC-*Version*U. lib \
      MFC-*Version*UD. LIB
      MF-*Version*U. lib \
      MF-*Version*UD. LIB
      MF-*Version*U. lib \
      MF-*Version*UD. LIB
      Uafxcw. LIB
      UAFXCWD.LIB
   :::column-end:::
   :::column span="":::
      MFC-*Version*U. pdb \
      MFC-*Version*UD. PDB
      MF-*Version*U. pdb \
      MF-*Version*UD. PDB
      MF-*Version*U. pdb \
      MF-*Version*UD. PDB
      Uafxcw. PDB
      UAFXCWD.PDB
   :::column-end:::
   :::column span="":::
      MFC-*Version*U.DLL \
      MFC-*Version*UD.DLL \
      MF-*Version*U.DLL \
      Mficm-*Version*UD.DLL
   :::column-end:::
:::row-end:::

(*Version* ist die Versionsnummer der Datei, z. b. "140", Version 14,0.)

`CString` basiert auf dem TCHAR-Datentyp. Wenn das Symbol _UNICODE für einen Build des Programms definiert ist, wird TCHAR als Typ **`wchar_t`** , ein 16-Bit-Zeichen Codierungstyp, definiert. Andernfalls ist Tchar definiert als **`char`** , die normale 8-Bit-Zeichencodierung. Daher setzt sich ein `CString` unter Unicode aus 16-Bit-Zeichen zusammen. Ohne Unicode besteht Sie aus Zeichen vom Typ **`char`** .

Um Unicode-Programmierung der Anwendung durchzuführen, benötigen Sie auch Folgendes:

- Verwenden Sie das _T-Makro, um Literalzeichenfolgen bedingt zu codieren, sodass Sie in Unicode

- Wenn Sie Zeichenfolgen übergeben, achten Sie darauf, ob für Funktionsargumente eine bestimmte Länge in Zeichen oder in Bytes erforderlich. Der Unterschied ist wichtig, wenn Sie Unicode-Zeichenfolgen verwenden.

- Verwenden Sie portable Versionen der C-Funktionen zur Behandlung von Zeichenfolgen zur Laufzeit.

- Verwenden Sie die folgenden Datentypen für Zeichen und Zeichenzeiger:

  - Verwenden Sie TCHAR, wo Sie verwenden würden **`char`** .

  - Verwenden Sie LPTSTR, um zu verwenden **`char`** <strong>\*</strong> .

  - Verwenden Sie LPCTSTR, um zu verwenden **`const char`** <strong>\*</strong> . `CString` stellt den LPCTSTR-Operator für die Konvertierung zwischen `CString` und LPCTSTR bereit.

`CString` stellt außerdem Unicode-kompatible Konstruktoren, Zuweisungsoperatoren und Vergleichsoperatoren bereit.

Der [Lauf Zeit Bibliotheks Verweis](../c-runtime-library/c-run-time-library-reference.md) definiert Portable Versionen aller zugehörigen Funktionen zur Verarbeitung von Zeichen folgen. Weitere Informationen finden Sie in der [kategorieinternationalisierungs](../c-runtime-library/internationalization.md)-.

## <a name="mfc-support-for-mbcs-strings"></a>MFC-Unterstützung für MBCS-Zeichenfolgen

Die Klassenbibliothek wird auch für Multibyte-Zeichensätze, jedoch nur für Doppelbyte-Zeichensätze (DBCS) aktiviert.

In einem Multibyte-Zeichensatz kann ein Zeichen ein oder zwei Bytes breit sein. Wenn es zwei Bytes breit ist, ist sein erstes Byte ein spezielles "führendes Byte", das je nach verwendeter Codepage aus einem bestimmten Bereich ausgewählt wird. Zusammen angewendet, geben die führenden und die "nachfolgenden Bytes" eine eindeutige Zeichencodierung an.

Wenn das Symbol _MBCS für einen Build des Programms definiert ist, geben Sie TCHAR, auf dem `CString` basiert, an **`char`** . Sie bestimmen, welche Bytes in einer `CString` führende Bytes und welche nachfolgende Bytes sind. Die Zubehörfunktionen der C-Laufzeitbibliothek unterstützen Sie dabei.

Unter DBCS kann eine angegebene Zeichenfolge alle Einzelbyte-ANSI-Zeichen, alle Doppelbytezeichen oder eine Kombination der beiden enthalten. Diese Methoden erfordern besondere Sorgfalt beim Parsen von Zeichenfolgen. Hierzu gehören `CString`-Objekte.

> [!NOTE]
> Mit der Serialisierung von Unicode-Zeichenfolgen in MFC können sowohl Unicode als auch MBCS-Zeichenfolgen unabhängig von der Version der Anwendung, die Sie ausführen, gelesen werden. Die Datendateien sind zwischen Unicode- und MBCS-Versionen des Programms übertragbar.

`CString`-Memberfunktionen verwenden spezielle Versionen der C-Laufzeitfunktionen mit "generischem Text", die aufgerufen werden, oder sie verwenden Unicode-kompatible Funktionen. Wenn daher eine `CString`-Funktion normalerweise `strcmp` aufrufen würde, ruft sie stattdessen die entsprechende Funktion `_tcscmp` für generischen Text auf. Abhängig davon, wie die Symbole _MBCS und _UNICODE definiert sind, wird `_tcscmp` wie folgt zugeordnet:

|Symbole|Funktion|
|-|-|
|_MBCS definiert|`_mbscmp`|
|_UNICODE definiert|`wcscmp`|
|Kein Symbol definiert|`strcmp`|

> [!NOTE]
> Die Symbole _MBCS und _UNICODE schließen sich gegenseitig aus.

Generische Text Funktions Zuordnungen für alle Routinen zur Laufzeit-Zeichen folgen Verarbeitung werden in der [C-Lauf Zeit Bibliotheks Referenz](../c-runtime-library/c-run-time-library-reference.md)erläutert. Eine Liste finden Sie unter [Internationalisierung](../c-runtime-library/internationalization.md).

Ebenso `CString` werden Methoden mithilfe von generischen Datentyp Zuordnungen implementiert. Zum Aktivieren von MBCS und Unicode verwendet MFC TCHAR für **`char`** oder **`wchar_t`** , LPTSTR für **`char`** <strong>\*</strong> oder `wchar_t*` und LPCTSTR für Konstante **char** <strong>\*</strong> oder `const wchar_t*` . Diese stellen die richtigen Zuordnungen für Unicode oder MBCS sicher.

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Zeichen folgen Bearbeitung](../c-runtime-library/string-manipulation-crt.md)
