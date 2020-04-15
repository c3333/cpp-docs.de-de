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
ms.openlocfilehash: 620a9ec58b3a5a8fcdac63626b81fbc4620de399
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371619"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX-Steuerelementcontainer: Verbinden eines ActiveX-Steuerelements mit einer Membervariablen

Die einfachste Möglichkeit, von der Steuerelementcontaineranwendung aus auf ein ActiveX-Steuerelement zuzugreifen, besteht darin, das ActiveX-Steuerelement einer Membervariablen der Dialogklasse zuzuordnen, die das Steuerelement enthält.

> [!NOTE]
> Dies ist nicht die einzige Möglichkeit, von einer Containerklasse aus auf ein eingebettetes Steuerelement zuzugreifen, aber für die Zwecke dieses Artikels ist es ausreichend.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>Hinzufügen einer Membervariablen zur Dialogklasse

1. Klicken Sie in der Klassenansicht mit der rechten Maustaste auf die Hauptdialogklasse, um das Kontextmenü zu öffnen. Beispiel: `CContainerDlg`.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann **auf Variable hinzufügen**.

1. Klicken Sie im Assistenten zum Hinzufügen von Mitgliedsvariablen auf **Steuerelementvariable**.

1. Wählen Sie im Listenfeld **Steuerungs-ID** die Steuer-ID des eingebetteten ActiveX-Steuerelements aus. Beispiel: `IDC_CIRCCTRL1`.

1. Geben Sie im Feld **Variablenname** einen Namen ein.

   *M_circctl*z. B. .

1. Klicken Sie auf **Fertig stellen,** um Ihre Auswahl zu akzeptieren, und beenden Sie den Assistenten zum Hinzufügen von Mitgliedsvariablen.

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](../mfc/activex-control-containers.md)
