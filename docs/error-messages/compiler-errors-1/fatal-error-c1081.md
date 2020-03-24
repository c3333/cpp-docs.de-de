---
title: Schwerwiegender Fehler C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204190"
---
# <a name="fatal-error-c1081"></a>Schwerwiegender Fehler C1081

' Symbol ': der Dateiname ist zu lang.

Die Länge eines Datei Pfadnamens überschreitet `_MAX_PATH` (von "STDLIB. h" als 260 Zeichen definiert). Kürzen Sie den Namen der Datei.

Wenn Sie "CL. exe" mit einem kurzen Dateinamen abrufen, muss der Compiler möglicherweise einen vollständigen Pfadnamen generieren. Beispielsweise kann `cl -c myfile.cpp` bewirken, dass der Compiler Folgendes generiert:

```
D:\<very-long-directory-path>\myfile.cpp
```
