---
title: 'Recordset: Lesezeichen und absolute Positionen (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367069"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Recordset: Lesezeichen und absolute Positionen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Wenn Sie durch ein Recordset navigieren, benötigen Sie häufig eine Möglichkeit, zu einem bestimmten Datensatz zurückzukehren. Das Lesezeichen eines Datensatzes und die absolute Position bieten zwei solcher Methoden.

In diesem Thema wird Folgendes erläutert:

- [So verwenden Sie Lesezeichen](#_core_bookmarks_in_mfc_odbc).

- [So legen Sie den aktuellen Datensatz mit absoluten Positionen fest.](#_core_absolute_positions_in_mfc_odbc)

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Lesezeichen in MFC ODBC

Ein Lesezeichen identifiziert einen Datensatz eindeutig. Wenn Sie durch ein Recordset navigieren, können Sie sich nicht immer auf die absolute Position eines Datensatzes verlassen, da Datensätze aus dem Recordset gelöscht werden können. Die zuverlässige Möglichkeit, die Position eines Datensatzes nachzuverfolgen, ist die Verwendung des Lesezeichens. Klasse `CRecordset` liefert Memberfunktionen für:

- Abrufen des Lesezeichens des aktuellen Datensatzes, damit Sie es in einer Variablen speichern können ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Schnelles Wechseln zu einem bestimmten Datensatz, indem Sie dessen Lesezeichen angeben, das Sie zuvor in einer Variablen ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)) gespeichert haben.

Im folgenden Beispiel wird veranschaulicht, wie diese Memberfunktionen verwendet werden, um den aktuellen Datensatz zu markieren und später zu ihm zurückzukehren:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Sie müssen den zugrunde liegenden Datentyp nicht aus dem [CDBVariant Class-Objekt](../../mfc/reference/cdbvariant-class.md) extrahieren. Weisen Sie `GetBookmark` dem Lesezeichen den Wert `SetBookmark`zu, und kehren Sie es mit zurück.

> [!NOTE]
> Je nach ODBC-Treiber und Recordset-Typ werden Lesezeichen möglicherweise nicht unterstützt. Sie können leicht bestimmen, ob Lesezeichen unterstützt werden, indem Sie [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)aufrufen. Wenn Lesezeichen unterstützt werden, müssen Sie diese explizit implementieren, `CRecordset::useBookmarks` indem Sie die Option in der Memberfunktion [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) angeben. Sie sollten auch die Persistenz von Lesezeichen nach bestimmten Recordset-Vorgängen überprüfen. Wenn Sie z. B. `Requery` ein Recordset haben, sind Lesezeichen möglicherweise nicht mehr gültig. Rufen Sie [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) auf, `SetBookmark`um zu überprüfen, ob Sie sicher aufrufen können.

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Absolute Positionen in MFC ODBC

Neben Lesezeichen können `CRecordset` Sie mit der Klasse den aktuellen Datensatz festlegen, indem Sie eine Ordinalposition angeben. Dies wird als absolute Positionierung bezeichnet.

> [!NOTE]
> Absolute Positionierung ist bei Vorwärts-Recordsets nicht verfügbar. Weitere Informationen zu Forward-Only-Recordsets finden Sie unter [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

Um den aktuellen Datensatzzeiger mit der absoluten Position zu verschieben, rufen Sie [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)auf. Wenn Sie einen `SetAbsolutePosition`Wert an übergeben, wird der Datensatz, der dieser Ordinalposition entspricht, zum aktuellen Datensatz.

> [!NOTE]
> Die absolute Position eines Datensatzes ist potenziell unzuverlässig. Wenn der Benutzer Datensätze aus dem Recordset löscht, ändert sich die Ordinalposition aller nachfolgenden Datensätze. Lesezeichen sind die empfohlene Methode zum Verschieben des aktuellen Datensatzes. Weitere Informationen finden Sie unter [Lesezeichen in MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Weitere Informationen zur Recordset-Navigation finden Sie unter [Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)
