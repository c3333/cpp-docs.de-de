---
title: Darstellung, ATL-Steuerelement-Assistent
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319394"
---
# <a name="appearance-atl-control-wizard"></a>Darstellung, ATL-Steuerelement-Assistent

Verwenden Sie diese Seite des Assistenten, um zusätzliche Benutzerelementoptionen für das Steuerelement zu identifizieren. Diese Seite ist für Steuerelemente verfügbar, die **unter** Steuerelementtyp unter **Steuerelementtyp** auf der Seite [Optionen, ATL-Steuerungs-Assistent](../../atl/reference/options-atl-control-wizard.md) gekennzeichnet sind.

## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente

- **Anzeigen des Status**

   Legt die Darstellung des Steuerelements innerhalb des Containers fest.

  - **Opaque**: Legt das VIEWSTATUS_OPAQUE Bit in der VIEWSTATUS-Enumeration fest und zeichnet das gesamte Steuerelementrechteck, das an die [CComControlBase::OnDraw-Methode](../../atl/reference/ccomcontrolbase-class.md#ondraw) übergeben wird. [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) Das Steuerelement erscheint völlig undurchsichtig, und keiner der Container wird hinter den Kontrollgrenzen angezeigt.

      Diese Einstellung hilft dem Container, das Steuerelement schneller zu zeichnen. Wenn diese Option nicht ausgewählt ist, kann das Steuerelement transparente Teile enthalten.

      Nur ein undurchsichtiges Steuerelement kann einen soliden Hintergrund haben.

  - **Solider Hintergrund**: Legt das VIEWSTATUS_SOLIDBKGND Bit in der VIEWSTATUS-Enumeration fest. Der Hintergrund des Steuerelements wird als Volltonfarbe ohne Muster angezeigt.

      Diese Option ist nur verfügbar, wenn die Option **"Opaque"** ebenfalls ausgewählt ist.

- **Hinzufügen von Steuerelementen basierend auf**

   Legt fest, dass das Steuerelement auf einem Windows-Steuerelementtyp basiert, indem der Klasse, die das Steuerelement implementiert, ein [CContainedWindow-Datenmember](ccontainedwindowt-class.md) hinzugefügt wird. Außerdem werden eine Meldungszuordnung und Nachrichtenhandlerfunktionen hinzugefügt, um Windows-Nachrichten für das Steuerelement zu verarbeiten. Wählen Sie aus der Liste den Typ des Windows-Steuerelements aus, das Sie erstellen möchten, falls vorhanden.

  - **Schaltfläche**

  - **ListBox**

  - **SysAnimate32**

  - **SysListView32**

  - **ComboBox**

  - **RichEdit**

  - **SysDateTimePick32**

  - **SysMonthCal32**

  - **ComboBoxEx32**

  - **ScrollBar**

  - **SysHeader32**

  - **SysTabControl32**

  - **Bearbeiten**

  - **Statische**

  - **SysIPAddress32**

  - **SysTreeView32**

- **Misc-Status**

   Legt zusätzliche Darstellungs- und Verhaltensoptionen für das Steuerelement fest.

  - **Unsichtbar zur Laufzeit:** Legt fest, dass das Steuerelement zur Laufzeit unsichtbar ist. Sie können unsichtbare Steuerelemente verwenden, um Vorgänge im Hintergrund auszuführen, z. B. Das Auslösen von Ereignissen in zeitgesteuerten Intervallen.

  - **Funktioniert wie die Schaltfläche**: Legt das OLEMISC_ACTSLIKEBUTTON Bit in der [OLEMISC-Enumeration](/windows/win32/api/oleidl/ne-oleidl-olemisc) fest, damit ein Steuerelement wie eine Schaltfläche funktioniert. Wenn der Container die Clientsite des Steuerelements als Standardschaltfläche markiert hat, ermöglicht die Auswahl dieser Option, dass sich das Schaltflächensteuerelement selbst als Standardschaltfläche anzeigen kann, indem es sich selbst mit einem dickeren Rahmen zeichnet. Weitere Informationen finden Sie unter [CComControlBase::GetAmbientDisplayAsDefault.](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)

  - **Funktioniert wie label**: Legt das OLEMISC_ACTSLIKELABEL Bit in der OLEMISC-Enumeration fest, damit ein Steuerelement die systemeigene Bezeichnung des Containers ersetzen kann. Der Container bestimmt, was mit diesem Flag zu tun ist, wenn überhaupt.

- **Andere**

   Legt zusätzliche Verhaltensoptionen für das Steuerelement fest.

  - **Normalisierter Domänencontroller**: Legt fest, dass das Steuerelement einen normalisierten Gerätekontext erstellt, wenn es aufgerufen wird, sich selbst zu zeichnen. Diese Aktion standardisiert die Darstellung des Steuerelements, macht das Zeichnen jedoch weniger effizient.

  - **Nur Fenster**: Gibt an, dass das Steuerelement nicht fensterlos sein kann. Wenn Sie diese Option nicht auswählen, wird das Steuerelement in Containern, die fensterlose Objekte unterstützen, automatisch fensterlos und automatisch in Containern angezeigt, die keine fensterlosen Objekte unterstützen. Wenn Sie diese Option auswählen, muss das Steuerelement auch in Containern, die fensterlose Objekte unterstützen, in einem Fenster gefenstert werden.

  - **Einfügung**: Wählen Sie diese Option aus, damit das Steuerelement im Dialogfeld **Objekt** einfügen von Anwendungen wie Word und Excel angezeigt wird. Das Steuerelement kann dann von jeder Anwendung eingefügt werden, die eingebettete Objekte über dieses Dialogfeld unterstützt.

## <a name="see-also"></a>Siehe auch

[ATL-Steuerungs-Assistent](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT-Beispiel: Superclasses ein Standard-Windows-Steuerelement](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
