---
title: Db_column (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: 98f546a243016fa85f6d71159ab2fc0a7963bae3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833114"
---
# <a name="db_column"></a>db_column

Bindet eine angegebene Spalte an eine Variable im Rowset.

## <a name="syntax"></a>Syntax

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parameter

*Ordnungszahl*<br/>
Die ordinalspaltennummer ( `DBCOLUMNINFO` Ordnungszahl) oder der Spaltenname (ANSI-oder Unicode-Zeichenfolge), die einem Feld im Rowset entspricht, an das Daten gebunden werden sollen. Wenn Sie Zahlen verwenden, können Sie aufeinander folgende ordinale überspringen (z. b.: 1, 2, 3, 5). Der Name kann Leerzeichen enthalten, wenn der von Ihnen verwendete OLE DB Anbieter ihn unterstützt. Sie können z. b. eines der folgenden Formate verwenden:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

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

**Db_column** bindet die angegebene Tabellenspalte an eine Variable im Rowset. Dabei werden Elementdaten begrenzt, die an OLE DB basierten Bindung teilnehmen können `IAccessor` . Mit diesem Attribut wird die Spalten Zuordnung festgelegt, die normalerweise mithilfe der OLE DB Consumer-Makros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md)und [COLUMN_ENTRY](../../data/oledb/column-entry.md)definiert wird. Diese bearbeiten die OLE DB [DBBINDING-Struktur](/previous-versions/windows/desktop/ms716845(v=vs.85)) , um die angegebene Spalte zu binden. Jeder Member, den Sie mit dem **Db_column** -Attribut markieren, belegt einen Eintrag in der Spalten Zuordnung in Form eines Spalten Eintrags. Daher wird dieses Attribut aufgerufen, wenn Sie die Spalten Zuordnung, d. h. in der Befehls-oder Tabellen Klasse, einfügen würden.

Verwenden Sie **Db_column** in Verbindung mit den Attributen [Db_table](db-table.md) oder [db_command](db-command.md) .

Wenn der Consumer-Attribut Anbieter dieses Attribut auf eine Klasse anwendet, benennt der Compiler die Klasse in den \_ *yourclassname*-Accessor um, wobei *yourclassname* der Name ist, den Sie der Klasse gegeben haben, und der Compiler erstellt außerdem eine Klasse namens *yourclassname*, die vom \_ *yourclassname*-Accessor abgeleitet wird.  In dieser Klassenansicht werden beide Klassen angezeigt.

Ein Beispiel für dieses Attribut, das in einer Anwendung verwendet wird, finden [Sie unter MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Beispiel

In diesem Beispiel wird eine Spalte in einer Tabelle an einen Datenmember gebunden, und es werden die **`long`** Felder Status und Länge angegeben.

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>Beispiel

In diesem Beispiel werden vier Spalten **`long`** `DB_NUMERIC` in dieser Reihenfolge an eine, eine Zeichenfolge, einen Zeitstempel und eine ganze Zahl gebunden.

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`** , Member, Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[OLE DB Consumer-Attribute](ole-db-consumer-attributes.md)<br/>
[Klassenattribute](class-attributes.md)
