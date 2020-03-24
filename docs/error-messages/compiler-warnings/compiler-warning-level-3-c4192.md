---
title: Compilerwarnung (Stufe 3) C4192
ms.date: 11/04/2016
f1_keywords:
- C4192
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
ms.openlocfilehash: 38b346e0a90729bda431b9cb578a03806be1ea4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198977"
---
# <a name="compiler-warning-level-3-c4192"></a>Compilerwarnung (Stufe 3) C4192

"Name" wird beim Importieren der Typbibliothek "Library" automatisch ausgeschlossen

Eine `#import` Bibliothek enthält ein Element *namens*, das auch in den Win32-Systemheadern definiert ist. Aufgrund von Einschränkungen von Typbibliotheken werden Namen wie **IUnknown** oder GUID häufig in einer Typbibliothek definiert und duplizieren die Definition aus den Systemheadern. `#import` werden diese Elemente erkennen und die Einbindung in die TLH-und TLI-Header Dateien ablehnen.

Um dieses Verhalten zu überschreiben, verwenden Sie `#import` Attribute [no_auto_exclude](../../preprocessor/no-auto-exclude.md) und [include ()](../../preprocessor/include-parens.md).
