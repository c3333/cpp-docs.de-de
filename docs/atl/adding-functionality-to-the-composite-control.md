---
title: Hinzufügen von Funktionen zum Composite-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317428"
---
# <a name="adding-functionality-to-the-composite-control"></a>Hinzufügen von Funktionen zum Composite-Steuerelement

Nachdem Sie alle erforderlichen Steuerelemente in das zusammengesetzte Steuerelement eingefügt haben, müssen Sie im nächsten Schritt neue Funktionen hinzufügen. Diese neue Funktionalität gliedert sich in die Regel in zwei Kategorien:

- Unterstützung zusätzlicher Schnittstellen und Anpassen des Verhaltens Ihres zusammengesetzten Steuerelements mit zusätzlichen, spezifischen Funktionen.

- Behandeln von Ereignissen aus dem enthaltenen ActiveX-Steuerelement (oder Steuerelemente).

Für Zweck und Umfang dieses Artikels konzentriert sich der Rest dieses Abschnitts ausschließlich auf die Behandlung von Ereignissen aus ActiveX-Steuerelementen.

> [!NOTE]
> Wenn Sie Nachrichten von Windows-Steuerelementen verarbeiten müssen, finden Sie weitere Informationen zur Nachrichtenbehandlung in ATL unter [Implementieren eines Fensters.](../atl/implementing-a-window.md)

Nachdem Sie ein ActiveX-Steuerelement in die Dialogfeldressource eingefügt haben, klicken Sie mit der rechten Maustaste auf das Steuerelement, und klicken Sie auf **Ereignishandler hinzufügen**. Wählen Sie das Ereignis aus, das Sie behandeln möchten, und klicken Sie auf **Hinzufügen und Bearbeiten**. Der Ereignishandlercode wird der .h-Datei des Steuerelements hinzugefügt.

Verbindungspunkte für ActiveX-Steuerelemente im zusammengesetzten Steuerelement werden automatisch über Aufrufe von [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)verbunden und getrennt.

## <a name="see-also"></a>Siehe auch

[Grundlagen von zusammengesetzten Steuerelementen](../atl/atl-composite-control-fundamentals.md)
