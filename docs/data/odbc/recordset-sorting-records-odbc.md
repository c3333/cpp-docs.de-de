---
title: 'Recordset: Sortieren von Datensätzen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366924"
---
# <a name="recordset-sorting-records-odbc"></a>Recordset: Sortieren von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie Sie Ihr Recordset sortieren. Sie können eine oder mehrere Spalten angeben, auf denen die Sortierung basieren soll, und Sie können aufsteigende oder absteigende Reihenfolge (**ASC** oder **DESC**; **ASC** ist die Standardeinstellung) für jede angegebene Spalte. Wenn Sie beispielsweise zwei Spalten angeben, werden die Datensätze zuerst nach der ersten Spalte mit dem Namen und dann nach der zweiten Spalte mit dem Namen sortiert. Eine SQL **ORDER BY-Klausel** definiert eine Sortierung. Wenn das Framework die **ORDER BY-Klausel** an die SQL-Abfrage des Recordsets anfügt, steuert die Klausel die Reihenfolge der Auswahl.

Sie müssen die Sortierreihenfolge eines Recordsets einrichten, nachdem `Open` Sie das Objekt erstellt `Requery` haben, aber bevor Sie `Open` seine Memberfunktion aufrufen (oder bevor Sie die Memberfunktion für ein vorhandenes Recordset-Objekt aufrufen, dessen Memberfunktion zuvor aufgerufen wurde).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>So geben Sie eine Sortierreihenfolge für ein Recordset-Objekt an

1. Erstellen Sie ein neues Recordset-Objekt (oder bereiten Sie sich darauf vor, ein vorhandenes Objekt aufzurufen). `Requery`

1. Legen Sie den Wert des [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) Datenmembers des Objekts fest.

   Die Sortierung ist eine null-terminierte Zeichenfolge. Es enthält den Inhalt der **ORDER BY-Klausel,** aber nicht das Schlüsselwort ORDER **BY**. Verwenden Sie z.B. Folgendes:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Legen Sie alle anderen Optionen fest, die Sie benötigen, z. B. einen Filter, einen Sperrmodus oder Parameter.

1. Rufen `Open` Sie das neue `Requery` Objekt (oder ein vorhandenes Objekt) auf.

Die ausgewählten Datensätze werden wie angegeben sortiert. Gehen Sie beispielsweise wie folgt vor, um einen Satz von Studentendatensätzen in absteigender Reihenfolge nach Nachnamen und dann nach dem Vornamen zu sortieren:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Das Recordset enthält alle Schülerdatensätze, sortiert in absteigender Reihenfolge (Z bis A) nach Nachnamen und dann nach Vornamen.

> [!NOTE]
> Wenn Sie die SQL-Standardzeichenfolge des Recordsets überschreiben möchten, `Open`indem Sie Ihre eigene SQL-Zeichenfolge an übergeben, legen Sie keine Sortierung fest, wenn Ihre benutzerdefinierte Zeichenfolge über eine **ORDER BY-Klausel** verfügt.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Parametrisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
