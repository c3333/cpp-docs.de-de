---
title: Zeichenfolgendatenverwaltung
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317464"
---
# <a name="string-data-management"></a>Zeichenfolgendatenverwaltung

Visual C++ bietet mehrere Möglichkeiten zum Verwalten von Zeichenfolgendaten:

- [String-Manipulation](../c-runtime-library/string-manipulation-crt.md) für die Arbeit mit Null-Termin-Zeichenfolgen im C-Stil

- Win32-API-Funktionen für die Verwaltung von Zeichenfolgen

- MFC-Klasse [CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md), die flexible, umlagebare Zeichenfolgenobjekte bereitstellt

- Klasse [CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md), die ein MFC-unabhängiges Zeichenfolgenobjekt mit der gleichen Funktionalität wie`CString`

Fast alle Programme arbeiten mit Zeichenfolgendaten. Die `CString` MFC-Klasse ist oft die beste Lösung für die flexible String-Handhabung. Ab Version 7.0 `CString` kann in MFC- oder MFC-unabhängigen Programmen verwendet werden. Sowohl die Laufzeitbibliothek `CString` als auch Unterstützungszeichenfolgen, die Multibyte (weit) Zeichen enthalten, wie in der Unicode- oder MBCS-Programmierung.

In diesem Artikel werden die allgemeinen Dienste beschrieben, die die Klassenbibliothek im Zusammenhang mit der Zeichenfolgenmanipulation bereitstellt. Zu den in diesem Artikel behandelten Themen gehören:

