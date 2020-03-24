---
title: Compilerwarnung (Stufe 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: dc5feb3613e45134a08e493b397eb738fffee8a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174777"
---
# <a name="compiler-warning-level-1-c4910"></a>Compilerwarnung (Stufe 1) C4910

'\<Identifier > ': ' __declspec (dllexport) ' und ' Extern ' sind bei einer expliziten Instanziierung nicht kompatibel.

Die explizite Vorlagen Instanziierung mit dem Namen *\<Bezeichner>* wird durch die Schlüsselwörter `__declspec(dllexport)` und `extern` geändert. Die beiden Schlüsselwörter schließen sich jedoch gegenseitig aus. Das `__declspec(dllexport)` -Schlüsselwort soll die Instanziierung der Vorlagenklasse bewirken, während das `extern` -Schlüsselwort verhindern soll, dass die Vorlagenklasse automatisch instanziiert wird.

## <a name="see-also"></a>Weitere Informationen

[Explizite Instantiierung](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Allgemeine Regeln und Einschränkungen](../../cpp/general-rules-and-limitations.md)
