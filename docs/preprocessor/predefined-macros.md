---
title: Vordefinierte Makros
description: In diesem Artikel werden die vordefinierten Präprozessormakros des Microsoft C++-Compilers aufgelistet und beschrieben.
ms.custom: update_every_version
ms.date: 11/20/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- __AVX512BW__ macro
- __AVX512CD__ macro
- __AVX512DQ__ macro
- __AVX512F__ macro
- __AVX512VL__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
no-loc:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
ms.openlocfilehash: 6da1ecd178c0bbeed3b741fb611571203d79cb76
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444940"
---
# <a name="predefined-macros"></a>Vordefinierte Makros

Der Microsoft C-/C++-Compiler (MSVC) definiert vorab bestimmte Präprozessormakros abhängig von der Programmiersprache (C oder C++), vom Kompilierungsziel und von den ausgewählten Compileroptionen.

MSVC unterstützt die vordefinierten Präprozessormakros, die laut dem ANSI/ISO-Standard C99 und den ISO-Standards C++14 und C++17 erforderlich sind. Die Implementierung unterstützt auch mehrere weitere Microsoft-spezifische Präprozessormakros. Einige Makros werden nur für bestimmte Buildumgebungen oder Compileroptionen definiert. Sofern nicht angegeben, werden die Makros über eine Übersetzungseinheit definiert, als ob sie als **/D**-Compileroptionsargumente angegeben würden. Wenn sie definiert wurden, werden die Makros vor der Kompilierung auf die vom Präprozessor angegebenen Werte erweitert. Von den vordefinierten Makros werden keine Argumente akzeptiert, und sie können nicht neu definiert werden.

## <a name="standard-predefined-identifier"></a>Vordefinierter Standardbezeichner

Der Compiler unterstützt diesen vordefinierten Bezeichner, der von ISO C99 und ISO C++11 angegeben wird.

- `__func__` Dieser Wert gibt den nicht qualifizierten und undekorierten Namen der einschließenden Funktion als funktionslokales **static const**-Array von **char** zurück.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Vordefinierte Standardmakros

Der Compiler unterstützt diese vordefinierten Makros, die von den ISO-Standards C99 und C++17 angegeben werden.

- `__cplusplus` Dieser Wert wird als literale ganze Zahl definiert, wenn die Übersetzungseinheit als C++ kompiliert wird. Andernfalls wird er nicht definiert.

- `__DATE__` Bei diesem Wert handelt es sich um das Kompilierungsdatum der aktuellen Quelldatei. Das Datum ist ein Zeichenfolgenliteral im Format *Mmm dd yyyy*, das eine konstante Länge aufweist. Der Monatsname *Mmm* entspricht dem abgekürzten Monatsnamen, der von der [asctime](../c-runtime-library/reference/asctime-wasctime.md)-Funktion der C-Laufzeitbibliothek (CRT) generiert wurde. Das erste Zeichen des Datums *dd* ist ein Leerzeichen, wenn der Wert kleiner als 10 ist. Dieses Makro wird immer definiert.

- `__FILE__` Dieser Wert ist der Name der aktuellen Quelldatei. `__FILE__` wird zu einem Zeichenfolgenliteral erweitert. Verwenden Sie [/FC (Vollständiger Pfad der Quellcodedatei bei Diagnosen)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md), um sicherzustellen, dass der vollständige Dateipfad zur Datei angezeigt wird. Dieses Makro wird immer definiert.

- `__LINE__` Dieses Makro wird als Zeilennummer (ganze Zahl) in der aktuellen Quelldatei definiert. Der Wert des `__LINE__`-Makros kann mithilfe einer `#line`-Anweisung geändert werden. Dieses Makro wird immer definiert.

- `__STDC__` Dieser Wert wird nur als 1 definiert, wenn er als C kompiliert und die Compileroption [/Za](../build/reference/za-ze-disable-language-extensions.md) angegeben wird. Andernfalls wird er nicht definiert.

- `__STDC_HOSTED__` Dieser Wert wird als 1 definiert, wenn es sich bei der Implementierung um eine *gehostete Implementierung* handelt, die die gesamte erforderliche Standardbibliothek unterstützt. Andernfalls wird er als 0 definiert.

- `__STDCPP_THREADS__` Dieser Wert wird nur dann als 1 definiert, wenn ein Programm über mehr als einen Ausführungsthread verfügen kann und als C++ kompiliert wird. Andernfalls wird er nicht definiert.

