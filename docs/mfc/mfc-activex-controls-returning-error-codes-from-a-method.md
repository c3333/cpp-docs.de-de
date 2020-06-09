---
title: 'MFC-ActiveX-Steuerelemente: Zurückgeben von Fehlercodes aus einer Methode'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 1f7564d750b476ac3f57656f3392e0801652e5d5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615519"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC-ActiveX-Steuerelemente: Zurückgeben von Fehlercodes aus einer Methode

In diesem Artikel wird beschrieben, wie Fehlercodes von einer ActiveX-Steuerelement Methode zurückgegeben werden.

Um anzugeben, dass ein Fehler in einer Methode aufgetreten ist, sollten Sie die [COleControl:: ThrowError](reference/colecontrol-class.md#throwerror) -Member-Funktion verwenden, die einen SCODE (Statuscode) als Parameter annimmt. Sie können einen vordefinierten SCODE verwenden oder einen eigenen definieren.

> [!NOTE]
> `ThrowError`ist nur als Methode zum Zurückgeben eines Fehlers innerhalb der Get-oder Set-Funktion einer Eigenschaft oder einer Automatisierungs Methode vorgesehen. Dies ist das einzige Mal, dass der entsprechende Ausnahmehandler auf dem Stapel vorhanden ist.

Hilfsfunktionen sind für die gängigsten vordefinierten scodes vorhanden, z. b. [COleControl:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl:: GetNotSupported](reference/colecontrol-class.md#getnotsupported)und [COleControl:: setnotzugelassene](reference/colecontrol-class.md#setnotpermitted).

Eine Liste der vordefinierten scodes und Anweisungen zum Definieren von benutzerdefinierten scodes finden Sie im Abschnitt [Behandeln von Fehlern in Ihrem ActiveX-Steuer](mfc-activex-controls-advanced-topics.md) Element in ActiveX-Steuerelementen: Advanced Topics.

Weitere Informationen zum Melden von Ausnahmen in anderen Bereichen Ihres Codes finden Sie unter [COleControl:: FireError](reference/colecontrol-class.md#fireerror) und im Abschnitt [Behandeln von Fehlern im ActiveX-Steuer](mfc-activex-controls-advanced-topics.md) Element in ActiveX-Steuerelemente: Weiterführende Themen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
