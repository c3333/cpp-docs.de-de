---
title: Definieren von C-Inlinefunktionen mit dllexport und dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
ms.openlocfilehash: 963e8f998e606a1b7011d58f93c927f36a263fb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226437"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definieren von C-Inlinefunktionen mit dllexport und dllimport

**Microsoft-spezifisch**

Sie können eine Funktion mit dem `dllexport`-Attribut als inline definieren. In diesem Fall wird die Funktion immer instanziiert und exportiert, unabhängig davon, ob ein beliebiges Modul im Programm auf die Funktion verweist oder nicht. Die Funktion wurde vermutlich von einem anderen Programm importiert.

Sie können auch eine Funktion als inline definieren, die mit dem **`dllimport`** -Attribut deklariert wurde. In diesem Fall kann die Funktion (gemäß der Compileroption-Spezifikation "/Ob (inline)") erweitert, aber niemals instanziiert werden. Insbesondere bei Verwendung der Adresse der inline-importierten Funktion wird die Adresse der Funktion in der DLL zurückgegeben. Dieses Verhalten stimmt mit der Übernahme der Adresse einer nicht-inline importierten Funktion überein.

Statische lokale Daten und Zeichenfolgen in Inlinefunktionen behalten die gleichen Identitäten zwischen der DLL und dem Client wie in einem einzelnen Programm (d. h. eine ausführbare Datei ohne DLL-Schnittstelle) bei.

Lassen Sie beim Bereitstellen von importierten Inlinefunktionen Sorgfalt walten. Gehen Sie beispielsweise beim Aktualisieren der DLL nicht davon aus, dass der Client die geänderte Version der DLL verwendet. Um sicherzustellen, dass Sie die richtige Version der DLL laden, erstellen Sie auch den DLL-Client neu.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Import- und Exportfunktionen einer DLL](../c-language/dll-import-and-export-functions.md)
