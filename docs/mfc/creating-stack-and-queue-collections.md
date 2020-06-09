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
ms.openlocfilehash: 5db90422f78fc6ca3bc2a182f9569c33db56cad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623206"
---
# <a name="creating-stack-and-queue-collections"></a>Erstellen von Stack- und Warteschlangenauflistungen

In diesem Artikel wird erläutert, wie Sie andere Datenstrukturen (z. b. [Stapel](#_core_stacks) und [Warteschlangen](#_core_queues)) aus MFC-Listen Klassen erstellen. In den Beispielen werden von abgeleitete Klassen verwendet `CList` , Sie können jedoch direkt verwenden, `CList` es sei denn, Sie müssen Funktionen hinzufügen.

## <a name="stacks"></a><a name="_core_stacks"></a>Stöcke

Da die Standard Listen Auflistung sowohl einen Head-als auch ein-Tail aufweist, ist es einfach, eine abgeleitete Listen Auflistung zu erstellen, die das Verhalten eines Last-in-First-Out-Stapels imitiert. Ein Stapel gleicht einem Stapel von Tabletts in einer Cafeteria. Beim Hinzufügen von Tabletts zum Stapel werden diese auf dem Stapel abgelegt. Die letzte hinzugefügte Leiste ist die erste, die entfernt werden soll. Die Member der Listen Auflistungs `AddHead` `RemoveHead` Elemente und können zum Hinzufügen und Entfernen von Elementen verwendet werden, die sich speziell am Anfang der Liste befinden. Daher ist das zuletzt hinzugefügte Element das erste zu entfernende Element.

#### <a name="to-create-a-stack-collection"></a>So erstellen Sie eine Stapel Sammlung

1. Leiten Sie eine neue Listen Klasse aus einer der vorhandenen MFC-Listen Klassen ab, und fügen Sie weitere Element Funktionen hinzu, um die Funktionalität von Stapel Vorgängen zu unterstützen.

   Im folgenden Beispiel wird gezeigt, wie Element Funktionen hinzugefügt werden, um Elemente auf den Stapel zu übertragen, das oberste Element des Stapels einzusehen und das oberste Element aus dem Stapel zu bewegen:

   [!code-cpp[NVC_MFCCollections#20](codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Beachten Sie, dass dieser Ansatz die zugrunde liegende-Klasse verfügbar macht `CObList` . Der Benutzer kann jede `CObList` Member-Funktion, unabhängig davon, ob er für einen Stapel sinnvoll ist, aufruft.

## <a name="queues"></a><a name="_core_queues"></a>-Warteschlangen

Da die Standard Listen Auflistung sowohl eine Spitze als auch ein Ende hat, ist es auch einfach, eine abgeleitete Listen Auflistung zu erstellen, die das Verhalten einer First-in-First-Out-Warteschlange imitiert. Eine Warteschlange ist eine Reihe von Personen in einer Cafeteria. Die erste Person in der Zeile ist der erste, der verarbeitet werden soll. Wenn immer mehr Leute kommen, werden Sie an das Ende der Zeile weitergeleitet, um Ihre Zeit zu warten. Die Member der Listen Auflistungs `AddTail` `RemoveHead` Elemente und können zum Hinzufügen und Entfernen von Elementen verwendet werden, die sich speziell am Anfang oder am Ende der Liste befinden. Daher ist das zuletzt hinzugefügte Element immer das letzte, das entfernt werden soll.

#### <a name="to-create-a-queue-collection"></a>So erstellen Sie eine Warteschlangen Sammlung

1. Leiten Sie eine neue Listen Klasse aus einer der vordefinierten Listen Klassen ab, die mit dem Microsoft Foundation Class-Bibliothek bereitgestellt werden, und fügen Sie weitere Element Funktionen zur Unterstützung der Semantik von Warteschlangen Vorgängen hinzu

   Im folgenden Beispiel wird gezeigt, wie Sie Member-Funktionen anfügen können, um am Ende der Warteschlange ein Element hinzuzufügen und das Element vom Anfang der Warteschlange zu erhalten.

   [!code-cpp[NVC_MFCCollections#21](codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Siehe auch

[Sammlungen](collections.md)
