---
title: Hinzufügen von ATL-Unterstützung zu einem MFC-Projekt
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 05c4e8ba54d9a573b422f136c9e8cf69e48d1c9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371683"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Hinzufügen von ATL-Unterstützung zu einem MFC-Projekt

Wenn Sie bereits eine MFC-basierte Anwendung erstellt haben, können Sie mithilfe der IDE problemlos Unterstützung für die Active Template Library (ATL) hinzufügen.

> [!NOTE]
> Diese Unterstützung gilt nur für einfache COM-Objekte, die einer MFC-Anwendung oder einem DLL-Projekt hinzugefügt werden. Sie können MFC-Projekten weitere COM-Objekte (einschließlich ActiveX-Steuerelemente) hinzufügen, die Objekte funktionieren jedoch möglicherweise nicht wie erwartet.

::: moniker range=">=vs-2019"

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten.

1. Klicken Sie im Kontextmenü auf **Hinzufügen**, und klicken Sie danach auf **Neues Element**.

1. Wählen Sie **ATL** im linken Bereich und dann **ATL Support** im mittleren Bereich aus.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>So fügen Sie Ihrem MFC-Projekt ATL-Unterstützung hinzu

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten.

1. Klicken Sie im Kontextmenü auf **Hinzufügen**, und dann auf **Klasse hinzufügen**.

1. Wählen Sie **ATL** im linken Bereich aus, und wählen Sie dann **ATL-Unterstützung zu MFC-Projekt** im mittleren Bereich hinzufügen aus.

::: moniker-end

Weitere Informationen dazu, wie das Hinzufügen von ATL-Unterstützung den Code Ihres MFC-Projekts ändert, finden Sie unter [Details zum ATL-Support, der vom ATL-Assistenten hinzugefügt](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md) wurde.

## <a name="see-also"></a>Siehe auch

[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Hinzufügen einer Memberfunktion](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable (Hinzufügen einer Membervariablen)](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function (Überschreiben einer virtuellen Funktion)](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler (MFC-Meldungshandler)](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigating the Class Structure (Navigieren in der Klassenstruktur)](../../ide/navigate-code-cpp.md)
