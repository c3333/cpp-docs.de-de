---
title: Db_accessor (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 1e9725dad39974b828d87bd8b4cdeac623f4e12f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214863"
---
# <a name="db_accessor"></a>db_accessor

Gruppiert `db_column` Attribute, die an `IAccessor`basierten Bindung beteiligt sind.

## <a name="syntax"></a>Syntax

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Parameter

*num*<br/>
Gibt die Accessornummer an (ein NULL basierter ganzzahliger Index). Sie müssen Accessor-Nummern in ansteigender Reihenfolge angeben, indem Sie ganze Zahlen oder definierte Werte verwenden.

*auto*<br/>
Ein boolescher Wert, der angibt, ob der Accessor automatisch abgerufen (true) oder nicht abgerufen wird (false).

## <a name="remarks"></a>Bemerkungen

**Db_accessor** definiert den zugrunde liegenden OLE DB Accessor für nachfolgende `db_column` und `db_param` Attribute innerhalb derselben Klasse oder Funktion. **Db_accessor** auf Element Ebene verwendbar und zum Gruppieren von `db_column` Attributen verwendet, die an OLE DB `IAccessor`basierten Bindung beteiligt sind. Sie wird in Verbindung mit den Attributen `db_table` oder `db_command` verwendet. Das Aufrufen dieses Attributs ähnelt dem Aufrufen der Makros " [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) " und " [END_ACCESSOR](../../data/oledb/end-accessor.md) ".

**Db_accessor** generiert ein Rowset und bindet es an die entsprechenden accessorzuordnungen. Wenn Sie **Db_accessor**nicht aufzurufen, wird der Accessor 0 automatisch generiert, und alle Spalten Bindungen werden diesem Accessorblock zugeordnet.

**Db_accessor** gruppiert Daten Bank Spalten Bindungen in einem oder mehreren Accessoren. Eine Erläuterung der Szenarien, in denen Sie mehrere Accessoren verwenden müssen, finden Sie unter [Verwenden mehrerer Accessoren für ein Rowset](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Siehe auch "Unterstützung von Benutzerdaten Sätzen für mehrere Accessoren" in [Benutzerdaten Sätzen](../../data/oledb/user-records.md).

Wenn der Consumer-Attribut Anbieter dieses Attribut auf eine Klasse anwendet, benennt der Compiler die Klasse in \_*yourclassname*-Accessor um, wobei *yourclassname* der Name ist, den Sie der Klasse gegeben haben, und der Compiler erstellt außerdem eine Klasse namens *yourclassname*, die von \_*yourclassname*-Accessor abgeleitet wird.  In dieser Klassenansicht werden beide Klassen angezeigt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird **Db_accessor** verwendet, um Spalten in der Orders-Tabelle aus der Northwind-Datenbank in zwei Accessoren zu gruppieren. Accessor 0 ist ein automatischer Accessor, und Accessor 1 ist nicht.

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Attribut Blöcke|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumerattribute](ole-db-consumer-attributes.md)
