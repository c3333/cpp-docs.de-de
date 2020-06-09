---
title: 'MFC-ActiveX-Steuerelemente: Verwenden von Bildern in einem ActiveX-Steuerelement'
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 9eb204dd240ae17421a20b7cddeff56c9a22c19b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618076"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Verwenden von Bildern in einem ActiveX-Steuerelement

In diesem Artikel werden der allgemeine Bildtyp und dessen Implementierung in das ActiveX-Steuerelement beschrieben. Dabei werden folgende Themen behandelt:

- [Übersicht über benutzerdefinierte Bildeigenschaften](#_core_overview_of_custom_picture_properties)

- [Implementieren einer benutzerdefinierten Bildeigenschaft in das ActiveX-Steuerelement](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Ergänzungen zum Steuerelement Projekt](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a> Übersicht über benutzerdefinierte Bildeigenschaften

Der Bildtyp (Picture) gehört zu einer Gruppe von Datentypen, die für einige ActiveX-Steuerelemente verfügbar sind. Dieser Typ behandelt Metadateien, Bitmaps oder Symbole und ermöglicht dem Benutzer die Festlegung eines Bildes, das in einem ActiveX-Steuerelement angezeigt werden soll. Benutzerdefinierte Bildeigenschaften werden mithilfe eines Bildobjekts und der Get-/Set-Funktionen implementiert, die dem Steuerelementbenutzer den Zugriff auf die Bildeigenschaft ermöglichen. Steuerelementbenutzer greifen über die vordefinierten Bildeeigenschaften auf die benutzerdefinierte Bildeigenschaft zu.

Neben dem Standardbildtyp sind auch Schriftart- und Farbtypen verfügbar. Weitere Informationen zur Verwendung des standardmäßigen Schriftarttyps im ActiveX-Steuerelement finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Verwenden von Schriftarten](mfc-activex-controls-using-fonts.md).

Die ActiveX-Steuerelementklassen stellen mehrere Komponenten bereit, die Sie zum Implementieren der Bildeigenschaft im Steuerelement verwenden können. Zu diesen Komponenten gehören:

- Die [CPictureHolder](reference/cpictureholder-class.md) -Klasse.

   Diese Klasse ermöglicht den einfachen Zugriff auf das Bildobjekt und die Funktionen des Elements, das mittels der benutzerdefinierten Bildeigenschaft angezeigt wird.

- Unterstützung der Eigenschaften vom Typ **LPPICTUREDISP**, die mit Get-/Set-Funktionen implementiert wurden.

   In der Klassenansicht können Sie schnell eine oder mehrere benutzerdefinierte Eigenschaften hinzufügen, die den Bildtyp unterstützen. Weitere Informationen zum Hinzufügen von ActiveX-Steuerelementeigenschaften in der Klassenansicht finden Sie unter [MFC-ActiveX-Steuerelemente: Eigenschaften](mfc-activex-controls-properties.md).

- Eine Eigenschaftenseite, über die die Bildeigenschaft(en) eines Steuerelements geändert werden.

   Diese Eigenschaftenseite ist Bestandteil einer Reihe vordefinierter Eigenschaftenseiten, die für ActiveX-Steuerelemente verfügbar sind. Weitere Informationen zu Eigenschaftenseiten von ActiveX-Steuerelementen finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Verwenden von vordefinierten Eigenschaftenseiten](mfc-activex-controls-using-stock-property-pages.md).

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implementieren einer benutzerdefinierten Bild Eigenschaft in das ActiveX-Steuerelement

Nachdem Sie die Schritte in diesem Abschnitt durchgeführt haben, kann das Steuerelement die vom Benutzer ausgewählten Bilder anzeigen. Der Benutzer kann das angezeigte Bild mithilfe einer Eigenschaftenseite ändern, auf der das aktuelle Bild angezeigt wird und die über eine Navigationsschaltfläche verfügt, die dem Benutzer die Auswahl verschiedener Bilder ermöglicht.

Eine benutzerdefinierte Bildeigenschaft wird in einem ähnlichen Prozess wie andere Eigenschaften implementiert. Der Hauptunterschied liegt darin, dass die benutzerdefinierte Eigenschaft einen Bildtyp unterstützen muss. Da das Element der Bildeigenschaft vom ActiveX-Steuerelement dargestellt werden muss, müssen eine Reihe von Zusätzen und Änderungen für die Eigenschaft vorgenommen werden, bevor sie vollständig implementiert werden kann.

Um eine benutzerdefinierte Bildeigenschaft zu implementieren, gehen Sie wie folgt vor:

