---
title: Db_table (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: dfdf012550359d0658d53b3f67c0619a124b6309
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834192"
---
# <a name="db_table"></a>db_table

Öffnet eine OLE DB Tabelle.

## <a name="syntax"></a>Syntax

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>Parameter

*db_table*<br/>
Eine Zeichenfolge, die den Namen einer Datenbanktabelle (z. b. "Products") angibt.

*name*<br/>
Optionale Der Name des Handles, das Sie verwenden, um mit der Tabelle zu arbeiten. Sie müssen diesen Parameter angeben, wenn Sie mehr als eine Zeile mit Ergebnissen zurückgeben möchten. **Db_table** generiert eine Variable mit dem angegebenen *Namen* , die verwendet werden kann, um das Rowset zu traversieren oder mehrere Aktions Abfragen auszuführen.

*source_name*<br/>
Optionale Die `CSession` Variable oder die Instanz einer Klasse, auf die das `db_source` Attribut angewendet wird, auf der der Befehl ausgeführt wird. Informationen hierzu finden Sie unter [db_source](db-source.md).

*HRESULT*<br/>
Optionale Gibt die Variable an, die das HRESULT dieses Daten Bank Befehls empfängt. Wenn die Variable nicht existiert, wird sie automatisch durch das Attribut eingefügt.

## <a name="remarks"></a>Bemerkungen

**Db_table** erstellt ein beschreibbares Objekt, das von einem OLE DB Consumer verwendet wird, [um eine Tabelle](../../data/oledb/ctable-class.md) zu öffnen. Dieses Attribut kann nur auf Klassenebene verwendet werden. Diese können nicht Inline verwendet werden. Verwenden `db_column` Sie, um Tabellen Spalten an Variablen zu binden `db_param` . verwenden Sie, um die Parameter zu begrenzen (legen Sie den Parametertyp usw.).

Wenn der Consumer-Attribut Anbieter dieses Attribut auf eine Klasse anwendet, benennt der Compiler die Klasse in den \_ *yourclassname*-Accessor um, wobei *yourclassname* der Name ist, den Sie der Klasse gegeben haben, und der Compiler erstellt außerdem eine Klasse namens *yourclassname*, die vom \_ *yourclassname*-Accessor abgeleitet wird.  In dieser Klassenansicht werden beide Klassen angezeigt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Products-Tabelle für die Verwendung mit geöffnet `CProducts` .

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

Ein Beispiel für dieses Attribut, das in einer Anwendung verwendet wird, finden [Sie unter MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[OLE DB Consumer-Attribute](ole-db-consumer-attributes.md)
