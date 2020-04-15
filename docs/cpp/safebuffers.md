---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365585"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft Specific**

Weist den Compiler an, keine Pufferüberlauf-Sicherheitsüberprüfungen für eine Funktion einzufügen.

## <a name="syntax"></a>Syntax

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Bemerkungen

Die Compileroption **/GS** bewirkt, dass der Compiler pufferüberläufe testet, indem Sicherheitsüberprüfungen auf dem Stapel eingefügt werden. Die Typen von Datenstrukturen, die für Sicherheitsüberprüfungen in Frage kommen, werden in [/GS (Buffer Security Check)](../build/reference/gs-buffer-security-check.md)beschrieben. Weitere Informationen zur Erkennung von Pufferüberläufen finden Sie [unter Sicherheitsfeatures in MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Ein fachmännischer manueller Code Review oder eine fachmännische manuelle externe Analyse kann bestimmen, dass eine Funktion vor einem Pufferüberlauf sicher ist. In diesem Fall können Sie Sicherheitsüberprüfungen für eine Funktion unterdrücken, indem Sie das Schlüsselwort **__declspec(safebuffers)** auf die Funktionsdeklaration anwenden.

> [!CAUTION]
> Puffer-Sicherheitsüberprüfungen bieten wichtige Sicherheit und haben eine geringfügige Auswirkung auf die Leistung. Daher empfiehlt es sich, sie nicht zu unterdrücken, außer in dem seltenen Fall, in dem die Leistung einer Funktion ein wichtiger Aspekt ist und die Funktion bekanntermaßen sicher ist.

## <a name="inline-functions"></a>Inlinefunktionen

Eine *primäre Funktion* kann ein [Inlining-Schlüsselwort](inline-functions-cpp.md) verwenden, um eine Kopie einer *sekundären Funktion*einzufügen. Wenn das **Schlüsselwort __declspec(safebuffers)** auf eine Funktion angewendet wird, wird die Pufferüberlauferkennung für diese Funktion unterdrückt. Inlining wirkt sich jedoch auf folgende Weise auf das **Schlüsselwort __declspec(safebuffers)** aus.

Angenommen, die Compileroption **/GS** wird für beide Funktionen angegeben, aber die primäre Funktion gibt das **Schlüsselwort __declspec(safebuffers)** an. Die Datenstrukturen in der sekundären Funktion machen sie besonders geeignet für Sicherheitsüberprüfungen, und die Funktion unterdrückt diese Überprüfungen nicht. In diesem Fall:

- Geben Sie das [Schlüsselwort __forceinline](inline-functions-cpp.md) für die sekundäre Funktion an, um den Compiler zu zwingen, diese Funktion unabhängig von Compileroptimierungen inlinezulegen.

- Da die sekundäre Funktion für Sicherheitsüberprüfungen in Frage kommt, werden Sicherheitsüberprüfungen auch auf die primäre Funktion angewendet, obwohl sie das Schlüsselwort **__declspec(safebuffers)** angibt.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das **Schlüsselwort __declspec(safebuffers)** verwendet wird.

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
