---
title: ATL-Modulklassen
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317374"
---
# <a name="atl-module-classes"></a>ATL-Modulklassen

In diesem Thema werden die Modulklassen erläutert, die in ATL 7.0 neu waren.

## <a name="ccommodule-replacement-classes"></a>CComModule-Ersatzklassen

Frühere Versionen von `CComModule`ATL verwendet . In ATL 7.0 wird die `CComModule` Funktionalität durch mehrere Klassen ersetzt:

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) Enthält Informationen, die von den meisten Anwendungen benötigt werden, die ATL verwenden. Enthält die HINSTANCE des Moduls und die Ressourceninstanz.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) Enthält Informationen, die für die COM-Klassen in ATL erforderlich sind.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) Enthält Informationen, die für die Fensterklassen in ATL erforderlich sind.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) Enthält Unterstützung für das Debuggen von Schnittstellen.

- [CAtlModule](../atl/reference/catlmodule-class.md) Die `CAtlModule`folgenden -abgeleiteten Klassen werden so angepasst, dass sie Informationen enthalten, die in einem bestimmten Anwendungstyp erforderlich sind. Die meisten Member in diesen Klassen können überschrieben werden:

  - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) Wird in DLL-Anwendungen verwendet. Stellt Code für die Standardexporte bereit.

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) Wird in EXE-Anwendungen verwendet. Stellt Code bereit, der in einer EXE erforderlich ist.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Bietet Unterstützung zum Erstellen von Windows NT- und Windows 2000-Diensten.

`CComModule`ist weiterhin für die Abwärtskompatibilität verfügbar.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Gründe für das Verteilen der CComModule-Funktionalität

Die Funktionalität `CComModule` von wurde aus folgenden Gründen in mehrere neue Klassen verteilt:

- Machen Sie `CComModule` die Funktionalität granular.

   Die Unterstützung für COM-, Fenster-, Schnittstellendebugging- und anwendungsspezifische Features (DLL oder EXE) befindet sich jetzt in separaten Klassen.

- Deklarieren Sie automatisch die globale Instanz jedes dieser Module.

   Eine globale Instanz der erforderlichen Modulklassen ist mit dem Projekt verknüpft.

- Entfernen Sie die Notwendigkeit, Init- und Term-Methoden aufzurufen.

   Init- und Term-Methoden wurden in die Konstruktoren und Destruktoren für die Modulklassen verschoben. es besteht keine Notwendigkeit mehr, Init und Term anzurufen.

## <a name="see-also"></a>Siehe auch

[Konzepte](../atl/active-template-library-atl-concepts.md)<br/>
[Klassenübersicht](../atl/atl-class-overview.md)
