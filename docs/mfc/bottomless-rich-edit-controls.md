---
title: Unbeschränkte Rich-Edit-Steuerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 567bb5b7f2eb2c203b40b9f1f6add82f5451d672
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616420"
---
# <a name="bottomless-rich-edit-controls"></a>Unbeschränkte Rich-Edit-Steuerelemente

Die Größe eines Rich-Edit-Steuer Elements ([CRichEditCtrl](reference/cricheditctrl-class.md)) kann von Ihrer Anwendung nach Bedarf geändert werden, sodass es immer die gleiche Größe wie der Inhalt hat. Ein Rich-Edit-Steuerelement unterstützt diese so genannte "nicht unterstützte" Funktion, indem das übergeordnete Fenster eine [EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize) Benachrichtigungs Meldung sendet, wenn sich die Größe seines Inhalts ändert.

Bei der Verarbeitung der **EN_REQUESTRESIZE** Benachrichtigungs Meldung sollte eine Anwendung die Größe des Steuer Elements auf die Dimensionen in der angegebenen [reqresize](/windows/win32/api/richedit/ns-richedit-reqresize) -Struktur ändern. Eine Anwendung kann auch alle Informationen in der Nähe des Steuer Elements verschieben, um die Änderung der Höhe des Steuer Elements zu ermöglichen. Um die Größe des Steuer Elements zu ändern, können Sie die `CWnd` Funktion [SetWindowPos](reference/cwnd-class.md#setwindowpos)verwenden.

Zum Senden einer **EN_REQUESTRESIZE** Benachrichtigungs Meldung mit der Member-Funktion [RequestResize](reference/cricheditctrl-class.md#requestresize) können Sie ein nicht verarbeiteter Rich-Edit-Steuerelement erzwingen. Diese Meldung kann im [OnSize](reference/cwnd-class.md#onsize) -Handler nützlich sein.

Um **EN_REQUESTRESIZE** Benachrichtigungs Meldungen zu empfangen, müssen Sie die Benachrichtigung mithilfe der `SetEventMask` Member-Funktion aktivieren.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
