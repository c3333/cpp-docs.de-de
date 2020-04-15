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
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364544"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC-ActiveX-Steuerelemente: Zurückgeben von Fehlercodes aus einer Methode

In diesem Artikel wird beschrieben, wie Fehlercodes von einer ActiveX-Steuerelementmethode zurückgegeben werden.

Um anzugeben, dass innerhalb einer Methode ein Fehler aufgetreten ist, sollten Sie die [Memberfunktion COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) verwenden, die einen SCODE (Statuscode) als Parameter verwendet. Sie können einen vordefinierten SCODE verwenden oder einen Eigenen definieren.

> [!NOTE]
> `ThrowError`soll nur verwendet werden, um einen Fehler innerhalb der Get- oder Set-Funktion einer Eigenschaft oder einer Automatisierungsmethode zurückzugeben. Dies sind die einzigen Male, in denen der entsprechende Ausnahmehandler auf dem Stapel vorhanden ist.

Hilfsfunktionen sind für die am häufigsten vordefinierten SCODEs vorhanden, z. B. [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)und [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

Eine Liste vordefinierter SCODEs und Anweisungen zum Definieren benutzerdefinierter SCODEs finden Sie im Abschnitt Behandeln von [Fehlern in Ihrem ActiveX-Steuerelement](../mfc/mfc-activex-controls-advanced-topics.md) in ActiveX-Steuerelementen: Erweiterte Themen.

Weitere Informationen zum Melden von Ausnahmen in anderen Bereichen des Codes finden Sie unter [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) und den Abschnitt [Behandeln von Fehlern in Ihrem ActiveX-Steuerelement](../mfc/mfc-activex-controls-advanced-topics.md) in ActiveX-Steuerelementen: Erweiterte Themen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
