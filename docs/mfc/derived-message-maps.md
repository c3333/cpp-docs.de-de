---
title: Abgeleitete Meldungszuordnungen
description: Beschreibt die MFC-Nachrichtenverarbeitung.
ms.date: 09/23/2020
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 44c2180e441c91d34350c65bc17a53d1b650607c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414216"
---
# <a name="derived-message-maps"></a>Abgeleitete Meldungszuordnungen

Während der Nachrichten Behandlung ist das Überprüfen der eigenen Meldungs Zuordnung einer Klasse nicht das Ende der Nachrichten Zuordnungs Story. Was geschieht, wenn die Klasse `CMyView` (die von abgeleitet `CView` ist) keinen übereinstimmenden Eintrag für eine Nachricht hat?

Beachten Sie, dass `CView` die Basisklasse von `CMyView` wiederum von abgeleitet wird `CWnd` . Folglich `CMyView` *ist* ein `CView` und *is* ein `CWnd` . Jede dieser Klassen verfügt über eine eigene Meldungs Zuordnung. Die folgende Abbildung zeigt die hierarchische Beziehung der-Klassen, aber beachten Sie, dass ein- `CMyView` Objekt ein einzelnes Objekt ist, das über die Merkmale aller drei Klassen verfügt.

![Ansichtshierarchie](../mfc/media/vc38621.gif "Ansichtshierarchie") <br/>
Eine Ansichts Hierarchie

Wenn eine Nachricht nicht in der Meldungs Zuordnung der Klasse abgeglichen werden kann `CMyView` , durchsucht das Framework auch die Meldungs Zuordnung der unmittelbaren Basisklasse. Das `BEGIN_MESSAGE_MAP` Makro am Anfang der Nachrichten Zuordnung gibt zwei Klassennamen als Argumente an:

[!code-cpp[NVC_MFCMessageHandling#2](codesnippet/cpp/derived-message-maps_1.cpp)]

Das erste Argument benennt die Klasse, zu der die Meldungs Zuordnung gehört. Das zweite Argument stellt in diesem Fall eine Verbindung mit der unmittelbaren Basisklasse bereit, `CView` sodass das Framework auch seine Meldungs Zuordnung durchsuchen kann.

Die in einer Basisklasse bereitgestellten Meldungs Handler werden daher von der abgeleiteten Klasse geerbt. Dies ähnelt den normalen virtuellen Element Funktionen, ohne dass alle handlermember-Funktionen virtuell sein müssen.

Wenn in einer der Basisklassen-Nachrichten Zuordnungen kein Handler gefunden wird, wird die Standard Verarbeitung der Nachricht ausgeführt. Wenn es sich bei der Nachricht um einen Befehl handelt, leitet das Framework Sie an das nächste Befehls Ziel weiter. Wenn es sich um eine standardmäßige Windows-Meldung handelt, wird die Nachricht an die entsprechende Standardfenster Prozedur übermittelt.

Um den Nachrichten Zuordnungs Abgleich zu beschleunigen, speichert das Framework letzte Übereinstimmungen mit der Wahrscheinlichkeit zwischen, dass die Nachricht erneut empfangen wird. Eine Folge davon ist, dass das Framework nicht behandelte Nachrichten Recht effizient verarbeitet. Nachrichten Zuordnungen sind auch mehr Speicherplatz effizienter als Implementierungen, die virtuelle Funktionen verwenden.

## <a name="see-also"></a>Weitere Informationen

[Wie das Framework Meldungs Zuordnungen durchsucht](how-the-framework-searches-message-maps.md)
