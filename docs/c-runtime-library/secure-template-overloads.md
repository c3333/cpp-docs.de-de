---
title: Sichere Vorlagenüberladungen
description: Eine Beschreibung der Microsoft C-Lauf Zeit Vorlagen Überladungen, die Funktionen mit erweiterter Sicherheit bereitstellen.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: 5e795d4d68aaeb176ba0809a08310def23662028
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589639"
---
# <a name="secure-template-overloads"></a>Sichere Vorlagenüberladungen

Microsoft hat viele veraltete CRT-Funktionen (C Runtime Library) durch Versionen mit verbesserter Sicherheit ersetzt. Beispielsweise ist `strcpy_s` der sicherere Ersatz für `strcpy`. Bei den veralteten Funktionen handelt es sich um gängige Quellen von Sicherheitsfehlern, da Sie keine Vorgänge verhindern, die Arbeitsspeicher überschreiben können. Standardmäßig generiert der Compiler bei Verwendung einer dieser Funktionen eine Veraltungswarnung. Die CRT bietet C++-Vorlagenüberladungen für diese Funktionen, um den Übergang zu sichereren Varianten zu vereinfachen.

Dieser Codeausschnitt generiert beispielsweise eine Warnung, da `strcpy` veraltet ist:

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

Die Veraltungswarnung ist dazu da, Ihnen mitzuteilen, dass der Code möglicherweise nicht sicher ist. Wenn Sie sich vergewissert haben, dass Ihr Code den Speicher nicht überschreiben kann, haben Sie mehrere Möglichkeiten. Sie können die Warnung auch ignorieren. Sie können das Symbol `_CRT_SECURE_NO_WARNINGS` vor den „include“-Anweisungen für die CRT-Header definieren, um die Warnung zu unterdrücken, oder den Code für das Verwenden von `strcpy_s` aktualisieren:

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Die Vorlagenüberladungen bieten weitere Optionen. Wenn Sie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` auf 1 festlegen, werden Vorlagenüberladungen von CRT-Standardfunktionen aktiviert, die automatisch die sichereren Varianten aufrufen. Wenn `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` auf 1 festgelegt ist, sind keine Änderungen am Code erforderlich. Im Hintergrund wird der Aufruf von `strcpy` in einen Aufruf von `strcpy_s` geändert, wobei das „size“-Argument automatisch angegeben wird.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Das Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` wirkt sich nicht auf die Funktionen aus, die eine Anzahl annehmen, z `strncpy` . b.. Um Vorlagenüberladungen für die „count“-Funktion zu aktivieren, legen Sie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` auf 1 fest. Doch zuvor müssen Sie sich vergewissern, dass Ihr Code die Anzahl von Zeichen und nicht die Größe des Puffers übergibt (ein häufiger Fehler). Darüber hinaus ist Code, der explizit einen NULL-Terminator am Ende des Puffers nach dem Funktionsaufruf schreibt, nicht erforderlich, wenn die sichere Variante aufgerufen wird. Wenn Sie ein Abschneideverhalten benötigen, siehe [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
> Das Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` erfordert, dass `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` auch auf 1 festgelegt wird. Wenn `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` auf 1 und `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` auf 0 festgelegt ist, führt die Anwendung keine Vorlagenüberladungen durch.

Durch Festlegen von `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` auf 1 werden Vorlagenüberladungen der sicheren Varianten (Namen, die auf „_s“ enden) ermöglicht. Wenn in diesem Fall `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` auf 1 festgelegt ist, muss eine kleine Änderung am ursprünglichen Code vorgenommen werden:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Nur der Name der Funktion muss geändert werden (durch Hinzufügen von „_s“). Die Vorlagenüberladung übernimmt das Angeben des „size“-Arguments.

In der Standardeinstellung sind `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` und `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` auf 0 (deaktiviert) festgelegt, und `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` ist auf 1 (aktiviert) festgelegt.

Diese Vorlagen Überladungen funktionieren nur für statische Arrays. Dynamisch zugewiesene Puffer erfordern zusätzliche Quellcodeänderungen. Siehe erneut die obigen Beispiele:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; change it to
                       // strcpy_s(szBuf, 10, "test");
```

Und dieses:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>Weitere Informationen

[Sicherheitsfunktionen in der CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)
