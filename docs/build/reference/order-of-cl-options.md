---
title: Reihenfolge der CL-C++Optionen ()-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439198"
---
# <a name="order-of-cl-options"></a>Reihenfolge von CL-Optionen

Optionen können an beliebiger Stelle in der CL-Befehlszeile angezeigt werden, mit Ausnahme der/Link-Option, die zuletzt auftreten muss. Der Compiler beginnt mit den Optionen, die in der [CL-Umgebungsvariablen](cl-environment-variables.md) angegeben sind, und liest dann die Befehlszeile von links nach rechts – Verarbeitungs Befehls Dateien in der Reihenfolge, in der Sie erkannt werden. Jede Option gilt für alle Dateien in der Befehlszeile. Wenn CL widersprüchliche Optionen feststellt, wird die Option ganz rechts verwendet.

## <a name="see-also"></a>Weitere Informationen

[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
