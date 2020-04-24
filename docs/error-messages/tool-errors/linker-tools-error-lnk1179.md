---
title: Linkertoolfehler LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754346"
---
# <a name="linker-tools-error-lnk1179"></a>Linkertoolfehler LNK1179

Ungültige oder beschädigte Datei: Duplizieren comDAT 'Dateiname'

Ein Objektmodul enthält zwei oder mehr COMDATs mit demselben Namen.

Dieser Fehler kann durch die Verwendung von [/H](../../build/reference/h-restrict-length-of-external-names.md)verursacht werden, das die Länge externer Namen begrenzt, und [/Gy](../../build/reference/gy-enable-function-level-linking.md), das Inpackungen in COMDATs verpackt.

## <a name="example"></a>Beispiel

Im folgenden Code `function1` `function2` und sind in den ersten acht Zeichen identisch. Durch das Kompilieren mit **/Gy** und **/H8** wird ein Linkfehler ausgelöst.

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
