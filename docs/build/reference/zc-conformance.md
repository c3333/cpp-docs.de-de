---
title: /Zc (Übereinstimmung)
description: Die/Zc-konformitätscompileroptionen aktivieren bzw. deaktivieren die Unterstützung für kompatibles oder abwärts kompatibles Verhalten.
ms.date: 09/10/2020
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 13e06cd75f1ee684c2ee1ad6239aeb77b805675e
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041522"
---
# <a name="zc-conformance"></a>`/Zc` Konformitäts

Mit den **`/Zc`** Compileroptionen können Sie das Standard-oder Microsoft-spezifische Compilerverhalten angeben.

## <a name="syntax"></a>Syntax

> **`/Zc:`**_Option_{,_Option_}

## <a name="remarks"></a>Bemerkungen

Wenn Visual Studio eine Erweiterung von C oder C++ implementiert hat, die nicht mit dem Standard kompatibel ist, können Sie eine **`/Zc`** Übereinstimmungs Option verwenden, um ein standardkonformes oder Microsoft-spezifisches Verhalten anzugeben. Bei einigen Optionen ist das Microsoft-spezifische Verhalten der Standardwert, um umfangreiche wichtige Änderungen an vorhandenem Code zu verhindern. In anderen Fällen ist der Standardwert das Standardverhalten, bei dem die Verbesserungen hinsichtlich Sicherheit, Leistung und Kompatibilität die Kosten für wichtige Änderungen überwiegen. In neueren Versionen von Visual Studio kann sich die Standardeinstellung der einzelnen Konformitäts Optionen ändern. Weitere Informationen zu den einzelnen Konformitäts Optionen finden Sie im Thema für die jeweilige Option. Mit der- [`/permissive-`](permissive-standards-conformance.md) Compileroption werden implizit die Übereinstimmungs Optionen festgelegt, die nicht standardmäßig auf Ihre konforme Einstellung festgelegt sind.

Dies sind die **`/Zc`** Compileroptionen:

| Option | Verhalten |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | Aktivieren Sie die mehrstufige dynamische Zuordnung von c++ 17 (standardmäßig in c++ 17). |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | Erzwingen Sie die neue C++-Standard Bedeutung für **`auto`** (standardmäßig aktiviert). |
| [`/Zc__cplusplus`](zc-cplusplus.md) | Ermöglicht dem `__cplusplus` Makro, den unterstützten Standard zu melden (standardmäßig deaktiviert). |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | Aktivieren Sie die externe Verknüpfung für **`constexpr`** Variablen (standardmäßig deaktiviert). |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | Standardmäßige C++-Bereichs **`for`** Regeln erzwingen (standardmäßig aktiviert). |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | Aktivieren Sie implizit **`noexcept`** für erforderliche Funktionen (standardmäßig aktiviert). |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | Entfernen Sie die Funktion oder die Daten, auf die nicht verwiesen wird, wenn es sich um COMDAT handelt oder nur eine interne Verknüpfung aufweist |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | Erzwingen von c++ 17- **`noexcept`** Regeln (standardmäßig in c++ 17 oder höher). |
| [`/Zc:preprocessor`](zc-preprocessor.md) | Verwenden Sie den neuen konformen Präprozessor (standardmäßig deaktiviert, außer in C11/C17). |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | Ein temporärer UDT wird nicht an einen nicht konstanten Lvalue-Verweis gebunden (standardmäßig deaktiviert). |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | Standard mäßige C++ explizite Typkonvertierungs Regeln erzwingen (standardmäßig deaktiviert). |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | Ermöglicht die Aufhebung der Zuordnung von c++ 14 globalen Größen (standardmäßig aktiviert). |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | String-Literale in `char*` or- `wchar_t*` Konvertierung deaktivieren (standardmäßig deaktiviert). |
| [`/Zc:ternary`](zc-ternary.md) | Erzwingen von bedingten Operator Regeln für Operanden Typen (standardmäßig deaktiviert). |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | Aktiviert die Thread sichere lokale statische Initialisierung (standardmäßig aktiviert). |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | Angenommen, **`operator new`** bei Fehler wird ausgelöst (standardmäßig deaktiviert). |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | Aktivieren von drei Diagrammen (veraltet, standardmäßig deaktiviert). |
| [`/Zc:twoPhase`](zc-twophase.md) | Verwenden Sie ein nicht konformes Vorlagen-Parametrisierungsverhalten (standardmäßig konform). |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** ist ein System eigener Typ, nicht TypeDef (standardmäßig aktiviert). |

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
