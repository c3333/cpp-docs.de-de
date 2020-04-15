---
title: Implementieren einer Dual Interface (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319466"
---
# <a name="implementing-a-dual-interface"></a>Implementieren einer dualen Schnittstelle

Sie können eine duale Schnittstelle mithilfe der [IDispatchImpl-Klasse](../atl/reference/idispatchimpl-class.md) implementieren, die eine Standardimplementierung der `IDispatch` Methoden in einer dualen Schnittstelle bereitstellt. Weitere Informationen finden Sie unter [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

So verwenden Sie diese Klasse:

- Definieren Sie Ihre duale Schnittstelle in einer Typbibliothek.

- Leiten Sie Ihre Klasse von `IDispatchImpl` einer Spezialisierung von ab (übergeben Sie Informationen über die Schnittstelle und die Typbibliothek als Vorlagenargumente).

- Fügen Sie der COM-Karte einen Eintrag (oder `QueryInterface`Einträge) hinzu, um die duale Schnittstelle über verfügbar zu machen.

- Implementieren Sie den vtable-Teil der Schnittstelle in Ihrer Klasse.

- Stellen Sie sicher, dass die Typbibliothek, die die Schnittstellendefinition enthält, für Ihre Objekte zur Laufzeit verfügbar ist.

## <a name="atl-simple-object-wizard"></a>ATL-Assistent für einfache Objekte

Wenn Sie eine neue Schnittstelle und eine neue Klasse zu ihrer Implementierung erstellen möchten, können Sie das [Dialogfeld ATL-Klasse hinzufügen](../ide/add-class-dialog-box.md)und dann den [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md)verwenden.

## <a name="implement-interface-wizard"></a>Assistent zum Implementieren von Schnittstellen

Wenn Sie über eine vorhandene Schnittstelle verfügen, können Sie den Assistenten zum Implementieren der [Schnittstelle](../atl/reference/adding-a-new-interface-in-an-atl-project.md) verwenden, um einer vorhandenen Klasse die erforderliche Basisklasse, COM-Zuordnungseinträge und Skelettmethodenimplementierungen hinzuzufügen.

> [!NOTE]
> Möglicherweise müssen Sie die generierte Basisklasse so anpassen, dass die Haupt- und `IDispatchImpl` Nebenversionsnummern der Typbibliothek als Vorlagenargumente an Ihre Basisklasse übergeben werden. Der Assistent zum Implementieren der Benutzeroberfläche überprüft nicht die Versionsnummer der Typbibliothek für Sie.

## <a name="implementing-idispatch"></a>Implementieren von IDispatch

Sie können `IDispatchImpl` eine Basisklasse verwenden, um eine Implementierung einer Dispinterface bereitzustellen, indem Sie nur den entsprechenden Eintrag in der COM-Zuordnung angeben (mit dem [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) oder [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) Makro), solange Sie über eine Typbibliothek verfügen, die eine entsprechende duale Schnittstelle beschreibt. Es ist durchaus üblich, die `IDispatch` Schnittstelle auf diese Weise zu implementieren, zum Beispiel. Der ATL Simple Object Wizard und der Implement `IDispatch` Interface Wizard gehen beide davon aus, dass Sie auf diese Weise implementieren möchten, sodass sie den entsprechenden Eintrag zur Karte hinzufügen.

> [!NOTE]
> ATL bietet die [Klassen IDispEventImpl](../atl/reference/idispeventimpl-class.md) und [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) an, die Ihnen bei der Implementierung von Dispinterfaces helfen, ohne dass eine Typbibliothek erforderlich ist, die die Definition einer kompatiblen dualen Schnittstelle enthält.

## <a name="see-also"></a>Siehe auch

[Dual E-Schnittstellen und ATL](../atl/dual-interfaces-and-atl.md)
