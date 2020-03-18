---
title: Die CCmdUI-Klasse
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 105aa7ad6c5cc6a5563dbde8145327a2b3d066a1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447140"
---
# <a name="the-ccmdui-class"></a>Die CCmdUI-Klasse

Wenn ein Update Befehl an seinen Handler weitergeleitet wird, übergibt das Framework den Handler einen Zeiger auf ein `CCmdUI` Objekt (oder auf ein Objekt einer `CCmdUI`abgeleiteten Klasse). Dieses Objekt stellt das Menü Element oder die Symbolleisten Schaltfläche oder ein anderes Benutzeroberflächen Objekt dar, das den Befehl generiert hat. Der Update Handler Ruft die Member-Funktionen der `CCmdUI` Struktur über den-Zeiger auf, um das Benutzeroberflächen Objekt zu aktualisieren. Hier ist beispielsweise ein Update Handler für das Menü Element Alle löschen:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Dieser Handler Ruft die `Enable` Member-Funktion eines Objekts mit Zugriff auf das Menü Element auf. `Enable` stellt das Element für die Verwendung zur Verfügung.

## <a name="see-also"></a>Weitere Informationen

[Vorgehensweise: Aktualisieren von Benutzeroberflächenobjekten](../mfc/how-to-update-user-interface-objects.md)