- [Fügen Sie dem Steuerelementprojekt Code hinzu](#_core_additions_to_your_control_project).

   Folgendes muss hinzugefügt werden: Eine Eigenschaftenseiten-ID für die Standardbildeigenschaften, ein Datenmember vom Typ `CPictureHolder`und eine benutzerdefinierte Eigenschaft vom Typ **LPPICTUREDISP** mit einer Get-/Set-Implementierung.

- [Ändern Sie mehrere Funktionen in der Steuerelementklasse](#_core_modifications_to_your_control_project).

   Diese Änderungen werden für mehrere Funktionen ausgeführt, die für die Darstellung des ActiveX-Steuerelements verantwortlich sind.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a> Zusätze zum Steuerelementprojekt

Um die Eigenschaften Seiten-ID für die Standardbild Eigenschaften Seite hinzuzufügen, fügen Sie die folgende Zeile nach dem BEGIN_PROPPAGEIDS-Makro in der Implementierungs Datei des Steuer Elements () ein. Cpp):

[!code-cpp[NVC_MFC_AxPic#1](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

Außerdem müssen Sie den count-Parameter des BEGIN_PROPPAGEIDS-Makros um 1 erhöhen. Die folgende Zeile veranschaulicht dies:

[!code-cpp[NVC_MFC_AxPic#2](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Um der Steuerelementklasse den `CPictureHolder` -Datenmember hinzuzufügen, fügen Sie in der Headerdatei des Steuerelements (.H) unter dem protected-Abschnitt der Deklaration der Steuerelementklasse die folgende Zeile ein:

[!code-cpp[NVC_MFC_AxPic#3](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

Es ist nicht notwendig, den Datenmember *m_pic*zu benennen; Jeder Name ist ausreichend.

Fügen Sie als nächstes eine benutzerdefinierte Eigenschaft hinzu, die einen Bildtyp unterstützt:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>So fügen Sie eine benutzerdefinierte Bildeigenschaft mit dem Assistenten zum Hinzufügen von Eigenschaften hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Wählen Sie im Kontextmenü **Hinzufügen** und dann **Eigenschaft hinzufügen**aus.

1. Geben Sie im Feld **Eigenschaftsname** den Namen der Eigenschaft ein. In diesem Verfahren wird z. B. `ControlPicture` verwendet.

1. Wählen Sie im Feld **Eigenschaftentyp** die Option **IPictureDisp** <strong>\*</strong> für den Eigenschaftentyp aus.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Geben Sie für die Get- und Set-Funktion eindeutige Namen ein, oder übernehmen Sie die Standardnamen. (In diesem Beispiel werden die Standardnamen `GetControlPicture` und `SetControlPicture` verwendet.

1. Klicken Sie auf **Fertig stellen**.

Der Assistent zum Hinzufügen von Eigenschaften fügt den folgenden Code zwischen den Kommentaren der Dispatchzuordnung in der Headerdatei (.h) des Steuerelements ein:

[!code-cpp[NVC_MFC_AxPic#4](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Zusätzlich wurde folgender Code in die Dispatchzuordnung der Implementierungsdatei (.CPP) des Steuerelements eingefügt:

[!code-cpp[NVC_MFC_AxPic#5](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

Der Assistent zum Hinzufügen von Eigenschaften fügt der Implementierungsdatei des Steuerelements auch die folgenden beiden Stubfunktionen hinzu:

[!code-cpp[NVC_MFC_AxPic#6](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> Die von Ihnen verwendeten Steuerelementklassen und Funktionsnamen können von denen im oben genannten Beispiel abweichen.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a> Änderungen am Steuerelementprojekt

Nachdem Sie dem Steuerelementprojekt die notwendigen Zusätze hinzugefügt haben, müssen Sie mehrere Funktionen ändern, die das Rendern des ActiveX-Steuerelements beeinflussen. Die Funktionen `OnResetState`und `OnDraw`sowie die Get-/Set-Funktionen einer benutzerdefinierten Bildeigenschaft befinden sich in der Implementierungsdatei des Steuerelements. (Beachten Sie, dass in diesem Beispiel die Steuerelement Klasse aufgerufen wird `CSampleCtrl` , der `CPictureHolder` Datenmember *m_pic*aufgerufen wird und der Name der benutzerdefinierten Bild Eigenschaft lautet `ControlPicture` .)

Fügen Sie in der `OnResetState` -Funktion des Steuerelements hinter dem Aufruf von `COleControl::OnResetState`die folgende optionale Zeile ein:

[!code-cpp[NVC_MFC_AxPic#7](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

Dadurch wird dem Bild des Steuerelements ein leeres Bild zugewiesen.

Rufen Sie [CPictureHolder::Render](reference/cpictureholder-class.md#render) in der `OnDraw` -Funktion des Steuerelements auf, um das Bild einwandfrei darzustellen. Ändern Sie die Funktion entsprechend dem folgenden Beispiel:

[!code-cpp[NVC_MFC_AxPic#8](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

Fügen Sie in der Get-Funktion der benutzerdefinierten Bildeigenschaft des Steuerelements die folgende Zeile hinzu:

[!code-cpp[NVC_MFC_AxPic#9](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

Fügen Sie in der Set-Funktion der benutzerdefinierten Bildeigenschaft des Steuerelements die folgenden Zeilen hinzu:

[!code-cpp[NVC_MFC_AxPic#10](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

Die Bildeigenschaft muss persistent sein, damit beim Entwurf hinzugefügte Informationen zur Laufzeit angezeigt werden. Fügen Sie der `COleControl`-Funktion der von `DoPropExchange` abgeleiteten Klasse die folgende Zeile hinzu:

[!code-cpp[NVC_MFC_AxPic#11](codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> Die von Ihnen verwendeten Klassen und Funktionsnamen können von denen im oben genannten Beispiel abweichen.

Nachdem Sie die Änderungen vorgenommen haben, erstellen Sie das Projekt neu, um die neue Funktionalität der benutzerdefinierten Bildeigenschaft einzubinden. Testen Sie die neue Eigenschaft dann mit dem Testcontainer. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](testing-properties-and-events-with-test-container.md) .

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Verwenden von Schriftarten](mfc-activex-controls-using-fonts.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaftenseite](mfc-activex-controls-property-pages.md)
