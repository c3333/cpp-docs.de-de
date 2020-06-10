---
title: 'MFC-ActiveX-Steuerelemente: Weiterführende Eigenschaftenimplementierung'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: f5abef4db2f9c6d375428c0b0fd313198ce6283f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621217"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC-ActiveX-Steuerelemente: Weiterführende Eigenschaftenimplementierung

Dieser Artikel beschreibt Themen im Zusammenhang mit der Implementierung von erweiterten Eigenschaften in einem ActiveX-Steuerelement.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

- [Schreibgeschützte und Lese geschützte Eigenschaften](#_core_read2donly_and_write2donly_properties)

- [Zurückgeben von Fehlercodes aus einer Eigenschaft](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Schreibgeschützte und Lese geschützte Eigenschaften

Der Assistent zum Hinzufügen von Eigenschaften bietet eine schnelle und einfache Methode zum Implementieren von schreibgeschützten oder Lese geschützten Eigenschaften für das Steuerelement.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>So implementieren Sie eine schreibgeschützte oder schreibgeschützte Eigenschaft

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der [Assistent zum Hinzufügen von Eigenschaften](../ide/names-add-property-wizard.md)geöffnet.

1. Geben Sie im Feld **Eigenschaftsname** den Namen der Eigenschaft ein.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Wählen Sie im Feld **Eigenschaftentyp** den richtigen Typ für die Eigenschaft aus.

1. Wenn Sie eine schreibgeschützte Eigenschaft wünschen, löschen Sie den Namen der Set-Funktion. Wenn Sie eine schreibgeschützte Eigenschaft wünschen, löschen Sie den Namen der Get-Funktion.

1. Klicken Sie auf **Fertig stellen**.

Wenn Sie dies tun, fügt der Assistent zum Hinzufügen von Eigenschaften die Funktion `SetNotSupported` oder `GetNotSupported` in den dispatchzuordnungseintrag anstelle einer normalen Set-oder Get-Funktion ein.

Wenn Sie eine vorhandene Eigenschaft so ändern möchten, dass Sie schreibgeschützt oder schreibgeschützt ist, können Sie die Dispatchzuordnung manuell bearbeiten und die unnötige Set-oder Get-Funktion aus der Steuerelement Klasse entfernen.

Wenn Sie möchten, dass eine Eigenschaft bedingt schreibgeschützt oder schreibgeschützt ist (z. b. nur, wenn das Steuerelement in einem bestimmten Modus betrieben wird), können Sie die Set-oder Get-Funktion wie gewohnt bereitstellen und die-oder-Funktion nach Bedarf aufzurufen `SetNotSupported` `GetNotSupported` . Beispiel:

[!code-cpp[NVC_MFC_AxUI#29](codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

In diesem Codebeispiel `SetNotSupported` wird aufgerufen, wenn der `m_bReadOnlyMode` Datenmember " **true**" ist. Wenn der Wert **false**ist, wird die-Eigenschaft auf den neuen Wert festgelegt.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Zurückgeben von Fehler Codes aus einer Eigenschaft

Um anzugeben, dass beim Versuch, eine Eigenschaft zu erhalten oder festzulegen, ein Fehler aufgetreten ist, verwenden Sie die- `COleControl::ThrowError` Funktion, die einen SCODE (Statuscode) als Parameter annimmt. Sie können einen vordefinierten SCODE verwenden oder einen eigenen definieren. Eine Liste der vordefinierten scodes und Anweisungen zum Definieren von benutzerdefinierten scodes finden [Sie unter Behandeln von Fehlern in Ihrem ActiveX-Steuer](mfc-activex-controls-advanced-topics.md) Element im Artikel ActiveX-Steuerelemente: Weiterführende Themen.

Hilfsfunktionen sind für die gängigsten vordefinierten scodes vorhanden, z. b. [COleControl:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl:: GetNotSupported](reference/colecontrol-class.md#getnotsupported)und [COleControl:: setnotzugelassene](reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`ist nur als Methode zum Zurückgeben eines Fehlers innerhalb der Get-oder Set-Funktion einer Eigenschaft oder einer Automatisierungs Methode vorgesehen. Dies ist das einzige Mal, dass der entsprechende Ausnahmehandler auf dem Stapel vorhanden ist.

Weitere Informationen zum Melden von Ausnahmen in anderen Codebereichen finden Sie unter [COleControl:: FireError](reference/colecontrol-class.md#fireerror) und im Abschnitt [Behandeln von Fehlern in Ihrem ActiveX-Steuer](mfc-activex-controls-advanced-topics.md) Element im Artikel ActiveX-Steuerelemente: Weiterführende Themen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaften](mfc-activex-controls-properties.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)
