---
title: Steuerelementeinstellungen, MFC-ActiveX-Steuerelement-Assistent
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 1578ca7f4134e51e0ba0d3c2b247dcafcb0fbd67
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405012"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Steuerelementeinstellungen, MFC-ActiveX-Steuerelement-Assistent

Auf dieser Seite des Assistenten können Sie angeben, wie sich das Steuerelement Verhalten soll. Beispielsweise können Sie das Steuerelement auf standardmäßigen Windows-Steuerelement Typen basieren, das Verhalten und die Darstellung optimieren oder angeben, dass das Steuerelement als Container für andere Steuerelemente fungieren kann.

Weitere Informationen zum Auswählen der Optionen auf dieser Seite, um die Effizienz des Steuer Elements zu maximieren, finden Sie unter [MFC-ActiveX-Steuerelemente: Optimierung](../../mfc/mfc-activex-controls-optimization.md).

## <a name="uielement-list"></a>UIElement-Liste

- **Erstellen eines Steuer Elements basierend auf**

   In dieser Liste können Sie die Art des Steuer Elements auswählen, von dem das Steuerelement erben soll. Die Liste ist eine Teilmenge der Steuerelement Klassen, die für verfügbar sind, `CreateWindowEx` sowie weitere allgemeine Steuerelemente, die in "kommctrl. h" angegeben sind. Die Auswahl bestimmt den Stil des Steuer Elements in der- `PreCreateWindow` Funktion in der Datei " *ProjName*Ctrl. cpp". Weitere Informationen finden Sie [unter MFC-ActiveX-Steuerelemente: Unterklassen für ein Windows-Steuer](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)Element.

   |Control|BESCHREIBUNG|
   |-------------|-----------------|
   |**Gedrückt**|Ein Windows-Schaltflächen Steuerelement|
   |**ComboBox**|Ein Kombinations Feld-Steuerelement von Windows|
   |**Bearbeiten**|Ein Windows-Bearbeitungsfeld-Steuerelement|
   |**ListBox**|Ein Windows-Listenfeld-Steuerelement|
   |**Bild Lauf Leiste**|Ein Windows-Scrollleisten-Steuerelement|
   |**Kum**|Ein statisches Windows-Steuerelement|
   |**msctls_hotkey32**|Ein gebräuchlicher Schlüssel Steuerelement|
   |**msctls_progress32**|Ein gängiges Steuerelement der Statusanzeige|
   |**msctls_statusbar32**|Allgemeine Steuerung der Statusleiste|
   |**msctls_trackbar32**|Ein gängiges Steuerelement der Trackleiste|
   |**msctls_updown32**|Ein gebräuchlicher Drehfeld (oder ein auf-ab-Steuerelement)|
   |**SysAnimate32**|Ein häufig verwendeter Animations Steuerelement|
   |**SysHeader32**|Ein gängiges Header Steuerelement|
   |**SysListView32**|Allgemeine Steuerung der Listenansicht|
   |**SysTabControl32**|Ein Registerkarten-Steuerelement|
   |**SysTreeView32**|Allgemeine Steuerelement Strukturansicht|

