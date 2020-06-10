---
title: 'Gewusst wie: Implementieren der Nachverfolgung im Code'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 3d71543261021c7e20041d317401b7b7b8d0616e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621668"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Gewusst wie: Implementieren der Nachverfolgung im Code

Zum Nachverfolgen eines OLE-Elements müssen bestimmte Ereignisse behandelt werden, die mit dem Element verknüpft sind, z. b. das Klicken auf das Element oder das Aktualisieren der Ansicht des Dokuments. In allen Fällen genügt es, ein temporäres [CRectTracker](reference/crecttracker-class.md) -Objekt zu deklarieren und das Element mithilfe dieses Objekts zu bearbeiten.

Wenn ein Benutzer ein Element auswählt oder ein Objekt mit einem Menübefehl einfügt, müssen Sie die Nachverfolgung mit den richtigen Stilen initialisieren, um den Status des OLE-Elements darzustellen. In der folgenden Tabelle werden die Konventionen erläutert, die vom OCLIENT-Beispiel verwendet werden. Weitere Informationen zu diesen Stilen finden Sie unter `CRectTracker` .

### <a name="container-styles-and-states-of-the-ole-item"></a>Container Stile und-Zustände des OLE-Elements

|Anzeige Stil|Status des OLE-Elements|
|---------------------|-----------------------|
|Gepunkteter Rahmen|Das Element ist verknüpft.|
|Solid Border|Das Element ist in das Dokument eingebettet.|
|Handles zum Ändern der Größe|Aktuell ausgewähltes Element|
|Schlüpfte Rahmen|Das Element ist zurzeit aktiv.|
|Schraffurüberlagerungen-Element|Der Element Server ist offen.|

Sie können diese Initialisierung problemlos behandeln, indem Sie eine Prozedur verwenden, die den Zustand des OLE-Elements überprüft und die entsprechenden Stile festlegt. Die `SetupTracker` im OCLIENT-Beispiel gefundene Funktion veranschaulicht die nach Verfolgungs Initialisierung. Die Parameter für diese Funktion sind die Adresse des Tracker, *ptracker*; Ein Zeiger auf das Client Element, das mit dem Tracker, *pitem*;, verknüpft ist. und einen Zeiger auf ein Rechteck, *ptrueru.* Ein ausführlichere Beispiel für diese Funktion finden Sie unter MFC-OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md).

Das Codebeispiel " **setuptracker** " stellt eine einzelne Funktion dar. die Zeilen der Funktion werden durch eine Erörterung der Funktionen der Funktion vermischt:

[!code-cpp[NVC_MFCOClient#1](codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

Die Nachverfolgung wird initialisiert, indem die Mindestgröße festgelegt und die Art der Nachverfolgung gelöscht wird.

[!code-cpp[NVC_MFCOClient#2](codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

Die folgenden Zeilen überprüfen, ob das Element derzeit ausgewählt ist und ob das Element mit dem Dokument verknüpft oder darin eingebettet ist. Handles zum Ändern der Größe, die sich innerhalb des Rahmens befinden, werden dem Stil hinzugefügt, was darauf hinweist, dass das Element derzeit ausgewählt ist. Wenn das Element mit dem Dokument verknüpft ist, wird die gepunktete Rahmenart verwendet. Ein voll solider Rahmen wird verwendet, wenn das Element eingebettet ist.

[!code-cpp[NVC_MFCOClient#3](codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

Der folgende Code überlagert das Element mit einem Schraffurmuster, wenn das Element derzeit geöffnet ist.

[!code-cpp[NVC_MFCOClient#4](codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

Sie können diese Funktion dann aufrufen, wenn die Nachverfolgung angezeigt werden muss. Beispiel: Diese Funktion wird von der- `OnDraw` Funktion der Ansichts Klasse aufgerufen. Dadurch wird die Darstellung des Tracker aktualisiert, wenn die Ansicht neu gezeichnet wird. Ein umfassendes Beispiel finden Sie unter der- `CMainView::OnDraw` Funktion des MFC-OLE- [beispieloclient](../overview/visual-cpp-samples.md).

In Ihrer Anwendung werden Ereignisse, die nach Verfolgungs Code erfordern, z. b. die Änderung der Größe, das Verschieben oder das Erkennen von Treffer, ausgelöst. Diese Aktionen geben in der Regel an, dass versucht wird, das Element zu erfassen oder zu verschieben. In diesen Fällen müssen Sie entscheiden, was gepackt wurde: ein Handle zum Ändern der Größe oder ein Teil des Rahmens zwischen Handles zur Größenänderung. Der `OnLButtonDown` Nachrichten Handler ist ein guter Ausgangspunkt, um die Position der Maus in Bezug auf das Element zu testen. Führen Sie einen-Rückruf aus `CRectTracker::HitTest` . Wenn der Test etwas anderes zurückgibt `CRectTracker::hitOutside` , wird die Größe des Elements geändert oder verschoben. Daher sollten Sie einen Rückruf für die Member- `Track` Funktion durchführen. Ein umfassendes Beispiel finden Sie unter der `CMainView::OnLButtonDown` Funktion im MFC-OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md) .

Die- `CRectTracker` Klasse stellt mehrere verschiedene Cursor Formen bereit, mit denen angegeben wird, ob ein Verschiebe-, größenwechsel-oder Zieh Vorgang stattfindet. Um dieses Ereignis zu behandeln, überprüfen Sie, ob das Element, das derzeit unter der Maus ist, ausgewählt ist. Wenn dies der Fall ist, führen Sie einen-Rückruf aus `CRectTracker::SetCursor` , oder nennen Sie den Standard Handler. Das folgende Beispiel basiert auf dem MFC-OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>Siehe auch

[Tracker: Implementieren von Trackern in einer OLE-Anwendung](trackers-implementing-trackers-in-your-ole-application.md)
