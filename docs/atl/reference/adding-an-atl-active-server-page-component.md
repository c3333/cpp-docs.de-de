---
title: Hinzufügen einer ATL Active Server Page-Komponente
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: 08d49baa547342843b525f871de9570d4e752068
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921164"
---
# <a name="adding-an-atl-active-server-page-component"></a>Hinzufügen einer ATL Active Server Page-Komponente

::: moniker range="msvc-160"

Der ATL Active Server Pages-Komponenten-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Um ein ATL-Objekt (Active Template Library) zu Ihrem Projekt hinzufügen zu können, muss Ihr Projekt als eine ATL-COM- oder MFC-Anwendung erstellt worden sein, die ATL-Unterstützung enthält. Sie können den [ATL-Projekt-Assistenten](../../atl/reference/atl-project-wizard.md) verwenden, um eine ATL-Anwendung zu erstellen, Sie können **ATL-Unterstützung zu MFC hinzufügen** im Dialogfeld [Klasse hinzufügen](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) auswählen, oder Sie können [ein ATL-Objekt zu Ihrer MFC-Anwendung hinzufügen](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), um ATL-Unterstützung für eine MFC-Anwendung zu implementieren.

Active Server Pages-Komponenten sind Bestandteil der Internetinformationsdienste-Architektur, die folgende erweiterte Webentwicklungsfunktionalität bereitstellt:

- Sie können ASP-Komponenten in Ihre HTML-Seiten einbetten, um dynamische, browserunabhängige Inhalte zu erstellen.

- Sie können ASP-Seiten verwenden, um auf Standards basierende Datenbankkonnektivität bereitzustellen.

- Sie können die ASP-Fehlerbehandlungsfunktionen für Ihre webbasierten Anwendungen nutzen.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>Hinzufügen einer ATL Active Server Pages-Komponente zu Ihrem Projekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Namen des Projekts, dem Sie die ATL Active Server Pages-Komponente hinzufügen möchten.

1. Klicken Sie im Kontextmenü auf die Option **Hinzufügen** , und klicken Sie danach auf **Klasse hinzufügen** .

1. Klicken Sie im Dialogfeld [Klasse hinzufügen](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) im Bereich **Vorlagen** auf **ATL Active Server Page-Komponente** , und klicken Sie dann auf **Öffnen** , um den [ATL Active Server Page-Komponenten-Assistenten](../../atl/reference/atl-active-server-page-component-wizard.md) anzuzeigen.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Hinzufügen einer neuen Schnittstelle in einem ATL-Projekt](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Hinzufügen von Verbindungs Punkten zu einem Objekt](../../atl/adding-connection-points-to-an-object.md)<br/>
[Adding a Method (Hinzufügen einer Methode)](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC-Klasse](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Hinzufügen einer generischen C++-Klasse](../../ide/adding-a-generic-cpp-class.md)
