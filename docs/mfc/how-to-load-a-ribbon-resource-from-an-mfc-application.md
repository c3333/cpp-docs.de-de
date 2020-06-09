---
title: 'Gewusst wie: Laden einer Menübandressource aus einer MFC-Anwendung'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 47a3b94bbcb14c6c2923524db1f6a83b687e50e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626401"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Gewusst wie: Laden einer Menübandressource aus einer MFC-Anwendung

Um die Menü Band Ressource in Ihrer Anwendung zu verwenden, ändern Sie die Anwendung, um die Menü Band Ressource zu laden.

### <a name="to-load-a-ribbon-resource"></a>So laden Sie eine Menü Band Ressource

1. Deklarieren Sie das- `Ribbon Control` Objekt in der- `CMainFrame` Klasse.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. `CMainFrame::OnCreate`Erstellen und initialisieren Sie in das Menüband-Steuerelement in.

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>Siehe auch

[Menüband-Designer (MFC)](ribbon-designer-mfc.md)
