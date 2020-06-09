---
title: Behandeln von QuickInfo-Benachrichtigungen
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 41e3dbfc2269f5fbf3c12dc00c19f8a2253fd16a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626449"
---
# <a name="handling-tool-tip-notifications"></a>Behandeln von QuickInfo-Benachrichtigungen

Wenn Sie den **TBSTYLE_TOOLTIPS** Stil angeben, erstellt und verwaltet die Symbolleiste ein QuickInfo-Steuerelement. Eine QuickInfo ist ein kleines Popup Fenster, das eine Textzeile enthält, in der eine Symbolleisten Schaltfläche beschrieben wird. Die QuickInfo ist ausgeblendet und wird nur angezeigt, wenn der Benutzer den Cursor auf eine Symbolleisten Schaltfläche setzt und ihn für ungefähr eine halbe Sekunde verlässt. Die QuickInfo wird in der Nähe des Cursors angezeigt.

Bevor die QuickInfo angezeigt wird, wird die **TTN_NEEDTEXT** Benachrichtigungs Meldung an das Besitzer Fenster der Symbolleiste gesendet, um den beschreibenden Text für die Schaltfläche abzurufen. Wenn das Besitzer Fenster der Symbolleiste ein `CFrameWnd` Fenster ist, werden Quick Infos ohne zusätzlichen Aufwand angezeigt, da `CFrameWnd` über einen Standard Handler für die **TTN_NEEDTEXT** Benachrichtigung verfügt. Wenn das Besitzer Fenster der Symbolleiste nicht von abgeleitet ist (z. b. `CFrameWnd` ein Dialogfeld oder eine Formularansicht), müssen Sie der Meldungs Zuordnung Ihres Besitzer Fensters einen Eintrag hinzufügen und einen Benachrichtigungs Handler in der Meldungs Zuordnung bereitstellen. Der Eintrag für die Meldungs Zuordnung Ihres Besitzer Fensters lautet wie folgt:

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>Hinweise

*Mitgliedschaft*<br/>
Die Member-Funktion, die aufgerufen werden soll, wenn Text für diese Schaltfläche benötigt wird.

Beachten Sie, dass die ID einer QuickInfo immer 0 ist.

Zusätzlich zur **TTN_NEEDTEXT** Benachrichtigung kann ein QuickInfo-Steuerelement die folgenden Benachrichtigungen an ein ToolBar-Steuerelement senden:

|benachrichtigungs-|Bedeutung|
|------------------|-------------|
|**TTN_NEEDTEXTA**|QuickInfo-Steuerelement erfordert ASCII-Text (nur Windows 95)|
|**TTN_NEEDTEXTW**|QuickInfo-Steuerelement erfordert Unicode-Text (nur Windows NT)|
|**TBN_HOTITEMCHANGE**|Gibt an, dass sich das heiße (hervorgehobene) Element geändert hat.|
|**NM_RCLICK**|Gibt an, dass der Benutzer rechts auf eine Schaltfläche geklickt hat.|
|**TBN_DRAGOUT**|Gibt an, dass der Benutzer auf die Schaltfläche geklickt und den Mauszeiger auf die Schaltfläche gezogen hat. Sie ermöglicht es einer Anwendung, Drag & Drop über eine Symbolleisten Schaltfläche zu implementieren. Beim Empfang dieser Benachrichtigung startet die Anwendung den Drag & Drop-Vorgang.|
|**TBN_DROPDOWN**|Gibt an, dass der Benutzer auf eine Schaltfläche geklickt hat, die den **TBSTYLE_DROPDOWN** Stil verwendet.|
|**TBN_GETOBJECT**|Gibt an, dass der Benutzer den Mauszeiger über eine Schaltfläche bewegt hat, die den **TBSTYLE_DROPPABLE** Stil verwendet.|

Eine Beispiel-Handlerfunktion und weitere Informationen zum Aktivieren von Quick Infos [finden Sie](tool-tips-in-windows-not-derived-from-cframewnd.md)unter Quick Infos.

## <a name="see-also"></a>Siehe auch

[Verwenden von CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