- [Unicode und MBCS bieten Portabilität](#_core_unicode_and_mbcs_provide_portability)

- [CStrings und const char Zeiger](#_core_cstrings_and_const_char_pointers)

- [CString-Referenzzählung](#_core_cstring_reference_counting)

Die [CStringT-Klassenklasse](../atl-mfc-shared/reference/cstringt-class.md) bietet Unterstützung für das Bearbeiten von Zeichenfolgen. Es soll die Funktionalität ersetzen und erweitern, die normalerweise vom C-Laufzeitbibliothekszeichenfolgenpaket bereitgestellt wird. Die `CString` Klasse stellt Memberfunktionen und Operatoren für eine vereinfachte Zeichenfolgenbehandlung bereit, ähnlich denen in Basic. Die Klasse stellt auch Konstruktoren und Operatoren zum `CString`Erstellen, Zuweisen und Vergleichen von s- und Standard-C++-Zeichenfolgendatentypen bereit. Da `CString` nicht von `CObject`abgeleitet ist, können Sie Objekte unabhängig von den meisten Microsoft Foundation-Klassenbibliotheken (MFC) verwenden. `CString`

`CString`Objekte folgen "Wertsemantik". Ein `CString` Objekt stellt einen eindeutigen Wert dar. Stellen Sie `CString` sich eine als tatsächliche Zeichenfolge vor, nicht als Zeiger auf eine Zeichenfolge.

Ein `CString` Objekt stellt eine Sequenz einer variablen Anzahl von Zeichen dar. `CString`Objekte können als Arrays von Zeichen betrachtet werden.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode und MBCS bieten Portabilität

Mit MFC-Version 3.0 und höher `CString`ist MFC, einschließlich , sowohl für Unicode- als auch für Multibyte-Zeichensätze (MBCS) aktiviert. Diese Unterstützung erleichtert Ihnen das Schreiben von portablen Anwendungen, die Sie für Unicode- oder ANSI-Zeichen erstellen können. Um diese Portabilität zu `CString` aktivieren, ist jedes Zeichen in `wchar_t` einem Objekt vom Typ TCHAR, das `char` so definiert ist, als ob Sie das Symbol _UNICODE definieren, wenn Sie Ihre Anwendung erstellen, oder als ob nicht. Ein `wchar_t` Zeichen ist 16 Bit breit. MBCS ist aktiviert, wenn Sie mit dem Symbol _MBCS definiert erstellen. MFC selbst wird entweder mit dem _MBCS Symbol (für die NAFX-Bibliotheken) oder dem _UNICODE Symbol (für die UAFX-Bibliotheken) erstellt.

> [!NOTE]
> Die `CString` Beispiele in diesem und den begleitenden Artikeln zu Zeichenfolgen zeigen Literalzeichenfolgen, die ordnungsgemäß für die Unicode-Portabilität formatiert sind, und verwenden das makro _T, das die Literalzeichenfolge in das Formular übersetzt:

`L"literal string"`

> [!NOTE]
> die der Compiler als Unicode-Zeichenfolge behandelt. Beispielsweise folgender Code:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> wird als Unicode-Zeichenfolge übersetzt, wenn _UNICODE definiert ist, oder als ANSI-Zeichenfolge, falls nicht. Weitere Informationen finden Sie im Artikel [Unicode and Multibyte Character Set (MBCS) Support](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

Ein `CString` Objekt kann bis zu INT_MAX (2.147.483.647) Zeichen speichern. Der TCHAR-Datentyp wird verwendet, um `CString` einzelne Zeichen innerhalb eines Objekts abzubekommen oder festzulegen. Im Gegensatz zu `CString` Zeichenarrays verfügt die Klasse über eine integrierte Speicherzuweisungsfunktion. Dadurch `CString` können Objekte nach Bedarf automatisch wachsen (d. h., `CString` Sie müssen sich keine Gedanken darüber machen, ein Objekt zu vergrößern, um längere Zeichenfolgen zu passen).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings und const char Zeiger

Ein `CString` Objekt kann auch wie eine literale `PCXSTR`Zeichenfolge im C-Stil fungieren (eine , die mit **const char** <strong>\*</strong> identisch ist, wenn nicht unter Unicode). Mit dem [Konvertierungsoperator CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) können `CString` Objekte in Funktionsaufrufen frei durch Zeichenzeiger ersetzt werden. Mit dem **CString( LPCWSTR** `pszSrc` **)** Konstruktor können Zeichenzeiger durch `CString` Objekte ersetzt werden.

Es wird kein `CString` Versuch unternommen, Objekte zu falten. Wenn Sie `CString` z. `Chicago`B. zwei Objekte `Chicago` mit einem Objekt erstellen, werden die Zeichen in an zwei Stellen gespeichert. (Dies gilt möglicherweise nicht für zukünftige Versionen von MFC, daher sollten Sie nicht darauf angewiesen sein.)

> [!NOTE]
> Verwenden Sie die Memberfunktionen [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) und [CSimpleStringT::ReleaseBuffer,](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) wenn Sie direkt auf einen `CString` als nicht konstanten Zeiger auf ein Zeichen zugreifen müssen.

> [!NOTE]
> Verwenden Sie die Memberfunktionen [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) und [CStringT::SetSysString,](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) um In-Automatisierung verwendete BSTR-Objekte (früher als OLE-Automatisierung bezeichnet) zuzuweisen und festzulegen.

> [!NOTE]
> Ordnen `CString` Sie nach Möglichkeit Objekte auf dem Frame und nicht auf dem Heap zu. Dies spart Speicher und vereinfacht die Parameterübergabe.

Die `CString` Klasse ist nicht als Microsoft Foundation-Klassenbibliothekssammlungsklasse implementiert, obwohl `CString` Objekte sicherlich als Elemente in Auflistungen gespeichert werden können.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString-Referenzzählung

Ab MFC-Version 4.0 erhöht MFC beim Kopieren von [CStringT-Klassenobjekten](../atl-mfc-shared/reference/cstringt-class.md) eine Verweisanzahl, anstatt die Daten zu kopieren. Dadurch wird das Übergeben `CString` von Parametern nach Wert und das Zurückgeben von Objekten nach Wert effizienter. Diese Vorgänge bewirken, dass der Kopierkonstruktor aufgerufen wird, manchmal mehr als einmal. Durch das Erhöhen einer Referenzanzahl wird der `CString` Aufwand für diese allgemeinen Vorgänge reduziert und die Verwendung einer attraktiveren Option erhöht.

Wenn jede Kopie zerstört wird, wird die Referenzanzahl im ursprünglichen Objekt dekrementiert. Das `CString` ursprüngliche Objekt wird erst zerstört, wenn seine Referenzanzahl auf Null reduziert wird.

Sie können `CString` die Memberfunktionen [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) und [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) verwenden, um die Referenzzählung zu deaktivieren oder zu aktivieren.

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
