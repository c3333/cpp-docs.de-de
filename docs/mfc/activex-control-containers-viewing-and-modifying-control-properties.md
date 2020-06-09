---
title: 'ActiveX-Steuerelementcontainer: Anzeigen und Ändern von Steuerelementeigenschaften'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: b0ca43f59cf70dea1348f22a08cfb4e89b45c3dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617357"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX-Steuerelementcontainer: Anzeigen und Ändern von Steuerelementeigenschaften

Wenn Sie ein ActiveX-Steuerelement in ein-Projekt einfügen, ist es hilfreich, die Eigenschaften anzuzeigen und zu ändern, die vom ActiveX-Steuerelement unterstützt werden. In diesem Artikel wird erläutert, wie Sie den Ressourcen-Editor für Visual C++ verwenden.

Wenn die Containeranwendung des ActiveX-Steuer Elements eingebettete Steuerelemente verwendet, können Sie die Eigenschaften des Steuer Elements im Ressourcen-Editor anzeigen und ändern. Sie können auch den Ressourcen-Editor verwenden, um Eigenschaftswerte während der Entwurfszeit festzulegen. Der Ressourcen-Editor speichert diese Werte dann automatisch in der Ressourcen Datei des Projekts. Für jede Instanz des Steuer Elements werden dann die Eigenschaften dieser Werte initialisiert.

Bei diesem Verfahren wird davon ausgegangen, dass Sie ein-Steuerelement in Ihr Projekt eingefügt haben. Weitere Informationen finden Sie unter [ActiveX-Steuerelement Container: Einfügen eines Steuer Elements in eine Steuerelement Container-Anwendung](inserting-a-control-into-a-control-container-application.md).

Der erste Schritt beim Anzeigen der Eigenschaften des-Steuer Elements besteht darin, der Dialogfeld Vorlage des Projekts eine Instanz des-Steuer Elements hinzuzufügen.

### <a name="to-view-the-properties-of-a-control"></a>So zeigen Sie die Eigenschaften eines Steuer Elements an

1. Öffnen Sie in Ressourcenansicht den **Dialog** Ordner.

1. Öffnen Sie die Haupt Dialogfeld Vorlage.

1. Fügen Sie ein ActiveX-Steuerelement mit dem Dialogfeld **ActiveX-Steuerelement einfügen** ein. Weitere Informationen finden Sie unter [anzeigen und Hinzufügen von ActiveX-Steuerelementen zu einem Dialog Feld](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. Wählen Sie das ActiveX-Steuerelement im Dialogfeld aus.

1. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche **Eigenschaften** .

Verwenden Sie das Dialogfeld **Eigenschaften** , um neue Eigenschaften sofort zu ändern und zu testen.

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](activex-control-containers.md)
