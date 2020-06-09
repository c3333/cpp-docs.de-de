---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Methoden'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: e32a1c372d89fc4ade414b20a0f77fa162807250
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626162"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Methoden

Benutzerdefinierte Methoden unterscheiden sich von den vordefinierten Methoden insofern, als Sie nicht bereits von implementiert wurden `COleControl` . Sie müssen die-Implementierung für jede benutzerdefinierte Methode angeben, die Sie dem Steuerelement hinzufügen.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Ein ActiveX-Steuerelement Benutzer kann jederzeit eine benutzerdefinierte Methode zum Ausführen von Steuerungs spezifischen Aktionen aufzurufen. Der dispatchzuordnungseintrag für benutzerdefinierte Methoden hat die Form DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Hinzufügen einer benutzerdefinierten Methode mithilfe des Assistenten zum Hinzufügen von Methoden

Im folgenden Verfahren wird das Hinzufügen der benutzerdefinierten Methode PtInCircle zum Skeleton-Code eines ActiveX-Steuer Elements veranschaulicht. PtInCircle bestimmt, ob die an das Steuerelement weiter gegebenen Koordinaten innerhalb oder außerhalb des Kreises liegen. Diese Prozedur kann auch verwendet werden, um weitere benutzerdefinierte Methoden hinzuzufügen. Ersetzen Sie den Namen und die Parameter der PtInCircle-Methode durch den benutzerdefinierten Methodennamen und seine Parameter.

> [!NOTE]
> In diesem Beispiel wird die- `InCircle` Funktion aus den Artikel Ereignissen verwendet. Weitere Informationen zu dieser Funktion finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Ereignissen zu einem ActiveX-Steuer](mfc-activex-controls-adding-custom-events.md)Element.

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>So fügen Sie die benutzerdefinierte Methode PtInCircle mithilfe des Assistenten zum Hinzufügen von Methoden hinzu

1. Laden Sie das Projekt des-Steuer Elements.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Methode hinzufügen**.

   Daraufhin wird der Assistent zum Hinzufügen von Methoden geöffnet.

1. Geben Sie im Feld **Methoden Name den Namen** *PtInCircle*ein.

1. Geben Sie im Feld **interner Name** den Namen der internen Funktion der Methode ein, oder verwenden Sie den Standardwert (in diesem Fall *PtInCircle*).

1. Klicken Sie im Feld **Rückgabetyp** auf **VARIANT_BOOL** für den Rückgabetyp der Methode.

1. Fügen Sie mit den para **Metern Parametertyp** und **Parameter Name** einen Parameter mit dem Namen *xcoord* (Type *OLE_XPOS_PIXELS*) hinzu.

1. Fügen Sie mit den para **Metern Parametertyp** und **Parameter Name** einen Parameter namens *yCoord* (Type *OLE_YPOS_PIXELS*) hinzu.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Hinzufügen von Methoden-Assistenten Änderungen für benutzerdefinierte Methoden

Wenn Sie eine benutzerdefinierte Methode hinzufügen, nimmt der Assistent zum Hinzufügen von Methoden Änderungen am Steuerelement Klassen Header (. H) und Implementierung (. Cpp-Dateien. Die folgende Zeile wird der dispatchmap-Deklaration im Header der Steuerelement Klasse () hinzugefügt. H):

[!code-cpp[NVC_MFC_AxUI#18](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Dieser Code deklariert einen dispatchmethodenhandler mit dem Namen `PtInCircle` . Diese Funktion kann vom Benutzer des Steuer Elements mit dem externen Namen aufgerufen werden `PtInCircle` .

Die folgende Zeile wird dem des-Steuer Elements hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#19](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Diese Zeile weist der `PtInCircle` Methode eine bestimmte ID-Nummer und die Position der Methode im Assistenten Methoden und Eigenschaften des Assistenten zum Hinzufügen von Methoden zu. Da der Assistent zum Hinzufügen von Methoden zum Hinzufügen der benutzerdefinierten Methode verwendet wurde, wurde der Eintrag automatisch dem Projekt hinzugefügt. IDL-Datei.

Außerdem befindet sich die folgende Zeile in der-Implementierung (. Cpp-Datei der Steuerelement Klasse, wird der dispatchmap des Steuer Elements hinzugefügt:

[!code-cpp[NVC_MFC_AxUI#20](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

Das DISP_FUNCTION-Makro ordnet die `PtInCircle` -Methode der Handlerfunktion des Steuer Elements zu, `PtInCircle` deklariert den Rückgabetyp, der **VARIANT_BOOL**werden soll, und deklariert zwei Parameter des Typs **VTS_XPOS_PIXELS** und **VTS_YPOSPIXELS** an `PtInCircle` .

Zum Schluss fügt der Assistent zum Hinzufügen von Methoden am `CSampleCtrl::PtInCircle` Ende der-Implementierung des-Steuer Elements (. Cpp-Datei. Damit `PtInCircle` wie zuvor angegeben funktioniert, muss es wie folgt geändert werden:

[!code-cpp[NVC_MFC_AxUI#21](codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[Symbole für Klassenansicht und Objektkatalog](/visualstudio/ide/class-view-and-object-browser-icons)
