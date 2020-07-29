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
ms.openlocfilehash: b32dbd8e1777f11998085a90e8851b25e4298e1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224993"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Verwenden der Datenbindung in einem ActiveX-Steuerelement

Eine der leistungsstärkeren Verwendungsmöglichkeiten von ActiveX-Steuerelementen ist die Datenbindung, mit der eine Eigenschaft des Steuer Elements an ein bestimmtes Feld in einer Datenbank gebunden werden kann. Wenn ein Benutzerdaten in dieser gebundenen Eigenschaft ändert, benachrichtigt das-Steuerelement die Datenbank und fordert an, dass das Daten Satz Feld aktualisiert wird. Die Datenbank benachrichtigt dann die Kontrolle über den Erfolg oder das Fehlschlagen der Anforderung.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

In diesem Artikel wird die Steuerungs Seite ihrer Aufgabe behandelt. Das Implementieren der Daten Bindungs Interaktionen mit der Datenbank liegt in der Verantwortung des Control-Containers. Die Verwaltung der Daten Bank Interaktionen in Ihrem Container geht über den Rahmen dieser Dokumentation hinaus. Wie Sie das Steuerelement für die Datenbindung vorbereiten, wird im restlichen Artikel erläutert.

![Konzeptionelles Diagramm eines Daten&#45;gebundenen Steuer Elements](../mfc/media/vc374v1.gif "Konzeptionelles Diagramm eines Daten&#45;gebundenen Steuer Elements") <br/>
Konzeptionelles Diagramm eines Daten gebundenen Steuer Elements

Die- `COleControl` Klasse stellt zwei Member-Funktionen bereit, die die Datenbindung zu einem leicht zu implementierenden Prozess machen. Die erste Funktion, [BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit), wird verwendet, um die Berechtigung zum Ändern des Eigenschafts Werts anzufordern. [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged), die zweite Funktion, wird aufgerufen, nachdem der Eigenschafts Wert erfolgreich geändert wurde.

In diesem Artikel werden die folgenden Themen behandelt:

- [Erstellen einer bindbaren Aktien Eigenschaft](#vchowcreatingbindablestockproperty)

- [Erstellen einer bindbaren Get/Set-Methode](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>Erstellen einer bindbaren Aktien Eigenschaft

Es ist möglich, eine Daten gebundene Aktien Eigenschaft zu erstellen, obwohl es wahrscheinlicher ist, dass Sie eine [bindbare Get/Set-Methode](#vchowcreatingbindablegetsetmethod)benötigen.

> [!NOTE]
> Die Eigenschaften und verfügen `bindable` `requestedit` standardmäßig über die Attribute und.

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>So fügen Sie mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine bindbare Aktien Eigenschaft hinzu

1. Startet ein Projekt mithilfe des [MFC-ActiveX-Steuer](reference/mfc-activex-control-wizard.md)Element-Assistenten.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellen Knoten für das Steuerelement.

   Dadurch wird das Kontextmenü geöffnet.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

1. Wählen Sie einen der Einträge aus der Dropdown Liste **Eigenschaften Name** aus. Beispielsweise können Sie **Text**auswählen.

   Da es sich bei **Text** um eine Aktien Eigenschaft handelt, sind die Attribute **bindbare** und **requestedit** bereits aktiviert.

1. Aktivieren Sie auf der Registerkarte **IDL-Attribute** die folgenden Kontrollkästchen: **Display BIND** und **Defaultbind** , um der Eigenschafts Definition im Projekt die Attribute hinzuzufügen. IDL-Datei. Durch diese Attribute wird das Steuerelement für den Benutzer sichtbar, und die Stock-Eigenschaft ist die Standard Eigenschaft für die bindbare-Eigenschaft.

An diesem Punkt kann das Steuerelement Daten aus einer Datenquelle anzeigen, aber der Benutzer kann Datenfelder nicht aktualisieren. Wenn Sie möchten, dass das Steuerelement Daten auch aktualisieren kann, ändern Sie die `OnOcmCommand` [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) -Funktion so, dass Sie wie folgt aussieht:

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

Sie können nun das Projekt erstellen, das das Steuerelement registriert. Wenn Sie das-Steuerelement in ein Dialogfeld einfügen, werden das **Datenfeld** und die **Datenquellen** Eigenschaften hinzugefügt, und Sie können nun eine Datenquelle und ein Feld auswählen, die im Steuerelement angezeigt werden sollen.

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>Erstellen einer bindbaren Get/Set-Methode

Zusätzlich zu einer Daten gebundenen Get/Set-Methode können Sie auch eine [bindbare Aktien Eigenschaft](#vchowcreatingbindablestockproperty)erstellen.

> [!NOTE]
> Bei dieser Prozedur wird davon ausgegangen, dass Sie ein ActiveX-Steuerelement Projekt haben, das ein Windows-Steuerelement

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>So fügen Sie mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine bindbare Get/Set-Methode hinzu

1. Laden Sie das Steuerelementprojekt.

1. Wählen Sie auf der Seite **Steuerungseinstellungen** eine Fenster Klasse für das Steuerelement für die Unterklasse aus. Beispielsweise kann es sein, dass Sie ein Bearbeitungs Steuerelement unterteilen möchten.

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellen Knoten für das Steuerelement.

   Dadurch wird das Kontextmenü geöffnet.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

1. Geben Sie im Feld **Eigenschaftsname** den Namen der Eigenschaft ein. Verwenden Sie `MyProp` für dieses Beispiel.

1. Wählen Sie im Dropdown-Listenfeld **Eigenschaftentyp** einen Datentyp aus. Verwenden Sie **`short`** für dieses Beispiel.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Aktivieren Sie auf der Registerkarte IDL-Attribute die folgenden Kontrollkästchen: **bindbare**, **requestedit**, **Display BIND**und **Defaultbind** , um die Attribute der Eigenschafts Definition im Projekt hinzuzufügen. IDL-Datei. Durch diese Attribute wird das Steuerelement für den Benutzer sichtbar, und die Stock-Eigenschaft ist die Standard Eigenschaft für die bindbare-Eigenschaft.

1. Klicken Sie auf **Fertig stellen**.

1. Ändern Sie den Text der `SetMyProp` Funktion so, dass Sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. Der-Parameter, der an die `BoundPropertyChanged` -Funktion und die-Funktion übergeben wird `BoundPropertyRequestEdit` , ist die DispID der-Eigenschaft, die dem-Parameter entspricht, der an das ID ()-Attribut für die-Eigenschaft in IDL-Datei.

1. Ändern Sie die [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md) -Funktion, sodass Sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. Ändern Sie die- `OnDraw` Funktion, sodass Sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. Fügen Sie dem Abschnitt Public der Header Datei die Header Datei für die Steuerelement Klasse die folgenden Definitionen (Konstruktoren) für Element Variablen hinzu:

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. Legen Sie die folgende Zeile in die letzte Zeile in der `DoPropExchange` Funktion:

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. Ändern Sie die- `OnResetState` Funktion, sodass Sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. Ändern Sie die- `GetMyProp` Funktion, sodass Sie den folgenden Code enthält:

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

Sie können nun das Projekt erstellen, das das Steuerelement registriert. Wenn Sie das-Steuerelement in ein Dialogfeld einfügen, werden das **Datenfeld** und die **Datenquellen** Eigenschaften hinzugefügt, und Sie können nun eine Datenquelle und ein Feld auswählen, die im Steuerelement angezeigt werden sollen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
