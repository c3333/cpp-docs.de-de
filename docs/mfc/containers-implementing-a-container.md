---
title: 'Container: Implementieren eines Containers'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ba8d4aea6b69fdbfeedfba59449d0d30433eb94
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623226"
---
# <a name="containers-implementing-a-container"></a>Container: Implementieren eines Containers

In diesem Artikel wird das Verfahren zum Implementieren eines Containers zusammengefasst, und Sie werden auf andere Artikel verwiesen, die Ausführlichere Erläuterungen zum Implementieren von Containern bereitstellen. Außerdem werden einige optionale OLE-Funktionen aufgelistet, die Sie implementieren können, sowie die Artikel, in denen diese Features beschrieben werden.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>So bereiten Sie die von CWinApp abgeleitete Klasse vor

1. Initialisieren Sie die OLE-Bibliotheken, indem Sie `AfxOleInit` in der `InitInstance` Member-Funktion aufrufen.

1. `CDocTemplate::SetContainerInfo`Wird in aufgerufen `InitInstance` , um die Menü-und Zugriffstasten Ressourcen zuzuweisen, die verwendet werden, wenn ein eingebettetes Element direkt aktiviert wird. Weitere Informationen zu diesem Thema finden Sie unter [Activation (Aktivierung](activation-cpp.md)).

Diese Features werden automatisch bereitgestellt, wenn Sie den MFC-Anwendungs-Assistenten verwenden, um eine Containeranwendung zu erstellen. Siehe [Erstellen eines MFC-exe-Programms](reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>So bereiten Sie die Ansichts Klasse vor

1. Behalten Sie die Nachverfolgung ausgewählter Elemente, indem Sie einen Zeiger oder eine Liste von Zeigern, wenn Sie die Mehrfachauswahl unterstützen, für die ausgewählten Elemente beibehalten. Die `OnDraw` Funktion muss alle OLE-Elemente zeichnen.

1. `IsSelected`Überschreiben Sie, um zu überprüfen, ob das an es übergebenen Element derzeit ausgewählt ist

1. Implementieren Sie einen Meldungs `OnInsertObject` Handler, um das Dialogfeld **Objekt einfügen** anzuzeigen.

1. Implementieren `OnSetFocus` Sie einen Nachrichten Handler, um den Fokus von der Ansicht auf ein direkt aktives OLE Embedded-Element zu übertragen.

1. Implementieren Sie einen Meldungs `OnSize` Handler, um ein OLE Embedded-Element zu informieren, dass es das Rechteck ändern muss, um die Größe der enthaltenden Ansicht widerzuspiegeln.

Da die Implementierung dieser Features von einer Anwendung zur nächsten abweicht, bietet der Anwendungs-Assistent nur eine einfache Implementierung. Sie müssen diese Funktionen wahrscheinlich anpassen, damit Ihre Anwendung ordnungsgemäß funktioniert. Ein Beispiel hierfür finden Sie im [Container](../overview/visual-cpp-samples.md) Beispiel.

#### <a name="to-handle-embedded-and-linked-items"></a>So verarbeiten Sie eingebettete und verknüpfte Elemente

1. Leiten Sie eine Klasse von [COleClientItem](reference/coleclientitem-class.md)ab. Objekte dieser Klasse stellen Elemente dar, die in das OLE-Dokument eingebettet oder mit diesem verknüpft wurden.

1. Überschreiben Sie `OnChange` , `OnChangeItemPosition` und `OnGetItemPosition` . Diese Funktionen behandeln das anpassen, positionieren und Ändern von eingebetteten und verknüpften Elementen.

Der Anwendungs-Assistent leitet die-Klasse für Sie ab, aber Sie müssen wahrscheinlich `OnChange` und die anderen darin aufgeführten Funktionen in Schritt 2 des vorherigen Verfahrens überschreiben. Die Gerüst Implementierungen müssen für die meisten Anwendungen angepasst werden, da diese Funktionen von einer Anwendung zur nächsten implementiert werden. Beispiele hierfür finden Sie in den MFC-Beispielen [DRAWCLI](../overview/visual-cpp-samples.md) und [Container](../overview/visual-cpp-samples.md).

Zur Unterstützung von OLE müssen Sie der Menüstruktur der Containeranwendung eine Reihe von Elementen hinzufügen. Weitere Informationen hierzu finden Sie unter [Menüs und Ressourcen: Container Ergänzungen](menus-and-resources-container-additions.md).

Möglicherweise möchten Sie auch einige der folgenden Features in ihrer Containeranwendung unterstützen:

- Direkte Aktivierung beim Bearbeiten eines eingebetteten Elements.

   Weitere Informationen finden Sie unter [Activation (Aktivierung](activation-cpp.md)).

- Erstellung von OLE-Elementen durchziehen und Ablegen einer Auswahl aus einer Serveranwendung.

   Weitere Informationen finden Sie unter [OLE Drag](drag-and-drop-ole.md)& amp; Drop.

- Links zu eingebetteten Objekten oder Kombinationen von Container-/Server-Anwendungen.

   Weitere Informationen finden Sie unter [Container: Erweiterte Funktionen](containers-advanced-features.md).

## <a name="see-also"></a>Siehe auch

[Container](containers.md)<br/>
[Container: Clientelemente](containers-client-items.md)
