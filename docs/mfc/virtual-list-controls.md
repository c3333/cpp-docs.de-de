---
title: Virtuelle Listensteuerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 12200697af90a3c83fea3df676bd4d2488598d45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215919"
---
# <a name="virtual-list-controls"></a>Virtuelle Listensteuerelemente

Ein virtuelles Listen Steuerelement ist ein Listenansicht-Steuerelement, das über den LVS_OWNERDATA Stil verfügt. Dieser Stil ermöglicht es dem Steuerelement, eine Element Anzahl bis zu einem **DWORD** zu unterstützen (die Standardelement Anzahl wird nur auf einen erweitert **`int`** ). Der größte Vorteil dieses Stils ist jedoch die Möglichkeit, jeweils nur eine Teilmenge der Datenelemente im Arbeitsspeicher zu haben. Dadurch kann sich das Steuerelement für die virtuelle Listenansicht für die Verwendung mit großen Datenbanken mit Informationen eignen, bei denen bestimmte Methoden für den Datenzugriff bereits vorhanden sind.

> [!NOTE]
> Zusätzlich zur Bereitstellung von Funktionen für virtuelle Listen in `CListCtrl` bietet MFC auch die gleiche Funktionalität in der [CListView](../mfc/reference/clistview-class.md) -Klasse.

Es gibt einige Kompatibilitätsprobleme, die bei der Entwicklung von Virtual List-Steuerelementen zu beachten sind. Weitere Informationen finden Sie im Abschnitt Kompatibilitätsprobleme des Themas Listenansicht-Steuerelemente in der Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Behandeln der LVN_GETDISPINFO Benachrichtigung

Virtuelle Listen Steuerelemente behalten sehr wenig Element Informationen bei. Mit Ausnahme der Elementauswahl und der Fokus Informationen werden alle Element Informationen vom Besitzer des Steuer Elements verwaltet. Informationen werden vom Framework über eine LVN_GETDISPINFO Benachrichtigungs Meldung angefordert. Um die angeforderten Informationen bereitzustellen, muss der Besitzer des Steuer Elements der virtuellen Liste (oder das Steuerelement selbst) diese Benachrichtigung verarbeiten. Dies kann problemlos mithilfe des Klassen- [Assistenten](reference/mfc-class-wizard.md) erfolgen (Weitere Informationen finden Sie unter [Mapping messages to Functions](../mfc/reference/mapping-messages-to-functions.md)). Der resultierende Code sollte in etwa wie im folgenden Beispiel aussehen (dabei `CMyDialog` ist das virtuelle Listen Steuerelement Objekt, und das Dialogfeld verarbeitet die Benachrichtigung):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

Im Handler für die LVN_GETDISPINFO Benachrichtigungs Meldung müssen Sie überprüfen, um festzustellen, welche Art von Informationen angefordert werden. Mögliche Werte:

- `LVIF_TEXT`Der *pszText* -Member muss ausgefüllt werden.

- `LVIF_IMAGE`Der *iImage* -Member muss ausgefüllt werden.

- `LVIF_INDENT`Der *iIndent* -Member muss ausgefüllt werden.

- `LVIF_PARAM`Der *LPARAM* -Member muss ausgefüllt werden. (Für unter Elemente nicht vorhanden.)

- `LVIF_STATE`Der *State* -Member muss ausgefüllt werden.

Anschließend sollten Sie alle Informationen bereitstellen, die an das Framework zurück angefordert werden.

Im folgenden Beispiel (aus dem Text des Benachrichtigungs Handlers für das Listen Steuerelement-Objekt entnommen) wird eine mögliche Methode veranschaulicht, indem Informationen für die Text Puffer und das Bild eines Elements bereitgestellt werden:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Caching und Virtual List-Steuerelemente

Da diese Art von Listen Steuerelement für große Datasets gedacht ist, sollten Sie angeforderte Elementdaten Zwischenspeichern, um die Abruf Leistung zu verbessern. Das Framework bietet einen Cache-Hinting-Mechanismus, der die Optimierung des Caches durch Senden einer LVN_ODCACHEHINT Benachrichtigungs Meldung unterstützt.

Im folgenden Beispiel wird der Cache mit dem an die Handlerfunktion Übergabe Bereich aktualisiert.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Weitere Informationen zum Vorbereiten und Verwalten eines Caches finden Sie im Abschnitt Cache Verwaltung des Themas Listenansicht-Steuerelemente in der Windows SDK.

## <a name="finding-specific-items"></a>Suchen nach bestimmten Elementen

Die LVN_ODFINDITEM Benachrichtigungs Meldung wird vom Virtual List-Steuerelement gesendet, wenn ein bestimmtes Listen Steuerungselement gefunden werden muss. Die Benachrichtigungs Meldung wird gesendet, wenn das Listenansicht-Steuerelement einen schnellen Schlüssel Zugriff erhält oder wenn eine LVM_FINDITEM Nachricht empfangen wird. Suchinformationen werden in Form einer " **LVFINDINFO** "-Struktur gesendet, die ein Member der **nmlvfinditem** -Struktur ist. Behandeln Sie diese Nachricht, indem `OnChildNotify` Sie die Funktion des Listen Steuerelement Objekts überschreiben und innerhalb des Text Körpers des Handlers die LVN_ODFINDITEM Nachricht überprüfen. Wenn Sie gefunden werden, führen Sie die entsprechende Aktion aus.

Sie sollten darauf vorbereitet sein, nach einem Element zu suchen, das den vom Listenansicht-Steuerelement angegebenen Informationen entspricht. Wenn kein übereinstimmendes Element gefunden wird, sollten Sie den Index des Elements zurückgeben, oder-1, wenn kein entsprechendes Element gefunden wurde.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
