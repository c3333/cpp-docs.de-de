---
title: 'Recordset: Sortieren von Datensätzen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 4bbe635cdda9152be6ba178b863147db93b7c706
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212744"
---
# <a name="recordset-sorting-records-odbc"></a>Recordset: Sortieren von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie Sie das Recordset sortieren. Sie können eine oder mehrere Spalten angeben, auf denen die Sortierung basieren soll, und Sie können eine aufsteigende oder absteigende Reihenfolge angeben (**ASC** **oder absteigend).** **ASC** ist die Standardeinstellung) für jede angegebene Spalte. Wenn Sie z. b. zwei Spalten angeben, werden die Datensätze zuerst nach der ersten Spalte mit dem Namen und dann nach der zweiten Spalte mit dem Namen sortiert. Eine SQL **Order by** -Klausel definiert eine Sortierung. Wenn das Framework die **Order by** -Klausel an die SQL-Abfrage des Recordsets anfügt, steuert die-Klausel die Reihenfolge der Auswahl.

Sie müssen die Sortierreihenfolge eines Recordsets festlegen, nachdem Sie das Objekt erstellt haben, aber bevor Sie die `Open` Member-Funktion aufrufen (oder bevor Sie die `Requery` Member-Funktion für ein vorhandenes Recordset-Objekt aufrufen, dessen `Open` Member-Funktion zuvor aufgerufen wurde).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>So geben Sie eine Sortierreihenfolge für ein Recordset-Objekt an

1. Erstellen Sie ein neues Recordset-Objekt (oder bereiten Sie `Requery` für ein vorhandenes fest).

1. Legen Sie den Wert für das [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) Datenmember des Objekts fest.

   Die Sortierung ist eine auf NULL endende Zeichenfolge. Sie enthält den Inhalt der **Order by** -Klausel, jedoch nicht das Schlüsselwort **Order by**. Verwenden Sie z.B. Folgendes:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Legen Sie alle anderen benötigten Optionen fest, z. b. einen Filter, einen Sperrmodus oder Parameter.

1. Ruft `Open` für das neue-Objekt (oder für ein vorhandenes-Objekt `Requery`) auf.

Die ausgewählten Datensätze werden wie angegeben geordnet. Gehen Sie beispielsweise wie folgt vor, um einen Satz von Student-Datensätzen in absteigender Reihenfolge nach Nachnamen zu sortieren:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Das Recordset enthält alle Student-Datensätze, sortiert in absteigender Reihenfolge (Z bis A) nach Nachnamen und dann nach Vorname.

> [!NOTE]
>  Wenn Sie die standardmäßige SQL-Zeichenfolge des Recordsets überschreiben möchten, indem Sie Ihre eigene SQL-Zeichenfolge an `Open`übergeben, legen Sie keine Sortierung fest, wenn die benutzerdefinierte Zeichenfolge eine **Order by** -Klausel aufweist.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Parametrisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
