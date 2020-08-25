---
title: Db_param (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 008a7f1ea07e6c23ad6d812ac4fbf3b30ef1da89
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833074"
---
# <a name="db_param"></a>db_param

Ordnet die angegebene Member-Variable einem Eingabe-oder Ausgabeparameter zu und begrenzt die Variable.

## <a name="syntax"></a>Syntax

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parameter

*Ordnungszahl*<br/>
Die Spaltennummer (DBCOLUMNINFO Ordinal), die einem Feld im Rowset entspricht, an das Daten gebunden werden sollen.

*ParamType*<br/>
Optionale Der Typ, der für den Parameter festgelegt werden soll. Anbieter unterstützen nur Parameter-e/a-Typen, die von der zugrunde liegenden Datenquelle unterstützt werden. Der Typ ist eine Kombination aus einem oder mehreren dbparameamioenum-Werten:

- DBPARAMIO_INPUT Ein Eingabeparameter.

- DBPARAMIO_OUTPUT Ein Ausgabeparameter.

- DBPARAMIO_NOTPARAM Der Accessor hat keine Parameter. `eParamIO`Wenn Sie diesen Wert in zeilenaccessoren festlegen, wird der Benutzer daran erinnert, dass Parameter ignoriert werden.

*DbType*<br/>
Optionale Ein OLE DB [Typindikator](/previous-versions/windows/desktop/ms711251(v=vs.85)) für den Spalten Eintrag.

*precision*<br/>
Optionale Die Genauigkeit, die für den Spalten Eintrag verwendet werden soll. Weitere Informationen finden Sie in der Beschreibung des- `bPrecision` Elements der [DBBINDING-Struktur](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*scale*<br/>
Optionale Die für den Spalten Eintrag zu verwendende Skala. Weitere Informationen finden Sie in der Beschreibung des- `bScale` Elements der [DBBINDING-Struktur](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*status*<br/>
Optionale Eine Element Variable, die zum Speichern des Status dieser Spalte verwendet wird. Der Status gibt an, ob der Spaltenwert ein Datenwert oder ein anderer Wert ist, z. b. NULL. Mögliche Werte finden Sie unter [Status](/previous-versions/windows/desktop/ms722617(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

*length*<br/>
Optionale Eine Element Variable, die zum Speichern der Größe der Spalte in Bytes verwendet wird.

## <a name="remarks"></a>Bemerkungen

**Db_param** definiert Parameter, die in Befehlen verwendet werden. Daher verwenden Sie diese mit `db_command` . Beispielsweise können Sie **Db_param** verwenden, um Parameter in SQL-Abfragen oder gespeicherten Prozeduren zu binden. Parameter in einer gespeicherten Prozedur werden durch Fragezeichen (?) bezeichnet, und Sie sollten die Datenmember in der Reihenfolge binden, in der die Parameter angezeigt werden.

**Db_param** begrenzt Elementdaten, die an OLE DB basierten Bindung teilnehmen können `ICommandWithParameters` . Sie legt den Parametertyp (Eingabe oder Ausgabe), den OLE DB Typ, die Genauigkeit, die Dezimalstellen, den Status und die Länge für den angegebenen Parameter fest. Mit diesem Attribut werden die OLE DB-Consumer-Makros eingefügt BEGIN_PARAM_MAP... END_PARAM_MAP. Jedes Element, das Sie mit dem **Db_param** -Attribut markieren, übernimmt einen Eintrag in der Zuordnung in Form einer COLUMN_ENTRY.

**Db_param** wird in Verbindung mit den Attributen " [Db_table](db-table.md) " oder " [db_command](db-command.md) " verwendet.

Wenn der Consumer-Attribut Anbieter dieses Attribut auf eine Klasse anwendet, benennt der Compiler die Klasse in den \_ *yourclassname*-Accessor um, wobei *yourclassname* der Name ist, den Sie der Klasse gegeben haben, und der Compiler erstellt außerdem eine Klasse namens *yourclassname*, die vom \_ *yourclassname*-Accessor abgeleitet wird.  In dieser Klassenansicht werden beide Klassen angezeigt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine Befehls Klasse erstellt, die auf der gespeicherten Prozedur salesbyyear in der Northwind-Datenbank basiert. Sie ordnet den ersten Parameter in der gespeicherten Prozedur der `m_RETURN_VALUE` Variablen zu und definiert Sie als Ausgabeparameter. Die letzten zwei (Eingabe-) Parameter werden mit `m_Beginning_Date` und verknüpft `m_Ending_Date` .

Im folgenden Beispiel wird die- `nOutput` Variable einem Output-Parameter zugeordnet.

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`** , Member, Methode, local|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[OLE DB Consumer-Attribute](ole-db-consumer-attributes.md)
