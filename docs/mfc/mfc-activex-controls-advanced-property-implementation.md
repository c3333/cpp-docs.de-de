---
title: 'MFC-ActiveX-Steuerelemente: Weiterführende Eigenschaftenimplementierung'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364651"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC-ActiveX-Steuerelemente: Weiterführende Eigenschaftenimplementierung

In diesem Artikel werden Themen im Zusammenhang mit der Implementierung erweiterter Eigenschaften in einem ActiveX-Steuerelement beschrieben.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

- [Schreibgeschützte und schreibgeschützte Eigenschaften](#_core_read2donly_and_write2donly_properties)

- [Zurückgeben von Fehlercodes aus einer Eigenschaft](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Schreibgeschützte und schreibgeschützte Eigenschaften

Der Add-Eigenschaften-Assistent bietet eine schnelle und einfache Methode zum Implementieren schreibgeschützter oder schreibgeschützter Eigenschaften für das Steuerelement.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>So implementieren Sie eine schreibgeschützte oder schreibgeschützte Eigenschaft

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der [Eigenschaften-Assistent hinzufügen](../ide/names-add-property-wizard.md)geöffnet.

1. Geben Sie im Feld **Eigenschaftenname** den Namen Ihrer Eigenschaft ein.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Wählen Sie im Feld **Eigenschaftentyp** den richtigen Typ für die Eigenschaft aus.

1. Wenn Sie eine schreibgeschützte Eigenschaft wünschen, deaktivieren Sie den Funktionsnamen Festlegen. Wenn Sie eine schreibgebundene Eigenschaft wünschen, deaktivieren Sie den Get-Funktionsnamen.

1. Klicken Sie auf **Fertig stellen**.

Wenn Sie dies tun, fügt der `SetNotSupported` `GetNotSupported` Eigenschaften-Assistent die Funktion oder in den Dispatch-Map-Eintrag anstelle einer normalen Set- oder Get-Funktion ein.

Wenn Sie eine vorhandene Eigenschaft schreibgeschützt oder schreibgeschützt ändern möchten, können Sie die Dispatchzuordnung manuell bearbeiten und die unnötige Set- oder Get-Funktion aus der Steuerelementklasse entfernen.

Wenn sie möchten, dass eine Eigenschaft bedingt schreibgeschützt oder schreibgeschützt ist (z. B. nur, wenn das Steuerelement in einem bestimmten `SetNotSupported` `GetNotSupported` Modus arbeitet), können Sie die Funktion Festlegen oder Abrufen als Normal bereitstellen und ggf. die oder-Funktion aufrufen. Beispiel:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Dieses Codebeispiel `SetNotSupported` ruft `m_bReadOnlyMode` auf, wenn der Datenmember **TRUE**ist. Wenn **FALSE**, dann wird die Eigenschaft auf den neuen Wert festgelegt.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Zurückgeben von Fehlercodes von einer Eigenschaft

Um anzugeben, dass beim Abholen oder Festlegen einer Eigenschaft `COleControl::ThrowError` ein Fehler aufgetreten ist, verwenden Sie die Funktion, die einen SCODE (Statuscode) als Parameter verwendet. Sie können einen vordefinierten SCODE verwenden oder einen Eigenen definieren. Eine Liste vordefinierter SCODEs und Anweisungen zum Definieren benutzerdefinierter SCODEs finden Sie unter Behandeln von [Fehlern in Ihrem ActiveX-Steuerelement](../mfc/mfc-activex-controls-advanced-topics.md) im Artikel ActiveX-Steuerelemente: Erweiterte Themen.

Hilfsfunktionen sind für die am häufigsten vordefinierten SCODEs vorhanden, z. B. [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)und [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`soll nur verwendet werden, um einen Fehler innerhalb der Get- oder Set-Funktion einer Eigenschaft oder einer Automatisierungsmethode zurückzugeben. Dies sind die einzigen Male, in denen der entsprechende Ausnahmehandler auf dem Stapel vorhanden ist.

Weitere Informationen zum Melden von Ausnahmen in anderen Bereichen des Codes finden Sie unter [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) und den Abschnitt [Umgang mit Fehlern in Ihrem ActiveX-Steuerelement](../mfc/mfc-activex-controls-advanced-topics.md) im Artikel ActiveX-Steuerelemente: Erweiterte Themen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaften](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](../mfc/reference/colecontrol-class.md)
