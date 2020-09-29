---
title: Hinzufügen eines einfachen ATL-Objekts
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 85c19c483ff27bd34431ec163e3baadac1855236
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499344"
---
# <a name="adding-an-atl-simple-object"></a>Hinzufügen eines einfachen ATL-Objekts

Um dem Projekt ein ATL-Objekt (Active Template Library) hinzuzufügen, muss das Projekt als ATL-Anwendung oder als MFC-Anwendung erstellt worden sein, die ATL-Unterstützung enthält. Mit dem [ATL-Projekt-Assistenten](../../atl/reference/atl-project-wizard.md) können Sie eine ATL-Anwendung erstellen oder [ihrer MFC-Anwendung ein ATL-Objekt hinzufügen](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) , um ATL-Unterstützung für eine MFC-Anwendung zu implementieren.

Sie können COM-Schnittstellen für das neue ATL-Objekt definieren, wenn Sie es erstmalig erstellen, oder Sie später hinzufügen, indem Sie den Befehl [Schnittstelle implementieren](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard) im Kontextmenü **Klassenansicht** verwenden.

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>So fügen Sie Ihrem ATL-COM-Projekt ein einfaches ATL-Objekt hinzu

1. Klicken Sie in **Projektmappen-Explorer** oder [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf den Namen des Projekts, dem Sie das einfache ATL-Objekt hinzufügen möchten.

1. Klicken Sie im Kontextmenü auf die Option **Hinzufügen**, und klicken Sie danach auf **Klasse hinzufügen**.

1. Klicken Sie im Dialogfeld [Klasse hinzufügen](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) im Bereich **Vorlagen** auf **einfaches ATL-Objekt**, und klicken Sie dann auf **Öffnen** , um den [ATL-Assistenten für einfache Objekte](../../atl/reference/atl-simple-object-wizard.md)anzuzeigen.

1. Legen Sie zusätzliche Optionen für das Projekt auf der Seite [Optionen](../../atl/reference/options-atl-simple-object-wizard.md) des **ATL** -Assistenten für einfache Objekte fest.

1. Klicken Sie auf **Fertig** stellen, um das Objekt dem Projekt hinzuzufügen.

## <a name="see-also"></a>Weitere Informationen

[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Hinzufügen einer neuen Schnittstelle in einem ATL-Projekt](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Hinzufügen von Verbindungs Punkten zu einem Objekt](../../atl/adding-connection-points-to-an-object.md)<br/>
[Adding a Method (Hinzufügen einer Methode)](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC Class (MFC-Klasse)](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Hinzufügen einer generischen C++-Klasse](../../ide/adding-a-generic-cpp-class.md)
