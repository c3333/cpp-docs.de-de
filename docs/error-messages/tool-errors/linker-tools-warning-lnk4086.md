---
title: Linkertoolwarnung LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: 6e012ceb5e20855353c69bbcde85fb78afad2011
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183422"
---
# <a name="linker-tools-warning-lnk4086"></a>Linkertoolwarnung LNK4086

EntryPoint ' function ' ist nicht __stdcall mit ' Number ' Bytes von Argumenten; Image kann möglicherweise nicht ausgeführt werden

Der Einstiegspunkt für eine DLL muss `__stdcall`werden. Kompilieren Sie entweder die Funktion mit der [/gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) -Option neu, oder geben Sie `__stdcall` oder WinAPI an, wenn Sie die Funktion definieren.
