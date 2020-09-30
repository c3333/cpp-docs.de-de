---
title: Befehle und Tabellen
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
ms.openlocfilehash: f65bd0f90832039d453d84ab9765781c30750318
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507377"
---
# <a name="commands-and-tables"></a>Befehle und Tabellen

Befehle und Tabellen ermöglichen den Zugriff auf Rowsets. Das heißt, dass Sie Rowsets öffnen, Befehle ausführen und Spalten binden. Die [CCommand](../../data/oledb/ccommand-class.md) -Klasse und die [CTable](../../data/oledb/ctable-class.md) -Klasse instanziieren die Befehls-bzw. Tabellen Objekte. Diese Klassen werden von [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) abgeleitet, wie in der folgenden Abbildung dargestellt.

![CCommand und CTable](../../data/oledb/media/vccommandstables.gif "CCommand und CTable")<br/>
Befehls-und Tabellen Klassen

In der vorherigen Tabelle kann es sich um `TAccessor` einen beliebigen Accessortyp handeln, der in [Accessortypen](../../data/oledb/accessors-and-rowsets.md)aufgeführt ist. `TRowset` kann ein beliebiger Rowsettyp sein, der in [Rowsettypen](../../data/oledb/accessors-and-rowsets.md)aufgeführt ist. `TMultiple` Gibt den Ergebnistyp an (ein einzelnes oder mehrere Resultsets).

Mit dem [ATL-OLE DB Consumer-Assistenten](../../atl/reference/atl-ole-db-consumer-wizard.md) können Sie angeben, ob Sie ein Befehls-oder Tabellenobjekt möchten.

- Für Datenquellen ohne Befehle können Sie die- `CTable` Klasse verwenden. Im Allgemeinen verwenden Sie es für einfache Rowsets, die keine Parameter angeben und nicht mehrere Ergebnisse erfordern. Diese einfache Klasse öffnet eine Tabelle in einer Datenquelle mit einem von Ihnen angegebenen Tabellennamen.

- Bei Datenquellen, die Befehle unterstützen, können Sie `CCommand` stattdessen die-Klasse verwenden. Um einen Befehl auszuführen, müssen Sie für diese Klasse " [Öffnen](./ccommand-class.md#open) " aufzurufen. Als Alternative können Sie auch aufzurufen, `Prepare` um einen Befehl vorzubereiten, den Sie mehrmals ausführen möchten.

   `CCommand` hat drei Vorlagen Argumente: einen Accessortyp, einen Rowsettyp und einen Ergebnistyp ( `CNoMultipleResults` standardmäßig oder `CMultipleResults` ). Wenn Sie angeben `CMultipleResults` , `CCommand` unterstützt die-Klasse die `IMultipleResults` -Schnittstelle und behandelt mehrere Rowsets. Das [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) -Beispiel zeigt, wie die verschiedenen Ergebnisse behandelt werden.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)
