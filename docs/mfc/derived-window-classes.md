---
title: Abgeleitete Fensterklassen
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: c84284b765e740fa0a13972e9902e7737e15bbab
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623175"
---
# <a name="derived-window-classes"></a>Abgeleitete Fensterklassen

Sie können Fenster direkt aus [CWnd](reference/cwnd-class.md)erstellen oder neue Fenster Klassen von ableiten `CWnd` . Im Allgemeinen erstellen Sie eigene, benutzerdefinierte Fenster auf diese Weise. Allerdings werden die meisten Fenster, die in einem Frameworkprogramm verwendet werden, stattdessen aus einer der von MFC bereitgestellten, von `CWnd` abgeleiteten Rahmenfensterklassen erstellt.

## <a name="frame-window-classes"></a>Klassen für Rahmenfenster

[CFrameWnd](reference/cframewnd-class.md)<br/>
Wird für SDI-Rahmenfenster verwendet, um ein einzelnes Dokument und dessen Ansicht zu gestalten. Das Rahmenfenster ist sowohl das Hauptrahmenfenster für die Anwendung als auch das Rahmenfenster für das aktuelle Dokument.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Wird als Hauptrahmenfenster für MDI-Anwendungen verwendet. Das Hauptrahmenfenster ist ein Container für alle MDI-Dokumentfenster und gibt seine Menüleiste für diese frei. Ein MDI-Rahmenfenster ist ein Fenster der obersten Ebene, das auf dem Desktop angezeigt wird.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Wird für einzelne Dokumente verwendet, die in einem MDI-Hauptrahmenfenster geöffnet werden. Jedes Dokument und seine Ansicht werden durch ein untergeordnetes MDI-Rahmenfenster eingerahmt, das im MDI-Hauptrahmenfenster enthalten ist. Ein untergeordnetes MDI-Fenster sieht einem typischen Rahmenfenster sehr ähnlich. Es befindet sich aber nicht auf dem Desktop, sondern bleibt in einem MDI-Rahmenfenster. Dem untergeordneten MDI-Fenster fehlt allerdings eine eigene Menüleiste, sodass es die Menüleiste des MDI-Rahmenfensters mitverwenden muss, in dem es enthalten ist.

Weitere Informationen finden Sie unter [Rahmen Fenster](frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Andere Fensterklassen, die von "CWnd" abgeleitet werden

Zusätzlich zu den Rahmenfenstern werden mehrere andere Hauptkategorien von Fenstern von `CWnd` abgeleitet:

*Ansichten*<br/>
Sichten werden mithilfe der von `CWnd` abgeleiteten Klasse [CView](reference/cview-class.md) (oder einer der abgeleiteten Klassen) erstellt. Eine Ansicht wird an ein Dokument angefügt und dient als Vermittler zwischen dem Dokument und dem Benutzer. Eine Ansicht ist ein untergeordnetes Fenster (kein untergeordnetes MDI-Fenster), das normalerweise den Clientbereich eines SDI-Rahmenfensters oder eines untergeordneten MDI-Rahmenfensters ausfüllt (oder den Teil des Clientbereichs, der nicht von einer Symbolleiste und/oder einer Statusleiste abgedeckt ist).

*Dialog Felder*<br/>
Dialog Felder werden mithilfe der von `CWnd` abgeleiteten Klasse [CDialog](reference/cdialog-class.md)erstellt.

*Formulare*<br/>
Formular Ansichten, die auf Dialogfeld Vorlagen Ressourcen basieren, z. b. Dialogfelder, werden mithilfe von Klassen [CFormView](reference/cformview-class.md), [CRecordView](reference/crecordview-class.md)oder [CDaoRecordView](reference/cdaorecordview-class.md)erstellt.

*Steuerelemente*<br/>
Steuerelemente wie Schaltflächen, Listenfelder und Kombinationsfelder werden mithilfe anderer Klassen erstellt, die von `CWnd` abgeleitet werden. Siehe [Steuerungs Themen](controls-mfc.md).

*Steuerleisten*<br/>
Untergeordnete Fenster, die Steuerelemente enthalten. Dazu zählen beispielsweise Symbolleisten und Statusleisten. Siehe [Steuer leisten](control-bars.md).

## <a name="window-class-hierarchy"></a>Fensterklassenhierarchie

Weitere Informationen finden Sie im [MFC-Hierarchie Diagramm](hierarchy-chart.md) in der *MFC-Referenz*. Sichten werden unter [Dokument-/Ansichtarchitektur](document-view-architecture.md)erläutert. Dialogfelder werden in [Dialogfeldern](dialog-boxes.md)erläutert.

## <a name="creating-your-own-special-purpose-window-classes"></a>Erstellen eigener Fensterklassen für spezielle Zwecke

Neben den Fensterklassen, die von der Klassenbibliothek bereitgestellt werden, benötigen Sie möglicherweise untergeordnete Fenster für besondere Zwecke. Erstellen Sie zum Erstellen eines solchen Fensters eine eigene, von [CWnd](reference/cwnd-class.md)abgeleitete Klasse, und machen Sie Sie zu einem untergeordneten Fenster eines Frames oder einer Ansicht. Bedenken Sie, dass das Framework den Umfang des Clientbereichs von einem Dokumentrahmenfenster verwaltet. Die Großteil des Clientbereichs wird durch eine Ansicht verwaltet, aber andere Fenster, z. B. Steuerleisten oder eigene, benutzerdefinierte Fenster, können sich den Platz mit der Ansicht teilen. Sie müssen möglicherweise mit den Mechanismen in den Klassen [CView](reference/cview-class.md) und [CControlBar](reference/ccontrolbar-class.md) interagieren, um untergeordnete Fenster im Client Bereich eines Rahmen Fensters zu positionieren.

Beim [Erstellen von Windows](creating-windows.md) wird die Erstellung von Fenster Objekten und den von Ihnen verwalteten Fenstern erläutert.

## <a name="see-also"></a>Siehe auch

[Fensterobjekte](window-objects.md)
