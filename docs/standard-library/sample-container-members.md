---
title: Sample Container-Member
ms.date: 11/04/2016
helpviewer_keywords:
- container classes
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
ms.openlocfilehash: ea30810177d936248f836e7e4462739d8b5f393a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846263"
---
# <a name="sample-container-members"></a>Sample Container-Member

> [!NOTE]
> Dieses Thema befindet sich in der Microsoft C++-Dokumentation als nicht funktionales Beispiel für Container, die in der C++-Standard Bibliothek verwendet werden. Weitere Informationen finden Sie unter [C++-Standardbibliothekscontainer](../standard-library/stl-containers.md).

## <a name="reference"></a>Referenz

## <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[const_iterator](../standard-library/container-class-const-iterator.md)|Beschreibt ein Objekt, das als konstanter Iterator für die gesteuerte Sequenz fungieren kann.|
|[const_reference](../standard-library/container-class-const-reference.md)|Beschreibt ein Objekt, das als Konstantenverweis auf ein Element der gesteuerten Sequenz fungieren kann|
|[const_reverse_iterator](../standard-library/container-class-const-reverse-iterator.md)|Beschreibt ein Objekt, das als konstanter Reverse-Iterator für die gesteuerte Sequenz fungieren kann|
|[difference_type](../standard-library/container-class-difference-type.md)|Beschreibt ein Objekt, das die Differenz zwischen den Adressen von zwei beliebigen Elementen in der gesteuerten Sequenz darstellen kann|
|[Iterator](../standard-library/container-class-iterator.md)|Beschreibt ein Objekt, das als Iterator für die gesteuerte Sequenz fungieren kann.|
|[Referenz](../standard-library/container-class-reference.md)|Beschreibt ein Objekt, das als Verweis auf ein Element der gesteuerten Sequenz fungieren kann|
|[reverse_iterator](../standard-library/container-class-reverse-iterator.md)|Beschreibt ein Objekt, das als Reverse-Iterator für die gesteuerte Sequenz fungieren kann.|
|[size_type](../standard-library/container-class-size-type.md)|Beschreibt ein Objekt, das die Länge einer beliebigen gesteuerten Sequenz darstellen kann|
|[value_type](../standard-library/container-class-value-type.md)|Fungiert als Synonym für den Vorlagen Parameter `Ty` .|

## <a name="member-functions"></a>Elementfunktionen

|Name|Beschreibung|
|-|-|
|[beginnen](../standard-library/container-class-begin.md)|Gibt einen Iterator zurück, der auf das erste Element der Sequenz zeigt (bzw. unmittelbar hinter das Ende einer leeren Sequenz)|
|[Löschen](../standard-library/container-class-clear.md)|Ruft [erase](../standard-library/container-class-erase.md)([begin](../standard-library/container-class-begin.md), [end](../standard-library/container-class-end.md)) auf.|
|[empty](../standard-library/container-class-empty.md)|Gibt **`true`** für eine leere gesteuerte Sequenz zurück.|
|[end](../standard-library/container-class-end.md)|Gibt einen Iterator zurück, der direkt hinter das Ende der Sequenz verweist|
|[erase](../standard-library/container-class-erase.md)|Löscht ein Element|
|[max_size](../standard-library/container-class-max-size.md)|Gibt die Länge der längsten Sequenz zurück, die das Objekt in konstanter Zeit und unabhängig von der Länge der gesteuerten Sequenz steuern kann|
|[rbegin](../standard-library/container-class-rbegin.md)|Gibt einen Reverse-Iterator zurück, der auf die Position unmittelbar hinter dem Ende der gesteuerten Sequenz zeigt und den Anfang der umgekehrten Sequenz festlegt|
|[rend](../standard-library/container-class-rend.md)|Die Memberfunktion gibt einen Reverse-Iterator zurück, der auf das erste Element der Sequenz zeigt (bzw. unmittelbar hinter das Ende einer leeren Sequenz) und das Ende der umgekehrte Sequenz festlegt.|
|[size](../standard-library/container-class-size.md)|Gibt die Länge der gesteuerten Sequenz zurück, in konstanter Zeit und unabhängig von der Länge der gesteuerten Sequenz.|
|[swap](../standard-library/container-class-swap.md)
