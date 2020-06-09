---
title: Muss ich von CObject neue Klassen ableiten?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 371ede0f0921182c066b4cb224e66b18eb6f1208
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616744"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Muss ich von CObject neue Klassen ableiten?

Nein, das ist nicht.

Leiten Sie eine Klasse von [CObject](reference/cobject-class.md) ab, wenn Sie die Funktionen benötigen, die Sie bereitstellt, z. b. Serialisierung oder dynamische Erstellung. Viele Daten Klassen müssen in Dateien serialisiert werden. Daher ist es häufig ratsam, Sie von abzuleiten `CObject` . Ein Beispiel für eine von abgeleitete Klasse `CObject` finden Sie im [Scribble](../overview/visual-cpp-samples.md)-Beispiel.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse: Häufig gestellte Fragen](cobject-class-frequently-asked-questions.md)
