---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: ebdbba130106ea5f9b893a9fd1d8277fd2dabdd4
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404690"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft-spezifisch**

Weist den Compiler an, keine Pufferüberlauf-Sicherheitsüberprüfungen für eine Funktion einzufügen.

## <a name="syntax"></a>Syntax

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Bemerkungen

Die **/GS** -Compileroption bewirkt, dass der Compiler auf Pufferüberläufe testet, indem Sicherheitsüberprüfungen für den Stapel eingefügt werden. Die Typen der Datenstrukturen, die für Sicherheitsüberprüfungen geeignet sind, werden in [/GS (Puffer-Sicherheitsüberprüfung)](../build/reference/gs-buffer-security-check.md)beschrieben. Weitere Informationen zur Pufferüberlauf Erkennung finden Sie unter [Security Features in MSVC](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/).

Ein fachmännischer manueller Code Review oder eine fachmännische manuelle externe Analyse kann bestimmen, dass eine Funktion vor einem Pufferüberlauf sicher ist. In diesem Fall können Sie die Sicherheitsüberprüfungen für eine Funktion unterdrücken, indem Sie das __declspec-Schlüsselwort **(safebuffers)** auf die Funktionsdeklaration anwenden.

> [!CAUTION]
> Puffer-Sicherheitsüberprüfungen bieten wichtige Sicherheit und haben eine geringfügige Auswirkung auf die Leistung. Daher empfiehlt es sich, sie nicht zu unterdrücken, außer in dem seltenen Fall, in dem die Leistung einer Funktion ein wichtiger Aspekt ist und die Funktion bekanntermaßen sicher ist.

## <a name="inline-functions"></a>Inlinefunktionen

Eine *primäre Funktion* kann ein [Inlining](inline-functions-cpp.md) -Schlüsselwort verwenden, um eine Kopie einer *sekundären Funktion*einzufügen. Wenn das __declspec-Schlüsselwort **(safebuffers)** auf eine Funktion angewendet wird, wird die Pufferüberlauf Erkennung für diese Funktion unterdrückt. Inlining wirkt sich allerdings auf das __declspec-Schlüsselwort **(safebuffers)** auf folgende Weise aus.

Angenommen, die **/GS** -Compileroption wird für beide Funktionen angegeben, aber die primäre Funktion gibt das __declspec Schlüsselwort **(safebuffers)** an. Die Datenstrukturen in der sekundären Funktion machen sie besonders geeignet für Sicherheitsüberprüfungen, und die Funktion unterdrückt diese Überprüfungen nicht. In diesem Fall:

- Geben Sie das [__forceinline](inline-functions-cpp.md) -Schlüsselwort in der sekundären Funktion an, um zu erzwingen, dass der Compiler die Funktion unabhängig von Compileroptimierungen Inline Inline

- Da die sekundäre Funktion für Sicherheitsüberprüfungen geeignet ist, werden Sicherheitsüberprüfungen auch auf die primäre Funktion angewendet, auch wenn Sie das __declspec Schlüsselwort **(safebuffers)** angibt.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das __declspec Schlüsselwort **(safebuffers)** verwendet wird.

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

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
