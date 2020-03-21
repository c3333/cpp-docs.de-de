---
title: Bestimmen des geeigneten Zugriffsmethodentyps
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: d729e2cf5b08ae227d0cc2e4d5ab7f8ac865cdc4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079656"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Bestimmen des geeigneten Zugriffsmethodentyps

Sie können die Datentypen in einem Rowset zur Kompilierzeit oder zur Laufzeit bestimmen.

Wenn Sie Datentypen zur Kompilierzeit ermitteln müssen, verwenden Sie einen statischen Accessor (z.B. `CAccessor`).

Wenn Sie Datentypen zur Laufzeit ermitteln müssen, verwenden Sie einen dynamischen (`CDynamicAccessor` oder seine untergeordneten Elemente) oder einen manuellen Accessor (`CManualAccessor`). Sie können in diesen Fällen `GetColumnInfo` für das Rowset aufrufen, um die Spaltenbindungsinformationen zurückzugeben, aufgrund derer Sie Typen bestimmen können.

Die folgende Tabelle enthält die Typen der Accessoren, die in den Consumervorlagen bereitgestellt werden. Jeder Accessor hat Vor- und Nachteile. Je nach Situation sollte ein Accessortyp Ihre Anforderungen erfüllen.

|Accessorklasse|Bindung|Parameter|Comment|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Erstellen Sie einen Benutzerdatensatz mit COLUMN_ENTRY-Makros. Die Makros binden einen Datenmember in diesem Datensatz an den Accessor. Wenn das Rowset erstellt wird, können Spaltenbindungen nicht aufgehoben werden.|Ja, mithilfe eines PARAM_MAP-Makro-Eintrags. Nach der Bindung kann die Bindung von Parametern nicht aufgehoben werden.|Schnellster Accessor aufgrund von wenig Code.|
|`CDynamicAccessor`|Automatisch.|Nein.|Nützlich, wenn Sie den Typ der Daten in einem Rowset nicht kennen.|
|`CDynamicParameterAccessor`|Automatisch, kann jedoch [überschrieben](../../data/oledb/overriding-a-dynamic-accessor.md) werden.|Ja, wenn der Anbieter `ICommandWithParameters` unterstützt. Parameter werden automatisch gebunden.|Langsamer als `CDynamicAccessor`, aber hilfreich zum Aufrufen generischer gespeicherter Prozeduren.|
|`CDynamicStringAccessor[A,W]`|Automatisch.|Nein.|Ruft Daten aus dem Datenspeicher, auf die zugegriffen wird, als Zeichenfolgendaten ab.|
|`CManualAccessor`|Manuell mithilfe von `AddBindEntry`.|Manuell mithilfe von `AddParameterEntry`.|Schnell; Parameter und Spalten werden nur einmal gebunden. Sie bestimmen den zu verwendenden Datentyp. (Ein Beispiel finden Sie unter [DBViewer](https://github.com/Microsoft/VCSamples) Sample.) Erfordert mehr Code als `CDynamicAccessor` oder `CAccessor`. Entspricht eher dem direkten Aufruf von OLE DB.|
|`CXMLAccessor`|Automatisch.|Nein.|Ruft Daten aus dem Datenspeicher, auf die zugegriffen wird, als Zeichenfolgendaten ab, und formatiert sie als XML-markierte Daten.|

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)