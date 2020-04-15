---
title: Hinzufügen einer MFC-Klasse aus einer Typbibliothek
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371720"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Hinzufügen einer MFC-Klasse aus einer Typbibliothek

Verwenden Sie diesen Assistenten, um eine MFC-Klasse aus einer Schnittstelle in einer verfügbaren Typbibliothek zu erstellen. Sie können eine MFC-Klasse in eine [MFC-Anwendung](../../mfc/reference/creating-an-mfc-application.md), eine [MFC-DLL](../../mfc/reference/creating-an-mfc-dll-project.md) oder ein [MFC-ActiveX-Steuerelement](../../mfc/reference/creating-an-mfc-activex-control.md) einfügen.

> [!NOTE]
> Sie müssen Ihr MFC-Projekt nicht mit aktivierter Automatisierung erstellen, um eine Klasse aus einer Typbibliothek hinzuzufügen.

Eine Typbibliothek enthält eine binäre Beschreibung der Schnittstellen, die von einer Komponente verfügbar gemacht werden, und definiert die Methoden zusammen mit ihren Parametern und Rückgabetypen. Ihre Typbibliothek muss registriert sein, damit sie in der Liste **Verfügbare Typbibliotheken** in der Add-Klasse aus dem Typelib-Assistenten angezeigt wird. Weitere Informationen finden Sie unter "Inside Distributed COM: Type Libraries and Language Integration" in der MSDN-Bibliothek.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>So fügen Sie eine MFC-Klasse aus einer Typbibliothek hinzu

1. Klicken Sie im **Projektmappen-Explorer** oder in der [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf den Namen des Projekts, dem Sie die Klasse hinzufügen möchten.

1. Klicken Sie im Kontextmenü auf die Option **Hinzufügen**, und klicken Sie danach auf **Klasse hinzufügen**.

1. Klicken Sie im Dialogfeld [Klassen hinzufügen](../../ide/add-class-dialog-box.md) im Bereich Vorlagen auf **MFC-Klasse in Typelib**, und klicken Sie dann auf **Öffnen,** um die [Klasse hinzufügen vom Typelib-Assistenten](../../mfc/reference/add-class-from-typelib-wizard.md)anzuzeigen.

Im Assistenten können Sie mehr als eine Klasse in einer Typbibliothek hinzufügen. Ebenso können Sie Klassen aus mehr als einer Typbibliothek in einer einzelnen Assistentensitzung hinzufügen.

Der Assistent erstellt eine MFC-Klasse, die von [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)abgeleitet ist, für jede Schnittstelle, die Sie aus der ausgewählten Typbibliothek hinzufügen. `COleDispatchDriver`implementiert die Clientseite der OLE-Automatisierung.

## <a name="see-also"></a>Siehe auch

[Automatisierungsclients](../../mfc/automation-clients.md)<br/>
[Automatisierungsclients: Verwenden von Typbibliotheken](../../mfc/automation-clients-using-type-libraries.md)
