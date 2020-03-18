---
title: Muss ich von CObject neue Klassen ableiten?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446927"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Muss ich von CObject neue Klassen ableiten?

Nein, das ist nicht.

Leiten Sie eine Klasse von [CObject](../mfc/reference/cobject-class.md) ab, wenn Sie die Funktionen benötigen, die Sie bereitstellt, z. b. Serialisierung oder dynamische Erstellung. Viele Daten Klassen müssen in Dateien serialisiert werden. Daher ist es häufig ratsam, Sie aus `CObject`abzuleiten. Ein Beispiel für eine Klasse, die von `CObject`abgeleitet wurde, finden Sie im [Scribble](../overview/visual-cpp-samples.md)-Beispiel.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse: Häufig gestellte Fragen](../mfc/cobject-class-frequently-asked-questions.md)
