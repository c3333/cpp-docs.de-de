---
title: Erstellen eines Grundleisten-Steuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 6828fa3b47eaa1e29579b09611d85cd68702c332
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617123"
---
# <a name="creating-a-rebar-control"></a>Erstellen eines Grundleisten-Steuerelements

Bevor das übergeordnete Objekt sichtbar ist, sollten [die Objekte erstellt](reference/crebarctrl-class.md) werden. Dadurch werden die Möglichkeiten zum Zeichnen von Problemen minimiert.

Beispielsweise werden die Grund leisten-Steuerelemente (die in Frame Fenster Objekten verwendet werden) häufig als übergeordnete Fenster für Symbolleisten-Steuerelemente verwendet. Daher ist das übergeordnete Element des Grund leisten-Steuer Elements das Rahmen Fenster Objekt. Da das Rahmen Fenster Objekt das übergeordnete Objekt ist, `OnCreate` ist die Member-Funktion (des übergeordneten Elements) ein hervorragender Ort zum Erstellen des Grund leisten-Steuer Elements.

Um ein- `CReBarCtrl` Objekt zu verwenden, führen Sie in der Regel die folgenden Schritte aus:

### <a name="to-use-a-crebarctrl-object"></a>So verwenden Sie ein "krebarctrl"-Objekt

1. Erstellen Sie das Objekt " [krebarctrl](reference/crebarctrl-class.md) ".

1. Rufen Sie [Create](reference/crebarctrl-class.md#create) auf, um das allgemeine Windows-Steuerelement für die Grund Leiste zu erstellen, und fügen Sie es an das- `CReBarCtrl` Objekt an.

1. Laden Sie eine Bitmap mit einem [CBitmap:: LoadBitmap](reference/cbitmap-class.md#loadbitmap)-Befehl, der als Hintergrund des Grund leisten-Steuerelement Objekts verwendet werden soll.

1. Erstellen und initialisieren Sie alle untergeordneten Fenster Objekte (Symbolleisten, Dialogfeld Steuerelemente usw.), die im Info leisten-Steuerelement Objekt enthalten sein werden.

1. Initialisieren Sie eine **REBARBANDINFO** -Struktur mit den erforderlichen Informationen, damit das Band eingefügt werden muss.

1. Fügen Sie [InsertBand](reference/crebarctrl-class.md#insertband) ein, um vorhandene untergeordnete Fenster (z `m_wndReToolBar` . b.) in das neue Grund leisten-Steuerelement einzufügen. Weitere Informationen zum Einfügen von Bändern in ein vorhandenes Grund leisten-Steuerelement finden Sie Untergrund leisten [-Steuerelemente und-Bänder](rebar-controls-and-bands.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von CReBarCtrl](using-crebarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
