---
title: /Zc (Übereinstimmung)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 4422524deab2a749c96d5e967bc3223d0c9c9873
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438669"
---
# <a name="zc-conformance"></a>/Zc (Übereinstimmung)

Mit den **/Zc** -Compileroptionen können Sie das Standard-oder Microsoft-spezifische Compilerverhalten angeben.

## <a name="syntax"></a>Syntax

> **/Zc:** _Option_{,_Option_}

## <a name="remarks"></a>Bemerkungen

Wenn Visual Studio eine Erweiterung in C implementiert hat oder C++ nicht mit dem Standard kompatibel ist, können Sie eine `/Zc` Übereinstimmungs Option verwenden, um ein standardkonformes oder Microsoft-spezifisches Verhalten anzugeben. Bei einigen Optionen ist das Microsoft-spezifische Verhalten der Standardwert, um umfangreiche wichtige Änderungen an vorhandenem Code zu verhindern. In anderen Fällen ist der Standardwert das Standardverhalten, bei dem die Verbesserungen hinsichtlich Sicherheit, Leistung und Kompatibilität die Kosten für wichtige Änderungen überwiegen. In neueren Versionen von Visual Studio kann sich die Standardeinstellung der einzelnen Konformitäts Optionen ändern. Weitere Informationen zu den einzelnen Konformitäts Optionen finden Sie im Thema für die jeweilige Option. Mit der [/permissive-](permissive-standards-conformance.md) -Compileroption werden implizit die Übereinstimmungs Optionen festgelegt, die nicht standardmäßig auf Ihre konforme Einstellung festgelegt sind.

Dies sind die `/Zc`-Compileroptionen:

|Option|Verhalten|
|---|---|
|[alignednew\[-\]](zc-alignednew.md)|Aktivieren Sie die mehrstufige dynamische Zuordnung von c++ 17 (standardmäßig in c++ 17).|
|[-automatisch\[\]](zc-auto-deduce-variable-type.md)|Erzwingen Sie die neue C++ Standard Bedeutung für `auto` (standardmäßig aktiviert).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Aktivieren Sie das **__cplusplus** -Makro, um den unterstützten Standard zu melden (standardmäßig deaktiviert).|
|[externconstexpr\[-\]](zc-externconstexpr.md)|Aktivieren Sie externe Verknüpfungen für `constexpr` Variablen (standardmäßig deaktiviert).|
|[-der forScope-\[\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Standard C++ Regeln für die `for`-Bereichs Einschränkung erzwingen (standardmäßig aktiviert).|
|[implicitnoaußer\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Aktivieren Sie implizites `noexcept` für erforderliche Funktionen (standardmäßig aktiviert).|
|[Inline\[-\]](zc-inline-remove-unreferenced-comdat.md)|Entfernen Sie die Funktion oder die Daten, auf die nicht verwiesen wird, wenn es sich um COMDAT handelt oder nur eine interne Verknüpfung aufweist|
|[noexcepttypes\[-\]](zc-noexcepttypes.md)|Erzwingen Sie c++ 17 noaußer-Regeln (standardmäßig in c++ 17 oder höher).|
|[referencebinding-\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Ein temporärer UDT wird nicht an einen nicht konstanten Lvalue-Verweis gebunden (standardmäßig deaktiviert).|
|[rvaluecast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Standardmäßige C++ explizite Typkonvertierungs Regeln erzwingen (standardmäßig deaktiviert).|
|[sizedabzuordc-\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Ermöglicht die Aufhebung der Zuordnung von c++ 14 globalen Größen (standardmäßig aktiviert).|
|[strictstrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Deaktivieren Sie String-Literale zum `char*` oder `wchar_t*` Konvertierung (standardmäßig deaktiviert).|
|[TERNÄRE\[-\]](zc-ternary.md)|Erzwingen von bedingten Operator Regeln für Operanden Typen (standardmäßig deaktiviert).|
|[threadsafeingeit-\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Aktiviert die Thread sichere lokale statische Initialisierung (standardmäßig aktiviert).|
|[throwingnew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Angenommen, `operator new` bei einem Fehler auslöst (standardmäßig deaktiviert).|
|[gibt\[-aus \]](zc-trigraphs-trigraphs-substitution.md)|Aktivieren von drei Diagrammen (veraltet, standardmäßig deaktiviert).|
|[twoPhase](zc-twophase.md)|Verwenden Sie ein nicht konformes Vorlagen-Parametrisierungsverhalten (standardmäßig konform).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` ist ein nativer Typ, nicht TypeDef (standardmäßig aktiviert).|

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
