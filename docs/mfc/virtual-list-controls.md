---
title: Virtuelle Listensteuerelemente
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375515"
---
# <a name="virtual-list-controls"></a>Virtuelle Listensteuerelemente

Ein virtuelles Listensteuerelement ist ein Listenansichtssteuerelement mit dem Stil LVS_OWNERDATA. Dieser Stil ermöglicht es dem Steuerelement, eine Elementanzahl bis zu einem **DWORD** zu unterstützen (die Standardelementanzahl erstreckt sich nur auf einen **int**). Der größte Vorteil dieses Stils ist jedoch die Möglichkeit, nur eine Teilmenge von Datenelementen gleichzeitig im Arbeitsspeicher zu haben. Auf diese Weise kann sich das Steuerelement für die virtuelle Listenansicht für die Verwendung mit großen Informationsdatenbanken eignen, in denen bereits bestimmte Methoden für den Zugriff auf Daten vorhanden sind.

> [!NOTE]
> Neben der Bereitstellung virtueller `CListCtrl`Listenfunktionen in bietet MFC auch die gleiche Funktionalität in der [CListView-Klasse.](../mfc/reference/clistview-class.md)

Es gibt einige Kompatibilitätsprobleme, die Sie beim Entwickeln virtueller Listensteuerelemente beachten sollten. Weitere Informationen finden Sie im Abschnitt Kompatibilitätsprobleme im Thema Listenansichtssteuerelemente im Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Behandeln der LVN_GETDISPINFO Benachrichtigung

Virtuelle Listensteuerelemente verwalten nur sehr wenige Elementinformationen. Mit Ausnahme der Artikelauswahl- und Fokusinformationen werden alle Elementinformationen vom Besitzer des Steuerelements verwaltet. Informationen werden vom Framework über eine LVN_GETDISPINFO Benachrichtigung angefordert. Um die angeforderten Informationen bereitzustellen, muss der Besitzer des virtuellen Listensteuerelements (oder das Steuerelement selbst) diese Benachrichtigung behandeln. Dies kann ganz einfach mit dem [Klassen-Assistenten](reference/mfc-class-wizard.md) erfolgen (siehe [Zuordnen von Nachrichten zu Funktionen](../mfc/reference/mapping-messages-to-functions.md)). Der resultierende Code sollte etwa wie im `CMyDialog` folgenden Beispiel aussehen (wo das virtuelle Listensteuerelementobjekt gehört und das Dialogfeld die Benachrichtigung verarbeitet):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

Im Handler für die LVN_GETDISPINFO Benachrichtigung müssen Sie überprüfen, welche Art von Informationen angefordert werden. Mögliche Werte:

- `LVIF_TEXT`Das *pszText-Element* muss ausgefüllt werden.

- `LVIF_IMAGE`Das *iImage-Member* muss ausgefüllt werden.

- `LVIF_INDENT`Das *iIndent-Element* muss ausgefüllt werden.

- `LVIF_PARAM`Das *lParam-Mitglied* muss ausgefüllt werden. (Nicht vorhanden für Unterpositionen.)

- `LVIF_STATE`Das *Landesmitglied* muss ausgefüllt werden.

Sie sollten dann alle angeforderten Informationen an den Rahmen zurückgeben.

Das folgende Beispiel (aus dem Text des Benachrichtigungshandlers für das Listensteuerelementobjekt) veranschaulicht eine mögliche Methode, indem Informationen für die Textpuffer und das Bild eines Elements zur Verfügung gestellt werden:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Zwischenspeichern und virtuelle Listensteuerelemente

Da dieser Typ von Listensteuerelement für große Datensätze vorgesehen ist, wird empfohlen, angeforderte Elementdaten zwischenzuspeichern, um die Abrufleistung zu verbessern. Das Framework bietet einen Cache-Hinweismechanismus, der die Optimierung des Caches durch Senden einer LVN_ODCACHEHINT Benachrichtigung unterstützt.

Im folgenden Beispiel wird der Cache mit dem Bereich aktualisiert, der an die Handlerfunktion übergeben wird.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Weitere Informationen zum Vorbereiten und Verwalten eines Caches finden Sie im Abschnitt Cacheverwaltung im Thema Listenansichtssteuerelemente im Windows SDK.

## <a name="finding-specific-items"></a>Suchen bestimmter Elemente

Die LVN_ODFINDITEM Benachrichtigungwird vom virtuellen Listensteuerelement gesendet wird, wenn ein bestimmtes Listensteuerelement gefunden werden muss. Die Benachrichtigung wird gesendet, wenn das Listenansichtssteuerelement schnellen Schlüsselzugriff empfängt oder wenn es eine LVM_FINDITEM Nachricht empfängt. Suchinformationen werden in Form einer **LVFINDINFO-Struktur** gesendet, die mitglied der **NMLVFINDITEM-Struktur** ist. Behandeln Sie diese Meldung, indem Sie die `OnChildNotify` Funktion des Listensteuerelements und innerhalb des Hauptteils des Handlers überschreiben, überprüfen Sie, ob die LVN_ODFINDITEM Nachricht. Wenn gefunden, führen Sie die entsprechende Aktion aus.

Sie sollten bereit sein, nach einem Element zu suchen, das den Informationen des Listenansichtssteuerelements entspricht. Sie sollten den Index des Elements zurückgeben, wenn es erfolgreich ist, oder -1, wenn kein übereinstimmendes Element gefunden wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](../mfc/using-clistctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
