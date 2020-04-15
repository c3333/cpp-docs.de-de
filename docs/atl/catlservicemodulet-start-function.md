---
title: CAtlServiceModuleT::Startfunktion
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317275"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::Startfunktion

Wenn der Dienst `_tWinMain` ausgeführt `CAtlServiceModuleT::WinMain`wird, ruft `CAtlServiceModuleT::Start`, die wiederum ruft .

`CAtlServiceModuleT::Start`richtet ein Array `SERVICE_TABLE_ENTRY` von Strukturen ein, die jeden Service seiner Startfunktion zuordnen. Dieses Array wird dann an die Win32-API-Funktion [StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)übergeben. Theoretisch könnte eine EXE mehrere Dienste verarbeiten, `SERVICE_TABLE_ENTRY` und das Array könnte mehrere Strukturen aufweisen. Derzeit unterstützt ein ATL-generierter Dienst jedoch nur einen Dienst pro EXE. Daher verfügt das Array über einen einzelnen `_ServiceMain` Eintrag, der den Dienstnamen und die Startfunktion enthält. `_ServiceMain`ist eine statische `CAtlServiceModuleT` Memberfunktion, die die nicht `ServiceMain`statische Memberfunktion aufruft.

> [!NOTE]
> Wenn `StartServiceCtrlDispatcher` keine Verbindung mit dem Dienststeuerungs-Manager (Service Control Manager, SCM) hergestellt wurde, bedeutet dies wahrscheinlich, dass das Programm nicht als Dienst ausgeführt wird. In diesem Fall ruft `CAtlServiceModuleT::Run` das Programm direkt auf, damit das Programm als lokaler Server ausgeführt werden kann. Weitere Informationen zum Ausführen des Programms als lokaler Server finden Sie unter [Debugging-Tipps](../atl/debugging-tips.md).

## <a name="see-also"></a>Siehe auch

[Dienste](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
