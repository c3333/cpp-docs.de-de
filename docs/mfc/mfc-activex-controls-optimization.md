---
title: 'MFC-ActiveX-Steuerelemente: Optimierung'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
ms.openlocfilehash: b4e12889ca1bb5f4bb423a1f1ede1c396f8d60b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615399"
---
# <a name="mfc-activex-controls-optimization"></a>MFC-ActiveX-Steuerelemente: Optimierung

Dieser Artikel erläutert Techniken, die Sie verwenden können, um die ActiveX-Steuerelemente für eine bessere Leistung zu optimieren.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

In den Themen zum [Aktivieren der Option wenn sichtbar aktivieren](turning-off-the-activate-when-visible-option.md) und [zur Bereitstellung von Maus Interaktion während inaktiv](providing-mouse-interaction-while-inactive.md) werden Steuerelemente erläutert, die bis zur Aktivierung kein Fenster erstellen. Das Thema [Bereitstellung der fensterlosen Aktivierung](providing-windowless-activation.md) erläutert Steuerelemente, die nie ein Fenster erstellen, selbst wenn Sie aktiviert sind.

Windows hat zwei wesentliche Nachteile für OLE-Objekte: Sie verhindern, dass Objekte transparent oder nicht rechteckig sind, wenn Sie aktiv sind, und Sie fügen einen großen mehr Aufwand für die Instanziierung und Anzeige von Steuerelementen hinzu. In der Regel nimmt das Erstellen eines Fensters 60 Prozent der Erstellungszeit eines Steuer Elements an. Mit einem einzelnen freigegebenen Fenster (normalerweise dem des Containers) und einem Teil des Verteilungs Codes erhält ein Steuerelement die gleichen Fenster Dienste, in der Regel ohne Leistungseinbußen. Ein Fenster ist größtenteils unnötig viel mehr Aufwand für das Objekt.

Einige Optimierungen verbessern die Leistung nicht notwendigerweise, wenn Ihr Steuerelement in bestimmten Containern verwendet wird. So haben beispielsweise Container, die vor 1996 freigegeben wurden, keine Fensterlose Aktivierung unterstützt. Daher bietet die Implementierung dieses Features keinen Vorteil in älteren Containern. Allerdings unterstützt fast jeder Container Persistenz, sodass die Optimierung des persistenzcodes Ihres Steuer Elements wahrscheinlich die Leistung in jedem Container verbessern kann. Wenn das Steuerelement speziell für die Verwendung mit einem bestimmten Containertyp vorgesehen ist, sollten Sie untersuchen, welche dieser Optimierungen von diesem Container unterstützt wird. Im Allgemeinen sollten Sie jedoch versuchen, so viele dieser Techniken zu implementieren, wie Sie für ihr bestimmtes Steuerelement gelten, um sicherzustellen, dass das Steuerelement genauso gut wie möglich in einer Vielzahl von Containern funktioniert.

Sie können viele dieser Optimierungen über den [MFC-ActiveX-Steuer](reference/mfc-activex-control-wizard.md)Element-Assistenten auf der Seite mit den Steuerelement [Einstellungen](reference/control-settings-mfc-activex-control-wizard.md) implementieren.

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC-ActiveX-Steuerelement-Assistent

|Steuerelement Einstellung im MFC-ActiveX-Steuerelement-Assistenten|Aktion|Weitere Informationen|
|-------------------------------------------------------|------------|----------------------|
|Kontrollkästchen **aktivieren, wenn sichtbar**|Löschen|[Deaktivieren der Option "bei sichtbar aktivieren"](turning-off-the-activate-when-visible-option.md)|
|Kontrollkästchen für die **Fensterlose Aktivierung**|Select|[Bereitstellung von fensterloser Aktivierung](providing-windowless-activation.md)|
|Kontrollkästchen für den **nicht geschnittenen Gerätekontext**|Select|[Verwenden eines Gerätekontexts ohne Clippingbereichsanpassung](using-an-unclipped-device-context.md)|
|Kontrollkästchen für die **flimmerfreie Aktivierung**|Select|[Bereitstellen flimmerfreier Aktivierung](providing-flicker-free-activation.md)|
|Kontrollkästchen für **Mauszeiger Benachrichtigungen, wenn inaktiv**|Select|[Bereitstellen von Mausinteraktionen in inaktiven Steuerelementen](providing-mouse-interaction-while-inactive.md)|
|**Optimierter Zeichnungs Code** (Kontrollkästchen)|Select|[Optimieren der Steuerelementdarstellung](optimizing-control-drawing.md)|

Ausführliche Informationen zu den Member-Funktionen, die diese Optimierungen implementieren, finden Sie unter [COleControl](reference/colecontrol-class.md).

Weitere Informationen finden Sie unter

- [Optimieren von Persistenz und Initialisierung](optimizing-persistence-and-initialization.md)

- [Bereitstellung von fensterloser Aktivierung](providing-windowless-activation.md)

- [Deaktivieren der Option "bei sichtbar aktivieren"](turning-off-the-activate-when-visible-option.md)

- [Bereitstellen von Mausinteraktionen in inaktiven Steuerelementen](providing-mouse-interaction-while-inactive.md)

- [Bereitstellen flimmerfreier Aktivierung](providing-flicker-free-activation.md)

- [Verwenden eines Gerätekontexts ohne Clippingbereichsanpassung](using-an-unclipped-device-context.md)

- [Optimieren der Steuerelementdarstellung](optimizing-control-drawing.md)

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
