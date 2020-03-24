---
title: Accessoren und Rowsets
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 45180b3ac2647c9f4f5d25a1322794552bd79004
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212380"
---
# <a name="accessors-and-rowsets"></a>Accessoren und Rowsets

Zum Festlegen und Abrufen von Daten verwenden OLE DB Vorlagen einen Accessor und ein Rowset über die [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) -Klasse. Diese Klasse kann mehrere Accessoren verschiedener Typen verarbeiten.

## <a name="accessor-types"></a>Zugriffsmethoden Typen

Alle Accessoren werden von [CAccessorBase](../../data/oledb/caccessorbase-class.md)abgeleitet. `CAccessorBase` stellt sowohl Parameter-als auch Spalten Bindungen bereit.

In der folgenden Abbildung werden die Accessortypen veranschaulicht.

![Zugriffsmethoden Typen](../../data/oledb/media/vcaccessortypes.gif "Zugriffsmethodentypen")<br/>
Accessor-Klassen

- [CAccessor](../../data/oledb/caccessor-class.md) Verwenden Sie diesen Accessor, wenn Sie die Struktur der Datenbankquelle zur Entwurfszeit kennen. mit `CAccessor` wird ein Daten Satz, der den Puffer enthält, statisch an die Datenquelle gebunden.

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Verwenden Sie diesen Accessor, wenn Sie die Struktur der Datenbank zur Entwurfszeit nicht kennen. `CDynamicAccessor` ruft `IColumnsInfo::GetColumnInfo` auf, um die Daten Bank Spalten Informationen zu erhalten. Er erstellt und verwaltet einen-Accessor und den-Puffer.

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) Verwenden Sie diesen Accessor, um unbekannte Befehls Typen zu behandeln. Wenn Sie die Befehle vorbereiten, können `CDynamicParameterAccessor` Parameterinformationen von der `ICommandWithParameters` Schnittstelle erhalten, wenn der Anbieter `ICommandWithParameters`unterstützt.

- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)und [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) verwenden diese Klassen, wenn Sie das Datenbankschema nicht kennen. `CDynamicStringAccessorA` Ruft Daten als ANSI-Zeichen folgen ab. `CDynamicStringAccessorW` Ruft Daten als Unicode-Zeichen folgen ab.

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) Mit dieser Klasse können Sie alle Datentypen verwenden, die Sie verwenden möchten, wenn der Anbieter den Typ konvertieren kann. Beide Ergebnis Spalten und Befehlsparameter werden behandelt.

In der folgenden Tabelle wird die Unterstützung in den OLE DB-Vorlagen Accessor-Typen zusammengefasst.

|Accessor-Typ|Dynamisch|Behandelt Parameter|Buffer|Mehrere Accessoren|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|Nein|Ja|Benutzer|Ja|
|`CDynamicAccessor`|Ja|Nein|OLE DB-Vorlagen|Nein|
|`CDynamicParameterAccessor`|Ja|Ja|OLE DB-Vorlagen|Nein|
|`CDynamicStringAccessor[A,W]`|Ja|Nein|OLE DB-Vorlagen|Nein|
|`CManualAccessor`|Ja|Ja|Benutzer|Ja|

## <a name="rowset-types"></a>Rowsettypen

Die OLE DB Vorlagen unterstützen drei Arten von Rowsets (siehe vorherige Abbildung): einzelne Rowsets (implementiert von [CRowset](../../data/oledb/crowset-class.md)), Bulk-Rowsets (implementiert durch [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) und Array-Rowsets (implementiert von [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Einzelne Rowsets rufen ein einzelnes Zeilen Handle ab, wenn `MoveNext` aufgerufen wird. Bulk-Rowsets können mehrere Zeilen Handles abrufen. Array-Rowsets sind Rowsets, auf die mithilfe der Array Syntax zugegriffen werden kann.

In der folgenden Abbildung werden die Rowsettypen veranschaulicht.

![RowsetType-Grafik](../../data/oledb/media/vcrowsettypes.gif "Grafik zu RowsetType")<br/>
Rowset-Klassen

[Schemarowsets](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) greifen nicht auf Daten im Datenspeicher zu, sondern auf Informationen über den Datenspeicher, die als Metadaten bezeichnet werden. Schemarowsets werden in der Regel in Situationen verwendet, in denen die Datenbankstruktur zum Zeitpunkt der Kompilierung nicht bekannt ist und zur Laufzeit abgerufen werden muss.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)
