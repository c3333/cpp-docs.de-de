---
title: 'Gewusst wie: Umwandeln eines vorhandenen MFC-Menübands in eine Menübandressource'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 56f36c977453d338b9e9bbd2462c1a8830ffe258
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620053"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Gewusst wie: Umwandeln eines vorhandenen MFC-Menübands in eine Menübandressource

Menü Band Ressourcen sind einfacher zu visualisieren, zu ändern und zu verwalten als manuell codierte Multifunktionsleisten. In diesem Thema wird beschrieben, wie ein manuell codiertes Menüband in einem MFC-Projekt in eine Menü Band Ressource konvertiert wird.

Sie müssen über ein vorhandenes MFC-Projekt verfügen, das über Code verfügt, der die MFC-Menü Band Klassen verwendet, z. b. [CMFCRibbonBar-Klasse](reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>So konvertieren Sie ein MFC-Menüband in eine Menü Band Ressource

1. Öffnen Sie in Visual Studio in einem vorhandenen MFC-Projekt die Quelldatei, in der das `CMFCRibbonBar` Objekt initialisiert wird. In der Regel ist die Datei "mainfrm. cpp". Fügen Sie den folgenden Code nach dem Initialisierungs Code für das Menüband hinzu.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Speichern und schließen Sie die Datei.

1. Erstellen Sie die MFC-Anwendung, und führen Sie Sie aus. Öffnen Sie dann in Editor die Datei ribbonoutput. txt, und kopieren Sie den Inhalt.

1. Klicken Sie in Visual Studio im Menü **Projekt** auf **Ressource hinzufügen**. Wählen Sie im Dialogfeld **Ressource hinzufügen** die Option **Menüband** aus, und klicken Sie auf **neu**.

   Visual Studio erstellt eine Menü Band Ressource und öffnet Sie in der Entwurfs Ansicht. Die Ressourcen-ID für das Menüband ist IDR_RIBBON1, das in **Ressourcenansicht**angezeigt wird. Das Menüband wird in der XML-Datei Ribbon1. MF cribbon-MS definiert.

1. Öffnen Sie in Visual Studio Ribbon1. MF cribbon-MS, löschen Sie den Inhalt, und fügen Sie dann den Inhalt von ribbonoutput. txt ein, den Sie zuvor kopiert haben. Speichern und schließen Sie Ribbon1. MF cribbon-ms.

1. Öffnen Sie erneut die Quelldatei, in der das cmscribbonbar-Objekt initialisiert wird (normalerweise "mainfrm. cpp"), und kommentieren Sie den vorhandenen Multifunktionsleisten-Code aus. Fügen Sie den folgenden Code nach dem auskommentierten Code hinzu.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Erstellen Sie das Projekt, und führen Sie das Programm aus.

## <a name="see-also"></a>Siehe auch

[Menüband-Designer (MFC)](ribbon-designer-mfc.md)
