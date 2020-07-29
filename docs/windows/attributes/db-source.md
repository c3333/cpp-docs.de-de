---
title: db_source (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: d328cd7bcfed257b423a440041b6806149736ed0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215295"
---
# <a name="db_source"></a>db_source

Erstellt eine Verbindung mit einer Datenquelle.

## <a name="syntax"></a>Syntax

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Parameter

*db_source*<br/>
Die Verbindungs Zeichenfolge zum Herstellen einer Verbindung mit der Datenquelle. Das Format der Verbindungs Zeichenfolge finden Sie unter Verbindungs Zeichenfolgen [und Daten Verknüpfungen](/previous-versions/windows/desktop/ms718376(v=vs.85)) im Microsoft Data Access Components (MDAC) SDK.

*name*<br/>
Optionale Wenn Sie **db_source** für eine Klasse verwenden, handelt es sich bei *Name* um eine Instanz eines Datenquellen Objekts, auf das das **db_source** -Attribut angewendet wird (siehe Beispiel 1). Wenn Sie **db_source** Inline in einer Methoden Implementierung verwenden, handelt es sich bei *Name* um eine Variable (lokale Methode der Methode), die für den Zugriff auf die Datenquelle verwendet werden kann (siehe Beispiel 2). Sie übergeben diesen *Namen* an den *source_name* -Parameter von `db_command` , um die Datenquelle einem Befehl zuzuordnen.

*HRESULT*<br/>
Optionale Gibt die Variable an, die das HRESULT dieses Daten Bank Befehls empfängt. Wenn die Variable nicht existiert, wird sie automatisch durch das Attribut eingefügt.

## <a name="remarks"></a>Bemerkungen

**db_source** erstellt ein [CDataSource](../../data/oledb/cdatasource-class.md) -und ein [CSession](../../data/oledb/csession-class.md) -Objekt, das zusammen eine Verbindung mit einer OLE DB consumerdatenquelle darstellt.

Wenn Sie **db_source** für eine Klasse verwenden, wird das- `CSession` Objekt zu einem Member der-Klasse.

Wenn Sie **db_source** in einer Methode verwenden, wird der eingefügte Code im Methoden Bereich ausgeführt, und das `CSession` Objekt wird als lokale Variable erstellt.

**db_source** fügt einer Klasse oder innerhalb einer Methode Datenquellen Eigenschaften hinzu. Sie wird in Verbindung mit verwendet `db_command` (wobei der *db_source* *Name* -Parameter als *source_name* -Parameter verwendet wird).

Wenn der Consumer-Attribut Anbieter dieses Attribut auf eine Klasse anwendet, benennt der Compiler die Klasse in den \_ *yourclassname*-Accessor um, wobei *yourclassname* der Name ist, den Sie der Klasse gegeben haben, und der Compiler erstellt außerdem eine Klasse namens *yourclassname*, die vom \_ *yourclassname*-Accessor abgeleitet wird.  In dieser Klassenansicht werden beide Klassen angezeigt.

Ein Beispiel für dieses Attribut, das in einer Anwendung verwendet wird, finden [Sie unter MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Beispiel

In diesem Beispiel wird **db_source** für eine-Klasse aufgerufen, um `ds` mithilfe der Northwind-Datenbank eine Verbindung mit der Datenquelle herzustellen. `ds`ist ein Handle für die Datenquelle, die intern für die-Klasse verwendet werden kann `CMyCommand` .

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")
]
class CMyCommand {};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`** , Member, Methode, local|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[OLE DB Consumer-Attribute](ole-db-consumer-attributes.md)
