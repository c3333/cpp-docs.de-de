---
title: Verwenden von manuellen Accessoren
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: a6c0e5236702229a61a828344ba5d0d288898aee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209325"
---
# <a name="using-manual-accessors"></a>Verwenden von manuellen Accessoren

Bei der Behandlung eines unbekannten Befehls sind vier Dinge zu tun:

- Bestimmen der Parameter

- Befehl ausführen

- Bestimmen der Ausgabespalten

- Überprüfen, ob mehrere Rückgabe-Rowsets vorhanden sind

Verwenden Sie die `CManualAccessor`-Klasse, und führen Sie die folgenden Schritte aus, um diese Schritte mit den OLE DB Consumer-Vorlagen auszuführen:

1. Öffnen Sie ein `CCommand` Objekt mit `CManualAccessor` als Vorlagen Parameter.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Fragen Sie die Sitzung nach der `IDBSchemaRowset`-Schnittstelle ab, und verwenden Sie das Prozedur Parameter-Rowset. Wenn die `IDBSchemaRowset`-Schnittstelle nicht verfügbar ist, Fragen Sie die `ICommandWithParameters`-Schnittstelle ab. Weitere Informationen finden Sie unter `GetParameterInfo`. Wenn keine der beiden Schnittstellen verfügbar ist, können Sie davon ausgehen, dass keine Parameter vorhanden sind.

1. Aufrufen Sie `AddParameterEntry` für jeden Parameter, um die Parameter hinzuzufügen und festzulegen.

1. Öffnen Sie das Rowset, und legen Sie den Parameter BIND auf **false**fest.

1. Rufen Sie `GetColumnInfo` auf, um die Ausgabespalten abzurufen. Verwenden Sie `AddBindEntry`, um der Bindung die Ausgabe Spalte hinzuzufügen.

1. Ruft `GetNextResult` auf, um zu bestimmen, ob weitere Rowsets verfügbar sind. Wiederholen Sie die Schritte 2 bis 5.

Ein Beispiel für einen manuellen Accessor finden Sie unter `CDBListView::CallProcedure` im [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) -Beispiel.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
