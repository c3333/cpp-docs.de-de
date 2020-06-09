---
title: Optimieren von Persistenz und Initialisierung
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 57b98f7e2e4f9e23175b8b01c2e37ff49c499949
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623996"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimieren von Persistenz und Initialisierung

Standardmäßig werden Persistenz und Initialisierung in einem-Steuerelement von der- `DoPropExchange` Member-Funktion behandelt. In einem typischen Steuerelement enthält diese Funktion Aufrufe mehrerer **PX_** Funktionen ( `PX_Color` , `PX_Font` usw.), eine für jede Eigenschaft.

Dieser Ansatz hat den Vorteil, dass eine einzelne `DoPropExchange` Implementierung für die Initialisierung, für Persistenz im Binärformat und für Persistenz im so genannten "Property-Bag"-Format, das von einigen Containern verwendet wird, verwendet werden kann. Diese eine Funktion stellt alle Informationen über die Eigenschaften und ihre Standardwerte an einem zentralen Ort bereit.

Diese Generalität wird jedoch auf Kosten der Effizienz gesteigert. Die **PX_** Funktionen erhalten Ihre Flexibilität durch mehrstufige Implementierungen, die grundsätzlich weniger effizient sind als direktere, aber weniger flexible Ansätze. Wenn außerdem ein Steuerelement einen Standardwert an eine **PX_** Funktion übergibt, muss dieser Standardwert jedes Mal angegeben werden, auch wenn der Standardwert nicht unbedingt verwendet werden kann. Wenn das Erstellen des Standardwerts eine nicht triviale Aufgabe ist (z. b. wenn der Wert aus einer Ambient-Eigenschaft abgerufen wird), erfolgt zusätzliche, unnötige Arbeit in Fällen, in denen der Standardwert nicht verwendet wird.

Sie können die binäre persistenzleistung Ihres Steuer Elements verbessern, indem Sie die Funktion des Steuer Elements überschreiben `Serialize` Die Standard Implementierung dieser Member-Funktion führt einen-Rückruf für Ihre `DoPropExchange` Funktion aus. Durch Überschreiben können Sie eine direktere Implementierung für die binäre Persistenz bereitstellen. Sehen Sie sich beispielsweise diese `DoPropExchange` Funktion an:

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Um die Leistung der binären Persistenz dieses Steuer Elements zu verbessern, können Sie die `Serialize` Funktion wie folgt überschreiben:

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

Die `dwVersion` lokale Variable kann verwendet werden, um die Version des permanenten Zustands des Steuer Elements zu erkennen, die geladen oder gespeichert wird. Sie können diese Variable anstelle des Aufrufs von [CPropExchange:: GetVersion](reference/cpropexchange-class.md#getversion)verwenden.

Wenn Sie für eine **boolesche** Eigenschaft wenig Speicherplatz im persistenten Format speichern möchten (und damit Sie mit dem von erzeugten Format kompatibel bleibt `PX_Bool` ), können Sie die Eigenschaft wie folgt als **Byte**speichern:

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Beachten Sie, dass im Lade Fall eine temporäre Variable verwendet und dann Ihr Wert zugewiesen wird, anstatt *m_boolProp* in einen **Byte** Verweis umzuwandeln. Das Umwandlungs Verfahren würde dazu führen, dass nur ein Byte von *m_boolProp* geändert wird, sodass die verbleibenden Bytes nicht initialisiert werden.

Für dasselbe Steuerelement können Sie die Initialisierung des Steuer Elements optimieren, indem Sie [COleControl:: OnResetState](reference/colecontrol-class.md#onresetstate) wie folgt überschreiben:

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Obwohl `Serialize` und `OnResetState` überschrieben wurden, sollte die `DoPropExchange` Funktion intakt bleiben, da Sie weiterhin für Persistenz im Eigenschaften Behälter-Format verwendet wird. Es ist wichtig, alle drei Funktionen beizubehalten, um sicherzustellen, dass das Steuerelement seine Eigenschaften konsistent verwaltet, unabhängig davon, welcher Persistenzmechanismus vom Container verwendet wird.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente: Optimierung](mfc-activex-controls-optimization.md)
