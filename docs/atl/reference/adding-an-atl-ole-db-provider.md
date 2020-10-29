---
title: Hinzufügen eines ATL-OLE DB-Anbieters
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: e593fdbd1c8c48a381cb2941971ebe4e0148965d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923776"
---
# <a name="adding-an-atl-ole-db-provider"></a>Hinzufügen eines ATL-OLE DB-Anbieters

::: moniker range="msvc-160"

Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Verwenden Sie diesen Assistenten, um einem Projekt einen ATL-OLE DB-Anbieter hinzuzufügen. Ein ATL-OLE DB-Anbieter besteht aus Datenquellen-, Sitzungs-, Befehls- und Rowsetklassen. Das Projekt muss als eine ATL-COM-Anwendung erstellt werden.

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>So fügen Sie Ihrem Projekt einen ATL-OLE DB-Anbieter hinzu

1. Klicken Sie in der **Klassenansicht** mit der rechten Maustaste auf das Projekt. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie danach auf **Klasse hinzufügen** .

1. Doppelklicken Sie im Ordner **Visual C++** auf das Symbol **ATL-OLE DB-Anbieter** , oder wählen Sie es aus. Klicken Sie dann auf **Öffnen** .

   Der ATL-OLE DB-Anbieter-Assistent wird geöffnet.

1. Definieren Sie die Einstellungen wie in [ATL-OLE DB-Anbieter-Assistent](../../atl/reference/atl-ole-db-provider-wizard.md) beschrieben.

1. Klicken Sie auf **Fertig stellen** , um den Assistenten zu schließen. Hierdurch wird der neu erstellte OLE DB-Anbietercode in Ihr Projekt eingefügt.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)
