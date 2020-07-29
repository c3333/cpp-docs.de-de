---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Eigenschaften'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 805fffcc6cafe92df91af6b01bb53240a0d70f51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230492"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Eigenschaften

Benutzerdefinierte Eigenschaften unterscheiden sich von den vordefinierten Eigenschaften darin, dass benutzerdefinierte Eigenschaften nicht bereits von der-Klasse implementiert werden `COleControl` . Eine benutzerdefinierte Eigenschaft wird verwendet, um einen bestimmten Zustand oder eine bestimmte Darstellung eines ActiveX-Steuer Elements für einen Programmierer mit dem-Steuerelement verfügbar zu machen.

In diesem Artikel wird beschrieben, wie Sie dem ActiveX-Steuerelement mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine benutzerdefinierte Eigenschaft hinzufügen und die resultierenden Codeänderungen erläutern. Dabei werden folgende Themen behandelt:

- [Verwenden des Assistenten zum Hinzufügen von Eigenschaften zum Hinzufügen einer benutzerdefinierten Eigenschaft](#_core_using_classwizard_to_add_a_custom_property)

- [Hinzufügen von Eigenschaften-Assistenten Änderungen für benutzerdefinierte Eigenschaften](#_core_classwizard_changes_for_custom_properties)

Benutzerdefinierte Eigenschaften sind in vier Arten von Implementierungen enthalten: Element Variable, Element Variable mit Benachrichtigung, Get/Set-Methoden und parametrisiert.

- Implementierung der Element Variablen

   Diese Implementierung stellt den Zustand der Eigenschaft als Member-Variable in der Steuerelement Klasse dar. Verwenden Sie die Implementierung der Element Variablen, wenn es nicht wichtig ist, zu wissen, wann sich der Eigenschafts Wert ändert. Von den drei Typen erstellt diese Implementierung die geringste Menge an Unterstützungs Code für die-Eigenschaft. Das Dispatch Map Entry-Makro für die Implementierung der Element Variablen ist [DISP_PROPERTY](reference/dispatch-maps.md#disp_property).

- Member-Variable mit Benachrichtigungs Implementierung

   Diese Implementierung besteht aus einer Element Variablen und einer Benachrichtigungsfunktion, die mit dem Assistenten zum Hinzufügen von Eigenschaften erstellt wurde. Die Benachrichtigungsfunktion wird automatisch vom Framework aufgerufen, nachdem sich der Eigenschafts Wert geändert hat. Verwenden Sie die Member-Variable mit der Benachrichtigungs Implementierung, wenn Sie benachrichtigt werden müssen, nachdem ein Eigenschafts Wert geändert wurde. Diese Implementierung erfordert mehr Zeit, da Sie einen Funktionsaufruf erfordert. Das Dispatch Map Entry-Makro für diese Implementierung ist [DISP_PROPERTY_NOTIFY](reference/dispatch-maps.md#disp_property_notify).

- Implementierung von Get/Set-Methoden

   Diese Implementierung besteht aus einem Paar von Element Funktionen in der Steuerelement Klasse. Die Get/Set-Methoden Implementierung ruft automatisch die Get Member-Funktion auf, wenn der Benutzer des Steuer Elements den aktuellen Wert der-Eigenschaft und die Set Member-Funktion anfordert, wenn der Benutzer des Steuer Elements anfordert, dass die-Eigenschaft geändert wird. Verwenden Sie diese Implementierung, wenn Sie den Wert einer Eigenschaft während der Laufzeit berechnen, einen vom Benutzer des Steuer Elements übergebenen Wert überprüfen müssen, bevor Sie die tatsächliche Eigenschaft ändern, oder einen Lese-oder schreibgeschützten Eigenschaftentyp implementieren. Das Dispatch Map Entry-Makro für diese Implementierung ist [DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex). Im folgenden Abschnitt [Verwenden des Assistenten zum Hinzufügen von Eigenschaften zum Hinzufügen einer benutzerdefinierten Eigenschaft](#_core_using_classwizard_to_add_a_custom_property)wird die benutzerdefinierte Eigenschaft CircleOffset verwendet, um diese Implementierung zu veranschaulichen.

- Parametrisierte Implementierung

   Parametrisierte Implementierung wird vom Assistenten zum Hinzufügen von Eigenschaften unterstützt. Eine parametrisierte Eigenschaft (manchmal als Eigenschafts Array bezeichnet) kann verwendet werden, um über eine einzelne Eigenschaft des Steuer Elements auf einen Satz von Werten zuzugreifen. Das Dispatch Map Entry-Makro für diese Implementierung ist DISP_PROPERTY_PARAM. Weitere Informationen zum Implementieren dieses Typs finden Sie unter [Implementieren einer parametrisierten Eigenschaft](mfc-activex-controls-advanced-topics.md) im Artikel ActiveX-Steuerelemente: Weiterführende Themen.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Verwenden des Assistenten zum Hinzufügen von Eigenschaften zum Hinzufügen einer benutzerdefinierten Eigenschaft

Im folgenden Verfahren wird das Hinzufügen der benutzerdefinierten Eigenschaft CircleOffset veranschaulicht, die die Implementierung der Get/Set-Methode verwendet. Die benutzerdefinierte Eigenschaft CircleOffset ermöglicht dem Benutzer des Steuer Elements, den Kreis von der Mitte des umgebenden Rechtecks des Steuer Elements zu versetzen. Die Vorgehensweise zum Hinzufügen benutzerdefinierter Eigenschaften mit einer anderen Implementierung als Get/Set-Methoden ist sehr ähnlich.

Diese Prozedur kann auch verwendet werden, um weitere benutzerdefinierte Eigenschaften hinzuzufügen. Ersetzen Sie den Namen und die Parameter der CircleOffset-Eigenschaft durch den Namen der benutzerdefinierten Eigenschaft.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>So fügen Sie die benutzerdefinierte Eigenschaft CircleOffset mithilfe des Assistenten zum Hinzufügen von Eigenschaften hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der [Assistent zum Hinzufügen von Eigenschaften](../ide/names-add-property-wizard.md)geöffnet.

1. Geben Sie im Feld **Eigenschafts Name den Namen** *CircleOffset*ein.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Wählen Sie im Feld **Eigenschaftentyp** aus **`short`** .

1. Geben Sie eindeutige Namen für die Get-und Set-Funktionen ein, oder übernehmen Sie die Standardnamen.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Hinzufügen von Eigenschaften-Assistenten Änderungen für benutzerdefinierte Eigenschaften

Wenn Sie die benutzerdefinierte Eigenschaft CircleOffset hinzufügen, nimmt der Assistent zum Hinzufügen von Eigenschaften Änderungen am Header vor (. H) und die-Implementierung (. Cpp-Dateien der Steuerelement Klasse.

Die folgenden Zeilen werden dem hinzugefügt. H-Datei zum Deklarieren von zwei Funktionen namens `GetCircleOffset` und `SetCircleOffset` :

[!code-cpp[NVC_MFC_AxUI#25](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Die folgende Zeile wird dem-Steuerelement des-Steuer Elements hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#26](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Diese Zeile weist der Eigenschaft "CircleOffset" eine bestimmte ID-Nummer zu, die aus der Position der Methode in der Liste Methoden und Eigenschaften des Assistenten zum Hinzufügen von Eigenschaften entnommen wurde.

Außerdem wird der dispatchkarte (in der die folgende Zeile hinzugefügt. Cpp-Datei der Steuerelement Klasse), um die Eigenschaft CircleOffset den zwei Handlerfunktionen des Steuer Elements zuzuordnen:

[!code-cpp[NVC_MFC_AxUI#27](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Schließlich werden die Implementierungen der- `GetCircleOffset` `SetCircleOffset` Funktion und der-Funktion am Ende des-Steuer Elements hinzugefügt. Cpp-Datei. In den meisten Fällen ändern Sie die Get-Funktion, um den Wert der-Eigenschaft zurückzugeben. Die Set-Funktion enthält normalerweise Code, der entweder vor oder nach dem Ändern der Eigenschaft ausgeführt werden soll.

[!code-cpp[NVC_MFC_AxUI#28](codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Beachten Sie, dass der Assistent zum Hinzufügen von Eigenschaften dem Text der Set-Funktion automatisch einen-Befehl, [SetModifiedFlag](reference/colecontrol-class.md#setmodifiedflag), hinzufügt. Durch Aufrufen dieser Funktion wird das-Steuerelement als geändert markiert. Wenn ein Steuerelement geändert wurde, wird der neue Zustand gespeichert, wenn der Container gespeichert wird. Diese Funktion sollte immer dann aufgerufen werden, wenn eine Eigenschaft, die als Teil des permanenten Zustands des Steuer Elements gespeichert ist, den Wert ändert.

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaften](mfc-activex-controls-properties.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)
