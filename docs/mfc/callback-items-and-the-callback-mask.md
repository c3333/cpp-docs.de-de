---
title: Rückrufelemente und die Rückrufmaske
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 1c46f6edb44e4898c0245209ca837cd0eb716304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624971"
---
# <a name="callback-items-and-the-callback-mask"></a>Rückrufelemente und die Rückrufmaske

Für alle Elemente speichert ein Listenansicht-Steuerelement in der Regel den Beschriftungs Text, den Bildlisten Index der Element Symbole und einen Satz von Bitflags für den Zustand des Elements. Sie können einzelne Elemente als Rückruf Elemente definieren, was nützlich ist, wenn Ihre Anwendung bereits einige der Informationen für ein Element speichert.

Ein Element wird als Rückruf Element definiert, indem geeignete Werte für die `pszText` -und-Member der-Struktur angegeben werden `iImage` `LVITEM` (siehe [CListCtrl:: GetItem](reference/clistctrl-class.md#getitem)). Wenn die Anwendung den Text des Elements oder des unter Elements verwaltet, geben Sie den **LPSTR_TEXTCALLBACK** Wert für den `pszText` Member an. Wenn die Anwendung das Symbol für das Element nachverfolgt, geben Sie den **I_IMAGECALLBACK** Wert für den `iImage` Member an.

Zusätzlich zum Definieren von Rückruf Elementen können Sie auch die Rückruf Maske des Steuer Elements ändern. Bei dieser Maske handelt es sich um einen Satz von Bitflags, die die Element Zustände angeben, für die die Anwendung und nicht das Steuerelement die aktuellen Daten speichert. Die Rückruf Maske gilt für alle Elemente des Steuer Elements, im Gegensatz zur Rückruf Element Bezeichnung, die für ein bestimmtes Element gilt. Die Rückruf Maske ist standardmäßig 0 (null), was bedeutet, dass das Steuerelement alle Element Zustände nachverfolgt. Um dieses Standardverhalten zu ändern, initialisieren Sie die Maske mit einer beliebigen Kombination der folgenden Werte:

- **LVIS_CUT** Das Element ist für einen Ausschneide-und Einfügevorgang gekennzeichnet.

- **LVIS_DROPHILITED** Das Element wird als Drag & Drop-Ziel hervorgehoben.

- **LVIS_FOCUSED** Das Element hat den Fokus.

- **LVIS_SELECTED** Das Element ist ausgewählt.

- **LVIS_OVERLAYMASK** Die Anwendung speichert den Abbild Listen Index des aktuellen Überlagerungs Bilds für jedes Element.

- **LVIS_STATEIMAGEMASK** Die Anwendung speichert den Abbild Listen Index des aktuellen Status Bilds für jedes Element.

Weitere Informationen zum Abrufen und Festlegen dieser Maske finden Sie unter [CListCtrl:: GetCallbackMask](reference/clistctrl-class.md#getcallbackmask) und [CListCtrl:: SetCallbackMask](reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Siehe auch

[Verwenden von CListCtrl](using-clistctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
