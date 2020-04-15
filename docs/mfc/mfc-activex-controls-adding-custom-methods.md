---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Methoden'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 88d486248eab5d980463764db34bf40b05b830dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364716"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Methoden

Benutzerdefinierte Methoden unterscheiden sich von Bestandsmethoden `COleControl`dadurch, dass sie nicht bereits von implementiert sind. Sie müssen die Implementierung für jede benutzerdefinierte Methode bereitstellen, die Sie dem Steuerelement hinzufügen.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Ein ActiveX-Steuerelementbenutzer kann jederzeit eine benutzerdefinierte Methode aufrufen, um steuerungsspezifische Aktionen auszuführen. Der Dispatch-Map-Eintrag für benutzerdefinierte Methoden ist vom Formular DISP_FUNCTION.

## <a name="adding-a-custom-method-with-the-add-method-wizard"></a><a name="_core_adding_a_custom_method_with_classwizard"></a>Hinzufügen einer benutzerdefinierten Methode mit dem Assistenten zum Hinzufügen der Methode

Das folgende Verfahren veranschaulicht das Hinzufügen der benutzerdefinierten Methode PtInCircle zum Skelettcode eines ActiveX-Steuerelements. PtInCircle bestimmt, ob sich die an das Steuerelement übergebenen Koordinaten innerhalb oder außerhalb des Kreises befinden. Dieselbe Prozedur kann auch verwendet werden, um andere benutzerdefinierte Methoden hinzuzufügen. Ersetzen Sie den benutzerdefinierten Methodennamen und seine Parameter durch den PtInCircle-Methodennamen und die Parameter.

> [!NOTE]
> In diesem `InCircle` Beispiel wird die Funktion aus dem Artikel Ereignisse verwendet. Weitere Informationen zu dieser Funktion finden Sie im Artikel [MFC ActiveX Controls: Adding Custom Events to a ActiveX Control](../mfc/mfc-activex-controls-adding-custom-events.md).

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>So fügen Sie die benutzerdefinierte PtInCircle-Methode mithilfe des Assistenten zum Hinzufügen von Methoden hinzu

1. Laden Sie das Projekt des Steuerelements.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Methode hinzufügen**.

   Dadurch wird der Assistenten zum Hinzufügen von Methoden geöffnet.

1. Geben Sie im Feld **Methodenname** *PtInCircle*ein.

1. Geben Sie im Feld **Interner Name** den Namen der internen Funktion der Methode ein, oder verwenden Sie den Standardwert (in diesem Fall *PtInCircle*).

1. Klicken Sie im Feld **Rückgabetyp** auf **VARIANT_BOOL** für den Rückgabetyp der Methode.

1. Fügen Sie mithilfe der Steuerelemente **Parametertyp** und **Parametername** einen Parameter namens *xCoord* (Typ *OLE_XPOS_PIXELS*) hinzu.

1. Fügen Sie mithilfe der Steuerelemente **Parametertyp** und **Parametername** einen Parameter namens *yCoord* hinzu (Typ *OLE_YPOS_PIXELS*).

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-method-wizard-changes-for-custom-methods"></a><a name="_core_classwizard_changes_for_custom_methods"></a>Hinzufügen von Methoden-Assistentenänderungen für benutzerdefinierte Methoden

Wenn Sie eine benutzerdefinierte Methode hinzufügen, nimmt der Assistent zum Hinzufügen von Methoden einige Änderungen am Steuerelementklassenheader (. H) und Umsetzung (. CPP)-Dateien. Die folgende Zeile wird der Dispatchzuordnungsdeklaration im Steuerelementklassenheader (. H) Datei:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

Dieser Code deklariert einen `PtInCircle`Dispatchmethodenhandler mit dem Namen . Diese Funktion kann vom Steuerelementbenutzer unter `PtInCircle`Verwendung des externen Namens aufgerufen werden.

Die folgende Zeile wird der des Steuerelements hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

Diese Zeile weist `PtInCircle` der Methode eine bestimmte ID-Nummer, die Position der Methode in der Methoden-Assistenten-Methoden- und Eigenschaftenliste hinzufügen zu. Da der Assistenten zum Hinzufügen der Methode verwendet wurde, um die benutzerdefinierte Methode hinzuzufügen, wurde der Eintrag dafür automatisch dem Projekt hinzugefügt. IDL-Datei.

Darüber hinaus befindet sich die folgende Zeile in der Implementierung (. CPP)-Datei der Steuerelementklasse, wird der Dispatch-Zuordnung des Steuerelements hinzugefügt:

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

Das DISP_FUNCTION-Makro `PtInCircle` ordnet die Methode der `PtInCircle`Handlerfunktion des Steuerelements zu, , deklariert den Rückgabetyp als `PtInCircle` **VARIANT_BOOL**und deklariert zwei Parameter vom Typ **VTS_XPOS_PIXELS** und **VTS_YPOSPIXELS,** die an übergeben werden sollen.

Schließlich fügt der Assistent zum `CSampleCtrl::PtInCircle` Hinzufügen von Methoden die Stubfunktion am unteren Rand der Implementierung des Steuerelements hinzu (. CPP)-Datei. Damit `PtInCircle` sie wie zuvor angegeben funktioniert, muss sie wie folgt geändert werden:

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[Klassenansicht und Objektbrowsersymbole](/visualstudio/ide/class-view-and-object-browser-icons)
