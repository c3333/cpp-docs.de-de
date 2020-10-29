---
title: Hinzufügen von ATL-Unterstützung zu einem MFC-Projekt
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 94303d1dfc7c06171def1224982f5e0aa5716ce4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924471"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Hinzufügen von ATL-Unterstützung zu einem MFC-Projekt

Wenn Sie bereits eine MFC-basierte Anwendung erstellt haben, können Sie die Unterstützung für die Active Template Library (ATL) problemlos mithilfe der IDE hinzufügen.

> [!NOTE]
> Diese Unterstützung gilt nur für einfache COM-Objekte, die einer MFC-Anwendung oder einem DLL-Projekt hinzugefügt werden. Sie können MFC-Projekten weitere COM-Objekte (einschließlich ActiveX-Steuerelementen) hinzufügen, die Objekte funktionieren jedoch möglicherweise nicht erwartungsgemäß.

::: moniker range=">=msvc-160"

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie danach auf **Neues Element** .

1. Wählen Sie im linken Bereich **ATL** aus, und wählen Sie dann im mittleren Bereich **ATL-Unterstützung** aus.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-add-atl-support-to-your-mfc-project"></a>So fügen Sie Ihrem MFC-Projekt ATL-Unterstützung hinzu

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Klasse hinzufügen** .

1. Wählen Sie im linken Bereich **ATL** aus, und wählen Sie dann im mittleren Bereich **ATL-Unterstützung zu MFC-Projekt hinzufügen** aus.

::: moniker-end

Weitere Informationen zum Ändern des MFC-Projekt Codes durch das Hinzufügen der ATL-Unterstützung finden Sie unter [Details der vom ATL-Assistenten hinzugefügten ATL-Unterstützung](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md) .

## <a name="see-also"></a>Siehe auch

[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Hinzufügen einer Memberfunktion](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable (Hinzufügen einer Membervariablen)](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function (Überschreiben einer virtuellen Funktion)](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler (MFC-Meldungshandler)](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigating the Class Structure (Navigieren in der Klassenstruktur)](../../ide/navigate-code-cpp.md)
