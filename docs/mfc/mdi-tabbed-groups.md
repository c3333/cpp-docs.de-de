---
title: MDI-Gruppen im Registerkartenformat
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: 0c1bf925003d5081b2cdc837012a57585b1ace60
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624363"
---
# <a name="mdi-tabbed-groups"></a>MDI-Gruppen im Registerkartenformat

Die MDI-Funktion (Multiple Document Interface) im Registerkarten Format ermöglicht es mehreren Dokumenten Schnittstellen (MDI)-Anwendungen, ein oder mehrere Fenster im Register Format (oder Gruppen von Fenstern im Registerkarten *Format) im*MDI-Client Bereich anzuzeigen. Die Fenster im Registerkarten Format können vertikal oder horizontal ausgerichtet werden. Wenn eine Anwendung mehr als eine MDI-Gruppe mit Registerkarten hostet, werden die Gruppen durch Splitters getrennt.

## <a name="features"></a>Features

Im folgenden sind die Features der MDI-Gruppen im Registerkarten Format aufgeführt:

- Eine Anwendung kann Fenster im Registerkarten Format dynamisch erstellen.

- Eine Anwendung kann Fenster im Registerkarten Format horizontal oder vertikal ausrichten.

- Gruppen von Fenstern im Registerkarten Format werden durch Splitters getrennt. Der Benutzer kann die Größe der Gruppen im Registerkarten Format mithilfe des Splitters ändern.

- Der Benutzer kann einzelne Registerkarten zwischen Gruppen ziehen.

- Der Benutzer kann einzelne Registerkarten ziehen, um neue Gruppen zu erstellen.

- Der Benutzer kann mithilfe eines Kontextmenüs Registerkarten verschieben oder neue Gruppen erstellen.

- Eine Anwendung kann das Layout von Fenstern im Registerkarten Format speichern und laden.

- Eine Anwendung kann die Liste der MDI-Dokumente speichern und laden.

- Eine Anwendung kann auf einzelne Gruppen im Registerkarten Format zugreifen und deren Parameter ändern.

### <a name="using-mdi-tabbed-groups"></a>Verwenden von MDI-Gruppen im Registerkarten Format

Im folgenden sind die Aufgaben aufgeführt, die häufig für MDI-Gruppen im Registerkarten Format ausgeführt

- Um MDI-Gruppen im Registerkarten Format für ein Hauptrahmen Fenster zu aktivieren, müssen Sie [CMDIFrameWndEx:: EnableMDITabbedGroups](reference/cmdiframewndex-class.md#enablemditabbedgroups)anfordern. Der zweite Parameter dieser Methode ist eine Instanz der- `CMDITabInfo` Klasse. Sie können die Standardparameter verwenden oder Sie vor dem Ausführen von ändern `CMDIFrameWndEx::EnableMDITabbedGroups` .

- Erstellen oder ändern Sie ein `CMDITabInfo` -Objekt, und rufen Sie erneut auf, um die Eigenschaften einer MDI-Gruppe im Registerkarten Format zur Laufzeit zu ändern. `CMDIFrameWndEx::EnableMDITabbedGroups`

- Rufen Sie auf, um eine Liste der MDI-Fenster im Registerkarten Format zu erhalten `CMDIFrameWndEx::GetMDITabGroups` .

- Rufen Sie auf, um eine neue MDI-Gruppe im Registerkarten Format neben einer aktiven Gruppe im Registerkarten Format zu erstellen `CMDIFrameWndEx::MDITabNewGroup` .

- Um den Eingabefokus auf das vorherige oder nächste Fenster einer Gruppe im Registerkarten Format zu verschieben, geben Sie an `CMDIFrameWndEx::MDITabMoveToNextGroup` .

- , Um zu bestimmen, ob ein Fenster ein Member eines MDI-Gruppen Aufrufes im Registerkarten Format ist `CMDIFrameWndEx::IsMemberOfMDITabGroup` .

- Um zu ermitteln, ob die MDI-Registerkarten oder MDI-Gruppen im Registerkarten Format für ein Hauptrahmen Fenster aktiviert sind, können Sie `CMDIFrameWndEx::AreMDITabs` Um nur festzustellen, ob MDI-Gruppen im Registerkarten Format aktiviert sind, wird aufgerufen `CMDIFrameWndEx::IsMDITabbedGroup` .

- Überschreiben Sie `CMDIFrameWndEx::OnShowMDITabContextMenu` in der von abgeleiteten Klasse, um ein Kontextmenü anzuzeigen, wenn der Benutzer auf eine Registerkarte klickt oder Sie in eine andere MDI-Gruppe mit Registerkarten zieht `CMDIFrameWndEx` . Wenn Sie diese Methode nicht implementieren, wird das Kontextmenü von der Anwendung nicht angezeigt.

- Um das Layout der MDI-Gruppen im Registerkarten Format in einer Anwendung zu speichern, wird aufgerufen `CMDIFrameWndEx::SaveMDIState` . Zum Laden eines zuvor gespeicherten MDI-Gruppen Profils im Registerkarten Format wird aufgerufen `CMDIFrameWndEx::LoadMDIState` . Diese Methoden können auch aufgerufen werden, um die Liste der geöffneten Dokumente in einer MDI-Anwendung zu laden oder zu speichern. Weitere Informationen zum Speichern und Laden des MDI-Zustands finden Sie unter [CMDIFrameWndEx:: loadmdistate](reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx-Klasse](reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx-Klasse](reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo-Klasse](reference/cmditabinfo-class.md)
