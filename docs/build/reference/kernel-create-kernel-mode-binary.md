---
title: /kernel (Binary für den Kernelmodus erstellen)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: bcef52144e4da932e9e1b6acbcd5f2170c4c7f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211943"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Binary für den Kernelmodus erstellen)

Erstellt eine Binärdatei, die im Windows-Kernel ausgeführt werden kann.

## <a name="syntax"></a>Syntax

```
/kernel[-]
```

## <a name="arguments"></a>Argumente

**/Kernel**<br/>
Der Code im aktuellen Projekt wird mithilfe einer Reihe von C++-Sprachregeln kompiliert und verknüpft, die für Code spezifisch sind, der im Kernel Modus ausgeführt wird.

**/Kernel**<br/>
Der Code im aktuellen Projekt wird kompiliert und verknüpft, ohne dass die C++-Sprachregeln verwendet werden, die für Code spezifisch sind, der im Kernel Modus ausgeführt wird.

## <a name="remarks"></a>Bemerkungen

Es gibt keine `#pragma`-Entsprechung, zum Steuern dieser Option.

Das Angeben der **/Kernel** -Option weist den Compiler und den Linker an, zu bestimmen, welche sprach Features im Kernel Modus zulässig sind, und um sicherzustellen, dass Sie über ausreichende Ausdruckskraft verfügen, um eine Instabilität der Laufzeit zu vermeiden, die nur für den Kernel Modus C++ Dies wird erreicht, indem die Verwendung von C++-sprach Features, die im Kernel Modus gestört sind, und die Bereitstellung von Warnungen für C++-sprach Features, die potenziell störend sind, jedoch nicht deaktiviert werden können, untersagt werden

Die **/Kernel** -Option gilt sowohl für die Compiler-als auch die Linker-Phase eines Builds und wird auf Projektebene festgelegt. Übergeben Sie den Schalter **/Kernel** , um dem Compiler mitzuteilen, dass die resultierende Binärdatei nach dem Verknüpfen in den Windows-Kernel geladen werden soll. Der Compiler wird das Spektrum der C++-Sprachfunktionen auf eine Teilmenge beschränken, die mit dem Kernel kompatibel ist.

In der folgenden Tabelle sind die Änderungen im Compilerverhalten aufgeführt, wenn **/Kernel** angegeben wird.

|Verhaltenstyp|**/Kernel** Verhalten|
|-------------------|---------------------------|
|C++-Ausnahmebehandlung|Deaktiviert. Alle Instanzen der **`throw`** **`try`** Schlüsselwörter und geben einen Compilerfehler aus (außer der Ausnahme Spezifikation `throw()` ). Keine **/eh** -Optionen sind mit **/Kernel**kompatibel, außer **/eh-**.|
|RTTI|Deaktiviert. Alle Instanzen der **`dynamic_cast`** **`typeid`** Schlüsselwörter und geben einen Compilerfehler aus, sofern nicht **`dynamic_cast`** statisch verwendet wird.|
|`new` und `delete`|Sie müssen den or- `new()` Operator explizit definieren `delete()` ; weder der Compiler noch die Runtime stellt eine Standard Definition bereit.|

Benutzerdefinierte Aufruf Konventionen, die [/GS](gs-buffer-security-check.md) -Buildoption und alle Optimierungen sind zulässig, wenn Sie die **/Kernel** -Option verwenden. Inlining ist größtenteils nicht von **/Kernel**betroffen, mit derselben Semantik, die vom Compiler berücksichtigt wird. Wenn Sie sicherstellen möchten, dass der **`__forceinline`** Inlining-Qualifizierer berücksichtigt wird, müssen Sie sicherstellen, dass die Warnung [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) aktiviert ist, damit Sie wissen, wenn eine bestimmte **`__forceinline`** Funktion nicht Inline ist.

Wenn der Compiler den **/Kernel** -Schalter übermittelt, definiert er ein Präprozessormakro mit `_KERNEL_MODE` dem Namen und hat den Wert **1**. Sie können dies verwenden, um Code bedingt zu kompilieren, je nachdem, ob sich die Ausführungsumgebung im Benutzermodus oder Kernel Modus befindet. Der folgende Code gibt z. b. an, dass sich die-Klasse in einem nicht ausführbaren Speichersegment befinden soll, wenn Sie für die kernelmodusausführung kompiliert wird.

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

Einige der folgenden Kombinationen der Zielarchitektur und der **/arch** -Option führen zu einem Fehler, wenn Sie mit **/Kernel**verwendet werden:

- **/arch: {SSE&#124;SSE2&#124;AVX}** werden auf x86 nicht unterstützt. Nur **/arch: ia32** wird mit **/Kernel** auf x86 unterstützt.

- **/arch: AVX** wird bei **/Kernel** auf x64 nicht unterstützt.

Das Gebäude mit **/Kernel** übergibt auch **/Kernel** an den Linker. Dies wirkt sich auf das linkerverhalten aus:

- Inkrementelles Verknüpfen ist deaktiviert. Wenn Sie **/Incremental** der Befehlszeile hinzufügen, gibt der Linker diesen schwerwiegenden Fehler aus:

   **Link: Schwerwiegender Fehler LNK1295: "/incremental" ist nicht kompatibel mit der Spezifikation "/Kernel". Verknüpfung ohne "/incremental"**

- Der Linker überprüft die einzelnen Objektdateien (oder alle enthaltenen Archivierungs Elemente aus statischen Bibliotheken), um festzustellen, ob die Kompilierung mit der **/Kernel** -Option möglich wäre, was jedoch nicht der Fall war. Wenn Instanzen dieses Kriterium erfüllen, wird der Linker weiterhin erfolgreich verknüpft, kann jedoch eine Warnung ausgeben, wie in der folgenden Tabelle dargestellt.

   ||**/Kernel** obj|**/Kernel-** obj, MASM obj oder cvtresed|Mischung aus **/Kernel** und **/Kernel-** obj|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**Link/Kernel**|Ja|Ja|Ja mit Warnung LNK4257|
   |**Verknüpfen**|Ja|Ja|Ja|

   **LNK4257-Verknüpfungs Objekt nicht mit/Kernel kompiliert; Image kann möglicherweise nicht ausgeführt werden**

Die **/Kernel** -Option und die **/Driver** -Option werden unabhängig voneinander ausgeführt und keines der beiden Auswirkungen auf die andere.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>So legen Sie die/Kernel-Compileroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie den Ordner **C/C++** aus.

1. Wählen Sie die Eigenschaften Seite **Befehlszeile** aus.

1. Fügen Sie im Feld **zusätzliche Optionen** `/kernel` oder hinzu `/kernel-` .

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
