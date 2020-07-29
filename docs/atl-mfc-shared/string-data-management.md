---
title: Zeichenfolgendatenverwaltung
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 2da8967effeb6ff439cf5b3cece31f63ee77a761
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219039"
---
# <a name="string-data-management"></a>Zeichenfolgendatenverwaltung

Visual C++ bietet mehrere Möglichkeiten, Zeichen folgen Daten zu verwalten:

- [Zeichen folgen Bearbeitung](../c-runtime-library/string-manipulation-crt.md) für die Arbeit mit null-terminierten Zeichen folgen im C-Stil

- Win32-API-Funktionen zum Verwalten von Zeichen folgen

- [CStringT](../atl-mfc-shared/reference/cstringt-class.md)-Klasse der MFC-Klasse, die flexible, Größe befähigbare Zeichen folgen Objekte bereitstellt

- Class [CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md), die ein MFC-unabhängiges Zeichen folgen Objekt mit derselben Funktionalität bereitstellt wie`CString`

Fast alle Programme arbeiten mit Zeichen folgen Daten. Die MFC- `CString` Klasse ist oft die beste Lösung für die flexible Zeichen folgen Verarbeitung. Ab Version 7,0 `CString` kann in MFC-oder MFC-unabhängigen Programmen verwendet werden. Sowohl die Lauf Zeit Bibliothek als auch die `CString` unterstützten Zeichen folgen mit mehr Byte Zeichen (breit Zeichen), wie in der Unicode-oder MBCS-Programmierung.

In diesem Artikel werden die allgemeinen Dienste beschrieben, die von der Klassenbibliothek in Bezug auf die Zeichen folgen Bearbeitung bereitstellt werden. Zu den in diesem Artikel behandelten Themen gehören:

