---
title: 'Container: Client-Element-Benachrichtigungen'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 54b1b2a64685b00fb265e0f80c1f6ad878a7da85
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623018"
---
# <a name="containers-client-item-notifications"></a>Container: Client-Element-Benachrichtigungen

In diesem Artikel werden die über schreibbaren Funktionen erläutert, die das MFC-Framework aufruft, wenn Server Anwendungen Elemente im Dokument Ihrer Client Anwendung ändern.

[COleClientItem](reference/coleclientitem-class.md) definiert mehrere über schreibbare Funktionen, die als Antwort auf Anforderungen von der Komponenten Anwendung aufgerufen werden, die auch als Serveranwendung bezeichnet wird. Diese außer Kraft setzungen fungieren in der Regel als Benachrichtigungen. Sie informieren die Containeranwendung über verschiedene Ereignisse, z. b. einen Bildlauf, eine Aktivierung oder eine Änderung der Position sowie über Änderungen, die der Benutzer beim Bearbeiten oder anderweitig bearbeiten des Elements vornimmt.

Das Framework benachrichtigt ihre Containeranwendung über die Änderungen durch einen-Befehl `COleClientItem::OnChange` , eine über schreibbare Funktion, deren Implementierung erforderlich ist. Diese geschützte Funktion empfängt zwei Argumente. Der erste gibt den Grund an, warum der Server das Element geändert hat:

|benachrichtigungs-|Bedeutung|
|------------------|-------------|
|**OLE_CHANGED**|Die Darstellung des OLE-Elements hat sich geändert.|
|**OLE_SAVED**|Das OLE-Element wurde gespeichert.|
|**OLE_CLOSED**|Das OLE-Element wurde geschlossen.|
|**OLE_RENAMED**|Das Server Dokument, das das OLE-Element enthält, wurde umbenannt.|
|**OLE_CHANGED_STATE**|Das OLE-Element wurde von einem Zustand in einen anderen geändert.|
|**OLE_CHANGED_ASPECT**|Der zeichnen-Aspekt des OLE-Elements wurde vom Framework geändert.|

Diese Werte stammen aus der **OLE_NOTIFICATION** -Enumeration, die in Afxole definiert ist. Micha.

Das zweite Argument für diese Funktion gibt an, wie sich das Element geändert hat oder welcher Zustand es eingegeben hat:

|Wenn das erste Argument ist|Zweites Argument|
|----------------------------|---------------------|
|**OLE_SAVED** oder **OLE_CLOSED**|Wird nicht verwendet.|
|**OLE_CHANGED**|Gibt den Aspekt des OLE-Elements an, das sich geändert hat.|
|**OLE_CHANGED_STATE**|Beschreibt den Zustand, der eingegeben wird (*emptystate*, *loadedstate*, *openstate*, *ActiveState*oder *activeuistate*).|

Weitere Informationen zu den Zuständen, die ein Client Element annehmen kann, finden Sie unter [Container: Client-Element-Zustände](containers-client-item-states.md).

Das Framework ruft auf `COleClientItem::OnGetItemPosition` , wenn ein Element für die direkte Bearbeitung aktiviert wird. Die Implementierung ist für Anwendungen erforderlich, die eine direkte Bearbeitung unterstützen. Der MFC-Anwendungs-Assistent bietet eine grundlegende-Implementierung, die die Koordinaten des Elements dem-Objekt zuweist, `CRect` das als Argument an das-Objekt übermittelt wird `OnGetItemPosition` .

Wenn die Position oder Größe eines OLE-Elements während der direkten Bearbeitung geändert wird, müssen die Informationen des Containers für die Position des Elements und die clippingrechtecke aktualisiert werden, und der Server muss Informationen zu den Änderungen erhalten. `COleClientItem::OnChangeItemPosition`Zu diesem Zweck Ruft das Framework auf. Der MFC-Anwendungs-Assistent bietet eine außer Kraft setzung, die die-Funktion der Basisklasse aufruft. Sie sollten die Funktion bearbeiten, die der Anwendungs-Assistent für die `COleClientItem` von abgeleitete Klasse schreibt, damit die Funktion alle Informationen aktualisiert, die von Ihrem Client-Element-Objekt aufbewahrt werden.

## <a name="see-also"></a>Siehe auch

[Container](containers.md)<br/>
[Container: Client-Element-Zustände](containers-client-item-states.md)<br/>
[COleClientItem:: OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)
