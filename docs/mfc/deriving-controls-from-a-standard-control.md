---
title: Ableiten von Steuerelementen von einem Standardsteuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
ms.openlocfilehash: 54e43c8445bb6b8db4c6a7a4b28890e81be52d6c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616954"
---
# <a name="deriving-controls-from-a-standard-control"></a>Ableiten von Steuerelementen von einem Standardsteuerelement

Wie bei jeder von [CWnd](reference/cwnd-class.md)abgeleiteten Klasse können Sie das Verhalten eines Steuer Elements ändern, indem Sie eine neue Klasse von einer vorhandenen Steuerelement Klasse ableiten.

### <a name="to-create-a-derived-control-class"></a>So erstellen Sie eine abgeleitete Steuerelement Klasse

1. Leiten Sie die Klasse von einer vorhandenen Steuerelement Klasse ab, und überschreiben Sie optional die `Create` Member-Funktion, sodass Sie die erforderlichen Argumente für die Basisklassen Funktion bereitstellt `Create` .

1. Stellen Sie Nachrichten Handler-Element Funktionen und Nachrichten Zuordnungs Einträge bereit, um das Verhalten des Steuer Elements als Reaktion auf bestimmte Windows-Meldungen zu ändern. Siehe [Mapping von Nachrichten zu Funktionen](reference/mapping-messages-to-functions.md).

1. Stellen Sie neue Element Funktionen bereit, um die Funktionalität des Steuer Elements zu erweitern (optional).

Die Verwendung eines abgeleiteten Steuer Elements in einem Dialogfeld erfordert zusätzliche Arbeit. Die Typen und Positionen von Steuerelementen in einem Dialogfeld werden normalerweise in einer Dialogfeld Vorlagen-Ressource angegeben. Wenn Sie eine abgeleitete Steuerelement Klasse erstellen, können Sie Sie nicht in einer Dialogfeld Vorlage angeben, da der Ressourcen Compiler nichts über die abgeleitete Klasse weiß.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>So platzieren Sie das abgeleitete Steuerelement in einem Dialogfeld

1. Betten Sie ein Objekt der abgeleiteten Steuerelement Klasse in die Deklaration der abgeleiteten Dialog Klasse ein.

1. Überschreiben `OnInitDialog` Sie die Member-Funktion in der Dialogfeld Klasse, um die Element `SubclassDlgItem` Funktion für das abgeleitete Steuerelement aufzurufen

`SubclassDlgItem`"dynamisch Unterklassen" ein Steuerelement, das aus einer Dialogfeld Vorlage erstellt wurde. Wenn ein Steuerelement dynamisch untergeordnet ist, werden Sie in Windows eingebunden, einige Nachrichten in ihrer eigenen Anwendung verarbeiten und dann die restlichen Nachrichten an Windows übergeben. Weitere Informationen finden Sie in der [SubclassDlgItem](reference/cwnd-class.md#subclassdlgitem) -Member-Funktion der-Klasse `CWnd` in der *MFC-Referenz*. Im folgenden Beispiel wird gezeigt, wie Sie eine außer Kraft Setzung von schreiben können `OnInitDialog` , um aufzurufen `SubclassDlgItem` :

[!code-cpp[NVC_MFCControlLadenDialog#3](codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Da das abgeleitete Steuerelement in die Dialogfeld Klasse eingebettet ist, wird es beim Konstruieren des Dialog Felds erstellt und beim Zerstören des Dialog Felds zerstört. Vergleichen Sie diesen Code mit dem Beispiel unter Manuelles [Hinzufügen von Steuerelementen](adding-controls-by-hand.md).

## <a name="see-also"></a>Siehe auch

[Erstellen und Verwenden von Steuerelementen](making-and-using-controls.md)<br/>
[Steuerelemente](controls-mfc.md)