- `__TIME__` Dieser Wert gibt die Zeit der Übersetzung der vorverarbeiteten Übersetzungseinheit an. Bei der Zeit handelt es sich um ein Zeichenfolgenliteral im Format *hh:mm:ss*, das der von der [asctime](../c-runtime-library/reference/asctime-wasctime.md)-Funktion der CRT zurückgegebenen Zeit entspricht. Dieses Makro wird immer definiert.

## <a name="microsoft-specific-predefined-macros"></a>Microsoft-spezifische vordefinierte Makros

MSVC unterstützt diese zusätzlichen vordefinierten Makros.

- `__ATOM__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX](../build/reference/arch-x86.md), [/arch:AVX2](../build/reference/arch-x86.md) oder [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX2__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX2](../build/reference/arch-x86.md) oder [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX512BW__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX512CD__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX512DQ__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX512F__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `__AVX512VL__` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:AVX512](../build/reference/arch-x86.md) festgelegt ist und das Compilerziel x86 oder x64 ist. Andernfalls wird er nicht definiert.

- `_CHAR_UNSIGNED` Dieser Wert wird als 1 definiert, wenn der Standard-**char**-Typ ohne Vorzeichen ist. Dieser Wert wird definiert, wenn die Compileroption [/J (Standard-char-Typ ist ohne Vorzeichen)](../build/reference/j-default-char-type-is-unsigned.md) festgelegt ist. Andernfalls wird er nicht definiert.

- `__CLR_VER` Dieser Wert wird als literale ganze Zahl definiert, die die Version der Common Language Runtime (CLR) darstellt, die zum Kompilieren der App verwendet wurde. Der Wert wird im Format `Mmmbbbbb` codiert, wobei `M` die Hauptversion der Runtime, `mm` die Nebenversion der Runtime und `bbbbb` die Buildnummer ist. `__CLR_VER` wird definiert, wenn die Compileroption [/clr](../build/reference/clr-common-language-runtime-compilation.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- `_CONTROL_FLOW_GUARD` Dieser Wert wird als 1 definiert, wenn die Compileroption [/guard:cf (Ablaufsteuerungsschutz aktivieren)](../build/reference/guard-enable-control-flow-guard.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `__COUNTER__` Dieser Wert wird zu einem Literal erweitert, das für eine ganze Zahl ab 0 steht. Der Wert wird jedes Mal, wenn er in einer Quelldatei oder in eingeschlossenen Headern der Quelldatei verwendet wird, um 1 erhöht. `__COUNTER__` speichert den Zustand beim Verwenden vorkompilierter Header. Dieses Makro wird immer definiert.

  In diesem Beispiel wird `__COUNTER__` verwendet, um eindeutige Bezeichner drei verschiedenen Objekten desselben Typs zuzuweisen. Der `exampleClass`-Konstruktor akzeptiert eine ganze Zahl als Parameter. In `main` deklariert die Anwendung drei Objekte des Typs `exampleClass`, wobei `__COUNTER__` als eindeutiger Bezeichnerparameter verwendet wird:

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- `__cplusplus_cli` Dieser Wert wird als literale ganze Zahl 200406 definiert, wenn er als C++ kompiliert und eine [/clr](../build/reference/clr-common-language-runtime-compilation.md)-Compileroption festgelegt ist. Andernfalls wird der Wert nicht definiert. Wenn der Wert `__cplusplus_cli` definiert wird, ist er in der gesamten Übersetzungseinheit aktiv.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- `__cplusplus_winrt` Dieser Wert wird als literale ganze Zahl 201009 definiert, wenn er als C++ kompiliert und die Compileroption [/ZW (Windows-Runtime-Kompilierung)](../build/reference/zw-windows-runtime-compilation.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_CPPRTTI` Dieser Wert wird als 1 definiert, wenn die Compileroption [/GR (Laufzeit-Typeninformationen aktivieren)](../build/reference/gr-enable-run-time-type-information.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_CPPUNWIND` Dieser Wert wird als 1 definiert, wenn mindestens eine der Compileroptionen [/GX (Ausnahmebehandlung aktivieren)](../build/reference/gx-enable-exception-handling.md), [/clr (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md) oder [/EH (Ausnahmebehandlungsmodell)](../build/reference/eh-exception-handling-model.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_DEBUG` Dieser Wert wird als 1 definiert, wenn die Compileroption [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/MDd](../build/reference/md-mt-ld-use-run-time-library.md), oder [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_DLL` Dieser Wert wird als 1 definiert, wenn die Compileroption [/MD](../build/reference/md-mt-ld-use-run-time-library.md) oder [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithread-DLL) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `__FUNCDNAME__` Dieser Wert wird als Zeichenfolgenliteral definiert, das den [dekorierten Namen](../build/reference/decorated-names.md) der einschließenden Funktion enthält. Das Makro wird nur innerhalb einer Funktion definiert. Das Makro `__FUNCDNAME__` wird nicht erweitert, wenn Sie die Compileroption [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) oder [/P](../build/reference/p-preprocess-to-a-file.md) verwenden.

   In diesem Beispiel werden die Makros `__FUNCDNAME__`, `__FUNCSIG__` und `__FUNCTION__` verwendet, um Funktionsinformationen anzuzeigen.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- `__FUNCSIG__` Dieser Wert wird als Zeichenfolgenliteral definiert, das die Signatur einer einschließenden Funktion enthält. Das Makro wird nur innerhalb einer Funktion definiert. Das Makro `__FUNCSIG__` wird nicht erweitert, wenn Sie die Compileroption [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) oder [/P](../build/reference/p-preprocess-to-a-file.md) verwenden. Bei der Kompilierung für ein 64-Bit-Ziel ist die Standardaufrufkonvention `__cdecl`. Ein Beispiel für die Verwendung finden Sie im `__FUNCDNAME__`-Makro.

- `__FUNCTION__` Dieser Wert wird als Zeichenfolgenliteral definiert, das den undekorierten Namen der einschließenden Funktion enthält. Das Makro wird nur innerhalb einer Funktion definiert. Das Makro `__FUNCTION__` wird nicht erweitert, wenn Sie die Compileroption [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) oder [/P](../build/reference/p-preprocess-to-a-file.md) verwenden. Ein Beispiel für die Verwendung finden Sie im `__FUNCDNAME__`-Makro.

- `_INTEGRAL_MAX_BITS` Dieser Wert wird als literale ganze Zahl 64 definiert, die maximale Größe (in Bit) eines integralen Typs, der kein Vektortyp ist. Dieses Makro wird immer definiert.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- `__INTELLISENSE__` Dieser Wert wird während einer IntelliSense-Compilerübergabe in der integrierten Entwicklungsumgebung von Visual Studio als 1 definiert. Andernfalls wird der Wert nicht definiert. Sie können dieses Makro verwenden, um den Code zu schützen, den der IntelliSense-Compiler nicht versteht. Außerdem können sie es dazu verwenden, zwischen dem Build- und dem IntelliSense-Compiler umzuschalten. Weitere Informationen finden Sie im Blogbeitrag zur [Problembehandlung bei Langsamkeit von IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- `_ISO_VOLATILE` Dieser Wert wird als 1 definiert, wenn die Compileroption [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_KERNEL_MODE` Dieser Wert wird als 1 definiert, wenn die Compileroption [/kernel (Binärdatei für den Kernelmodus erstellen)](../build/reference/kernel-create-kernel-mode-binary.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_AMD64` Dieser Wert wird für Kompilierungen, die x64-Prozessoren als Ziel verwenden, als literale ganze Zahl 100 definiert. Andernfalls wird der Wert nicht definiert.

- `_M_ARM` Dieser Wert wird für Kompilierungen, die ARM-Prozessoren als Ziel verwenden, als literale ganze Zahl 7 definiert. Andernfalls wird der Wert nicht definiert.

- `_M_ARM_ARMV7VE` Dieser Wert wird als 1 definiert, wenn die Compileroption [/arch:ARMv7VE](../build/reference/arch-arm.md) für Kompilierungen festgelegt ist, die ARM-Prozessoren als Ziel verwenden. Andernfalls wird der Wert nicht definiert.

- `_M_ARM_FP` Dieser Wert wird als literale ganze Zahl definiert, die angibt, welche [/arch](../build/reference/arch-arm.md)-Compileroption für ARM-Prozessorziele festgelegt wurde. Andernfalls wird der Wert nicht definiert.

  - Ein Wert im Bereich 30–39, wenn keine `/arch`-ARM-Option festgelegt wurde, die angibt, dass die Standardarchitektur für ARM festgelegt wurde (`VFPv3`)

  - Ein Wert im Bereich 40–49, wenn `/arch:VFPv4` festgelegt wurde

  - Weitere Informationen finden Sie unter [/arch (ARM)](../build/reference/arch-arm.md).

- `_M_ARM64` Dieser Wert wird für Kompilierungen mit 64-Bit-ARM-Prozessoren als Ziel als 1 definiert. Andernfalls wird der Wert nicht definiert.

- `_M_CEE` Dieser Wert wird als 001 definiert, wenn eine beliebige [/clr](../build/reference/clr-common-language-runtime-compilation.md)-Compileroption (Common Language Runtime-Kompilierung) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_CEE_PURE` Dieser Wert gilt ab Visual Studio 2015 als veraltet. Dieser Wert wird als 001 definiert, wenn die Compileroption [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_CEE_SAFE` Dieser Wert gilt ab Visual Studio 2015 als veraltet. Dieser Wert wird als 001 definiert, wenn die Compileroption [/clr:safe](../build/reference/clr-common-language-runtime-compilation.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_FP_EXCEPT` Dieser Wert wird als 1 definiert, wenn die Compileroption [/fp:except](../build/reference/fp-specify-floating-point-behavior.md) oder [/fp:strict](../build/reference/fp-specify-floating-point-behavior.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_FP_FAST` Dieser Wert wird als 1 definiert, wenn die Compileroption [/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_FP_PRECISE` Dieser Wert wird als 1 definiert, wenn die Compileroption [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_FP_STRICT` Dieser Wert wird als 1 definiert, wenn die Compileroption [/fp:strict](../build/reference/fp-specify-floating-point-behavior.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_M_IX86` Dieser Wert wird für Kompilierungen, die x86-Prozessoren als Ziel verwenden, als literale ganze Zahl 600 definiert. Dieses Makro ist nicht für x64- oder ARM-Kompilierungsziele definiert.

- `_M_IX86_FP` Dieser Wert wird als literale ganze Zahl definiert, die die festgelegte [/arch](../build/reference/arch-arm.md)-Compileroption oder die Standardoption angibt. Dieses Makro wird immer definiert, wenn es sich beim Kompilierungsziel um einen x86-Prozessor handelt. Andernfalls wird der Wert nicht definiert. Wenn er definiert wird, lautet der Wert:

  - 0, wenn die Compileroption `/arch:IA32` festgelegt wurde.

  - 1, wenn die Compileroption `/arch:SSE` festgelegt wurde.

  - 2, wenn die Compileroption `/arch:SSE2`, `/arch:AVX`, `/arch:AVX2` oder `/arch:AVX512` festgelegt wurde. Dieser Wert ist der Standardwert, wenn keine `/arch`-Compileroption angegeben wurde. Bei Angabe von `/arch:AVX` wird auch das Makro `__AVX__` definiert. Bei Angabe von `/arch:AVX2` werden `__AVX__` und `__AVX2__` ebenfalls definiert. Bei Angabe von `/arch:AVX512` werden `__AVX__`, `__AVX2__`, `__AVX512BW__`, `__AVX512CD__`, `__AVX512DQ__`, `__AVX512F__` und `__AVX512VL__` ebenfalls definiert.

  - Weitere Informationen finden Sie unter [/arch (x86)](../build/reference/arch-x86.md).

- `_M_X64` Dieser Wert wird für Kompilierungen, die x64-Prozessoren als Ziel verwenden, als literale ganze Zahl 100 definiert. Andernfalls wird der Wert nicht definiert.

- `_MANAGED` Dieser Wert wird als 1 definiert, wenn die Compileroption [/clr](../build/reference/clr-common-language-runtime-compilation.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_MSC_BUILD` Dieser Wert wird als literale ganze Zahl definiert, die das Revisionsnummernelement der Versionsnummer des Compilers enthält. Die Revisionsnummer ist das vierte Element der durch Punkte getrennten Versionsnummer. Wenn die Versionsnummer des Microsoft C-/C++-Compilers beispielsweise „15.00.20706.01“ lautet, ergibt die Auswertung des `_MSC_BUILD`-Makros 1. Dieses Makro wird immer definiert.

- `_MSC_EXTENSIONS` Dieser Wert wird als 1 definiert, wenn die standardmäßig aktivierte Compileroption [/Ze (Programmierspracherweiterungen aktivieren)](../build/reference/za-ze-disable-language-extensions.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_MSC_FULL_VER` Dieser Wert wird als literale ganze Zahl definiert, die die Nummernelemente der Haupt- und Nebenversion sowie der Buildnummer der Versionsnummer des Compilers codiert. Die Nummer der Hauptversion ist das erste Element der durch Punkte getrennten Versionsnummer. Die Nummer der Nebenversion ist das zweite Element und die Buildnummer das dritte Element. Wenn die Versionsnummer des Microsoft C-/C++-Compilers beispielsweise „15.00.20706.01“ lautet, ergibt die Auswertung des `_MSC_FULL_VER`-Makros 150020706. Geben Sie `cl /?` in die Befehlszeile ein, um die Versionsnummer des Compilers anzuzeigen. Dieses Makro wird immer definiert.

- `_MSC_VER` Dieser Wert wird als literale ganze Zahl definiert, die die Nummernelemente der Haupt- und der Nebenversion der Versionsnummer des Compilers codiert. Die Nummer der Hauptversion ist das erste Element der durch Punkte getrennten Versionsnummer und die Nummer der Nebenversion ist das zweite Element. Wenn die Versionsnummer des Microsoft C-/C++-Compilers beispielsweise „17.00.51106.1“ lautet, ergibt die Auswertung des `_MSC_VER`-Makros 1700. Geben Sie `cl /?` in die Befehlszeile ein, um die Versionsnummer des Compilers anzuzeigen. Dieses Makro wird immer definiert.

   |Visual Studio-Version|`_MSC_VER`|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1\.310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1\.900|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 Version 15.3|1911|
   |Visual Studio 2017 Version 15.5|1912|
   |Visual Studio 2017 Version 15.6|1913|
   |Visual Studio 2017-Version 15.7|1914|
   |Visual Studio 2017 Version 15.8|1915|
   |Visual Studio 2017 Version 15.9|1916|
   |Visual Studio 2019 RTW (16.0)|1920|
   |Visual Studio 2019 Version 16.1|1921|
   |Visual Studio 2019 Version 16.2|1922|
   |Visual Studio 2019, Version 16.3|1923|
   |Visual Studio 2019, Version 16.4|1924|
   |Visual Studio 2019 Version 16.5|1925|
   |Visual Studio 2019, Version 16.6|1926|

   Verwenden Sie den `>=`-Operator, um eine bestimmte oder eine höhere Version von Visual Studio auf Compilerreleases oder -updates zu überprüfen. Sie können ihn in einer bedingten Anweisung verwenden, um `_MSC_VER` mit dieser bekannten Version zu vergleichen. Wenn Sie über mehrere sich gegenseitig ausschließende Versionen verfügen, ordnen Sie Ihre Vergleiche in absteigender Reihenfolge nach der Versionsnummer an. Mit diesem Code wird beispielsweise auf Compiler überprüft, die in Visual Studio 2017 oder höher veröffentlicht wurden. Als Nächstes überprüft er auf Compiler, die in Visual Studio 2015 oder höher veröffentlicht wurden. Anschließend überprüft er auf alle Compiler, die in Visual Studio-Versionen vor Visual Studio 2015 veröffentlicht wurden:

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Weitere Informationen finden Sie im Artikel zur [Visual C++-Compilerversion](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) im Teamblog zu Microsoft C++.

- `_MSVC_LANG` Dieser Wert wird als literale ganze Zahl definiert, die den C++-Sprachstandard angibt, die der Compiler als Ziel verwendet. Dieser Wert wird nur in Code festgelegt, der als C++ kompiliert wird. Der Standardwert dieses Makros oder der Wert bei Angabe der Compileroption [/std:c++14](../build/reference/std-specify-language-standard-version.md) ist die literale ganze Zahl 201402L. Das Makro wird auf 201703L festgelegt, wenn die Compileroption [/std:c++17](../build/reference/std-specify-language-standard-version.md) angegeben wird. Wenn die Option [/std:c++latest](../build/reference/std-specify-language-standard-version.md) angegeben ist, wird der Wert auf einen höheren, unbestimmten Wert festgelegt. Andernfalls wird das Makro nicht definiert. Das Makro `_MSVC_LANG` und die [/std](../build/reference/std-specify-language-standard-version.md)-Compileroptionen (Standardversion für die Sprache festlegen) sind ab dem Update 3 von Visual Studio 2015 verfügbar.

- `__MSVC_RUNTIME_CHECKS` Dieser Wert wird als 1 definiert, wenn eine der [/RTC](../build/reference/rtc-run-time-error-checks.md)-Compileroptionen festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_MSVC_TRADITIONAL` Dieser Wert wird als 0 definiert, wenn die Compileroption [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) des Präprozessorkonformitätsmodus festgelegt ist. Dieser Wert wird standardmäßig oder bei festgelegter Compileroption [/experimental:preprocessor-](../build/reference/experimental-preprocessor.md) als 1 definiert, um anzugeben, dass der herkömmliche Präprozessor verwendet wird. Das Makro `_MSVC_TRADITIONAL` und die Compileroption [/experimental:preprocessor (Präprozessorkonformitätsmodus aktivieren)](../build/reference/experimental-preprocessor.md) sind ab Version 15.8 von Visual Studio 2017 verfügbar.

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- `_MT` Dieser Wert wird als 1 definiert, wenn [/MD oder /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithread-DLL) oder [/MT oder /MTd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithread) angegeben wird. Andernfalls wird der Wert nicht definiert.

- `_NATIVE_WCHAR_T_DEFINED` Dieser Wert wird als 1 definiert, wenn die Compileroption [/Zc:wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_OPENMP` Dieser Wert wird als literale ganze Zahl 200203 definiert, wenn die Compileroption [/openmp (OpenMP 2.0-Unterstützung aktivieren)](../build/reference/openmp-enable-openmp-2-0-support.md) festgelegt ist. Dieser Wert stellt das Datum der von MSVC implementierten OpenMP-Spezifikation dar. Andernfalls wird der Wert nicht definiert.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- `_PREFAST_` Dieser Wert wird als 1 definiert, wenn die Compileroption [/analyze](../build/reference/analyze-code-analysis.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `__TIMESTAMP__` Dieser Wert wird als ein Zeichenfolgenliteral definiert, das das Datum und die Uhrzeit der letzten Änderung der aktuellen Quelldatei enthält. Es weist das von der CRT-Funktion [asctime](../c-runtime-library/reference/asctime-wasctime.md) zurückgegebene abgekürzte Format mit konstanter Länge auf und sieht z. B. so aus: `Fri 19 Aug 13:32:58 2016`. Dieses Makro wird immer definiert.

- `_VC_NODEFAULTLIB` Dieser Wert wird als 1 definiert, wenn die Compileroption [/Zl (Kein Standardbibliotheksname)](../build/reference/zl-omit-default-library-name.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

- `_WCHAR_T_DEFINED` Dieser Wert wird als 1 definiert, wenn die Standardcompileroption [/Zc:wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) festgelegt ist. Das `_WCHAR_T_DEFINED`-Makro wird definiert, weist jedoch keinen Wert auf, wenn die Compileroption `/Zc:wchar_t-` festgelegt ist und **wchar_t** in einer Systemheaderdatei in Ihrem Projekt definiert ist. Andernfalls wird der Wert nicht definiert.

- `_WIN32` Dieser Wert wird als 1 definiert, wenn das Kompilierungsziel 32-Bit-ARM, 64-Bit-ARM, x86 oder x64 ist. Andernfalls wird der Wert nicht definiert.

- `_WIN64` Dieser Wert wird als 1 definiert, wenn das Kompilierungsziel 64-Bit-ARM oder x64 ist. Andernfalls wird der Wert nicht definiert.

- `_WINRT_DLL` Dieser Wert wird als 1 definiert, wenn er als C++ kompiliert wird und sowohl die Compileroption [/ZW (Windows-Runtime-Kompilierung)](../build/reference/zw-windows-runtime-compilation.md) als auch [/LD oder /LDd](../build/reference/md-mt-ld-use-run-time-library.md) festgelegt ist. Andernfalls wird der Wert nicht definiert.

Der Compiler definiert keine Präprozessormakros vor, die die ATL- oder MFC-Bibliotheksversion identifizieren. ATL- und MFC-Bibliotheksheader definieren diese Versionsmakros intern. Sie sind in Präprozessoranweisungen, die erstellt wurden, bevor der erforderliche Header eingeschlossen wurde, nicht definiert.

- `_ATL_VER` Dieser Wert wird in \<atldef.h> als literale ganze Zahl definiert, die die ATL-Versionsnummer codiert.

- `_MFC_VER` Dieser Wert wird in \<afxver_.h> als literale ganze Zahl definiert, die die MFC-Versionsnummer codiert.

## <a name="see-also"></a>Siehe auch

[Makros (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Präprozessoroperatoren](../preprocessor/preprocessor-operators.md)<br/>
[Präprozessoranweisungen](../preprocessor/preprocessor-directives.md)
