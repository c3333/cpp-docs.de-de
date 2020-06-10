---
title: Globale Abkürzungstasten
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 5fdcfbef1db0d20126f8eac144f74f8b92410504
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618735"
---
# <a name="global-hot-keys"></a>Globale Abkürzungstasten

Eine globale Hot-Taste ist einem bestimmten nicht untergeordneten Fenster zugeordnet. Es ermöglicht dem Benutzer, das Fenster in jedem Teil des Systems zu aktivieren. Eine Anwendung legt eine globale Taste für ein bestimmtes Fenster fest, indem die [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) Meldung an dieses Fenster gesendet wird. Wenn beispielsweise `m_HotKeyCtrl` das [CHotKeyCtrl](reference/chotkeyctrl-class.md) -Objekt ist und `pMainWnd` ein Zeiger auf das Fenster ist, das aktiviert werden soll, wenn die Hot-Taste gedrückt wird, können Sie den folgenden Code verwenden, um die im-Steuerelement angegebene Hot-Taste mit dem Fenster zuzuordnen, auf das von gezeigt wird `pMainWnd` .

[!code-cpp[NVC_MFCControlLadenDialog#18](codesnippet/cpp/global-hot-keys_1.cpp)]

Wenn der Benutzer eine globale Hot-Taste drückt, empfängt das angegebene Fenster eine [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) Meldung, die **SC_HOTKEY** als Typ des Befehls angibt. Diese Meldung aktiviert auch das Fenster, in dem Sie empfangen wird. Da diese Nachricht keine Informationen über die exakte Taste enthält, die gedrückt wurde, lässt die Verwendung dieser Methode nicht zu, dass unterschiedliche heiße Tasten unterscheiden, die an dasselbe Fenster angefügt werden können. Die Hot-Taste bleibt gültig, bis die Anwendung, die **WM_SETHOTKEY** gesendet hat, beendet wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CHotKeyCtrl](using-chotkeyctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
