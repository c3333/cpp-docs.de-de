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
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366942"
---
# <a name="recordset-scrolling-odbc"></a>Recordset: Scrollen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Nachdem Sie ein Recordset geöffnet haben, müssen Sie auf die Datensätze zugreifen, um Werte anzuzeigen, Berechnungen durchzuführen, Berichte zu generieren usw. Durch Scrollen können Sie innerhalb Ihres Recordsets von Datensatz zu Datensatz wechseln.

In diesem Thema wird Folgendes erläutert:

- [Scrollen von einem Datensatz zu einem anderen in einem Recordset](#_core_scrolling_from_one_record_to_another).

- [Unter welchen Umständen wird das Scrollen unterstützt.](#_core_when_scrolling_is_supported)

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Scrollen von einem Datensatz zum anderen

Die `CRecordset` Klasse `Move` stellt die Memberfunktionen zum Scrollen innerhalb eines Recordsets bereit. Diese Funktionen verschieben den aktuellen Datensatz durch Rowsets. Wenn Sie das Abrufen von `Move` Massenzeilen implementiert haben, positioniert ein Vorgang das Recordset nach der Größe des Rowsets neu. Wenn Sie das Abrufen von Massenzeilen nicht `Move` implementiert haben, wird das Recordset jedes Mal durch einen Datensatz neu positioniert. Weitere Informationen zum Abrufen von Massenzeilen finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Beim Durchlaufen eines Recordsets werden gelöschte Datensätze möglicherweise nicht übersprungen. Weitere Informationen finden [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) Sie unter IsDeleted-Memberfunktion.

Zusätzlich zu `Move` den `CRecordset` Funktionen bietet Memberfunktionen, um zu überprüfen, ob Sie am Ende oder vor dem Anfang Ihres Recordsets gescrollt haben.

Um zu bestimmen, ob ein Bildlauf `CanScroll` in Ihrem Recordset möglich ist, rufen Sie die Memberfunktion auf.

#### <a name="to-scroll"></a>So scrollen Sie

1. Einen Datensatz oder ein Rowset weiterleiten: Rufen Sie die [MoveNext-Memberfunktion](../../mfc/reference/crecordset-class.md#movenext) auf.

1. Rückwärts ein Datensatz oder ein Rowset: Rufen Sie die [MovePrev-Memberfunktion](../../mfc/reference/crecordset-class.md#moveprev) auf.

1. Zum ersten Datensatz im Recordset: Rufen Sie die [MoveFirst-Memberfunktion](../../mfc/reference/crecordset-class.md#movefirst) auf.

1. Zum letzten Datensatz im Recordset oder zum letzten Rowset: Rufen Sie die [MoveLast-Memberfunktion](../../mfc/reference/crecordset-class.md#movelast) auf.

1. *N* Datensätze relativ zur aktuellen Position: Rufen Sie die [Memberfunktion Verschieben](../../mfc/reference/crecordset-class.md#move) auf.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>So testen Sie für das Ende oder den Anfang des Recordsets

1. Haben Sie den letzten Datensatz hinter sich? Rufen Sie die [IsEOF-Memberfunktion](../../mfc/reference/crecordset-class.md#iseof) auf.

1. Haben Sie vor dem ersten Datensatz gescrollt (rückwärts bewegen)? Rufen Sie die [IsBOF-Memberfunktion](../../mfc/reference/crecordset-class.md#isbof) auf.

Im folgenden Codebeispiel werden die Grenzen eines Recordsets beim Scrollen in beide Richtungen verwendet `IsBOF` und `IsEOF` erkannt.

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

`IsEOF`gibt einen Wert ungleich Null zurück, wenn das Recordset über den letzten Datensatz hinaus positioniert wird. `IsBOF`gibt einen Wert ungleich Null zurück, wenn das Recordset vor dem ersten Datensatz (vor allen Datensätzen) positioniert ist. In beiden Fällen gibt es keinen aktuellen Datensatz, auf dem ausgeführt werden kann. Wenn Sie `MovePrev` `IsBOF` when is already `MoveNext` `IsEOF` oder call when is `CDBException`already TRUE aufrufen, löst das Framework eine aus. Sie können `IsBOF` auch `IsEOF` ein leeres Recordset verwenden und überprüfen.

Weitere Informationen zur Recordset-Navigation finden Sie unter [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Wenn Scrollen unterstützt wird

Wie ursprünglich geplant, stellte SQL nur Vorwärts-Scrolling bereit, aber ODBC erweitert die Scrollfunktionen. Die verfügbare Unterstützung für das Scrollen hängt von den ODBC-Treibern ab, mit dem Ihre Anwendung arbeitet, der ODBC-API-Konformitätsebene Ihres Treibers und davon, ob die ODBC-Cursorbibliothek in den Arbeitsspeicher geladen wird. Weitere Informationen finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und [ODBC: The ODBC Cursor Library](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
> Sie können steuern, ob die Cursorbibliothek verwendet wird. Siehe die Parameter *bUseCursorLib* und *dwOptions* in [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
> Im Gegensatz zu den MFC-DAO-Klassen stellen die `Find` MFC-ODBC-Klassen keine Funktionen zum Auffinden des nächsten (oder vorherigen) Datensatzes bereit, der bestimmte Kriterien erfüllt.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
