---
title: Hinzufügen eines ATL-Steuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: fac1efeb3d373a8324828a8b10f0570f253f6103
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499286"
---
# <a name="adding-an-atl-control"></a>Hinzufügen eines ATL-Steuerelements

Verwenden Sie diesen Assistenten, um einem Projekt, das Schnittstellen für alle potenziellen Container unterstützt, ein Benutzeroberflächen Objekt hinzuzufügen. Um diese Schnittstellen zu unterstützen, muss das Projekt als ATL-Anwendung oder als MFC-Anwendung erstellt worden sein, die ATL-Unterstützung enthält. Mit dem [ATL-Projekt-Assistenten](../../atl/reference/atl-project-wizard.md) können Sie eine ATL-Anwendung erstellen oder [ihrer MFC-Anwendung ein ATL-Objekt hinzufügen](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) , um ATL-Unterstützung für eine MFC-Anwendung zu implementieren.

## <a name="to-add-an-atl-control-to-your-project"></a>So fügen Sie dem Projekt ein ATL-Steuerelement hinzu

1. Klicken Sie in **Projektmappen-Explorer** oder [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf den Namen des Projekts, dem Sie das einfache ATL-Objekt hinzufügen möchten.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Klasse hinzufügen**.

1. Klicken Sie im Dialogfeld [Klasse hinzufügen](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) im Bereich Vorlagen auf **ATL-Steuer**Element, und klicken Sie dann auf **Hinzufügen** , um den [ATL-Steuer](../../atl/reference/atl-control-wizard.md)Element-Assistenten anzuzeigen.

Mit dem **ATL-Steuer**Element-Assistenten können Sie einen von drei Typen von Steuerelementen erstellen:

- Ein Standard Steuerelement

- Zusammengesetztes Steuerelement

- Ein DHTML-Steuerelement

Außerdem können Sie die Größe des Steuer Elements reduzieren und Schnittstellen entfernen, die nicht von den meisten Containern verwendet werden, indem Sie auf der Options Seite des Assistenten die **Option** **Minimal Steuerung** auswählen.

## <a name="see-also"></a>Weitere Informationen

[Hinzufügen von Funktionen zum zusammengesetzten Steuerelement](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Grundlagen von ATL-COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md)
