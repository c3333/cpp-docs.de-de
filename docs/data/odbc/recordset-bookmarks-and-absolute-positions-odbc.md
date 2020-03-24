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
ms.openlocfilehash: 9a25c0fe4c1f08d376824fbc02211d22c7c14435
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212965"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Recordset: Lesezeichen und absolute Positionen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Wenn Sie durch ein Recordset navigieren, benötigen Sie häufig eine Methode, um zu einem bestimmten Datensatz zurückzukehren. Die Lesezeichen und die absolute Position eines Datensatzes stellen zwei solche Methoden bereit.

In diesem Thema wird Folgendes erläutert:

- Gewusst [wie: Verwenden von Lesezeichen](#_core_bookmarks_in_mfc_odbc)

- [Festlegen des aktuellen Datensatzes mit absoluten Positionen](#_core_absolute_positions_in_mfc_odbc).

##  <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Lesezeichen in MFC ODBC

Ein Lesezeichen identifiziert einen Datensatz eindeutig. Wenn Sie durch ein Recordset navigieren, können Sie sich nicht immer auf die absolute Position eines Datensatzes verlassen, da Datensätze aus dem Recordset gelöscht werden können. Die zuverlässige Möglichkeit, die Position eines Datensatzes nachzuverfolgen, ist die Verwendung seines Lesezeichens. Klassen `CRecordset` stellt Element Funktionen für Folgendes bereit:

- Das Lesezeichen des aktuellen Datensatzes wird abgerufen, sodass Sie ihn in einer Variablen ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)) speichern können.

- Schnelles verschieben zu einem bestimmten Datensatz durch angeben seines Lesezeichens, das Sie zuvor in einer Variablen ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)) gespeichert haben.

Im folgenden Beispiel wird veranschaulicht, wie diese Member-Funktionen verwendet werden, um den aktuellen Datensatz zu markieren und später dorthin zurückzukehren:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Der zugrunde liegende Datentyp muss nicht aus dem [CDBVariant-Klassen](../../mfc/reference/cdbvariant-class.md) Objekt extrahiert werden. Weisen Sie den Wert `GetBookmark` zu, und kehren Sie mit `SetBookmark`zu diesem Lesezeichen zurück.

> [!NOTE]
>  Abhängig von Ihrem ODBC-Treiber und Recordsettyp werden Lesezeichen möglicherweise nicht unterstützt. Sie können leicht feststellen, ob Lesezeichen durch Aufrufen von [CRecordset:: CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)unterstützt werden. Außerdem müssen Sie, wenn Lesezeichen unterstützt werden, explizit festlegen, dass diese implementiert werden, indem Sie die `CRecordset::useBookmarks`-Option in der [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) -Member-Funktion angeben. Außerdem sollten Sie die Persistenz von Lesezeichen nach bestimmten recordsetvorgängen überprüfen. Wenn Sie z. b. ein Recordset `Requery`, sind Lesezeichen möglicherweise nicht mehr gültig. [CDatabase:: getbookmarkpersistenz](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) aufrufen, um zu überprüfen, ob Sie `SetBookmark`sicher aufrufen können.

##  <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Absolute Positionen in MFC ODBC

Neben Lesezeichen können Sie mithilfe von Class `CRecordset` den aktuellen Datensatz festlegen, indem Sie eine Ordinalposition angeben. Dies wird als absolute Positionierung bezeichnet.

> [!NOTE]
>  Absolute Positionierung ist in Vorwärts Recordsets nicht verfügbar. Weitere Informationen zu Vorwärts-Recordsets finden Sie unter [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

Um den aktuellen Daten Satz Zeiger mithilfe der absoluten Position zu verschieben, nennen Sie [CRecordset:: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Wenn Sie einen Wert an `SetAbsolutePosition`übergeben, wird der Datensatz, der dieser Ordinalposition entspricht, zum aktuellen Datensatz.

> [!NOTE]
>  Die absolute Position eines Datensatzes ist potenziell unzuverlässig. Wenn der Benutzerdaten Sätze aus dem Recordset löscht, ändert sich die Ordinalposition eines nachfolgenden Datensatzes. Lesezeichen sind die empfohlene Methode zum Verschieben des aktuellen Datensatzes. Weitere Informationen finden Sie unter [Lesezeichen in MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Weitere Informationen zur Recordsetnavigation finden Sie unter [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)
