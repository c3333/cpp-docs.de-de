---
title: 'Automatisierungsserver: Probleme mit der Objektlebensdauer'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 8031902318a091b0ed5f340b454a14b9df195069
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225084"
---
# <a name="automation-servers-object-lifetime-issues"></a>Automatisierungsserver: Probleme mit der Objektlebensdauer

Wenn ein Automatisierungs Client ein OLE-Element erstellt oder aktiviert, übergibt der Server dem Client einen Zeiger auf das Objekt. Der Client erstellt einen Verweis auf das Objekt, indem er die OLE-Funktion [IUnknown:: adressf](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)aufruft. Dieser Verweis ist wirksam, bis der Client [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)aufruft. (Bei Client Anwendungen, die mit den OLE-Klassen der Microsoft Foundation Class-Bibliothek geschrieben wurden, müssen diese Aufrufe nicht durchführt werden. Das OLE-System und der Server selbst können Verweise auf das Objekt erstellen. Ein Server sollte ein Objekt nicht zerstören, solange externe Verweise auf das Objekt in Kraft bleiben.

Das Framework verwaltet eine interne Anzahl von Verweisen auf ein beliebiges Server Objekt, das von [CCmdTarget](reference/ccmdtarget-class.md)abgeleitet ist. Diese Anzahl wird aktualisiert, wenn ein Automation-Client oder eine andere Entität einen Verweis auf das-Objekt hinzufügt oder freigibt.

Wenn der Verweis Zähler auf 0 festgelegt wird, ruft das Framework die virtuelle Funktion [CCmdTarget:: OnFinalRelease](reference/ccmdtarget-class.md#onfinalrelease)auf. Die Standard Implementierung dieser Funktion Ruft den- **`delete`** Operator auf, um dieses Objekt zu löschen.

Der Microsoft Foundation Class-Bibliothek bietet zusätzliche Funktionen zum Steuern des Anwendungs Verhaltens, wenn externe Clients Verweise auf die Objekte der Anwendung haben. Neben der Beibehaltung der Anzahl der Verweise auf jedes Objekt behalten die Server eine globale Anzahl aktiver Objekte bei. Die globalen Funktionen [AfxOleLockApp](reference/application-control.md#afxolelockapp) und [AfxOleUnlockApp](reference/application-control.md#afxoleunlockapp) aktualisieren die Anzahl aktiver Objekte der Anwendung. Wenn diese Anzahl nicht 0 (null) ist, wird die Anwendung nicht beendet, wenn der Benutzer im Menü "System" die Option schließen auswählt oder im Menü Datei auf Beenden klickt. Stattdessen wird das Hauptfenster der Anwendung ausgeblendet (aber nicht zerstört), bis alle ausstehenden Client Anforderungen abgeschlossen sind. `AfxOleLockApp` `AfxOleUnlockApp` In der Regel werden und in den Konstruktoren bzw. debugktoren von Klassen aufgerufen, die Automation unterstützen.

Manchmal erzwingen Umstände, dass der Server beendet wird, während ein Client noch über einen Verweis auf ein Objekt verfügt. Beispielsweise kann eine Ressource, von der der Server abhängt, möglicherweise nicht mehr verfügbar sein, sodass auf dem Server ein Fehler auftritt. Der Benutzer kann auch ein Server Dokument schließen, das Objekte enthält, auf die andere Anwendungen verweisen.

Informationen zum Windows SDK finden Sie unter `IUnknown::AddRef` und `IUnknown::Release` .

## <a name="see-also"></a>Siehe auch

[Automatisierungsserver](automation-servers.md)<br/>
[AfxOleCanExitApp](reference/application-control.md#afxolecanexitapp)
