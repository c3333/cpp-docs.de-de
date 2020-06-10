---
title: 'MFC-ActiveX-Steuerelemente: Erstellen eines Automatisierungsservers'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: f2c941e43e810845560b4c35c558ec70248c21ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622386"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC-ActiveX-Steuerelemente: Erstellen eines Automatisierungsservers

Sie können ein MFC-ActiveX-Steuerelement als Automatisierungsserver für die programmgesteuerte Einbettung dieses Steuer Elements in eine andere Anwendung und das Aufrufen von Methoden im-Steuerelement aus der Anwendung entwickeln. Ein solches Steuerelement wäre weiterhin zum Hosten in einem ActiveX-Steuerelement Container verfügbar.

### <a name="to-create-a-control-as-an-automation-server"></a>So erstellen Sie ein Steuerelement als Automatisierungsserver

1. [Erstellen](reference/mfc-activex-control-wizard.md) Sie das-Steuerelement.

1. [Fügen Sie Methoden hinzu](mfc-activex-controls-methods.md).

1. Überschreiben Sie [isinvokeallowed](reference/colecontrol-class.md#isinvokeallowed).

1. Erstellen Sie das Steuerelement.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>So greifen Sie Programm gesteuert auf die Methoden in einem Automatisierungsserver zu

1. Erstellen Sie eine Anwendung, z. b. eine [MFC-exe](reference/mfc-application-wizard.md)-Datei.

1. Fügen Sie am Anfang der- `InitInstance` Funktion die folgende Zeile hinzu:

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. Klicken Sie in Klassenansicht mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Klasse aus Export der Typbibliothek hinzufügen aus** , um die Typbibliothek zu importieren.

   Dadurch werden dem Projektdateien mit dem Dateinamen Extensions. h und cpp hinzugefügt.

1. Fügen Sie in der Header Datei der Klasse, in der eine oder mehrere Methoden im ActiveX-Steuerelement aufgerufen werden, die folgende Zeile hinzu: `#include filename.h` , wobei Dateiname der Name der Header Datei ist, die beim Importieren der Typbibliothek erstellt wurde.

1. Fügen Sie in der Funktion, in der ein-Vorgang an einer Methode im ActiveX-Steuerelement aufgerufen wird, Code hinzu, der ein Objekt der Wrapper Klasse des Steuer Elements erstellt und das ActiveX-Objekt erstellt. Der folgende MFC-Code instanziiert z. b. ein `CCirc` -Steuerelement, ruft die Caption-Eigenschaft ab und zeigt das Ergebnis an, wenn in einem Dialogfeld auf die Schaltfläche OK geklickt wird:

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Wenn Sie dem ActiveX-Steuerelement nach der Verwendung in einer Anwendung Methoden hinzufügen, können Sie die neueste Version des-Steuer Elements in der Anwendung verwenden, indem Sie die Dateien löschen, die beim Importieren der Typbibliothek erstellt wurden. Importieren Sie die Typbibliothek dann erneut.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
