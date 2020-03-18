---
title: Verwenden von CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: e2002d96a1eba913e260fa92281f730355a83ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447241"
---
# <a name="using-chotkeyctrl"></a>Verwenden von CHotKeyCtrl

Bei einem von der Klasse [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)dargestellten Steuerelement für den Hot Key handelt es sich um ein Fenster, in dem eine Textdarstellung der Tastenkombination angezeigt wird, die der Benutzer eingibt, wie z. b. Strg + Umschalt + Q. Außerdem verwaltet er eine interne Darstellung dieses Schlüssels in Form eines Codes für einen virtuellen Schlüssel und einen Satz von Flags, die den UMSCHALT Zustand darstellen. Mit dem Steuerelement "Hot Key" wird die Hot Key-Taste nicht festgelegt – Dies liegt an Ihrem Programm. (Eine Liste der virtuellen Standardschlüssel Codes finden Sie unter Winuser. h.)

Verwenden Sie ein Hot Key-Steuerelement, um die Eingabe eines Benutzers zu erhalten, dem ein Fenster oder Thread zugeordnet werden soll. Hot Key-Steuerelemente werden häufig in Dialogfeldern verwendet, z. b. Wenn Sie den Benutzer auffordern, einen Hot Key zuzuweisen. Es ist Aufgabe des Programms, die Werte abzurufen, die den Hot-Schlüssel aus dem Steuerelement "Hot Key" beschreiben, und die entsprechenden Funktionen aufzurufen, um den Hot Key einem Fenster oder einem Thread zuzuordnen.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Verwenden eines Abkürzungstasten-Steuerelements](../mfc/using-a-hot-key-control.md)

- [Festlegen einer Abkürzungstaste](../mfc/setting-a-hot-key.md)

- [Globale Abkürzungstasten](../mfc/global-hot-keys.md)

- [Threadspezifische Abkürzungstasten](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Weitere Informationen

[Kontrollen](../mfc/controls-mfc.md)
