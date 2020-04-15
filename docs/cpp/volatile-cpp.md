---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371900"
---
# <a name="volatile-c"></a>volatile (C++)

Ein Typqualifizierer, den Sie verwenden können, um zu deklarieren, dass ein Objekt im Programm von der Hardware geändert werden kann.

## <a name="syntax"></a>Syntax

```
volatile declarator ;
```

## <a name="remarks"></a>Bemerkungen

Sie können den Compilerschalter [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) verwenden, um zu ändern, wie der Compiler dieses Schlüsselwort interpretiert.

Visual Studio interpretiert das **volatile** Schlüsselwort je nach Zielarchitektur unterschiedlich. Wenn für ARM keine **/volatile-Compileroption** angegeben ist, führt der Compiler so aus, als ob **/volatile:iso** angegeben wäre. Bei anderen Architekturen als ARM führt der Compiler, wenn keine **/volatile-Compileroption** angegeben ist, so aus, als ob **/volatile:ms** angegeben wurde. Daher wird bei anderen Architekturen als ARM dringend empfohlen, **/volatile:iso**anzugeben und explizite Synchronisierungsprimitive und Systeminterne Compiler zu verwenden, wenn Sie mit Speicher zu tun haben, der über Threads hinweg freigegeben wird.

Sie können den **flüchtigen** Qualifizierer verwenden, um Zugriff auf Speicherspeicherorte zu gewähren, die von asynchronen Prozessen wie Interrupthandlern verwendet werden.

Wenn **volatile** für eine Variable verwendet wird, die auch das [Schlüsselwort __restrict](../cpp/extension-restrict.md) hat, hat **volatile** Vorrang.

Wenn ein **Strukturelement** als **flüchtig**markiert ist, wird **volatile** auf die gesamte Struktur weitergegeben. Wenn eine Struktur keine Länge hat, die mithilfe einer Anweisung auf die aktuelle Architektur kopiert werden kann, kann **volatile** in dieser Struktur vollständig verloren gehen.

Das **volatile** Schlüsselwort hat möglicherweise keine Auswirkungen auf ein Feld, wenn eine der folgenden Bedingungen zutrifft:

- Die Länge des flüchtigen Felds überschreitet die maximale Größe, die in der aktuellen Architektur mithilfe einer Anweisung kopiert werden kann.

- Die Länge der äußersten **Struktur**– oder wenn sie Mitglied einer möglicherweise geschachtelten **Struktur**ist – überschreitet die maximale Größe, die mithilfe einer Anweisung in die aktuelle Architektur kopiert werden kann.

Obwohl der Prozessor nicht wieder speicherfähige Speicherzugriffe anordnet, müssen nicht zwischenspeicherbare Variablen als **flüchtig** markiert werden, um sicherzustellen, dass der Compiler die Speicherzugriffe nicht neu anordnet.

Objekte, die als **flüchtig** deklariert werden, werden in bestimmten Optimierungen nicht verwendet, da sich ihre Werte jederzeit ändern können.  Das System liest bei jeder Anforderung den aktuellen Wert eines flüchtigen Objekts, selbst wenn eine vorherige Anweisung bereits den Wert des gleichen Objekts abgefragt hatte.  Außerdem wird der Wert des Objekts sofort durch Zuweisung geschrieben.

## <a name="iso-compliant"></a>ISO-Kompatibilität

Wenn Sie mit dem Schlüsselwort "C" volatile oder mit dem Verhalten von **volatilen** in früheren Versionen des Microsoft C++-Compilers (MSVC) vertraut sind, beachten Sie, dass das Schlüsselwort C++11 ISO Standard **volatile** anders ist und in MSVC unterstützt wird, wenn die Compileroption [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) angegeben wird. (In ARM ist es standardmäßig festgelegt). Das **volatile** Schlüsselwort im C++11 ISO-Standardcode darf nur für den Hardwarezugriff verwendet werden. verwenden Sie es nicht für die Interthread-Kommunikation. Verwenden Sie für die Kommunikation zwischen Threads Mechanismen wie [std::atomic\<T>](../standard-library/atomic.md) aus der [C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Ende ISO-Kompatibilität

**Microsoft Specific**

Wenn die Compileroption **/volatile:ms** verwendet wird – standardmäßig, wenn andere Architekturen als ARM ausgerichtet sind –, generiert der Compiler zusätzlichen Code, um die Reihenfolge zwischen Verweisen auf flüchtige Objekte beizubehalten und die Reihenfolge für Verweise auf andere globale Objekte beizubehalten. Dies gilt insbesondere für:

- Das Schreiben in ein flüchtiges Objekt (auch als flüchtiger Schreibvorgang bezeichnet) weist Release-Semantik auf. Das heißt, dass ein Verweis auf ein globales oder statisches Objekt, das vor einem Schreibvorgang in ein flüchtiges Objekt in der Anweisungsabfolge auftritt, vor diesem flüchtigen Schreibvorgang in der kompilierten Binärdatei auftritt.

- Das Lesen eines flüchtigen Objekts (auch als flüchtiger Lesevorgang bezeichnet) weist Acquire-Semantik auf. Das heißt, dass ein Verweis auf ein globales oder statisches Objekt, das nach dem Lesevorgang eines flüchtigen Arbeitsspeichers in der Anweisungsabfolge auftritt, nach dem flüchtigen Lesevorgang in der kompilierten Binärdatei auftritt.

Dadurch können flüchtige Objekte für Arbeitsspeichersperren und -freigaben in Multithreadanwendungen verwendet werden.

> [!NOTE]
> Wenn sie auf der erweiterten Garantie beruht, die bei verwendung der Compileroption **/volatile:ms** bereitgestellt wird, ist der Code nicht portierbar.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const und flüchtige Zeiger](../cpp/const-and-volatile-pointers.md)