- [Unicode und MBCS bieten Portabilität](#_core_unicode_and_mbcs_provide_portability)

- [Cstrings und Konstante char-Zeiger](#_core_cstrings_and_const_char_pointers)

- [CString-Verweis Zählung](#_core_cstring_reference_counting)

Die Klasse [CStringT](../atl-mfc-shared/reference/cstringt-class.md) bietet Unterstützung für die Bearbeitung von Zeichen folgen. Er soll die Funktionalität ersetzen und erweitern, die normalerweise vom C-Lauf Zeit Bibliotheks-Zeichen folgen Paket bereitgestellt wird. Die `CString` -Klasse stellt Member-Funktionen und-Operatoren für die vereinfachte Zeichen folgen Behandlung bereit, ähnlich wie in Basic. Die-Klasse stellt auch Konstruktoren und Operatoren zum Erstellen, zuweisen und Vergleichen von `CString` s-und C++-Standard Zeichenfolgen-Datentypen bereit. Da `CString` nicht von abgeleitet ist `CObject` , können Sie- `CString` Objekte unabhängig von den meisten Microsoft Foundation Class-Bibliothek (MFC) verwenden.

`CString`Objekte folgen "Wert Semantik". Ein- `CString` Objekt stellt einen eindeutigen Wert dar. Stellen `CString` Sie sich als eine tatsächliche Zeichenfolge vor, nicht als Zeiger auf eine Zeichenfolge.

Ein- `CString` Objekt stellt eine Sequenz einer Variablen Anzahl von Zeichen dar. `CString`Objekte können als Zeichen Arrays betrachtet werden.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode und MBCS bieten Portabilität

Bei MFC-Version 3,0 und höher ist MFC, einschließlich `CString` , für Unicode-und Multibytezeichen-Zeichensätze (MBCS) aktiviert. Diese Unterstützung erleichtert Ihnen das Schreiben von portablen Anwendungen, die Sie für Unicode-oder ANSI-Zeichen erstellen können. Um diese Portabilität zu aktivieren, ist jedes Zeichen in einem- `CString` Objekt vom Typ TCHAR, das so definiert ist, als **`wchar_t`** ob Sie das Symbol _UNICODE definieren, wenn Sie die Anwendung erstellen, oder als wäre dies nicht der Fall **`char`** . Ein **`wchar_t`** Zeichen ist 16 Bits breit. MBCS ist aktiviert, wenn Sie mit dem Symbol _MBCS erstellt haben, das definiert ist. MFC selbst wird entweder mit dem _MBCS Symbol (für die nafx-Bibliotheken) oder dem _UNICODE Symbol (für die uafx-Bibliotheken) erstellt.

> [!NOTE]
> `CString`In den Beispielen in diesem und den zugehörigen Artikeln zu Zeichen folgen werden Literalzeichenfolgen, die für die Unicode-Portabilität ordnungsgemäß formatiert sind, mithilfe des _T-Makros angezeigt

`L"literal string"`

> [!NOTE]
> , den der Compiler als Unicode-Zeichenfolge behandelt. Beispielsweise folgender Code:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> wird als Unicode-Zeichenfolge übersetzt, wenn _UNICODE definiert ist, andernfalls als eine ANSI-Zeichenfolge. Weitere Informationen finden Sie im Artikel [Unicode-und Multibyte-Zeichensatz Unterstützung (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

Ein- `CString` Objekt kann bis zu INT_MAX (2.147.483.647) Zeichen speichern. Der TCHAR-Datentyp wird verwendet, um einzelne Zeichen innerhalb eines-Objekts zu erhalten oder festzulegen `CString` . Im Gegensatz zu Zeichen Arrays `CString` verfügt die-Klasse über eine integrierte Speicher Belegungs Funktion. Dies ermöglicht `CString` die automatische Vergrößerung von Objekten (d. h., Sie müssen sich keine Gedanken darüber machen, wie Sie ein- `CString` Objekt vergrößern, um längere Zeichen folgen anzupassen).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>Cstrings und Konstante char-Zeiger

Ein- `CString` Objekt kann auch wie eine literale Zeichenfolge im C-Stil (ein-Objekt `PCXSTR` , das mit dem **Konstanten** Zeichen identisch ist, <strong>\*</strong> Wenn es nicht unter Unicode ist) fungieren. Der [CSimpleStringT:: Operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) -Konvertierungs Operator ermöglicht das `CString` freie Ersetzen von Zeichen Zeigern in Funktionsaufrufen. Der **CString (LPCWSTR** `pszSrc` **)** -Konstruktor ermöglicht, dass Zeichen Zeiger für `CString` Objekte ersetzt werden.

Es wird kein Versuch unternommen, `CString` Objekte zu falten. Wenn Sie beispielsweise zwei-Objekte erstellen, `CString` die enthalten, `Chicago` werden die Zeichen in `Chicago` an zwei Stellen gespeichert. (Dies gilt möglicherweise nicht für zukünftige Versionen von MFC, daher sollten Sie nicht davon abhängen.)

> [!NOTE]
> Verwenden Sie die [CSimpleStringT:: GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) -und [CSimpleStringT:: ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) -Member-Funktionen, wenn Sie direkt `CString` auf einen als nicht Konstanten Zeiger auf ein Zeichen zugreifen müssen.

> [!NOTE]
> Verwenden Sie die [CStringT:: AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) -und [CStringT:: SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) -Member-Funktionen, um BSTR-Objekte zuzuordnen und festzulegen, die in Automation (früher als OLE-Automatisierung bezeichnet) verwendet werden.

> [!NOTE]
> Wenn möglich, sollten Sie `CString` Objekte im Frame anstatt auf dem Heap zuordnen. Dadurch wird Arbeitsspeicher gespart und die Parameter Übergabe vereinfacht.

Die- `CString` Klasse ist nicht als Microsoft Foundation Class-Bibliothek Auflistungs Klasse implementiert, obwohl- `CString` Objekte sicherlich als Elemente in Auflistungen gespeichert werden können.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString-Verweis Zählung

Ab MFC Version 4,0 erhöht MFC einen Verweis Zähler, anstatt die Daten zu kopieren, wenn [CStringT-Klassen](../atl-mfc-shared/reference/cstringt-class.md) Objekte kopiert werden. Dadurch wird die Übergabe von Parametern nach Wert und die Rückgabe `CString` von Objekten nach Wert effizienter. Diese Vorgänge bewirken, dass der Kopierkonstruktor aufgerufen wird, manchmal mehrmals. Durch das Inkrementieren eines Verweis zählungs Aufwands wird der Aufwand für diese gängigen Vorgänge reduziert und die Verwendung `CString` einer attraktiveren Option ermöglicht.

Wenn jede Kopie zerstört wird, wird der Verweis Zähler im ursprünglichen Objekt dekrementiert. Das ursprüngliche `CString` Objekt wird erst zerstört, wenn der Verweis Zähler auf 0 (null) reduziert wird.

Sie können die `CString` Member-Funktionen [CSimpleStringT:: LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) und [CSimpleStringT:: UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) verwenden, um die Verweis Zählung zu deaktivieren oder zu aktivieren.

## <a name="see-also"></a>Weitere Informationen

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
