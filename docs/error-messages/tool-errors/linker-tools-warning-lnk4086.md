---
title: Linkertoolwarnung LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: f692f848825cd3d8e5e1fc042cb94d7cce8ea6bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195810"
---
# <a name="linker-tools-warning-lnk4086"></a>Linkertoolwarnung LNK4086

EntryPoint ' function ' ist nicht __stdcall mit ' Number ' Bytes von Argumenten; Image kann möglicherweise nicht ausgeführt werden

Der Einstiegspunkt für eine DLL muss lauten **`__stdcall`** . Kompilieren Sie entweder die Funktion mit der [/gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) -Option neu, oder geben **`__stdcall`** Sie oder WinAPI an, wenn Sie die Funktion definieren.
