---
title: Implementieren von Eigenschaftenseiten
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: c9b1c0c159a15ec7d9a5c99208baa2ed6af2d6d1
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923899"
---
# <a name="implementing-property-pages"></a>Implementieren von Eigenschaftenseiten

::: moniker range="msvc-160"

Der ATL-Eigenschaftenseiten-Assistent ist in Visual Studio 2019 und höher nicht verfügbar.

::: moniker-end

::: moniker range="<=msvc-150"

Eigenschaftenseiten sind COM-Objekte, die die Schnittstelle `IPropertyPage` oder die Schnittstelle `IPropertyPage2` implementieren. ATL bietet Unterstützung für die Implementierung von Eigenschaftenseiten mit dem [ATL-Eigenschaftenseiten-Assistenten](../atl/reference/atl-property-page-wizard.md) im [Dialogfeld „Klasse hinzufügen“](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box).

So erstellen Sie eine Eigenschaftenseite mithilfe von ATL:

- Erstellen oder öffnen Sie ein ATL-DLL-Serverprojekt (Dynamic Link Library).

- Öffnen Sie das [Dialogfeld „Klasse hinzufügen“](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box), und wählen Sie **ATL-Eigenschaftenseite** aus.

- Stellen Sie sicher dass Ihre Eigenschaftenseite über einen Apartmentthread verfügt (da sie eine Benutzeroberfläche aufweist).

- Legen Sie den Titel, die Beschreibung (Dokumentzeichenfolge) und die Hilfedatei fest, der bzw. die Ihrer Seite zugeordnet werden soll.

- Fügen Sie der generierten Dialogfeldressource, die als Benutzeroberfläche Ihrer Eigenschaftenseite dienen soll, Steuerelemente hinzu.

- Reagieren Sie auf Änderungen auf der Benutzeroberfläche der Seite, um eine Überprüfung durchzuführen, die Site der Seite zu aktualisieren oder die Objekte zu aktualisieren, die der Seite zugeordnet sind. Rufen Sie insbesondere [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) auf, wenn ein Benutzer die Eigenschaftenseite ändert.

- Überschreiben Sie optional die `IPropertyPageImpl`-Methoden mithilfe der folgenden Anweisungen.

   |IPropertyPageImpl-Methode|Grund für Überschreibung|Notizen|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Sie möchten grundlegende Integritätsprüfungen für die an Ihre Seite übergebenen Objekten sowie die von ihnen unterstützten Schnittstellen ausführen.|Führen Sie Ihren eigenen Code aus, bevor Sie die Implementierung der Basisklasse aufrufen. Wenn die festgelegten Objekte Ihren Erwartungen nicht entsprechen, sollten Sie den Aufruf schnellstmöglich als fehlerhaft kennzeichnen.|
   |[Aktivieren](../atl/reference/ipropertypageimpl-class.md#activate)|Sie möchten die Benutzeroberfläche Ihrer Seite initialisieren (z.B. möchten Sie Dialogfeldsteuerelemente mit aktuellen Eigenschaftswerten aus Objekten festlegen, Steuerelemente dynamisch erstellen oder andere Initialisierungen durchführen).|Rufen Sie die Implementierung der Basisklasse vor Ihrem Code auf, sodass die Basisklasse das Dialogfeldfenster und alle Steuerelemente erstellen kann, bevor Sie versuchen, diese zu aktualisieren.|
   |[Anwenden](../atl/reference/ipropertypageimpl-class.md#apply)|Sie möchten die Eigenschafteneinstellungen überprüfen und die Objekte aktualisieren.|Sie müssen die Implementierung der Basisklasse nicht aufrufen, da diese außer der Ablaufverfolgung für den Aufruf keine Aktionen ausführt.|
   |[Deaktivieren](../atl/reference/ipropertypageimpl-class.md#deactivate)|Sie möchten fensterbezogene Elemente bereinigen.|Die Implementierung der Basisklasse zerstört das Dialogfeld, das die Eigenschaftenseite repräsentiert. Wenn Sie vor der Zerstörung des Dialogfelds eine Bereinigung durchführen müssen, sollten Sie Ihren Code vor dem Aufruf der Basisklasse hinzufügen.|

Ein Beispiel für eine Implementierung einer Eigenschaften Seite finden Sie unter [Beispiel: Implementieren einer Eigenschaften Seite](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Wenn Sie auf Ihrer Eigenschaftenseite ActiveX-Steuerelemente hosten möchten, müssen Sie die Ableitung Ihrer vom Assistenten generierten Klasse ändern. Ersetzen Sie **CDialogImpl \<CYourClass>** durch **CAxDialogImpl \<CYourClass>** in der Liste der Basisklassen.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Eigenschaftenseiten](../atl/atl-com-property-pages.md)<br/>
[ATLPages-Beispiel](../overview/visual-cpp-samples.md)
