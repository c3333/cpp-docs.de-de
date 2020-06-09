---
title: Optimieren der Steuerelementdarstellung
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 17cb7318e667fe4e16416d51e7e7fba02553cfe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621017"
---
# <a name="optimizing-control-drawing"></a>Optimieren der Steuerelementdarstellung

Wenn ein Steuerelement angewiesen wird, sich in einen vom Container bereitgestellten Gerätekontext zu zeichnen, wählt es normalerweise GDI-Objekte (z. b. Stifte, Pinsel und Schriftarten) in den Gerätekontext aus, führt seine Zeichnungsvorgänge aus und stellt die vorherigen GDI-Objekte wieder her. Wenn der Container mehrere Steuerelemente enthält, die in denselben Gerätekontext gezeichnet werden sollen, und jedes Steuerelement die erforderlichen GDI-Objekte auswählt, kann die Zeit gespart werden, wenn die Steuerelemente zuvor ausgewählte Objekte nicht einzeln wiederherstellen. Nachdem alle Steuerelemente gezeichnet wurden, kann der Container die ursprünglichen Objekte automatisch wiederherstellen.

Um zu ermitteln, ob ein Container dieses Verfahren unterstützt, kann ein Steuerelement die [COleControl:: IsOptimizedDraw](reference/colecontrol-class.md#isoptimizeddraw) -Member-Funktion aufrufen. Wenn diese Funktion " **true**" zurückgibt, kann das Steuerelement den normalen Schritt der Wiederherstellung der zuvor ausgewählten Objekte überspringen.

Nehmen Sie ein Steuerelement mit der folgenden (nicht optimierten) `OnDraw` Funktion:

[!code-cpp[NVC_MFC_AxOpt#15](codesnippet/cpp/optimizing-control-drawing_1.cpp)]

Der Stift und der Pinsel in diesem Beispiel sind lokale Variablen, d. h., ihre Dekonstruktoren werden aufgerufen, wenn Sie den Gültigkeitsbereich verlassen (wenn die `OnDraw` Funktion beendet wird). Die dektoren versuchen, die entsprechenden GDI-Objekte zu löschen. Sie sollten jedoch nicht gelöscht werden, wenn Sie planen, Sie bei der Rückgabe von in den Gerätekontext auszuwählen `OnDraw` .

Um zu verhindern, dass [CPen](reference/cpen-class.md) -und [CBrush](reference/cbrush-class.md) -Objekte zerstört werden `OnDraw` , wenn abgeschlossen ist, speichern Sie Sie in Element Variablen anstelle von lokalen Variablen. Fügen Sie in der Klassen Deklaration des Steuer Elements Deklarationen für zwei neue Element Variablen hinzu:

[!code-cpp[NVC_MFC_AxOpt#16](codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](codesnippet/cpp/optimizing-control-drawing_3.h)]

Anschließend kann die `OnDraw` Funktion wie folgt umgeschrieben werden:

[!code-cpp[NVC_MFC_AxOpt#18](codesnippet/cpp/optimizing-control-drawing_4.cpp)]

Bei dieser Vorgehensweise wird die Erstellung des Stifts und Pinsels vermieden, wenn `OnDraw` aufgerufen wird. Die Geschwindigkeitsverbesserung umfasst die Kosten für die Wartung zusätzlicher Instanzdaten.

Wenn sich die ForeColor-Eigenschaft oder die BackColor-Eigenschaft ändert, muss der Stift oder Pinsel erneut erstellt werden. Überschreiben Sie zu diesem Zweck die [OnForeColorChanged](reference/colecontrol-class.md#onforecolorchanged) -und [OnBackColorChanged](reference/colecontrol-class.md#onbackcolorchanged) -Member-Funktionen:

[!code-cpp[NVC_MFC_AxOpt#19](codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Um zum Schluss unnötige Aufrufe zu vermeiden `SelectObject` , ändern Sie `OnDraw` wie folgt:

[!code-cpp[NVC_MFC_AxOpt#20](codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente: Optimierung](mfc-activex-controls-optimization.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)<br/>
[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelement-Assistent](reference/mfc-activex-control-wizard.md)<br/>
[MFC-ActiveX-Steuerelemente: Darstellen eines ActiveX-Steuerelements](mfc-activex-controls-painting-an-activex-control.md)
