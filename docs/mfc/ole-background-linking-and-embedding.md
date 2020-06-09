---
title: 'OLE-Hintergrund: Verlinken und Einbetten'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 6b6032d2e772728495d4ddb1dbfaa5daf7348b60
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619886"
---
# <a name="ole-background-linking-and-embedding"></a>OLE-Hintergrund: Verlinken und Einbetten

Wenn Sie den Befehl Einfügen in einer Containeranwendung verwenden, kann eine eingebettete Komponente oder ein eingebettetes Element erstellt werden. Die Quelldaten für ein eingebettetes Element werden als Teil des OLE-Dokuments gespeichert, in dem es enthalten ist. Auf diese Weise kann eine Dokument Datei für ein textprozessordokument Text enthalten und auch Bitmaps, Diagramme, Formeln oder beliebige andere Datentypen enthalten.

OLE bietet eine weitere Möglichkeit zum Einbinden von Daten aus einer anderen Anwendung: das Erstellen einer verknüpften Komponente, eines verknüpften Elements oder eines Links. Die Schritte zum Erstellen eines verknüpften Elements ähneln denen zum Erstellen eines eingebetteten Elements, mit dem Unterschied, dass Sie den Befehl Link einfügen anstelle des Befehls einfügen verwenden. Anders als bei einer eingebetteten Komponente speichert eine verknüpfte Komponente einen Pfad zu den ursprünglichen Daten, die sich häufig in einer separaten Datei befinden.

Wenn Sie z. b. in einem textprozessordokument arbeiten und ein verknüpftes Element für einige tabellenkalkulationstabellen erstellen, werden die Daten für das verknüpfte Element im ursprünglichen Tabellen Dokument gespeichert. Das textprozessordokument enthält nur die Informationen, die angeben, wo das Element gefunden werden kann, d. h., es enthält einen Link zum ursprünglichen Tabellen Dokument. Wenn Sie auf die Zellen doppelklicken, wird die Anwendung für die Kalkulations Tabelle gestartet, und das ursprüngliche Tabellen Dokument wird aus dem Speicherort geladen.

Jedem OLE-Element, ob eingebettet oder verknüpft, ist ein Typ zugeordnet, der auf der Anwendung basiert, die es erstellt hat. Beispielsweise ist ein Microsoft-Pinsel Element ein Elementtyp, und ein Microsoft Excel-Element ist ein anderer Typ. Einige Anwendungen können jedoch mehr als einen Elementtyp erstellen. Beispielsweise kann Microsoft Excel Arbeitsblatt Elemente, Diagramm Elemente und Makro Blatt Elemente erstellen. Jedes dieser Elemente kann durch das System mithilfe eines Klassen Bezeichners oder einer **CLSID**eindeutig identifiziert werden.

## <a name="see-also"></a>Siehe auch

[OLE-Hintergrund](ole-background.md)<br/>
[OLE-Hintergrund: Container und Server](ole-background-containers-and-servers.md)<br/>
[Container: Clientelemente](containers-client-items.md)<br/>
[Server: Serverelemente](servers-server-items.md)
