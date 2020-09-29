---
title: nonextensible-Attribut
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: fda2a0d43144b6e9832e061e7198b3f3e65f8b86
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500105"
---
# <a name="nonextensible-attribute"></a>nonextensible-Attribut

Wenn eine duale Schnittstelle nicht zur Laufzeit erweitert wird (d. h. Sie stellen keine Methoden oder Eigenschaften über bereit, die `IDispatch::Invoke` über die Vtable nicht verfügbar sind), sollten Sie das **nicht erweiterbare** Attribut auf ihre Schnittstellen Definition anwenden. Dieses Attribut stellt Informationen für Client Sprachen (z. b. Visual Basic) bereit, die verwendet werden können, um die vollständige Code Überprüfung zur Kompilierzeit zu aktivieren. Wenn dieses Attribut nicht angegeben wird, können Fehler bis zur Laufzeit im Client Code verborgen bleiben.

Weitere Informationen über das **nonextensible** -Attribut und ein Beispiel finden Sie unter [nonextensible](../windows/attributes/nonextensible.md).

## <a name="see-also"></a>Weitere Informationen

[Duale Schnittstellen und ATL](../atl/dual-interfaces-and-atl.md)
