---
title: SIMD-Erweiterung
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366449"
---
# <a name="simd-extension"></a>SIMD-Erweiterung

Visual C++ unterstützt derzeit den OpenMP 2.0-Standard, Aber Visual Studio 2019 bietet jetzt auch SIMD-Funktionalität.

> [!NOTE]
> Um SIMD zu verwenden, kompilieren Sie mit dem Switch, der `-openmp:experimental` zusätzliche OpenMP-Funktionen aktiviert, die bei Verwendung des `-openmp` Switches nicht verfügbar sind.
>
> Der `-openmp:experimental` Schalter subsumiert, `-openmp`was bedeutet, dass alle OpenMP 2.0-Features in seiner Verwendung enthalten sind.

Weitere Informationen finden Sie unter [SIMD-Erweiterung auf C++ OpenMP in Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD in Visual C++

OpenMP SIMD, eingeführt im OpenMP 4.0-Standard, zielt auf vektorfreundliche Schleifen ab. Durch die `simd` Verwendung der Direktive vor einer Schleife kann der Compiler Vektorabhängigkeiten ignorieren, die Schleife so vektorfreundlich wie möglich gestalten und die Absicht der Benutzer respektieren, mehrere Schleifeniterationen gleichzeitig auszuführen.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ bietet ähnliche Nicht-OpenMP-Schleifen-Pragmas wie `#pragma vector` und `#pragma ivdep`, aber mit OpenMP SIMD kann der Compiler mehr tun, wie:

- Immer zulässig, um vorhandene Vektorabhängigkeiten zu ignorieren.
- `/fp:fast`ist innerhalb der Schleife aktiviert.
- Äußere Schleifen und Schleifen mit Funktionsaufrufen sind vektorfreundlich.
- Verschachtelte Schleifen können zu einer Schleife zusammengezwickt und vektorfreundlich gemacht werden.
- Hybridbeschleunigung `#pragma omp for simd` mit zur Ermöglichung grobkörniger Multithreading- und Feinkornvektoren.  

Bei vektorfreundlichen Schleifen bleibt der Compiler stumm, es sei denn, Sie verwenden einen Vektorunterstützungsprotokollschalter:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Bei nicht vektorfreundlichen Schleifen gibt der Compiler jeweils eine Meldung aus:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Klauseln

Die OpenMP SIMD-Direktive kann auch die folgenden Klauseln verwenden, um die Vektorunterstützung zu verbessern:

|Direktive|BESCHREIBUNG|
|---|---|
|`simdlen(length)`|Geben Sie die Anzahl der Vektorspuren an.|
|`safelen(length)`|Geben Sie den Vektorabhängigkeitsabstand an.|
|`linear(list[ : linear-step]`)|Die lineare Zuordnung von der Schleifeninduktionsvariablen zum Arrayabonnement.|
|`aligned(list[ : alignment])`|Die Ausrichtung der Daten.|
|`private(list)`|Geben Sie die Datenprivatisierung an.|
|`lastprivate(list)`|Geben Sie die Datenprivatisierung mit dem endgültigen Wert aus der letzten Iteration an.|
|`reduction(reduction-identifier:list)`|Geben Sie benutzerdefinierte Reduktionsvorgänge an.|
|`collapse(n)`|Coalescing Loop Nest.|

> [!NOTE]
> Nicht effektive SIMD-Klauseln werden vom Compiler mit einer Warnung analysiert und ignoriert.
>
> Die Verwendung des folgenden Codes gibt z. B. eine Warnung aus:
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>Beispiel
  
Die OpenMP SIMD-Direktive bietet Benutzern eine Möglichkeit, den Compiler zu diktieren, schleifen vektorfreundlich zu machen. Durch Kommentieren einer Schleife mit der OpenMP SIMD-Direktive beabsichtigen Benutzer, mehrere Schleifeniterationen gleichzeitig ausführen zu lassen.

Die folgende Schleife wird z. B. mit der OpenMP SIMD-Direktive mit Anmerkungen angezeigt. Es gibt keine perfekte Parallelität zwischen Schleifeniterationen, da es eine Rückwärtsabhängigkeit von a[i] zu a[i-1] gibt, aber aufgrund der SIMD-Direktive ist es dem Compiler weiterhin erlaubt, aufeinander folgende Iterationen der ersten Anweisung in eine Vektoranweisung zu packen und parallel auszuführen.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Daher ist die folgende transformierte Vektorform der Schleife **zulässig,** da der Compiler das sequenzielle Verhalten jeder ursprünglichen Schleifeniteration beibehält. Mit anderen `a[i]` Worten, wird `a[-1]` `b[i]` nach `a[i]` ausgeführt, ist `bar` nach und der Aufruf zu geschieht zuletzt.

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

Es ist **nicht legal,** den `*c` Speicherverweis aus der Schleife `a[i]` `b[i]`zu verschieben, wenn er alias mit oder sein kann. Es ist auch nicht legal, die Anweisungen in einer ursprünglichen Iteration neu anzuordnen, wenn die sequenzielle Abhängigkeit unterbrochen wird. Die folgende transformierte Schleife ist z. B. nicht legal:

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>Siehe auch

[/openmp (Aktivieren der OpenMP 2.0-Unterstützung)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
