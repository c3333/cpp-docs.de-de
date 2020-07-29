---
title: 'Container: Client-Element-Zustände'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 660b544a0f061ae2e4435777cdd934367f2e7652
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228647"
---
# <a name="containers-client-item-states"></a>Container: Client-Element-Zustände

In diesem Artikel werden die verschiedenen Zustände erläutert, die ein Client Element während seiner Lebensdauer durchläuft.

Ein Client Element durchläuft mehrere Zustände, wenn es erstellt, aktiviert, geändert und gespeichert wird. Jedes Mal, wenn sich der Zustand des Elements ändert, ruft das Framework [COleClientItem:: OnChange](reference/coleclientitem-class.md#onchange) mit der **OLE_CHANGED_STATE** Benachrichtigung auf. Der zweite Parameter ist ein Wert aus der- `COleClientItem::ItemState` Enumeration. Folgende Werte sind möglich:

- *COleClientItem:: emptystate*

- *COleClientItem:: loadedstate*

- *COleClientItem:: openstate*

- *COleClientItem:: ActiveState*

- *COleClientItem:: activeuistate*

Im leeren Zustand ist ein Client Element noch nicht vollständig ein Element. Es wurde Arbeitsspeicher zugeordnet, aber noch nicht mit den Daten des OLE-Elements initialisiert. Dies ist der Zustand, in dem sich ein Client Element befindet, wenn es durch einen-Rückruf erstellt wurde, **`new`** aber noch nicht im zweiten Schritt der typischen zweistufigen Erstellung durchlaufen wurde.

Im zweiten Schritt, der durch einen Rückruf von `COleClientItem::CreateFromFile` oder eine andere `CreateFrom` *xxxx* -Funktion ausgeführt wird, wird das Element vollständig erstellt. Die OLE-Daten (aus einer Datei oder einer anderen Quelle, z. b. der Zwischenablage), wurden dem von `COleClientItem` abgeleiteten Objekt zugeordnet. Nun befindet sich das Element im geladenen Zustand.

Wenn ein Element im Fenster des Servers geöffnet wurde und nicht im Dokument des Containers geöffnet ist, befindet es sich im geöffneten (oder vollständigen geöffneten) Zustand. In diesem Zustand wird in der Regel eine Kreuz Schraffur über die Darstellung des Elements im Fenster des Containers gezeichnet, um anzugeben, dass das Element an anderer Stelle aktiv ist.

Wenn ein Element an Ort und Stelle aktiviert wurde, wird es normalerweise nur kurz durch den aktiven Status geleitet. Anschließend wechselt er in den aktiven Zustand der Benutzeroberfläche, in dem der Server seine Menüs, Symbolleisten und andere Benutzeroberflächen Komponenten mit denen des Containers zusammengeführt hat. Wenn diese Benutzeroberflächen Komponenten vorhanden sind, wird der aktive Zustand der UI vom aktiven Zustand unterschieden. Andernfalls ähnelt der aktive Zustand dem aktiven Zustand der UI. Wenn der Server rückgängig unterstützt, muss der Server die rückgängig-Zustandsinformationen des OLE-Elements aufbewahren, bis er den Status "geladen" oder "geöffnet" erreicht.

## <a name="see-also"></a>Siehe auch

[Container](containers.md)<br/>
[Aktivierung](activation-cpp.md)<br/>
[Container: Client-Element-Benachrichtigungen](containers-client-item-notifications.md)<br/>
[Tracker](trackers.md)<br/>
[CRectTracker-Klasse](reference/crecttracker-class.md)
