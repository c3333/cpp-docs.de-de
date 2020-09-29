---
title: Hinzufügen einer neuen Schnittstelle in einem ATL-Projekt
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 8bf0138f85929e06b67e9a2e294eda8a2f385e1a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499384"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Hinzufügen einer neuen Schnittstelle in einem ATL-Projekt

Wenn Sie dem Objekt oder Steuerelement eine Schnittstelle hinzufügen, erstellen Sie Stub-out-Funktionen für jede Methode in dieser Schnittstelle. In Ihrem Objekt oder Steuerelement können Sie nur Schnittstellen hinzufügen, die derzeit in einer vorhandenen Typbibliothek gefunden werden. Außerdem muss die Klasse, in der Sie die-Schnittstelle hinzufügen, das [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) -Makro implementieren, oder, wenn das Projekt attributiert ist, muss es über das- `coclass` Attribut verfügen.

Sie können dem Steuerelement eine neue Schnittstelle auf zwei Arten hinzufügen: manuell oder mithilfe von Code-Assistenten in Klassenansicht.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>So verwenden Sie Code-Assistenten in Klassenansicht zum Hinzufügen einer Schnittstelle zu einem vorhandenen Objekt oder Steuerelement

1. Klicken Sie in [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code)mit der rechten Maustaste auf den Klassennamen eines Steuer Elements. Beispielsweise ein vollständiges Steuerelement oder ein zusammengesetztes Steuerelement oder eine beliebige andere Steuerelement Klasse, die in der Header Datei ein BEGIN_COM_MAP Makro implementiert.

1. Klicken Sie im Kontextmenü auf **Hinzufügen**, und klicken Sie dann auf **Schnittstelle implementieren**.

1. Wählen Sie im Assistenten zum Implementieren der [Schnittstelle](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard)die zu implementierenden Schnittstellen aus Wenn die Schnittstelle in keinem verfügbaren TypeLib vorhanden ist, müssen Sie Sie manuell der IDL-Datei hinzufügen.

## <a name="to-add-a-new-interface-manually"></a>So fügen Sie eine neue Schnittstelle manuell hinzu

1. Fügen Sie die Definition der neuen Schnittstelle der IDL-Datei hinzu.

1. Leiten Sie das Objekt oder Steuerelement von der-Schnittstelle ab.

1. Erstellen Sie eine neue [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) für die-Schnittstelle, oder fügen Sie, wenn das Projekt attributiert ist, das- `coclass` Attribut hinzu.

1. Implementieren Sie Methoden für die-Schnittstelle.

## <a name="see-also"></a>Weitere Informationen

[ATL-Projekt-Assistent](../../atl/reference/atl-project-wizard.md)<br/>
[C++-Projektvorlagen](../../build/reference/visual-cpp-project-types.md)<br/>
[Programmieren mit ATL-und C-Lauf Zeit Code](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Grundlagen von ATL-COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Standardmäßige ATL-Projekt Konfigurationen](../../atl/reference/default-atl-project-configurations.md)
