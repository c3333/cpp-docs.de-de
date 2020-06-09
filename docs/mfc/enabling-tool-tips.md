---
title: Erstellen von QuickInfos
ms.date: 11/04/2016
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
ms.openlocfilehash: bdd5c54f9174c42e17db0be7e13ea31acfea2dcf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615731"
---
# <a name="enabling-tool-tips"></a>Erstellen von QuickInfos

Sie können die QuickInfo-Unterstützung für die untergeordneten Steuerelemente eines Fensters aktivieren (z. b. die Steuerelemente in einer Formularansicht oder einem Dialogfeld).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>So aktivieren Sie Quick Infos für die untergeordneten Steuerelemente eines Fensters

1. Ruft `EnableToolTips` für das Fenster auf, für das Sie Quick Infos bereitstellen möchten.

1. Geben Sie für jedes Steuerelement im [TTN_NEEDTEXT Benachrichtigungs](handling-ttn-needtext-notification-for-tool-tips.md) Handler eine Zeichenfolge an. Der Handler befindet sich in der Meldungs Zuordnung des Fensters, das die untergeordneten Steuerelemente enthält (z. b. Ihre Formular Ansichts Klasse). Dieser Handler sollte eine Funktion aufzurufen, die das-Steuerelement identifiziert und **pszText** festlegt, um den Text anzugeben, der vom QuickInfo-Steuerelement verwendet wird.

## <a name="see-also"></a>Siehe auch

[QuickInfos in Fenstern, die nicht von CFrameWnd abgeleitet sind](tool-tips-in-windows-not-derived-from-cframewnd.md)