- **Aktiviert, wenn sichtbar**

   Gibt an, dass ein Fenster für das-Steuerelement erstellt wird, wenn darauf zugegriffen wird. Standardmäßig wird **aktiviert, wenn** die Option sichtbar ausgewählt ist. Deaktivieren Sie diese Option, wenn Sie die Aktivierung der Steuerung verzögern möchten, bis Sie vom Container benötigt wird (z. b. Wenn ein Benutzer auf die Maus klickt). Wenn diese Funktion deaktiviert ist, entstehen für das Steuerelement keine Kosten der Fenster Erstellung, bis es erforderlich ist. Weitere Informationen finden Sie unter [Ausschalten der Option "aktivieren, wenn sichtbar](../../mfc/turning-off-the-activate-when-visible-option.md)".

- **Unsichtbar zur Laufzeit**

   Gibt an, dass das Steuerelement zur Laufzeit keine Benutzeroberfläche hat. Ein Timer ist eine Art Steuerelement, das Sie möglicherweise unsichtbar sein sollten.

- **Hat ein Info-Dialogfeld**

   Gibt an, dass das-Steuerelement **über** das Standard Dialogfeld Windows Info verfügt, in dem Versionsnummer und Copyright Informationen angezeigt werden.

   > [!NOTE]
   > Wie der Benutzer auf die Hilfe für das Steuerelement zugreift, hängt davon ab, wie Sie die Hilfe implementiert haben und ob Sie die Steuerungs Hilfe in die Container Hilfe integriert haben.

   Wenn Sie diese Option auswählen, wird die `AboutBox` Steuermethode in der Projekt Steuerungs Klasse (C*ProjName*STRG. cpp) eingefügt, und der Projekt Dispatchzuordnung wird die Option AboutBox hinzugefügt. Diese Option ist standardmäßig ausgewählt.

- **Optimierter Zeichnungs Code**

   Gibt an, dass der Container die ursprünglichen GDI-Objekte automatisch wiederherstellt, nachdem alle Container Steuerelemente, die in denselben Gerätekontext gezogen werden, gezeichnet wurden. Weitere Informationen zu dieser Funktion finden Sie unter [Optimieren der Steuerelement Zeichnung](../../mfc/optimizing-control-drawing.md).

- **Fensterlose Aktivierung**

   Gibt an, dass das Steuerelement kein Fenster erzeugt, wenn es aktiviert wird. Die Fensterlose Aktivierung ermöglicht nicht rechteckige oder transparente Steuerelemente, und für ein fensterloses Steuerelement ist weniger System Aufwand erforderlich als für ein Steuerelement, für das ein Fenster erforderlich ist. Ein fensterloses Steuerelement lässt keinen nicht geschnittenen Gerätekontext oder eine flimmerfreie Aktivierung zu. Container, die vor 1996 erstellt wurden, unterstützen keine Fensterlose Aktivierung. Weitere Informationen zur Verwendung dieser Option finden Sie unter [Bereitstellen der fensterlosen Aktivierung](../../mfc/providing-windowless-activation.md).

- **Nicht abgeschnittener Gerätekontext**

   Überschreibt [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) im Steuerelement Header (*Projektname*STRG. h), um den Aufrufen `IntersectClipRect` von zu deaktivieren `COleControl` . Wenn Sie diese Option auswählen, bietet Sie einen kleinen Vorteil. Wenn Sie die Option für die **Fensterlose Aktivierung**auswählen, ist dieses Feature nicht verfügbar. Weitere Informationen finden Sie unter [Verwenden eines nicht geschnittenen Geräte Kontexts](../../mfc/using-an-unclipped-device-context.md).

- **Flimmerfreie Aktivierung**

   Entfernt die Zeichnungsvorgänge und den zugehörigen visuellen Flimmer, die zwischen den aktiven und inaktiven Zuständen des Steuer Elements auftreten. Wenn Sie die Option für die **Fensterlose Aktivierung**auswählen, ist dieses Feature nicht verfügbar. Wenn Sie diese Option festlegen, `noFlickerActivate` ist das Flag eines der Flags, die von [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)zurückgegeben werden. Weitere Informationen finden Sie unter [Bereitstellen der Flimmer freien Aktivierung](../../mfc/providing-flicker-free-activation.md).

- **Verfügbar im Dialogfeld "Objekt einfügen"**

   Gibt an, dass das Steuerelement im Dialogfeld **Objekt einfügen** für aktivierte Container verfügbar ist. Wenn Sie diese Option auswählen, `afxRegInsertable` ist das Flag eines der Flags, die von zurückgegeben werden `AfxOleRegisterControlClass` . Mithilfe des Dialog Felds **Objekt einfügen** kann ein Benutzer neu erstellte oder vorhandene Objekte in ein Verbund Dokument einfügen.

- **Mauszeiger Benachrichtigungen, wenn inaktiv**

   Ermöglicht dem Steuerelement, Mauszeiger Benachrichtigungen zu verarbeiten, unabhängig davon, ob das Steuerelement aktiv ist oder nicht. Wenn Sie diese Option auswählen, `pointerInactive` ist das Flag eines der Flags, die von [COleControl:: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)zurückgegeben werden. Weitere Informationen zur Verwendung dieser Option finden Sie unter [Bereitstellen der Maus Interaktion in inaktiver](../../mfc/providing-mouse-interaction-while-inactive.md)Weise.

- **Fungiert als einfaches Rahmen Steuerelement**

   Gibt an, dass das Steuerelement ein Container für andere Steuerelemente ist, indem das OLEMISC_SIMPLEFRAME Bit für das Steuerelement festgelegt wird. Weitere Informationen finden Sie unter [Containment (Simple Frame Site Containment](/windows/win32/com/simple-frame-site-containment)).

- **Lädt Eigenschaften asynchron.**

   Ermöglicht das Zurücksetzen vorheriger asynchroner Daten und initiiert eine neue Last der asynchronen Eigenschaft des Steuer Elements.

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelement-Assistent](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Anwendungseinstellungen, MFC-ActiveX-Steuerelement-Assistent](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Steuerelementnamen, MFC-ActiveX-Steuerelement-Assistent](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
