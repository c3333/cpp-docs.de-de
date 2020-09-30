---
title: Hinzufügen einer MFC-Klasse aus einer Typbibliothek
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: 45bad00155cc1587980e6f3b25843a7a22e7e754
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503039"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Hinzufügen einer MFC-Klasse aus einer Typbibliothek

Mit diesem Assistenten erstellen Sie eine MFC-Klasse aus einer Schnittstelle in einer verfügbaren Typbibliothek. Sie können eine MFC-Klasse in eine [MFC-Anwendung](../../mfc/reference/creating-an-mfc-application.md), eine [MFC-DLL](../../mfc/reference/creating-an-mfc-dll-project.md) oder ein [MFC-ActiveX-Steuerelement](../../mfc/reference/creating-an-mfc-activex-control.md) einfügen.

> [!NOTE]
> Sie müssen das MFC-Projekt nicht mit aktivierter Automatisierung erstellen, um eine Klasse aus einer Typbibliothek hinzuzufügen.

Eine Typbibliothek enthält eine binäre Beschreibung der Schnittstellen, die von einer Komponente verfügbar gemacht werden, wobei die Methoden zusammen mit ihren Parametern und Rückgabe Typen definiert werden. Die Typbibliothek muss registriert sein, damit Sie in der Liste **Verfügbare Typbibliotheken** im Assistenten zum Hinzufügen von Klassen aus TypeLib angezeigt wird.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>So fügen Sie eine MFC-Klasse aus einer Typbibliothek hinzu

1. Klicken Sie in **Projektmappen-Explorer** oder [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf den Namen des Projekts, dem Sie die Klasse hinzufügen möchten.

1. Klicken Sie im Kontextmenü auf die Option **Hinzufügen**, und klicken Sie danach auf **Klasse hinzufügen**.

1. Klicken Sie im Dialogfeld [Klasse hinzufügen](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) im Bereich Vorlagen auf **MFC-Klasse aus TypeLib**, und klicken Sie dann auf **Öffnen** , um den [Assistenten zum Hinzufügen von Klassen aus TypeLib](../../mfc/reference/add-class-from-typelib-wizard.md)anzuzeigen.

Im Assistenten können Sie mehr als eine Klasse in einer Typbibliothek hinzufügen. Ebenso können Sie Klassen aus mehreren Typbibliotheken in einer einzelnen Assistenten Sitzung hinzufügen.

Der Assistent erstellt eine von [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)abgeleitete MFC-Klasse für jede Schnittstelle, die Sie aus der ausgewählten Typbibliothek hinzufügen. `COleDispatchDriver` implementiert die Clientseite der OLE-Automatisierung.

## <a name="see-also"></a>Weitere Informationen

[Automatisierungs Clients](../../mfc/automation-clients.md)<br/>
[Automatisierungs Clients: Verwenden von Typbibliotheken](../../mfc/automation-clients-using-type-libraries.md)
