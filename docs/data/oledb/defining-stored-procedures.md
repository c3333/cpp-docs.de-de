---
title: Definieren von gespeicherten Prozeduren
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 9bab086bf6982eae5779d3199cfd2ac2c8efe77f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211003"
---
# <a name="defining-stored-procedures"></a>Definieren von gespeicherten Prozeduren

Bevor Sie eine gespeicherte Prozedur aufrufen, müssen Sie Sie zunächst mithilfe des [DEFINE_COMMAND](../../data/oledb/define-command.md) -Makros definieren. Wenn Sie den Befehl definieren, kennzeichnen Sie Parameter mit einem Fragezeichen (?) als Parameter Markierung:

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

Die Syntax (die Verwendung von geschweiften Klammern usw.), die in den Codebeispielen in diesem Thema verwendet wird, ist spezifisch für SQL Server. Die Syntax, die Sie in den gespeicherten Prozeduren verwenden, kann je nach verwendeter Anbieter variieren.

Geben Sie anschließend in der Parameter Zuordnung die Parameter an, die Sie im Befehl verwendet haben, und geben Sie die Parameter in der Reihenfolge an, in der Sie im Befehl auftreten:

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

Im vorherigen Beispiel wird eine gespeicherte Prozedur im Laufe der Zeit definiert. Für eine effiziente Wiederverwendung von Code enthält eine Datenbank in der Regel einen Satz vordefinierter gespeicherter Prozeduren mit Namen wie `Sales by Year` oder `dt_adduserobject`. Sie können ihre Definitionen mithilfe SQL Server Enterprise-Managers anzeigen. Sie werden wie folgt aufgerufen (die Platzierung des *?* Parameter hängen von der-Schnittstelle der gespeicherten Prozedur ab):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

Deklarieren Sie anschließend die Befehls Klasse:

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

Zum Schluss wird die gespeicherte Prozedur in `OpenRowset` wie folgt aufgerufen:

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

Beachten Sie außerdem, dass Sie eine gespeicherte Prozedur mit dem Daten Bank Attribut [db_command](../../windows/db-command.md) wie folgt definieren können:

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von gespeicherten Prozeduren](../../data/oledb/using-stored-procedures.md)
