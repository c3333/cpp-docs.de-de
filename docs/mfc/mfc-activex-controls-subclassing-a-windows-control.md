---
title: 'MFC-ActiveX-Steuerelemente: Erstellen einer Fenstersteuerelement-Unterklasse'
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: c68a7c9764e7f52131a90d38db22d2645eed9a4f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625413"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC-ActiveX-Steuerelemente: Erstellen einer Fenstersteuerelement-Unterklasse

In diesem Artikel wird der Prozess zum Unterklassen eines allgemeinen Windows-Steuer Elements zum Erstellen eines ActiveX-Steuer Elements beschrieben. Die Unterklassen eines vorhandenen Windows-Steuer Elements sind eine schnelle Möglichkeit, ein ActiveX-Steuerelement zu entwickeln. Das neue Steuerelement verfügt über die Möglichkeiten des untergeordneten Windows-Steuer Elements, z. b. das Zeichnen von und das reagieren auf Mausklicks. Die Beispiel [Schaltfläche](../overview/visual-cpp-samples.md) für MFC-ActiveX-Steuerelemente ist ein Beispiel für das Unterklassen-Steuerelement.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Führen Sie die folgenden Aufgaben aus, um ein Windows-Steuerelement zu unterteilen:

- [Überschreiben der Member-Funktionen von IsSubclassedControl und prekreatewindow von COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Ändern der OnDraw-Member-Funktion](#_core_modifying_the_ondraw_member_function)

- [Verarbeiten aller mit dem Steuerelement reflektierten ActiveX-Steuerelement Meldungen (OCM)](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Ein Großteil dieser Aufgaben wird vom ActiveX-Steuerelement-Assistenten ausgeführt, wenn Sie auf der Seite mit den **Steuerelement Einstellungen** die Dropdown Liste über **geordnete Fenster Klasse auswählen** auswählen.

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Überschreiben von IsSubclassedControl und prekreatewindow

Um und zu überschreiben `PreCreateWindow` `IsSubclassedControl` , fügen Sie dem **geschützten** Abschnitt der Deklaration der Steuerelement Klasse die folgenden Codezeilen hinzu:

[!code-cpp[NVC_MFC_AxSub#1](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

In der Implementierungs Datei des Steuer Elements (. Cpp) fügen Sie die folgenden Codezeilen hinzu, um die beiden überschriebenen Funktionen zu implementieren:

[!code-cpp[NVC_MFC_AxSub#2](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Beachten Sie, dass in diesem Beispiel das Windows-Schaltflächen-Steuerelement in angegeben wird `PreCreateWindow` . Allerdings können alle standardmäßigen Windows-Steuerelemente untergeordnet werden. Weitere Informationen zu standardmäßigen Windows-Steuerelementen finden Sie unter Steuer [Elemente](controls-mfc.md).

Beim Durchlaufen eines Windows-Steuer Elements können Sie bestimmte Fenster Stile (WS_) oder erweiterte Fenster Stil-Flags (WS_EX_) angeben, die zum Erstellen des Steuer Elements des Steuer Elements verwendet werden sollen. Sie können Werte für diese Parameter in der `PreCreateWindow` Member-Funktion festlegen, indem Sie die `cs.style` `cs.dwExStyle` Struktur Felder und ändern. Änderungen an diesen Feldern sollten mithilfe eines- **oder** -Vorgangs vorgenommen werden, um die Standardflags beizubehalten, die von der-Klasse festgelegt werden `COleControl` . Wenn das Steuerelement beispielsweise das Schaltflächen-Steuerelement Unterklassen und das Steuerelement als Kontrollkästchen angezeigt werden soll, fügen Sie die folgende Codezeile in die-Implementierung von `CSampleCtrl::PreCreateWindow` vor der Return-Anweisung ein:

[!code-cpp[NVC_MFC_AxSub#3](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Durch diesen Vorgang wird das BS_CHECKBOX stilflag hinzugefügt, während das standardstilflag (WS_CHILD) der Klasse `COleControl` intakt bleibt.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Ändern der OnDraw-Member-Funktion

Wenn Sie möchten, dass das untergeordnete Steuerelement die gleiche Darstellung wie das entsprechende Windows-Steuerelement behält, `OnDraw` sollte die Member-Funktion für das Steuerelement nur einen aufzurufenden `DoSuperclassPaint` Member enthalten, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFC_AxSub#4](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

Die `DoSuperclassPaint` Member-Funktion, die von implementiert wird, `COleControl` verwendet die Fenster Prozedur des Windows-Steuer Elements, um das Steuerelement im angegebenen Gerätekontext innerhalb des umgebenden Rechtecks zu zeichnen. Dadurch wird das Steuerelement sichtbar, auch wenn es nicht aktiv ist.

> [!NOTE]
> Die `DoSuperclassPaint` Member-Funktion kann nur mit den Steuerelement Typen verwendet werden, die es ermöglichen, einen Gerätekontext als *wParam* einer WM_PAINT Nachricht zu erhalten. Dies schließt einige der standardmäßigen Windows-Steuerelemente ein, z. b. ScrollBar und Schaltfläche sowie alle allgemeinen Steuerelemente. Für Steuerelemente, die dieses Verhalten nicht unterstützen, müssen Sie Ihren eigenen Code bereitstellen, damit ein inaktives Steuerelement ordnungsgemäß angezeigt wird.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Behandeln von reflektierten Fenster Meldungen

Windows-Steuerelemente senden normalerweise bestimmte Fenster Meldungen an das übergeordnete Fenster. Einige dieser Nachrichten, wie z. b. WM_COMMAND, stellen eine Benachrichtigung über eine Aktion durch den Benutzer bereit. Andere, wie z. b. WM_CTLCOLOR, werden zum Abrufen von Informationen aus dem übergeordneten Fenster verwendet. Ein ActiveX-Steuerelement kommuniziert in der Regel mit dem übergeordneten Fenster auf andere Weise. Benachrichtigungen werden durch das Auslösen von Ereignissen (Senden von Ereignis Benachrichtigungen) kommuniziert, und Informationen zum Steuerelement Container werden durchzugreifen auf die Umgebungs Eigenschaften des Containers abgerufen. Da diese Kommunikationstechniken vorhanden sind, wird von ActiveX-Steuerelement Containern nicht erwartet, dass vom Steuerelement gesendete Fenster Meldungen verarbeitet werden.

Um zu verhindern, dass der Container die Fenster Meldungen empfängt, die von einem untergeordneten Windows-Steuerelement gesendet werden, `COleControl` erstellt ein zusätzliches Fenster, das als übergeordnetes Element des Steuer Elements fungiert. Dieses zusätzliche Fenster, das als "Reflektor" bezeichnet wird, wird nur für ein ActiveX-Steuerelement erstellt, das ein Windows-Steuerelement unterteilt und dieselbe Größe und Position wie das Steuerelement Fenster hat. Das Reflektorfenster fängt bestimmte Fenster Meldungen ab und sendet Sie zurück an das-Steuerelement. Das-Steuerelement kann dann in seiner Fenster Prozedur diese reflektierten Meldungen durch Ausführen von Aktionen verarbeiten, die für ein ActiveX-Steuerelement geeignet sind (z. b. das Auslösen eines Ereignisses). Eine Liste der abgefangenen Windows-Meldungen und der zugehörigen reflektierten Meldungen finden Sie unter [Message IDs des reflektierten Fensters](reflected-window-message-ids.md) .

Ein ActiveX-Steuerelement Container kann zur Durchführung der Nachrichten Reflektion entworfen werden. Dadurch entfällt die Notwendigkeit `COleControl` , das Reflektorfenster zu erstellen und den Lauf Zeitaufwand für ein untergeordnetes Windows-Steuerelement zu verringern. `COleControl`erkennt, ob der Container diese Funktion unterstützt, indem eine MessageReflect Ambient-Eigenschaft mit dem Wert **true**überprüft wird.

Fügen Sie der Steuerelement Meldungs Zuordnung einen Eintrag hinzu, und implementieren Sie eine Handlerfunktion, um eine reflektierte Fenster Meldung zu verarbeiten. Da reflektierte Nachrichten nicht Teil des Standardsatzes der von Windows definierten Nachrichten sind, unterstützt Klassenansicht das Hinzufügen solcher Nachrichten Handler nicht. Es ist jedoch nicht schwierig, manuell einen Handler hinzuzufügen.

Gehen Sie zum Hinzufügen eines Meldungs Handlers für eine reflektierte Fenster Meldung manuell wie folgt vor:

- In der Steuerelement Klasse. H-Datei, deklarieren Sie eine Handlerfunktion. Die Funktion sollte den Rückgabetyp **LRESULT** und zwei Parameter mit den Typen **wParam** bzw. **LPARAM**aufweisen. Beispiel:

   [!code-cpp[NVC_MFC_AxSub#5](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- In der Steuerelement Klasse. Cpp-Datei, fügen Sie der Meldungs Zuordnung einen ON_MESSAGE Eintrag hinzu. Die Parameter dieses Eintrags sollten der Nachrichten Bezeichner und der Name der Handlerfunktion sein. Beispiel:

   [!code-cpp[NVC_MFC_AxSub#7](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Auch in der. Cpp-Datei, implementieren `OnOcmCommand` Sie die Member-Funktion, um die reflektierte Nachricht zu verarbeiten. Die *wParam* -Parameter und die *LPARAM* -Parameter sind identisch mit denen der ursprünglichen Fenster Meldung.

Ein Beispiel für die Verarbeitung von reflektierten Nachrichten finden Sie in der Beispiel [Schaltfläche](../overview/visual-cpp-samples.md)MFC-ActiveX-Steuerelemente. Es veranschaulicht einen `OnOcmCommand` Handler, der den BN_CLICKED Benachrichtigungs Code erkennt und antwortet, indem er ein-Ereignis auslöst (sendet) `Click` .

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
