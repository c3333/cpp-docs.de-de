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
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375995"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>MFC-ActiveX-Steuerelemente: Erstellen einer Fenstersteuerelement-Unterklasse

In diesem Artikel wird der Prozess zum Unterklasseneines eines gemeinsamen Windows-Steuerelements zum Erstellen eines ActiveX-Steuerelements beschrieben. Das Unterklassen eines vorhandenen Windows-Steuerelements ist eine schnelle Möglichkeit, ein ActiveX-Steuerelement zu entwickeln. Das neue Steuerelement verfügt über die Fähigkeiten des unterklassigen Windows-Steuerelements, z. B. das Malen und Reagieren auf Mausklicks. Das MFC ActiveX-Steuerelementbeispiel [BUTTON](../overview/visual-cpp-samples.md) ist ein Beispiel für die Unterklasse eines Windows-Steuerelements.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Um ein Windows-Steuerelement unterzuklassieren, führen Sie die folgenden Aufgaben aus:

- [Überschreiben der IsSubclassedControl- und PreCreateWindow-Memberfunktionen von COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Ändern der OnDraw-Memberfunktion](#_core_modifying_the_ondraw_member_function)

- [Behandeln Sie alle ActiveX-Steuermeldungen (OCM), die auf das Steuerelement](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Ein Großteil dieser Arbeit wird vom ActiveX Control Wizard erledigt, wenn Sie das Steuerelement auswählen, das mithilfe der Dropdownliste **"Übergeordnete Fensterklasse auswählen"** auf der Seite **Steuerelementeinstellungen** unterklassig sein soll.

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Überschreiben von IsSubclassedControl und PreCreateWindow

Um zu `PreCreateWindow` `IsSubclassedControl`überschreiben und fügen Sie dem **geschützten** Abschnitt der Steuerelementklassendeklaration die folgenden Codezeilen hinzu:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

In der Kontrollimplementierungsdatei (. CPP), fügen Sie die folgenden Codezeilen hinzu, um die beiden überschriebenen Funktionen zu implementieren:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Beachten Sie, dass in diesem Beispiel das `PreCreateWindow`Windows-Schaltflächensteuerelement in angegeben ist. Alle standardmäßigen Windows-Steuerelemente können jedoch unterklassifiziert werden. Weitere Informationen zu Standard-Windows-Steuerelementen finden Sie unter [Steuerelemente](../mfc/controls-mfc.md).

Wenn Sie ein Windows-Steuerelement unterklassen, können Sie bestimmte Fensterstil- (WS_) oder erweiterte Fensterstil-Flags (WS_EX_) angeben, die beim Erstellen des Steuerelementfensters verwendet werden sollen. Sie können Werte für diese `PreCreateWindow` Parameter in der `cs.style` Memberfunktion festlegen, indem Sie die und die `cs.dwExStyle` Strukturfelder ändern. Änderungen an diesen Feldern sollten mithilfe eines **ODER-Vorgangs** vorgenommen werden, um die Standardflags beizubehalten, die von class `COleControl`festgelegt werden. Wenn das Steuerelement z. B. das BUTTON-Steuerelement unterklassifiziert und das Steuerelement als Kontrollkästchen angezeigt werden `CSampleCtrl::PreCreateWindow`soll, fügen Sie die folgende Codezeile in die Implementierung von ein, vor der Rückgabeanweisung:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Dieser Vorgang fügt das BS_CHECKBOX Stilflag hinzu, während das `COleControl` Standardstilflag (WS_CHILD) der Klasse intakt bleibt.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Ändern der OnDraw-Memberfunktion

Wenn das steuerelement unterklassige Steuerelement die gleiche Darstellung wie `OnDraw` das entsprechende Windows-Steuerelement beibehalten soll, sollte die Memberfunktion für das Steuerelement nur einen Aufruf der `DoSuperclassPaint` Memberfunktion enthalten, wie im folgenden Beispiel:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

Die `DoSuperclassPaint` Memberfunktion, `COleControl`implementiert von , verwendet die Fensterprozedur des Windows-Steuerelements, um das Steuerelement im angegebenen Gerätekontext innerhalb des umgebenden Rechtecks zu zeichnen. Dadurch wird das Steuerelement auch dann sichtbar, wenn es nicht aktiv ist.

> [!NOTE]
> Die `DoSuperclassPaint` Memberfunktion funktioniert nur mit den Steuerelementtypen, die es ermöglichen, einen Gerätekontext als *wParam* einer WM_PAINT Nachricht zu übergeben. Dazu gehören einige der standardmäßigen Windows-Steuerelemente, z. B. SCROLLBAR und BUTTON, sowie alle gängigen Steuerelemente. Für Steuerelemente, die dieses Verhalten nicht unterstützen, müssen Sie eigenen Code bereitstellen, um ein inaktives Steuerelement ordnungsgemäß anzuzeigen.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Umgang mit reflektierten Fensternachrichten

Windows-Steuerelemente senden in der Regel bestimmte Fensternachrichten an das übergeordnete Fenster. Einige dieser Nachrichten, z. B. WM_COMMAND, stellen eine Benachrichtigung über eine Aktion des Benutzers bereit. Andere, z. B. WM_CTLCOLOR, werden verwendet, um Informationen aus dem übergeordneten Fenster abzuholen. Ein ActiveX-Steuerelement kommuniziert in der Regel auf andere Weise mit dem übergeordneten Fenster. Benachrichtigungen werden durch auslösende Ereignisse (Senden von Ereignisbenachrichtigungen) kommuniziert, und Informationen über den Steuerelementcontainer werden durch Den Zugriff auf die Umgebungseigenschaften des Containers abgerufen. Da diese Kommunikationstechniken vorhanden sind, wird von ActiveX-Steuerelementcontainern nicht erwartet, dass sie Fensternachrichten verarbeiten, die vom Steuerelement gesendet werden.

Um zu verhindern, dass der Container die Fensternachrichten `COleControl` empfängt, die von einem Windows-Steuerelement unter Klasse gesendet werden, wird ein zusätzliches Fenster erstellt, das als übergeordnetes Steuerelement dient. Dieses zusätzliche Fenster, das als "Reflektor" bezeichnet wird, wird nur für ein ActiveX-Steuerelement erstellt, das ein Windows-Steuerelement unterklassen und die gleiche Größe und Position wie das Steuerfenster hat. Das Reflektorfenster fängt bestimmte Fensternachrichten ab und sendet sie zurück an das Steuerelement. Das Steuerelement kann dann in seiner Fensterprozedur diese reflektierten Nachrichten verarbeiten, indem es Aktionen ausnimmt, die für ein ActiveX-Steuerelement geeignet sind (z. B. auslösen eines Ereignisses). Eine Liste der abgefangenen Windows-Nachrichten und der zugehörigen reflektierten Nachrichten finden Sie unter ["Reflektierte Fensternachrichten-IDs".](../mfc/reflected-window-message-ids.md)

Ein ActiveX-Steuerelementcontainer kann so konzipiert werden, dass `COleControl` er die Nachrichtenreflektion selbst durchführt, sodass das Reflektorfenster nicht mehr erstellt werden muss, und der Laufzeitaufwand für ein Windows-Steuerelement unter Klasse reduziert wird. `COleControl`erkennt, ob der Container diese Funktion unterstützt, indem er nach einer MessageReflect-Umgebungseigenschaft mit dem Wert **TRUE**sucht.

Um eine reflektierte Fensternachricht zu behandeln, fügen Sie der Steuermeldungszuordnung einen Eintrag hinzu, und implementieren Sie eine Handlerfunktion. Da reflektierte Nachrichten nicht Teil des von Windows definierten Standardsatzes von Nachrichten sind, unterstützt die Klassenansicht das Hinzufügen solcher Nachrichtenhandler nicht. Es ist jedoch nicht schwierig, einen Handler manuell hinzuzufügen.

Gehen Sie wie folgt vor, um einen Nachrichtenhandler für eine reflektierte Fensternachricht manuell hinzuzufügen:

- In der Steuerungsklasse . H-Datei, deklarieren Sie eine Handlerfunktion. Die Funktion sollte einen Rückgabetyp von **LRESULT** und zwei Parameter mit den Typen **WPARAM** und **LPARAM**aufweisen. Beispiel:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- In der Steuerungsklasse . CPP-Datei, fügen Sie der Meldungszuordnung einen ON_MESSAGE Eintrag hinzu. Die Parameter dieses Eintrags sollten der Nachrichtenbezeichner und der Name der Handlerfunktion sein. Beispiel:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Auch in der . CPP-Datei, `OnOcmCommand` implementieren Sie die Memberfunktion, um die reflektierte Nachricht zu verarbeiten. Die Parameter *wParam* und *lParam* entsprechen denen der ursprünglichen Fensternachricht.

Ein Beispiel für die Verarbeitung von reflektierten Nachrichten finden Sie im Beispiel der MFC ActiveX-Steuerelemente [BUTTON](../overview/visual-cpp-samples.md). Es zeigt `OnOcmCommand` einen Handler, der die BN_CLICKED-Benachrichtigungscodes erkennt `Click` und durch Auslösen (Senden) eines Ereignisses antwortet.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
