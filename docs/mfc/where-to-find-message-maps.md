---
title: Wo sich Meldungszuordnungen befinden
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360168"
---
# <a name="where-to-find-message-maps"></a>Wo sich Meldungszuordnungen befinden

Wenn Sie mit dem Anwendungs-Assistenten eine neue Skelettanwendung erstellen, schreibt der Anwendungs-Assistent eine Meldungszuordnung für jede Befehlszielklasse, die er für Sie erstellt. Dazu gehören die abgeleiteten Anwendungs-, Dokument-, Ansichts- und Framefensterklassen. Einige dieser Meldungszuordnungen verfügen bereits über die Vom Anwendungs-Assistenten für bestimmte Nachrichten und vordefinierten Befehle bereitgestellten Einträge, und einige sind nur Platzhalter für Handler, die Sie hinzufügen.

Die Meldungszuordnung einer Klasse befindet sich im . CPP-Datei für die Klasse. Wenn Sie mit den grundlegenden Nachrichtenzuordnungen arbeiten, die der Anwendungs-Assistent erstellt, verwenden Sie den [Klassen-Assistenten,](reference/mfc-class-wizard.md) um Einträge für die Nachrichten und Befehle hinzuzufügen, die von jeder Klasse verarbeitet werden. Eine typische Meldungszuordnung könnte wie folgt aussehen, nachdem Sie einige Einträge hinzugefügt haben:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Die Nachrichtenzuordnung besteht aus einer Sammlung von Makros. Zwei Makros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) und [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), klammern die Meldungszuordnung in Klammern. Andere Makros, `ON_COMMAND`z. B. , füllen den Inhalt der Meldungszuordnung aus.

> [!NOTE]
> Auf die Message-Map-Makros folgen keine Semikolons.

Wenn Sie den Assistenten zum Hinzufügen von Klassen verwenden, um eine neue Klasse zu erstellen, stellt er eine Meldungszuordnung für die Klasse bereit. Alternativ können Sie eine Meldungszuordnung manuell mit dem Quellcode-Editor erstellen.

## <a name="see-also"></a>Siehe auch

[So durchsucht das Framework Meldungszuordnungen](../mfc/how-the-framework-searches-message-maps.md)
