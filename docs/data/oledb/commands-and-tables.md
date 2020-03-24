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
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211522"
---
# <a name="commands-and-tables"></a>Befehle und Tabellen

Befehle und Tabellen ermöglichen den Zugriff auf Rowsets. Das heißt, dass Sie Rowsets öffnen, Befehle ausführen und Spalten binden. Die [CCommand](../../data/oledb/ccommand-class.md) -Klasse und die [CTable](../../data/oledb/ctable-class.md) -Klasse instanziieren die Befehls-bzw. Tabellen Objekte. Diese Klassen werden von [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) abgeleitet, wie in der folgenden Abbildung dargestellt.

![CCommand und CTable](../../data/oledb/media/vccommandstables.gif "CCommand und CTable")<br/>
Befehls-und Tabellen Klassen

In der obigen Tabelle können `TAccessor` beliebige Accessortypen sein, die in [Zugriffsmethoden Typen](../../data/oledb/accessors-and-rowsets.md)aufgeführt sind. `TRowset` kann jeder in [Rowsettypen](../../data/oledb/accessors-and-rowsets.md)aufgelistete Rowsettyp sein. `TMultiple` gibt den Ergebnistyp an (ein einzelnes oder mehrere Resultsets).

Mit dem [ATL-OLE DB Consumer-Assistenten](../../atl/reference/atl-ole-db-consumer-wizard.md) können Sie angeben, ob Sie ein Befehls-oder Tabellenobjekt möchten.

- Für Datenquellen ohne Befehle können Sie die `CTable`-Klasse verwenden. Im Allgemeinen verwenden Sie es für einfache Rowsets, die keine Parameter angeben und nicht mehrere Ergebnisse erfordern. Diese einfache Klasse öffnet eine Tabelle in einer Datenquelle mit einem von Ihnen angegebenen Tabellennamen.

- Bei Datenquellen, die Befehle unterstützen, können Sie stattdessen die `CCommand`-Klasse verwenden. Um einen Befehl auszuführen, müssen Sie für diese Klasse " [Öffnen](../../data/oledb/ccommand-open.md) " aufzurufen. Als Alternative können Sie `Prepare` aufzurufen, um einen Befehl vorzubereiten, den Sie mehrmals ausführen möchten.

   `CCommand` hat drei Vorlagen Argumente: einen Accessortyp, einen Rowsettyp und einen Ergebnistyp (standardmäßig`CNoMultipleResults`, oder `CMultipleResults`). Wenn Sie `CMultipleResults`angeben, unterstützt die `CCommand`-Klasse die `IMultipleResults`-Schnittstelle und verarbeitet mehrere Rowsets. Das [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) -Beispiel zeigt, wie die verschiedenen Ergebnisse behandelt werden.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)
