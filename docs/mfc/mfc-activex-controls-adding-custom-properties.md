---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Eigenschaften'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: 00f7a879582bca562ce626fe224206094fd19bc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364700"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Eigenschaften

Benutzerdefinierte Eigenschaften unterscheiden sich von Bestandseigenschaften dadurch, dass benutzerdefinierte Eigenschaften nicht bereits von der `COleControl` Klasse implementiert wurden. Eine benutzerdefinierte Eigenschaft wird verwendet, um einen bestimmten Status oder eine bestimmte Darstellung eines ActiveX-Steuerelements für einen Programmierer verfügbar zu machen, der das Steuerelement verwendet.

In diesem Artikel wird beschrieben, wie Sie dem ActiveX-Steuerelement mithilfe des Assistenten zum Hinzufügen von Eigenschaften eine benutzerdefinierte Eigenschaft hinzufügen und die resultierenden Codeänderungen erklären. Dabei werden folgende Themen behandelt:

- [Verwenden des Assistenten zum Hinzufügen von Eigenschaften zum Hinzufügen einer benutzerdefinierten Eigenschaft](#_core_using_classwizard_to_add_a_custom_property)

- [Eigenschaften-Assistenten-Änderungen für benutzerdefinierte Eigenschaften hinzufügen](#_core_classwizard_changes_for_custom_properties)

Benutzerdefinierte Eigenschaften sind in vier Implementierungsvarianten erhältlich: Membervariable, Membervariable mit Benachrichtigung, Ab/Set-Methoden und Parameterized.

- Implementierung von Membervariablen

   Diese Implementierung stellt den Status der Eigenschaft als Membervariable in der Steuerelementklasse dar. Verwenden Sie die Membervariable-Implementierung, wenn es nicht wichtig ist zu wissen, wann sich der Eigenschaftswert ändert. Von den drei Typen erstellt diese Implementierung den geringsten Supportcode für die Eigenschaft. Das Dispatch-Map-Eintragsmakro für die Implementierung der Membervariablen ist [DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property).

- Mitgliedsvariable mit Benachrichtigungsimplementierung

   Diese Implementierung besteht aus einer Membervariablen und einer Benachrichtigungsfunktion, die vom Add Property Wizard erstellt wurde. Die Benachrichtigungsfunktion wird automatisch vom Framework aufgerufen, nachdem sich der Eigenschaftswert geändert hat. Verwenden Sie die Membervariable mit Benachrichtigungsimplementierung, wenn Sie benachrichtigt werden müssen, nachdem sich ein Eigenschaftswert geändert hat. Diese Implementierung erfordert mehr Zeit, da sie einen Funktionsaufruf erfordert. Das Dispatch-Map-Eintragsmakro für diese Implementierung ist [DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify).

- Implementierung von Abrufen/Festlegen von Methoden

   Diese Implementierung besteht aus einem Paar von Memberfunktionen in der Steuerelementklasse. Die Implementierung "Methoden abrufen/Festlegen" ruft automatisch die Memberfunktion Abrufen auf, wenn der Benutzer des Steuerelements den aktuellen Wert der Eigenschaft und die Elementfunktion Festlegen anfordert, wenn der Benutzer des Steuerelements anfordert, dass die Eigenschaft geändert wird. Verwenden Sie diese Implementierung, wenn Sie den Wert einer Eigenschaft während der Laufzeit berechnen, einen vom Benutzer des Steuerelements übergebenen Wert überprüfen müssen, bevor Sie die tatsächliche Eigenschaft ändern, oder einen Schreib- oder Schreibeigenschaftstyp implementieren. Das Dispatch-Map-Eintragsmakro für diese Implementierung ist [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex). Im folgenden Abschnitt verwendet [der Assistent zum Hinzufügen einer benutzerdefinierten Eigenschaft](#_core_using_classwizard_to_add_a_custom_property)die benutzerdefinierte CircleOffset-Eigenschaft, um diese Implementierung zu demonstrieren.

- Parametrierte Implementierung

   Die parametrisierte Implementierung wird vom Add Property Wizard unterstützt. Eine parametrisierte Eigenschaft (manchmal auch als Eigenschaftsarray bezeichnet) kann verwendet werden, um über eine einzelne Eigenschaft des Steuerelements auf einen Satz von Werten zuzugreifen. Das Dispatch-Map-Eintragsmakro für diese Implementierung ist DISP_PROPERTY_PARAM. Weitere Informationen zum Implementieren dieses Typs finden Sie unter [Implementieren einer Parametrierten Eigenschaft](../mfc/mfc-activex-controls-advanced-topics.md) im Artikel ActiveX-Steuerelemente: Erweiterte Themen.

## <a name="using-the-add-property-wizard-to-add-a-custom-property"></a><a name="_core_using_classwizard_to_add_a_custom_property"></a>Verwenden des Eigenschaften-Assistenten hinzufügen zum Hinzufügen einer benutzerdefinierten Eigenschaft

Das folgende Verfahren veranschaulicht das Hinzufügen einer benutzerdefinierten Eigenschaft, CircleOffset, die die Get/Set Methods-Implementierung verwendet. Die benutzerdefinierte CircleOffset-Eigenschaft ermöglicht es dem Benutzer des Steuerelements, den Kreis von der Mitte des umgebenden Rechtecks des Steuerelements zu verrechnen. Das Verfahren zum Hinzufügen benutzerdefinierter Eigenschaften mit einer anderen Implementierung als Get/Set-Methoden ist sehr ähnlich.

Das gleiche Verfahren kann auch verwendet werden, um andere benutzerdefinierte Eigenschaften hinzuzufügen, die Sie möchten. Ersetzen Sie Ihren benutzerdefinierten Eigenschaftsnamen durch den CircleOffset-Eigenschaftsnamen und die Parameter.

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>So fügen Sie die benutzerdefinierte CircleOffset-Eigenschaft mithilfe des Eigenschaften-Assistenten hinzufügen hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Eigenschaft hinzufügen**.

   Dadurch wird der [Eigenschaften-Assistent hinzufügen](../ide/names-add-property-wizard.md)geöffnet.

1. Geben Sie im Feld **Eigenschaftenname** *CircleOffset*ein.

1. Klicken Sie unter **Implementierungstyp**auf **Get/Set-Methoden**.

1. Wählen Sie im Feld **Eigenschaftentyp** **kurze**aus.

1. Geben Sie eindeutige Namen für Ihre Get- und Set-Funktionen ein, oder akzeptieren Sie die Standardnamen.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-property-wizard-changes-for-custom-properties"></a><a name="_core_classwizard_changes_for_custom_properties"></a>Eigenschaften-Assistenten-Änderungen für benutzerdefinierte Eigenschaften hinzufügen

Wenn Sie die benutzerdefinierte CircleOffset-Eigenschaft hinzufügen, nimmt der Eigenschaften-Assistent zum Hinzufügen Änderungen am Header (. H) und die Umsetzung (. CPP)-Dateien der Kontrollklasse.

Die folgenden Zeilen werden der hinzugefügt. H-Datei, um `GetCircleOffset` zwei `SetCircleOffset`aufgerufene Funktionen zu deklarieren und:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

Die folgende Zeile wird der . IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

Diese Zeile weist der CircleOffset-Eigenschaft eine bestimmte ID-Nummer zu, die von der Position der Methode in der Methoden- und Eigenschaftenliste des Eigenschaften-Assistenten hinzufügen übernommen wird.

Darüber hinaus wird der Dispatch-Map die folgende Zeile hinzugefügt (im . CPP-Datei der Steuerelementklasse), um die CircleOffset-Eigenschaft den beiden Handlerfunktionen des Steuerelements zuzuordnen:

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

Schließlich werden die Implementierungen der `GetCircleOffset` und `SetCircleOffset` Funktionen am Ende des Steuerelements hinzugefügt. CPP-Datei. In den meisten Fällen ändern Sie die Get-Funktion, um den Wert der Eigenschaft zurückzugeben. Die Set-Funktion enthält in der Regel Code, der entweder vor oder nach den Änderungen der Eigenschaft ausgeführt werden soll.

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

Beachten Sie, dass der Assistent zum Hinzufügen von Eigenschaften automatisch einen Aufruf zu [SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)zum Text körperder Funktion Festlegen hinzufügt. Wenn Sie diese Funktion aufrufen, wird das Steuerelement als geändert markiert. Wenn ein Steuerelement geändert wurde, wird sein neuer Status gespeichert, wenn der Container gespeichert wird. Diese Funktion sollte aufgerufen werden, wenn eine Eigenschaft, die als Teil des persistenten Zustands des Steuerelements gespeichert wird, den Wert ändert.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Eigenschaften](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](../mfc/reference/colecontrol-class.md)
