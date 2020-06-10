---
title: 'Gewusst wie: Hinzufügen von Menüband-Steuerelementen und Ereignishandlern'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 560524c36dbf57faec3b4b6372cade047f9fe7de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618485"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Gewusst wie: Hinzufügen von Menüband-Steuerelementen und Ereignishandlern

Menü Band Steuerelemente sind Elemente, wie z. b. Schaltflächen und Kombinations Felder, die Sie zu Panels hinzufügen. Panels sind Bereiche der Menü Band Leiste, die eine Gruppe verwandter Steuerelemente anzeigen.

In diesem Thema öffnen Sie den Menüband-Designer, fügen eine Schaltfläche hinzu und verknüpfen dann ein Ereignis, das "Hallo Welt" anzeigt.

### <a name="to-open-the-ribbon-designer"></a>So öffnen Sie den Menüband-Designer

1. Klicken Sie in Visual Studio im Menü **Ansicht** auf **Ressourcenansicht**.

1. Doppelklicken Sie in **Ressourcenansicht**auf die Menüband-Ressource, um Sie auf der Entwurfs Oberfläche anzuzeigen.

### <a name="to-add-a-button-and-an-event-handler"></a>So fügen Sie eine Schaltfläche und einen Ereignis Handler hinzu

1. Klicken Sie in der **Symbolleiste**auf die **Schalt** Fläche, und ziehen Sie Sie in ein Panel auf der Entwurfs Oberfläche.

1. Klicken Sie mit der rechten Maustaste auf die Schaltfläche und dann auf **Ereignis Handler hinzufügen**.

1. Bestätigen Sie im **ereignishandlerassistenten**die Standardeinstellungen, und klicken Sie auf **Hinzufügen und bearbeiten**. Weitere Informationen finden Sie unter [ereignishandlerassistent](../ide/event-handler-wizard.md).

1. Fügen Sie im Code-Editor der Handlerfunktion den folgenden Code hinzu:

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>Siehe auch

[Ribbongadgets-Beispiel: Menüband-Gadgets-Anwendung](../overview/visual-cpp-samples.md)<br/>
[Menüband-Designer (MFC)](ribbon-designer-mfc.md)
