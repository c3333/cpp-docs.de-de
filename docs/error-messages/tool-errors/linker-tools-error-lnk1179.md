---
title: Linkertoolfehler LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: a267019f1be08cc8dcffdff3b4ba0b73357cccd4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183956"
---
# <a name="linker-tools-error-lnk1179"></a>Linkertoolfehler LNK1179

Ungültige oder beschädigte Datei: doppelter COMDAT "Dateiname".

Ein Objekt Modul enthält mindestens zwei COMDATs mit demselben Namen.

Dieser Fehler kann durch die Verwendung von [/H](../../build/reference/h-restrict-length-of-external-names.md)verursacht werden, wodurch die Länge externer Namen und die [/Gy](../../build/reference/gy-enable-function-level-linking.md)-Funktion, die in COMDATs verpackt werden, eingeschränkt werden.

## <a name="example"></a>Beispiel

Im folgenden Code sind `function1` und `function2` in den ersten acht Zeichen identisch. Beim Kompilieren mit **/Gy** und **/h8** wird ein Link Fehler erzeugt.

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
