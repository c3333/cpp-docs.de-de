---
title: Compilerwarnung (Stufe 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186789"
---
# <a name="compiler-warning-level-1-c4420"></a>Compilerwarnung (Stufe 1) C4420

"Operator": Operator nicht verfügbar, verwendet stattdessen "Operator". die Lauf Zeit Überprüfung ist möglicherweise beeinträchtigt.

Diese Warnung wird generiert, wenn Sie die [/RTCv](../../build/reference/rtc-run-time-error-checks.md) -Überprüfung (Vector New/DELETE) verwenden und wenn kein Vektor Formular gefunden wird. In diesem Fall wird das nicht Vektor Formular verwendet.

Damit/RTCv ordnungsgemäß funktioniert, sollte der Compiler immer die Vektor Form [New](../../cpp/new-operator-cpp.md)/[Delete](../../cpp/delete-operator-cpp.md) abrufen, wenn die Vektor Syntax verwendet wurde.
