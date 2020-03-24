---
title: 'Recordset: Scrollen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212770"
---
# <a name="recordset-scrolling-odbc"></a>Recordset: Scrollen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Nachdem Sie ein Recordset geöffnet haben, müssen Sie auf die Datensätze zugreifen, um Werte anzuzeigen, Berechnungen durchzuführen, Berichte zu generieren usw. Beim Scrollen können Sie von Datensatz zu Datensatz innerhalb Ihres Recordsets wechseln.

In diesem Thema wird Folgendes erläutert:

- Gewusst [wie: Scrollen von einem Datensatz zu einem anderen Datensatz in einem Recordset](#_core_scrolling_from_one_record_to_another)

- [Unter welchen Umständen ist das Scrollen und wird nicht unterstützt](#_core_when_scrolling_is_supported).

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Scrollen von einem Datensatz zu einem anderen

Class `CRecordset` stellt die `Move` Member-Funktionen zum Scrollen innerhalb eines Recordsets bereit. Diese Funktionen verschieben den aktuellen Datensatz nach Rowsets. Wenn Sie das Massen Abrufen von Zeilen implementiert haben, positioniert ein `Move`-Vorgang das Recordset um die Größe des Rowsets neu. Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, wird das Recordset durch einen Aufruf einer `Move`-Funktion jedes Mal um einen Datensatz neu positioniert. Weitere Informationen zum Abrufen von Massen Zeilen finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Beim Durchlaufen eines Recordsets werden gelöschte Datensätze möglicherweise nicht übersprungen. Weitere Informationen finden Sie unter der [isDeleted](../../mfc/reference/crecordset-class.md#isdeleted) -Member-Funktion.

Zusätzlich zu den `Move` Funktionen stellt `CRecordset` Member-Funktionen bereit, mit denen überprüft werden kann, ob Sie einen Rollup hinter dem Ende oder vor dem Anfang des Recordsets durchgeführt haben.

Um zu ermitteln, ob ein Bildlauf im Recordset möglich ist, können Sie die `CanScroll` Member-Funktion aufzurufen.

#### <a name="to-scroll"></a>So Scrollen Sie

1. Einen Datensatz oder ein Rowset weiterleiten: nennen Sie die Member-Funktion von " [wvenext](../../mfc/reference/crecordset-class.md#movenext) ".

1. Rückwärts ein Datensatz oder ein Rowset: Rufen Sie die Member-Funktion von " [muveprev](../../mfc/reference/crecordset-class.md#moveprev) " auf.

1. Zum ersten Datensatz im Recordset: Ruft die Member-Funktion von " [muvefirst](../../mfc/reference/crecordset-class.md#movefirst) " auf.

1. Mit dem letzten Datensatz im Recordset oder dem letzten Rowset: Ruft die Member-Funktion von " [wvelast](../../mfc/reference/crecordset-class.md#movelast) " auf.

1. *N* Datensätze relativ zur aktuellen Position: Ruft die [Move](../../mfc/reference/crecordset-class.md#move) Member-Funktion auf.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>So testen Sie das Ende oder den Anfang des Recordsets

1. Haben Sie einen Rollup des letzten Datensatzes durchgeführt? Ruft die [IsEOF](../../mfc/reference/crecordset-class.md#iseof) -Member-Funktion auf.

1. Haben Sie den ersten Datensatz vor dem ersten Datensatz verschoben (rückwärts)? Ruft die [IsBOF](../../mfc/reference/crecordset-class.md#isbof) -Member-Funktion auf.

Im folgenden Codebeispiel wird `IsBOF` und `IsEOF` verwendet, um die Grenzwerte eines Recordsets beim Scrollen in beide Richtungen zu erkennen.

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF` gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset hinter dem letzten Datensatz positioniert ist. `IsBOF` gibt einen Wert ungleich 0 (null) zurück, wenn das Recordset vor dem ersten Datensatz (vor allen Datensätzen) positioniert ist. In beiden Fällen gibt es keinen aktuellen Datensatz, mit dem Sie arbeiten können. Wenn Sie `MovePrev` aufzurufen, wenn `IsBOF` bereits true ist, oder `MoveNext` aufruft, wenn `IsEOF` bereits true ist, löst das Framework eine `CDBException`aus. Sie können auch `IsBOF` und `IsEOF` verwenden, um nach einem leeren Recordset zu suchen.

Weitere Informationen zur Recordsetnavigation finden Sie unter [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Beim Scrollen wird unterstützt.

Wie ursprünglich entworfen, war SQL nur vorwärts scrollen, aber ODBC erweitert die scrollfunktionen. Der verfügbare Grad der Unterstützung für den Bildlauf hängt von den ODBC-Treibern ab, mit denen Ihre Anwendung arbeitet, von der ODBC-API-Konformität Ihres Treibers und davon, ob die ODBC-Cursor Bibliothek in den Speicher geladen wird Weitere Informationen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und [ODBC: die ODBC-Cursor Bibliothek](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Sie können steuern, ob die Cursor Bibliothek verwendet wird. Weitere Informationen finden Sie in den Parametern *bUseCursorLib* und *dwOptions* für [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  Im Gegensatz zu den MFC-DAO-Klassen bieten die MFC-ODBC-Klassen keinen Satz von `Find` Funktionen zum Suchen des nächsten (oder vorherigen) Datensatzes, der die angegebenen Kriterien erfüllt.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset:: checkrowseterror](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
