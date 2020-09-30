---
title: /kernel (Binärdatei für den Kernelmodus erstellen)
description: Die/Kernel-Option des Microsoft C/C++-Compilers erstellt und verknüpft Projekte für die Kernel Modus-Ausführung.
ms.date: 09/28/2020
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: 8a8c02a6f102a52afbc52c154ce215ede3f38f74
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509349"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Binärdatei für den Kernelmodus erstellen)

Erstellt eine Binärdatei, die im Windows-Kernel ausgeführt werden kann. Der Code im aktuellen Projekt wird kompiliert und mit einem vereinfachten Satz von C++-sprach Features verknüpft, die für Code spezifisch sind, der im Kernel Modus ausgeführt wird.

## <a name="syntax"></a>Syntax

> **`/kernel`**

## <a name="remarks"></a>Bemerkungen

Die Angabe der **`/kernel`** -Option weist den Compiler und den Linker an, zu bestimmen, welche sprach Features im Kernel Modus zulässig sind, und um sicherzustellen, dass Sie über ausreichende Ausdruckskraft verfügen, um eine Instabilität der Laufzeit zu vermeiden, die für den Kernel Modus C++ eindeutig ist Dies erfolgt durch das verbieten der Verwendung von C++-sprach Features, die im Kernel Modus gestört werden. Der Compiler erzeugt Warnungen für C++-sprach Features, die potenziell störend sind, aber nicht deaktiviert werden können.

Die- **`/kernel`** Option gilt für die Compiler-und linkerphasen eines Builds und wird auf Projektebene festgelegt. Übergeben Sie den **`/kernel`** Schalter, um dem Compiler mitzuteilen, dass die resultierende Binärdatei nach dem Verknüpfen in den Windows-Kernel geladen werden soll. Der Compiler wird das Spektrum der C++-Sprachfunktionen auf eine Teilmenge beschränken, die mit dem Kernel kompatibel ist.

In der folgenden Tabelle sind die Änderungen im Compilerverhalten aufgeführt, wenn **`/kernel`** angegeben wird.

| Verhaltenstyp | **`/kernel`** Verhalten |
|--|--|
| C++-Ausnahmebehandlung | Deaktiviert. Alle Instanzen der **`throw`** **`try`** Schlüsselwörter und geben einen Compilerfehler aus (außer der Ausnahme Spezifikation `throw()` ). **`/EH`** Mit Ausnahme von sind keine Optionen kompatibel **`/kernel`** **`/EH-`** . |
| RTTI | Deaktiviert. Alle Instanzen der **`dynamic_cast`** **`typeid`** Schlüsselwörter und geben einen Compilerfehler aus, sofern nicht **`dynamic_cast`** statisch verwendet wird. |
| `new` und `delete` | Sie müssen den or- `new()` Operator explizit definieren `delete()` . Der Compiler und die Laufzeit stellen keine Standard Definition bereit. |

Benutzerdefinierte Aufruf Konventionen, die [`/GS`](gs-buffer-security-check.md) Buildoption und alle Optimierungen sind zulässig, wenn Sie die **`/kernel`** Option verwenden. Inlining ist größtenteils nicht von betroffen **`/kernel`** , mit derselben Semantik, die vom Compiler berücksichtigt wird. Wenn Sie sicherstellen möchten, dass der **`__forceinline`** Inlining-Qualifizierer berücksichtigt wird, müssen Sie sicherstellen, dass die Warnung [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) aktiviert ist, damit Sie wissen, wenn eine bestimmte **`__forceinline`** Funktion nicht Inline ist.

Es gibt keine `#pragma` Entsprechung, um diese Option zu steuern.

Wenn der-Compiler an den **`/kernel`** -Schalter übermittelt wird, definiert er ein Präprozessormakro mit `_KERNEL_MODE` dem Namen und hat den Wert **1**. Sie können dieses Makro verwenden, um Code bedingt zu kompilieren, je nachdem, ob sich die Ausführungsumgebung im Benutzermodus oder Kernel Modus befindet. Der folgende Code gibt z. b. an, dass sich die `MyNonPagedClass` -Klasse in einem nicht ausführbaren Speichersegment befinden soll, wenn Sie für die kernelmodusausführung kompiliert wird.

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

Einige der folgenden Kombinationen der Zielarchitektur und die- **`/arch`** Option führen zu einem Fehler, wenn Sie mit verwendet werden **`/kernel`** :

- **`/arch:SSE`**, **`/arch:SSE2`** , **`/arch:AVX`** , **`/arch:AVX2`** und werden **`/arch:AVX512`** auf x86 nicht unterstützt. **`/arch:IA32`** Wird nur mit **`/kernel`** auf x86 unterstützt.

- **`/arch:AVX`**, **`/arch:AVX2`** und werden **`/arch:AVX512`** mit auf x64 nicht unterstützt **`/kernel`** .

Der Aufbau mit wird **`/kernel`** auch **`/kernel`** an den Linker weitergeleitet. So wirkt sich die Option auf das linkerverhalten aus:

- Inkrementelles Verknüpfen ist deaktiviert. Wenn Sie **`/incremental`** die Befehlszeile hinzufügen, gibt der Linker diesen schwerwiegenden Fehler aus:

   **Schwerwiegender Fehler LNK1295: "/incremental" ist nicht kompatibel mit der Spezifikation "/Kernel". Verknüpfung ohne "/incremental"**

- Der Linker prüft jede Objektdatei (oder ein beliebiges enthaltenes Archiv Element von statischen Bibliotheken), um festzustellen, ob es mit der Option kompiliert werden konnte, **`/kernel`** aber nicht. Wenn Instanzen dieses Kriterium erfüllen, wird der Linker weiterhin erfolgreich verknüpft, kann jedoch eine Warnung ausgeben, wie in der folgenden Tabelle dargestellt.

   | Get-Help | **`/kernel`** obj | Non- **`/kernel`** obj, MASM obj oder CVTRES obj | Mischung aus **`/kernel`** und nicht- **`/kernel`** obj |
   |--|--|--|--|
   | **`link /kernel`** | Ja | Ja | Ja mit Warnung LNK4257 |
   | **`link`** | Ja | Ja | Ja |

   **LNK4257-Verknüpfungs Objekt nicht mit/Kernel kompiliert; Image kann möglicherweise nicht ausgeführt werden**

Die **`/kernel`** -Option und die- **`/driver`** Option werden unabhängig voneinander ausgeführt. Sie haben keine Auswirkungen auf einander.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>So legen Sie die/Kernel-Compileroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Fügen Sie im Feld **zusätzliche Optionen** hinzu *`/kernel`* . Wählen Sie **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
