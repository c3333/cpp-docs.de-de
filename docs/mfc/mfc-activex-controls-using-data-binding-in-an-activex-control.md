---
title: 'MFC-ActiveX-Steuerelemente: Verwenden der Datenbindung in einem ActiveX-Steuerelement'
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 41ac0180242aea3143a1df2c32dc81fb18cd7dca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370782"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Verwenden der Datenbindung in einem ActiveX-Steuerelement

Eine der leistungsstärkeren Verwendungen von ActiveX-Steuerelementen ist die Datenbindung, die es einer Eigenschaft des Steuerelements ermöglicht, eine Bindung an ein bestimmtes Feld in einer Datenbank zu ermöglichen. Wenn ein Benutzer Daten in dieser gebundenen Eigenschaft ändert, benachrichtigt das Steuerelement die Datenbank und fordert an, dass das Datensatzfeld aktualisiert wird. Die Datenbank benachrichtigt dann die Steuerung des Erfolgs oder Misserfolgs der Anforderung.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Dieser Artikel behandelt die Steuerungsseite Ihrer Aufgabe. Das Implementieren der Datenbindungsinteraktionen mit der Datenbank liegt in der Verantwortung des Steuerelementcontainers. Die Verwaltung der Datenbankinteraktionen in Ihrem Container geht über den Rahmen dieser Dokumentation hinaus. Wie Sie das Steuerelement für die Datenbindung vorbereiten, wird im Rest dieses Artikels erläutert.

![Konzeptdiagramm eines Daten-&#45;gebundenen Steuerelements](../mfc/media/vc374v1.gif "Konzeptdiagramm eines Daten-&#45;gebundenen Steuerelements") <br/>
Konzeptdiagramm eines datengebundenen Steuerelements

Die `COleControl` Klasse stellt zwei Memberfunktionen bereit, die die Datenbindung einfach zu implementieren machen. Die erste Funktion, [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), wird verwendet, um die Berechtigung zum Ändern des Eigenschaftswerts anzufordern. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), die zweite Funktion, wird aufgerufen, nachdem der Eigenschaftswert erfolgreich geändert wurde.

In diesem Artikel werden die folgenden Themen behandelt:

- [Erstellen einer bindbaren Bestandseigenschaft](#vchowcreatingbindablestockproperty)

- [Erstellen einer bindbaren Get/Set-Methode](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Erstellen einer bindbaren Bestandseigenschaft

Es ist möglich, eine datengebundene Bestandseigenschaft zu erstellen, obwohl es wahrscheinlicher ist, dass Sie eine [bindbare get/set-Methode](#vchowcreatingbindablegetsetmethod)benötigen.

> [!NOTE]
> Bestandseigenschaften `bindable` haben `requestedit` die und Attribute standardmäßig.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>So fügen Sie eine bindbare Bestandseigenschaft mithilfe des Eigenschaften-Assistenten hinzufügen hinzu

1. Starten Sie ein Projekt mit dem [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md).

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten für Ihr Steuerelement.

   Dadurch wird das Kontextmenü geöffnet.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

1. Wählen Sie einen der Einträge aus der Dropdownliste **Eigenschaftenname** aus. Sie können z. B. **Text**auswählen.

   Da **Text** eine bestandsgebundene Eigenschaft ist, sind die **Attribute bindable** und **requestedit** bereits überprüft.

1. Aktivieren Sie die folgenden Kontrollkästchen auf der Registerkarte **IDL Attribute:** **displaybind** und **defaultbind,** um die Attribute der Eigenschaftsdefinition im Projekt hinzuzufügen. IDL-Datei. Diese Attribute machen das Steuerelement für den Benutzer sichtbar und machen die stock-Eigenschaft zur standardmäßig bindbaren Eigenschaft.

An diesem Punkt kann das Steuerelement Daten aus einer Datenquelle anzeigen, aber der Benutzer kann keine Datenfelder aktualisieren. Wenn Ihr Steuerelement auch Daten aktualisieren kann, `OnOcmCommand` ändern Sie die [OnOcmCommand-Funktion so,](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) dass sie wie folgt aussieht:

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Sie können nun das Projekt erstellen, das das Steuerelement registriert. Wenn Sie das Steuerelement in ein Dialogfeld einfügen, werden die **Eigenschaften Datenfeld** und **Datenquelle** hinzugefügt, und Sie können nun eine Datenquelle und ein Feld auswählen, die im Steuerelement angezeigt werden sollen.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Erstellen einer bindbaren Get/Set-Methode

Zusätzlich zu einer datengebundenen get/set-Methode können Sie auch eine [bindbare Bestandseigenschaft](#vchowcreatingbindablestockproperty)erstellen.

> [!NOTE]
> Bei diesem Verfahren wird davon ausgegangen, dass Sie über ein ActiveX-Steuerelementprojekt verfügen, das ein Windows-Steuerelement unterklassen.

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>So fügen Sie eine bindbare get/set-Methode mithilfe des Eigenschaften-Assistenten hinzufügen

1. Laden Sie das Steuerelementprojekt.

1. Wählen Sie auf der Seite **Steuerelementeinstellungen** eine Fensterklasse für das Steuerelement für die Unterklasse aus. Sie können z. B. ein EDIT-Steuerelement unterklassieren.

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten für Ihr Steuerelement.

   Dadurch wird das Kontextmenü geöffnet.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

1. Geben Sie den Eigenschaftsnamen in das Feld **Eigenschaftenname** ein. Verwenden `MyProp` Sie diese Beispieldatei.

1. Wählen Sie einen Datentyp aus dem Dropdown-Listenfeld **Eigenschaftentyp** aus. Verwenden Sie für dieses Beispiel **kurz.**

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Aktivieren Sie die folgenden Kontrollkästchen auf der Registerkarte IDL-Attribute: **bindable**, **requestedit**, **displaybind**und **defaultbind,** um die Attribute der Eigenschaftsdefinition im Projekt hinzuzufügen. IDL-Datei. Diese Attribute machen das Steuerelement für den Benutzer sichtbar und machen die stock-Eigenschaft zur standardmäßig bindbaren Eigenschaft.

1. Klicken Sie auf **Fertig stellen**.

1. Ändern Sie den `SetMyProp` Text der Funktion so, dass sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Der Parameter, `BoundPropertyChanged` der `BoundPropertyRequestEdit` an die und-Funktionen übergeben wird, ist die Dispid der Eigenschaft, d. h. der Parameter, der an das id()-Attribut für die Eigenschaft im übergeben wird. IDL-Datei.

1. Ändern Sie die [OnOcmCommand-Funktion so,](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) dass sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Ändern `OnDraw` Sie die Funktion so, dass sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Fügen Sie dem öffentlichen Abschnitt der Headerdatei die Headerdatei für die Steuerelementklasse hinzu, und fügen Sie die folgenden Definitionen (Konstruktoren) für Membervariablen hinzu:

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Machen Sie die folgende Zeile `DoPropExchange` zur letzten Zeile in der Funktion:

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Ändern `OnResetState` Sie die Funktion so, dass sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Ändern `GetMyProp` Sie die Funktion so, dass sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Sie können nun das Projekt erstellen, das das Steuerelement registriert. Wenn Sie das Steuerelement in ein Dialogfeld einfügen, werden die **Eigenschaften Datenfeld** und **Datenquelle** hinzugefügt, und Sie können nun eine Datenquelle und ein Feld auswählen, die im Steuerelement angezeigt werden sollen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
