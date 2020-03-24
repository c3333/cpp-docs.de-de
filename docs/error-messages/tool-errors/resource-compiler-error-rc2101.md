---
title: 'Ressourcencompiler: Fehler RC2101'
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 3fb576758e447c54e4ddfe7ddb024a1fd35a65f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191651"
---
# <a name="resource-compiler-error-rc2101"></a>Ressourcencompiler: Fehler RC2101

Ungültige Direktive in der vorverarbeiteten RC-Datei.

Die Ressourcen Compiler-Datei enthält eine **#pragma** -Direktive.

Verwenden Sie die **#ifndef** -Präprozessordirektive mit der RC_INVOKED-Konstante, die der Ressourcen Compiler definiert, wenn er eine Includedatei verarbeitet. Platzieren Sie die **#pragma** -Direktive in einem Codeblock, der nicht verarbeitet wird, wenn die RC_INVOKED Konstante definiert ist. Der Code im Block wird nur vom C/C++ Compiler und nicht vom Ressourcen Compiler verarbeitet. Der folgende Beispielcode veranschaulicht diese Vorgehensweise:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

Die **#pragma** -Präprozessordirektive hat keine Bedeutung in. RC-Datei. Die **#include** -Präprozessordirektive wird häufig in einer verwendet. RC-Datei zum Einschließen einer Header Datei (entweder eine Projekt basierte benutzerdefinierte Header Datei oder eine Standard Header Datei, die von Microsoft mit einem seiner Produkte bereitgestellt wird). Einige dieser Include-Dateien enthalten die **#pragma** -Direktive. Da eine Header Datei eine oder mehrere andere Header Dateien enthalten kann, ist die Datei, die die angreifende **#pragma** Direktive enthält, möglicherweise nicht sofort offensichtlich.

Die **#ifndef** RC_INVOKED Technik kann das Einschließen von Header Dateien in projektbasierten Header Dateien steuern.
