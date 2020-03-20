---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: 61bd60b63490303c65729843c3c0351a570a8056
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545726"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

Die `CCustomCommand`-Klasse ist die Implementierung für das Provider-Befehls Objekt. Sie stellt die Implementierung für die Schnittstellen `IAccessor`, `ICommandText`und `ICommandProperties` bereit. Die `IAccessor`-Schnittstelle ist identisch mit der-Schnittstelle im Rowset. Das Command-Objekt verwendet den-Accessor, um Bindungen für Parameter anzugeben. Das Rowsetobjekt verwendet diese zum Angeben von Bindungen für Ausgabespalten. Die `ICommandText`-Schnittstelle ist eine nützliche Möglichkeit, einen Befehl textutional anzugeben. Dieses Beispiel verwendet die `ICommandText`-Schnittstelle später, wenn benutzerdefinierten Code hinzugefügt wird. Außerdem wird die `ICommand::Execute`-Methode überschrieben. Die `ICommandProperties`-Schnittstelle verarbeitet alle Eigenschaften für die Befehls-und Rowsetobjekte.

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

Die `IAccessor`-Schnittstelle verwaltet alle Bindungen, die in Befehlen und Rowsets verwendet werden. Der Consumer ruft `IAccessor::CreateAccessor` mit einem Array von `DBBINDING` Strukturen auf. Jede `DBBINDING` Struktur enthält Informationen darüber, wie die Spalten Bindungen behandelt werden sollen (z. b. Typ und Länge). Der Anbieter empfängt die Strukturen und bestimmt dann, wie die Daten übertragen werden sollen und ob Konvertierungen erforderlich sind. Die `IAccessor`-Schnittstelle wird im Command-Objekt verwendet, um alle Parameter im Befehl zu verarbeiten.

Das Command-Objekt stellt außerdem eine Implementierung von `IColumnsInfo`bereit. OLE DB erfordert die `IColumnsInfo`-Schnittstelle. Die-Schnittstelle ermöglicht dem Consumer das Abrufen von Informationen zu Parametern aus dem Befehl. Das Rowsetobjekt verwendet die `IColumnsInfo`-Schnittstelle, um Informationen über die Ausgabespalten an den Anbieter zurückzugeben.

Der Anbieter enthält auch eine Schnittstelle mit dem Namen `IObjectWithSite`. Die `IObjectWithSite`-Schnittstelle wurde in ATL 2,0 implementiert und ermöglicht dem Implementierer, Informationen über sich selbst an das untergeordnete Element zu übergeben. Das Command-Objekt verwendet die `IObjectWithSite` Informationen, um generierte Rowsetobjekte darüber zu informieren, wer Sie erstellt hat.

## <a name="see-also"></a>Siehe auch

[Vom Anbieter-Assistenten generierte Dateien](../../data/oledb/provider-wizard-generated-files.md)