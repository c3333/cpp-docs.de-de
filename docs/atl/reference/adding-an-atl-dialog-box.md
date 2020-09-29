---
title: Hinzufügen eines ATL-Dialogfelds
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: 71290cf0763ac6594985acc4cb11562efe7028e6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499376"
---
# <a name="adding-an-atl-dialog-box"></a>Hinzufügen eines ATL-Dialogfelds

Um dem Projekt ein ATL-Dialogfeld hinzuzufügen, muss das Projekt entweder ein ATL-Projekt oder ein MFC-Projekt sein, das ATL-Unterstützung umfasst. Mit dem [ATL-Projekt-Assistenten](../../atl/reference/atl-project-wizard.md) können Sie eine ATL-Anwendung erstellen oder [ihrer MFC-Anwendung ein ATL-Objekt hinzufügen](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) , um ATL-Unterstützung für eine MFC-Anwendung zu implementieren.

Standardmäßig implementiert der ATL-Dialogfeld-Assistent ein Dialog Feld, das von [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)abgeleitet ist. Diese Klasse unterstützt das Hosting von ActiveX-und Windows-Steuerelementen. Wenn Sie den Aufwand für die Unterstützung von ActiveX-Steuerelementen nicht wünschen, können Sie nach dem Generieren des Codes alle Instanzen von `CAxDialogImpl` durch [CSimpleDialog](../../atl/reference/csimpledialog-class.md) oder [CDialogImpl](../../atl/reference/cdialogimpl-class.md) als Basisklasse ersetzen.

> [!NOTE]
> `CSimpleDialog` erstellt nur modale Dialogfelder, die nur allgemeine Windows-Steuerelemente unterstützen. `CDialogImpl` erstellt modale oder nicht modale Dialogfelder.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>So fügen Sie dem Projekt eine ATL-Dialog Ressource hinzu

1. Erstellen Sie mit dem [ATL-Projekt-Assistenten](../../atl/reference/atl-project-wizard.md)ein ATL-Projekt.

1. Klicken Sie in [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann im Kontextmenü auf **Hinzufügen** . Klicken Sie auf **Klasse hinzufügen**.

1. Klicken Sie im Bereich **Vorlagen** des Dialog Felds [Klasse hinzufügen](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) auf **ATL-Dialog**Feld. Klicken Sie auf **Öffnen** , um den [ATL-Dialog-Assistenten](../../atl/reference/atl-dialog-wizard.md)anzuzeigen.

Weitere Informationen finden Sie unter [Implementieren eines Dialog](../../atl/implementing-a-dialog-box.md)Felds.

## <a name="see-also"></a>Weitere Informationen

[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Fenster Klassen](../../atl/atl-window-classes.md)<br/>
[Meldungs Zuordnungen](../../atl/message-maps-atl.md)
