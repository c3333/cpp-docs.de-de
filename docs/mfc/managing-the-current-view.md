---
title: Verwalten der aktuellen Ansicht
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
ms.openlocfilehash: d2ce9d77234260ebcb1946dd381264fb6654a91c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621312"
---
# <a name="managing-the-current-view"></a>Verwalten der aktuellen Ansicht

Im Rahmen der Standard Implementierung von Rahmen Fenstern verfolgt ein Rahmen Fenster eine derzeit aktive Ansicht. Wenn das Rahmen Fenster mehr als eine Ansicht enthält, wie z. b. in einem Splitter Fenster, ist die aktuelle Ansicht die letzte Ansicht, die verwendet wird. Die aktive Ansicht ist unabhängig vom aktiven Fenster in Windows oder dem aktuellen Eingabefokus.

Wenn sich die aktive Ansicht ändert, benachrichtigt das Framework die aktuelle Ansicht durch Aufrufen der [OnActivateView](reference/cview-class.md#onactivateview) -Member-Funktion. Sie können erkennen, ob die Ansicht aktiviert oder deaktiviert wird, indem Sie `OnActivateView` den *bactivate* -Parameter untersuchen. Standardmäßig `OnActivateView` legt den Fokus auf die aktuelle Ansicht bei Aktivierung fest. Sie können `OnActivateView` überschreiben, um eine spezielle Verarbeitung durchzuführen, wenn die Ansicht deaktiviert oder erneut aktiviert wird. Beispielsweise können Sie besondere visuelle Hinweise bereitstellen, um die aktive Ansicht von anderen, inaktiven Ansichten zu unterscheiden.

Ein Rahmen Fenster leitet Befehle an die aktuelle (aktive) Ansicht weiter, wie in [Befehls Routing](command-routing.md)als Teil des Standard Befehls Routings beschrieben.

## <a name="see-also"></a>Siehe auch

[Verwenden von Rahmenfenstern](using-frame-windows.md)
