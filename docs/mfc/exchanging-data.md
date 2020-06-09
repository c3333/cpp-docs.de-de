---
title: Datenaustausch
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: 5be82567e02fd5e935d42f9eff5bdee20fa0d5a8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622705"
---
# <a name="exchanging-data"></a>Datenaustausch

Wie bei den meisten Dialogfeldern ist der Datenaustausch zwischen dem Eigenschaften Blatt und der Anwendung eine der wichtigsten Funktionen des Eigenschaften Blatts. In diesem Artikel wird beschrieben, wie Sie diese Aufgabe ausführen.

Beim Austauschen von Daten mit einem Eigenschaften Blatt geht es tatsächlich um den Datenaustausch mit den einzelnen Eigenschaften Seiten des Eigenschaften Blatts. Die Vorgehensweise zum Austauschen von Daten mit einer Eigenschaften Seite entspricht der Vorgehensweise beim Austauschen von Daten mit einem Dialogfeld, da ein [CPropertyPage](reference/cpropertypage-class.md) -Objekt nur ein spezielles [CDialog](reference/cdialog-class.md) -Objekt ist. Die-Prozedur nutzt die DDX-Funktion (Dialog Datenaustausch) des Frameworks, die Daten zwischen Steuerelementen in einem Dialogfeld und Element Variablen des Dialogfeld Objekts austauscht.

Der wichtige Unterschied zwischen dem Austauschen von Daten mit einem Eigenschaften Blatt und einem normalen Dialogfeld besteht darin, dass das Eigenschaften Blatt über mehrere Seiten verfügt, sodass Sie Daten mit allen Seiten im Eigenschaften Blatt austauschen müssen. Weitere Informationen zu DDX finden Sie unter [Dialog Datenaustausch und-Validierung](dialog-data-exchange-and-validation.md).

Das folgende Beispiel veranschaulicht den Austausch von Daten zwischen einer Sicht und zwei Seiten eines Eigenschaften Blatts:

[!code-cpp[NVC_MFCDocView#4](codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Eigenschaften Blätter](property-sheets-mfc.md)
