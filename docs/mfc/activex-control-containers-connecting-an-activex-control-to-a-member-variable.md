---
title: 'ActiveX-Steuerelementcontainer: Verbinden eines ActiveX-Steuerelements mit einer Membervariablen'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: 87cb560a1054a912a4e8574cfe2dee74d5e61fe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625132"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX-Steuerelementcontainer: Verbinden eines ActiveX-Steuerelements mit einer Membervariablen

Die einfachste Möglichkeit, über die Steuerelement Container-Anwendung auf ein ActiveX-Steuerelement zuzugreifen, besteht darin, das ActiveX-Steuerelement einer Element Variablen der Dialogfeld Klasse zuzuordnen, die das Steuerelement enthalten wird.

> [!NOTE]
> Dies ist nicht die einzige Möglichkeit für den Zugriff auf ein eingebettetes Steuerelement aus einer Container Klasse, aber im Rahmen dieses Artikels genügt es.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Hinzufügen einer Element Variablen zur Dialogfeld Klasse

1. Klicken Sie in Klassenansicht mit der rechten Maustaste auf die Haupt Dialogklasse, um das Kontextmenü zu öffnen. Beispiel: `CContainerDlg`.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und fügen Sie dann **Variable hinzu**.

1. Klicken Sie im Assistenten zum Hinzufügen von Element Variablen auf **Steuerungs Variable**.

1. Wählen Sie im Listenfeld Steuerelement- **ID** die Steuerelement-ID des eingebetteten ActiveX-Steuer Elements aus. Beispiel: `IDC_CIRCCTRL1`.

1. Geben Sie im Feld **Variablenname** einen Namen ein.

   Beispielsweise *m_circctl*.

1. Klicken Sie auf **Fertig** stellen, um Ihre Auswahl zu akzeptieren und den Assistenten zum Hinzufügen von Mitgliedsvariablen

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](activex-control-containers.md)
