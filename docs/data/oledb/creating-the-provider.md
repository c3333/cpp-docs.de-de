---
title: Erstellen des Anbieters
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 5a24245ae19fc6fa2a66d4bf102765b712b4cf5c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921502"
---
# <a name="creating-the-provider"></a>Erstellen des Anbieters

::: moniker range="msvc-160"

Der ATL-OLE DB-Anbieter-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>So erstellen Sie mit dem ATL-OLE DB-Anbieter-Assistenten einen OLE DB-Anbieter

1. Klicken Sie mit der rechten Maustaste auf das Projekt.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Klasse hinzufügen** .

1. Wählen Sie im Dialogfeld **Klasse hinzufügen** unter **Installiert** > **Visual C++** > **ATL** das Symbol **ATL-OLE DB-Anbieter** aus, und klicken Sie dann auf **Öffnen** .

1. Geben Sie im **ATL-OLE DB-Anbieter-Assistenten** im Feld **Kurzname** einen Kurznamen für Ihren Anbieter ein. In den folgenden Themen wird der Kurzname *Custom* verwendet, aber Sie können einen anderen Namen verwenden. Die weiteren Namensfelder werden basierend auf dem eingegebenen Namen automatisch aufgefüllt.

1. Bearbeiten Sie bei Bedarf die weiteren Namensfelder. Zusätzlich zu den Objekt- und Dateinamen können Sie folgende Felder bearbeiten:

   - **Coclass** : der Name, der von com zum Erstellen des Anbieters verwendet wird.

   - **ProgID** : der programmatische Bezeichner, bei dem es sich um eine Text Zeichenfolge handelt, die anstelle einer GUID verwendet werden kann.

   - **Version** : wird zusammen mit der ProgID und der Co-Klasse verwendet, um eine Versions abhängige Programm-ID zu generieren.

1. Klicken Sie auf **Fertig stellen** .

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Erstellen eines OLE DB Anbieters](../../data/oledb/creating-an-ole-db-provider.md)
