---
title: Ausgabeparameter
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: ece626eb7fbecae9b90321ccc2569607897cf520
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209858"
---
# <a name="output-parameters"></a>Ausgabeparameter

Das Aufrufen einer gespeicherten Prozedur ähnelt der Ausführung eines SQL-Befehls. Der Hauptunterschied besteht darin, dass gespeicherte Prozeduren Ausgabeparameter (oder "OutParameters") und Rückgabewerte verwenden.

In der folgenden gespeicherten Prozedur ist das erste '? ' der Rückgabewert (Phone), und das zweite '? ' ist der Eingabeparameter (Name):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

Sie geben die Parameter "in" und "out" in der Parameter Zuordnung an:

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

Die Anwendung muss die von gespeicherten Prozeduren zurückgegebene Ausgabe verarbeiten. Die Rückgabe von Ausgabeparametern und Rückgabewerten erfolgt bei verschiedenen OLE DB-Anbietern zu unterschiedlichen Zeitpunkten während der Ergebnisverarbeitung. Beispielsweise stellt der Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB) keine Ausgabeparameter und Rückgabecodes bereit, bis der Consumer die von der gespeicherten Prozedur zurückgegebenen Resultsets abgerufen oder abgebrochen hat. Die Ausgabe wird im letzten TDS-Paket vom Server zurückgegeben.

## <a name="row-count"></a>Zeilenanzahl

Wenn Sie die OLE DB Consumer-Vorlagen verwenden, um eine gespeicherte Prozedur mit OutParameters auszuführen, wird die Zeilen Anzahl erst festgelegt, wenn Sie das Rowset schließen.

Stellen Sie sich z. b. eine gespeicherte Prozedur mit einem Rowset und einem outparameter vor:

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

Der `@_rowcount` outparameter gibt an, wie viele Zeilen aus der Test Tabelle zurückgegeben wurden. Diese gespeicherte Prozedur schränkt jedoch die Anzahl der Zeilen auf 50 ein. Wenn z. b. 100 Zeilen im Test vorhanden waren, wäre die Zeilen Anzahl 50 (da dieser Code nur die obersten 50 Zeilen abruft). Wenn in der Tabelle nur 30 Zeilen vorhanden sind, beträgt die Zeilen Anzahl 30. Stellen Sie sicher, dass Sie `Close` oder `CloseAll` aufrufen, um den outparameter aufzufüllen, bevor Sie seinen Wert abrufen.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von gespeicherten Prozeduren](../../data/oledb/using-stored-procedures.md)
