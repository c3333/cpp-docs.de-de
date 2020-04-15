---
title: Erstellen von Stack- und Warteschlangenauflistungen
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: 5b3427f7bb2e46435ddf2768bcbb816f9d7e5c1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371609"
---
# <a name="creating-stack-and-queue-collections"></a>Erstellen von Stack- und Warteschlangenauflistungen

In diesem Artikel wird erläutert, wie Sie aus MFC-Listenklassen andere Datenstrukturen, z. B. [Stapel](#_core_stacks) und [Warteschlangen,](#_core_queues)erstellen. Die Beispiele verwenden `CList`Klassen, die `CList` von abgeleitet sind, sie können jedoch direkt verwendet werden, es sei denn, Sie müssen Funktionen hinzufügen.

## <a name="stacks"></a><a name="_core_stacks"></a>Stacks

Da die Standardlistenauflistung sowohl einen Kopf als auch einen Schwanz hat, ist es einfach, eine abgeleitete Listenauflistung zu erstellen, die das Verhalten eines Last-in-First-Out-Stacks imitiert. Ein Stapel ist wie ein Stapel Von Tabletts in einer Cafeteria. Wenn Schalen dem Stapel hinzugefügt werden, werden sie auf den Stapel gesetzt. Das letzte hinzugefügte Fach ist das erste, das entfernt wird. Die Listenauflistungsmemberfunktionen `AddHead` und `RemoveHead` können verwendet werden, um Elemente speziell aus dem Kopf der Liste hinzuzufügen und zu entfernen. Daher ist das zuletzt hinzugefügte Element das erste, das entfernt wird.

#### <a name="to-create-a-stack-collection"></a>So erstellen Sie eine Stapelsammlung

1. Leiten Sie eine neue Listenklasse von einer der vorhandenen MFC-Listenklassen ab, und fügen Sie weitere Memberfunktionen hinzu, um die Funktionalität von Stapelvorgängen zu unterstützen.

   Das folgende Beispiel zeigt, wie Sie Memberfunktionen hinzufügen, um Elemente auf den Stapel zu verschieben, einen Blick auf das obere Element des Stapels zu werfen und das oberste Element aus dem Stapel zu platzieren:

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Beachten Sie, dass dieser `CObList` Ansatz die zugrunde liegende Klasse verfügbar macht. Der Benutzer kann `CObList` jede Memberfunktion aufrufen, unabhängig davon, ob dies für einen Stack sinnvoll ist oder nicht.

## <a name="queues"></a><a name="_core_queues"></a>-Warteschlangen

Da die Standardlistenauflistung sowohl einen Kopf als auch einen Schwanz hat, ist es auch einfach, eine abgeleitete Listenauflistung zu erstellen, die das Verhalten einer First-in-First-Out-Warteschlange imitiert. Eine Warteschlange ist wie eine Schlange von Menschen in einer Cafeteria. Die erste Person in der Reihe ist die erste, die bedient wird. Wenn immer mehr Leute kommen, gehen sie ans Ende der Linie, um zu warten, bis sie an der Reihe sind. Die Listenauflistungsmemberfunktionen `AddTail` können `RemoveHead` verwendet werden, um Elemente speziell aus dem Kopf oder Schwanz der Liste hinzuzufügen und zu entfernen. Daher ist das zuletzt hinzugefügte Element immer das letzte, das entfernt wird.

#### <a name="to-create-a-queue-collection"></a>So erstellen Sie eine Warteschlangensammlung

1. Leiten Sie eine neue Listenklasse aus einer der vordefinierten Listenklassen ab, die mit der Microsoft Foundation-Klassenbibliothek bereitgestellt werden, und fügen Sie weitere Memberfunktionen hinzu, um die Semantik von Warteschlangenvorgängen zu unterstützen.

   Das folgende Beispiel zeigt, wie Sie Memberfunktionen anfügen können, um ein Element am Ende der Warteschlange hinzuzufügen und das Element von der Vorderseite der Warteschlange abzurufen.

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Siehe auch

[Sammlungen](../mfc/collections.md)
