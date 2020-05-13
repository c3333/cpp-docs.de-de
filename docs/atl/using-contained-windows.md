---
title: Verwenden von enthaltenen Windows
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329308"
---
# <a name="using-contained-windows"></a>Verwenden von enthaltenen Windows

ATL implementiert enthaltene Fenster mit [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Ein enthaltenes Fenster stellt ein Fenster dar, das seine Nachrichten an ein Containerobjekt delegiert, anstatt sie in einer eigenen Klasse zu behandeln.

> [!NOTE]
> Sie müssen keine Klasse ableiten, `CContainedWindowT` um enthaltene Fenster zu verwenden.

Mit enthaltenen Fenstern können Sie entweder eine vorhandene Windows-Klasse oder eine vorhandene Windows-Klasse überklassen. Um ein Fenster zu erstellen, das eine vorhandene Windows-Klasse überklassen, `CContainedWindowT` geben Sie zunächst den vorhandenen Klassennamen im Konstruktor für das Objekt an. Rufen `CContainedWindowT::Create`Sie dann an. Um ein vorhandenes Fenster unterzuklassieren, müssen Sie keinen Windows-Klassennamen angeben (NULL an den Konstruktor übergeben). Rufen Sie `CContainedWindowT::SubclassWindow` einfach die Methode auf, wobei das Handle in das Unterklassefenster unterteilt ist.

In der Regel verwenden Sie enthaltene Fenster als Datenmember einer Containerklasse. Der Container muss kein Fenster sein. Sie muss jedoch von [CMessageMap](../atl/reference/cmessagemap-class.md)ableiten.

Ein enthaltenes Fenster kann alternative Nachrichtenzuordnungen verwenden, um seine Nachrichten zu verarbeiten. Wenn Sie über mehr als ein enthaltenes Fenster verfügen, sollten Sie mehrere alternative Nachrichtenzuordnungen deklarieren, die jeweils einem separaten geschlossenen Fenster entsprechen.

## <a name="example"></a>Beispiel

Im Folgenden finden Sie ein Beispiel für eine Containerklasse mit zwei enthaltenen Fenstern:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Weitere Informationen zu enthaltenen Fenstern finden Sie im [SUBEDIT-Beispiel.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)

## <a name="see-also"></a>Siehe auch

[Fensterklassen](../atl/atl-window-classes.md)
