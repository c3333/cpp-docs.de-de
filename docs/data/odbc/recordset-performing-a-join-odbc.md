---
title: 'Recordset: Ausführen einer Verknüpfung (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 7e8d42f2b96911cd57aca7c132b53ed7c10162be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212796"
---
# <a name="recordset-performing-a-join-odbc"></a>Recordset: Ausführen einer Verknüpfung (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

## <a name="what-a-join-is"></a>Was ist ein Join?

Der Joinvorgang, eine gängige Datenzugriffs Aufgabe, ermöglicht Ihnen das Arbeiten mit Daten aus mehr als einer Tabelle mithilfe eines einzelnen Recordset-Objekts. Das beitreten von zwei oder mehr Tabellen ergibt ein Recordset, das Spalten aus jeder Tabelle enthalten kann, aber als eine einzelne Tabelle für Ihre Anwendung angezeigt wird. In manchen Fällen verwendet der Join alle Spalten aus allen Tabellen, aber manchmal verwendet die SQL **Select** -Klausel in einem Join nur einige der Spalten aus jeder Tabelle. Die Datenbankklassen unterstützen schreibgeschützte Joins, aber keine aktualisierbaren Joins.

Um Datensätze mit Spalten aus verbundenen Tabellen auszuwählen, benötigen Sie Folgendes:

- Eine Tabellenliste, die die Namen aller miteinander verbundenen Tabellen enthält.

- Eine Spaltenliste, die die Namen aller teilnehmenden Spalten enthält. Spalten mit demselben Namen, aber aus unterschiedlichen Tabellen werden durch den Tabellennamen qualifiziert.

- Ein Filter (SQL- **Where** -Klausel), der die Spalten angibt, mit denen die Tabellen verknüpft sind. Dieser Filter hat das Format "Table1. KeyCol = Table2. KeyCol" und führt den Join tatsächlich aus.

Sie können mehr als zwei Tabellen auf die gleiche Weise verknüpfen, indem Sie mehrere Spalten Paare zuordnen, wobei jedes Paar mit dem SQL-Schlüsselwort **und**verknüpft ist.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Deklarieren einer Klasse für eine vordefinierte Abfrage (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Recordset: Erneutes Abfragen eines Recordsets (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
