---
title: Verwenden von CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447103"
---
# <a name="using-canimatectrl"></a>Verwenden von CAnimateCtrl

Ein Animations Steuerelement, das von der-Klasse [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)dargestellt wird, ist ein Fenster, das einen Clip im Audio Video Interleaved Format (AVI) anzeigt – das standardmäßige Windows-Video-/Audio-Format. Ein AVI-Clip ist eine Reihe von bitmapframes, wie z. b. ein Film.

Da der Thread weiterhin ausgeführt wird, während der AVI-Clip angezeigt wird, besteht eine häufige Verwendung eines Animations Steuer Elements darin, die Systemaktivität während eines langen Vorgangs anzuzeigen. Im Dialogfeld Windows-Suche wird z. b. ein beweglicher Vergrößerungsglas angezeigt, während das System nach einer Datei sucht.

Animations Steuerelemente können nur einfache AVI-Clips abspielen, und Sie unterstützen keine Sounds. (Eine umfassende Liste der Einschränkungen finden Sie unter [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Da die Funktionen eines Animations Steuer Elements stark eingeschränkt sind und geändert werden können, sollten Sie eine Alternative verwenden, wie z. b. das mciwnd-Steuerelement, wenn Sie ein Steuerelement zum Bereitstellen von Multimedia-Wiedergabe-und/oder Aufzeichnungsfunktionen benötigen. Weitere Informationen zum mciwnd-Steuerelement finden Sie in der Multimedia-Dokumentation.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Verwenden eines Animationssteuerelements](../mfc/using-an-animation-control.md)

- [Von Animationssteuerelementen gesendete Benachrichtigungen](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Weitere Informationen

[Kontrollen](../mfc/controls-mfc.md)
