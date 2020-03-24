---
title: Compilerfehler C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206660"
---
# <a name="compiler-error-c2220"></a>Compilerfehler C2220

Warnung als Fehler behandelt - keine Objektdatei generiert

[/WX](../../build/reference/compiler-option-warning-level.md) weist den Compiler an, alle Warnungen als Fehler zu behandeln. Da ein Fehler aufgetreten ist, wurde kein Objekt und keine ausführbare Datei generiert.

Dieser Fehler wird nur angezeigt, wenn das **/WX** -Flag festgelegt ist und während der Kompilierung eine Warnung auftritt. Um diesen Fehler zu beheben, müssen Sie jede Warnung im Projekt ausschließen.

### <a name="to-fix-use-one-of-the-following-techniques"></a>So beheben Sie den Fehler mit einer der folgenden Methoden

- Korrigieren Sie die Probleme, die Warnungen im Projekt verursachen.

- Kompilieren Sie auf einer niedrigeren Warnstufe – verwenden Sie z. b. **/w3** anstelle von **/W4**.

- Verwenden Sie ein [Warning](../../preprocessor/warning.md) -Pragma, um eine bestimmte Warnung zu deaktivieren oder zu unterdrücken.

- Verwenden Sie zum Kompilieren nicht **/WX** .
