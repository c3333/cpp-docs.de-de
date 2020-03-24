---
title: Erfolgreiche Durchführung der OLE DB-Konformitätstests
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: eda4dccda147ddd4776bb56e649f539a7550abd1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209772"
---
# <a name="passing-ole-db-conformance-tests"></a>Erfolgreiche Durchführung der OLE DB-Konformitätstests

Damit die Anbieter konfizierer werden, stellt das Datenzugriffs-SDK eine Reihe von OLE DB Konformitätstests bereit. Die Tests überprüfen alle Aspekte Ihres Anbieters und Gewährleistung, dass Ihr Anbieter erwartungsgemäß funktioniert. Die OLE DB Konformitätstests finden Sie im Microsoft Data Access SDK. Dieser Abschnitt konzentriert sich auf Dinge, die Sie tun sollten, um die Konformitätstests zu bestehen. Weitere Informationen zum Ausführen der OLE DB Konformitätstests finden Sie im SDK.

## <a name="running-the-conformance-tests"></a>Ausführen der Konformitäts Tests

In Visual C++ 6,0 haben die OLE DB Anbieter Vorlagen eine Reihe von Verknüpfungen hinzugefügt, mit denen Sie Werte und Eigenschaften überprüfen können. Die meisten dieser Funktionen wurden als Reaktion auf die Konformitätstests hinzugefügt.

> [!NOTE]
> Sie müssen mehrere Validierungs Funktionen für Ihren Anbieter hinzufügen, um die OLE DB Konformitätstests zu übergeben.

Dieser Anbieter erfordert zwei Validierungs Routinen. Die erste Routine, `CRowsetImpl::ValidateCommandID`, ist Teil der Rowsetklasse. Sie wird beim Erstellen des Rowsets durch die Anbieter Vorlagen aufgerufen. Das Beispiel verwendet diese Routine, um Consumer mitzuteilen, dass Sie keine Indizes unterstützt. Der erste Rückruf besteht darin, `CRowsetImpl::ValidateCommandID` (Beachten Sie, dass der Anbieter die `_RowsetBaseClass` typedef verwendet, die in der Schnittstellen Zuordnung für `CCustomRowset` in der [Anbieter Unterstützung für Lesezeichen](../../data/oledb/provider-support-for-bookmarks.md)hinzugefügt wurde, sodass Sie diese lange Zeile von Vorlagen Argumenten nicht eingeben müssen). Geben Sie als nächstes DB_E_NOINDEX zurück, wenn der Index Parameter nicht NULL ist (Dies deutet darauf hin, dass der Consumer einen Index für uns verwenden möchte). Weitere Informationen zu Befehls-IDs finden Sie in der OLE DB Spezifikation und untersuchen nach `IOpenRowset::OpenRowset`.

Der folgende Code stellt die `ValidateCommandID` Validierungs Routine dar:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Die Anbieter Vorlagen wenden die `OnPropertyChanged`-Methode immer dann an, wenn jemand eine Eigenschaft in der DBPROPSET_ROWSET Gruppe ändert. Wenn Sie Eigenschaften für andere Gruppen behandeln möchten, fügen Sie diese dem entsprechenden Objekt hinzu (d. h. DBPROPSET_SESSION Überprüfungen in der `CCustomSession`-Klasse).

Der Code prüft zunächst, ob die-Eigenschaft mit einer anderen verknüpft ist. Wenn die Eigenschaft verkettet wird, wird die DBPROP_BOOKMARKS-Eigenschaft auf `True`festgelegt. Anhang C der OLE DB Spezifikation enthält Informationen zu Eigenschaften. Diese Informationen zeigen auch, ob die-Eigenschaft mit einer anderen verkettet ist.

Möglicherweise möchten Sie dem Code auch die `IsValidValue` Routine hinzufügen. Der Vorlagen Rückruf `IsValidValue`, wenn versucht wird, eine Eigenschaft festzulegen. Sie würden diese Methode überschreiben, wenn Sie zusätzliche Verarbeitungsschritte benötigen, wenn Sie einen Eigenschafts Wert festlegen. Sie können eine dieser Methoden für jeden Eigenschaften Satz festlegen.

## <a name="see-also"></a>Weitere Informationen

[Erweiterte Anbietertechniken](../../data/oledb/advanced-provider-techniques.md)
