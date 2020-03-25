---
title: Erstellen eines Projekts für den Anbieter
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: f2ff42ba8a2e908f672db7e96fc9f24f51a1fd9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211405"
---
# <a name="creating-a-project-for-the-provider"></a>Erstellen eines Projekts für den Anbieter

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>So erstellen Sie ein Projekt, in dem sich der OLE DB-Anbieter befindet

1. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

1. Klicken Sie im Bereich **Projekttypen** auf den Ordner **installiert** > **Visual C++**  > **MFC/ATL** . Klicken Sie im Bereich **Vorlagen** auf **ATL-Projekt**.

    > [!NOTE]
    > In früheren Versionen von Visual Studio finden Sie den Projekttyp unter **installierte** > **Vorlagen** >  **C++ Visual** > **ATL**.

1. Geben Sie im Feld **Name** einen Namen für das Projekt ein, und klicken Sie dann auf **OK**.

   Der **ATL-Projekt-Assistent** wird angezeigt.

1. Wählen Sie im **ATL-Projekt-Assistenten**die Option **Dynamic Link Library (dll)** als **Anwendungstyp**aus.

1. Klicken Sie auf **Fertig stellen**.

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines OLE DB-Anbieters](../../data/oledb/creating-an-ole-db-provider.md)
