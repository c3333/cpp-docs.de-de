---
title: 'Server: Implementieren eines In-Place-Frame-Fensters'
ms.date: 09/09/2019
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: a082afe141a21e4175886f13a26043694ac0d426
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230466"
---
# <a name="servers-implementing-in-place-frame-windows"></a>Server: Implementieren eines In-Place-Frame-Fensters

In diesem Artikel wird erläutert, was Sie tun müssen, um direkte Rahmen Fenster in Ihrer Anwendung für die visuelle Bearbeitung zu implementieren, wenn Sie die Serveranwendung nicht mit dem Anwendungs-Assistenten erstellen. Anstelle des in diesem Artikel beschriebenen Verfahrens können Sie eine vorhandene direkte Frame Fenster Klasse entweder aus einer vom Anwendungs Assistenten generierten Anwendung oder aus einem mit Visual C++ bereitgestellten Beispiel verwenden.

#### <a name="to-declare-an-in-place-frame-window-class"></a>So deklarieren Sie eine direkte Frame-Window-Klasse

1. Leiten Sie eine direkte Frame Fenster Klasse von ab `COleIPFrameWnd` .

   - Verwenden Sie das DECLARE_DYNCREATE-Makro in der Klassen Header Datei.

   - Verwenden Sie das IMPLEMENT_DYNCREATE-Makro in der Klassen Implementierungs Datei (. cpp). Dadurch können Objekte dieser Klasse vom Framework erstellt werden.

1. Deklarieren Sie einen `COleResizeBar` Member in der Frame-Window-Klasse. Dies ist erforderlich, wenn Sie die direkte Größe von Server Anwendungen unterstützen möchten.

   Deklarieren Sie einen `OnCreate` Nachrichten Handler (mit dem [Klassen-Assistenten](reference/mfc-class-wizard.md)), und rufen `Create` Sie für den `COleResizeBar` Member auf, sofern Sie ihn definiert haben.

1. Wenn Sie über eine Symbolleiste verfügen, deklarieren Sie einen `CToolBar` Member in der Frame-Window-Klasse.

   Überschreiben `OnCreateControlBars` Sie die Member-Funktion, um eine Symbolleiste zu erstellen, wenn der Server aktiv ist. Beispiel:

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   Weitere Informationen finden Sie in der Erörterung dieses Codes nach Schritt 5.

1. Fügen Sie die Header Datei für diese direkte Frame-Window-Klasse in die Datei "Main. cpp" ein.

1. `InitInstance`Nennen Sie in für die Anwendungsklasse die `SetServerInfo` -Funktion des Dokumentvorlagen Objekts, um die Ressourcen und das direkte Rahmen Fenster anzugeben, das bei der geöffneten und direkten Bearbeitung verwendet werden soll.

Die Reihe von Funktionsaufrufen in der- **`if`** Anweisung erstellt die Symbolleiste aus den Ressourcen, die der Server bereitgestellt hat. An diesem Punkt ist die Symbolleiste Teil der Fenster Hierarchie des Containers. Da diese Symbolleiste von abgeleitet ist `CToolBar` , übergibt Sie die Nachrichten an ihren Besitzer, das Rahmen Fenster der Containeranwendung, es sei denn, Sie ändern den Besitzer. Aus diesem Grund ist der-Rückruf `SetOwner` erforderlich. Mit diesem Befehl wird das Fenster geändert, in dem Befehle an das direkte Rahmen Fenster des Servers gesendet werden, sodass die Nachrichten an den Server übermittelt werden. Dies ermöglicht es dem Server, auf Vorgänge auf der Symbolleiste zu reagieren, die er bereitstellt.

Die ID für die Symbolleisten-Bitmap sollte mit den anderen direkten Ressourcen identisch sein, die in der Serveranwendung definiert sind. Weitere Informationen finden Sie unter [Menüs und Ressourcen: Server Ergänzungen](../mfc/menus-and-resources-server-additions.md) .

Weitere Informationen finden Sie unter [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md)und [CDocTemplate:: setserverinfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) in der *Klassen Bibliotheks Referenz*.

## <a name="see-also"></a>Weitere Informationen

[Server](../mfc/servers.md)<br/>
[Server: Implementieren eines Servers](../mfc/servers-implementing-a-server.md)<br/>
[Server: Implementieren von Server Dokumenten](../mfc/servers-implementing-server-documents.md)<br/>
[Server: Server Elemente](../mfc/servers-server-items.md)
