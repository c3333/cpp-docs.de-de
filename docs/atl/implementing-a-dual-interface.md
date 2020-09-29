---
title: Implementieren einer Dual-Schnittstelle (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: 97d8cd912c85a74f3550a9ca6c7b87a9717d4075
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499555"
---
# <a name="implementing-a-dual-interface"></a>Implementieren einer Dual-Schnittstelle

Sie können eine duale Schnittstelle mit der [IDispatchImpl](../atl/reference/idispatchimpl-class.md) -Klasse implementieren, die eine Standard Implementierung der `IDispatch` Methoden in einer Dual-Schnittstelle bereitstellt. Weitere Informationen finden Sie unter [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

So verwenden Sie diese Klasse:

- Definieren Sie die duale Schnittstelle in einer Typbibliothek.

- Leiten Sie die Klasse von einer Spezialisierung von ab `IDispatchImpl` (übergeben Sie Informationen über die Schnittstelle und die Typbibliothek als Vorlagen Argumente).

- Fügen Sie der com-Zuordnung einen Eintrag (oder Einträge) hinzu, um die duale Schnittstelle durch verfügbar zu machen `QueryInterface` .

- Implementieren Sie den vtable-Teil der-Schnittstelle in der-Klasse.

- Stellen Sie sicher, dass die Typbibliothek mit der Schnittstellen Definition für Ihre Objekte zur Laufzeit verfügbar ist.

## <a name="atl-simple-object-wizard"></a>ATL-Assistent für einfache Objekte

Wenn Sie eine neue Schnittstelle und eine neue Klasse erstellen möchten, um Sie zu implementieren, können Sie das [Dialogfeld ATL-Klasse hinzufügen](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box)und dann den [ATL-Assistenten für einfache Objekte](../atl/reference/atl-simple-object-wizard.md)verwenden.

## <a name="implement-interface-wizard"></a>Assistent zum Implementieren von Schnittstellen

Wenn Sie über eine vorhandene Schnittstelle verfügen, können Sie mit dem [Assistenten zum Implementieren von Schnitt](../atl/reference/adding-a-new-interface-in-an-atl-project.md) stellen die erforderliche Basisklasse, com-Zuordnungs Einträge und Skeleton-Methoden Implementierungen zu einer vorhandenen Klasse hinzufügen.

> [!NOTE]
> Möglicherweise müssen Sie die generierte Basisklasse so anpassen, dass die Haupt-und neben Versionsnummern der Typbibliothek als Vorlagen Argumente an Ihre Basisklasse übermittelt werden `IDispatchImpl` . Der Assistent zum Implementieren von Schnittstellen überprüft nicht die Versionsnummer der Typbibliothek.

## <a name="implementing-idispatch"></a>Implementieren von IDispatch

Sie können eine `IDispatchImpl` Basisklasse verwenden, um eine Implementierung einer dispinterface bereitzustellen, indem Sie einfach den entsprechenden Eintrag in der com-Zuordnung angeben (mit dem [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) -oder [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) -Makro), sofern Sie über eine Typbibliothek verfügen, die eine entsprechende duale Schnittstelle beschreibt. Es ist üblich, die- `IDispatch` Schnittstelle auf diese Weise zu implementieren, z. b.. Der ATL-Assistent für einfache Objekte und der Assistent zum Implementieren von Schnittstellen gehen davon aus, dass Sie auf `IDispatch` diese Weise implementieren möchten, sodass Sie den entsprechenden Eintrag zur Karte hinzufügen.

> [!NOTE]
> ATL bietet die [IDispEventImpl](../atl/reference/idispeventimpl-class.md) -und [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) -Klassen, die Ihnen bei der Implementierung von DISP helfen, ohne dass eine Typbibliothek mit der Definition einer kompatiblen Dual-Schnittstelle erforderlich ist.

## <a name="see-also"></a>Weitere Informationen

[Duale Schnittstellen und ATL](../atl/dual-interfaces-and-atl.md)
