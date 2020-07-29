---
title: /sdl (Aktivieren zusätzlicher Sicherheitsüberprüfungen)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: d5a85f9648ebcc4064146f22cf5da020e06b7ba3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218974"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Aktivieren zusätzlicher Sicherheitsüberprüfungen)

Fügt empfohlene SDL-Prüfungen (Security Development Lifecycle) hinzu. Diese Prüfungen enthalten zusätzliche sicherheitsrelevante Warnungen als Fehler und zusätzliche sichere Codegenerierungsfunktionen.

## <a name="syntax"></a>Syntax

> **`/sdl`**[**`-`**]

## <a name="remarks"></a>Bemerkungen

**/SDL** aktiviert eine supermenge der grundlegenden Sicherheitsüberprüfungen, die von und über schreibungen bereitgestellt werden [`/GS`](gs-buffer-security-check.md) **`/GS-`** . Standardmäßig **`/sdl`** ist deaktiviert. **`/sdl-`** deaktiviert die zusätzlichen Sicherheitsüberprüfungen.

## <a name="compile-time-checks"></a>Überprüfungen zur Kompilierzeit

**`/sdl`** aktiviert diese Warnungen als Fehler:

|Durch /sdl aktivierte Warnung|Entsprechender Befehlszeilenschalter|BESCHREIBUNG|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Ein unärer Subtraktionsoperator wurde auf einen vorzeichenlosen Typ angewendet, was zu einem Ergebnis ohne Vorzeichen führte.|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Eine negative integrale Konstante wurde in einen vorzeichenlosen Typ konvertiert, was zu einem möglicherweise bedeutungslosen Ergebnis führte.|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Die Verwendung von- `continue` ,- `break` oder- `goto` Schlüsselwörtern in einem- `__finally` / `finally` Block weist ein nicht definiertes Verhalten auf|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Der Code, der eine Variable initialisiert, wird nicht ausgeführt.|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Verwendung einer nicht initialisierten lokalen Variablen.|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Verwendung einer möglicherweise nicht initialisierten lokalen Zeigervariablen.|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Pufferüberlauf, wenn bestimmte CRT-Funktionen (C Run-Time) verwendet werden.|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Verwendung einer Funktion, die mit dem Pragma gekennzeichnet ist [`deprecated`](../../preprocessor/deprecated-c-cpp.md) .|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Verwendung einer Funktion, die als gekennzeichnet ist [`deprecated`](../../cpp/deprecated-cpp.md) .|

## <a name="runtime-checks"></a>Laufzeitüberprüfungen

Wenn **`/sdl`** aktiviert ist, generiert der Compiler Code zum Ausführen dieser Überprüfungen zur Laufzeit:

- Aktiviert den Strict-Modus der **`/GS`** Lauf Zeitpuffer Überlauf Erkennung, was der Kompilierung mit entspricht `#pragma strict_gs_check(push, on)` .

- Führt eingeschränkte Zeigerbereinigung aus. In Ausdrücken, die keine Dereferenzierungen und Typen enthalten, die keinen benutzerdefinierten Dekonstruktor aufweisen, werden Zeiger Verweise nach einem-Rückruf auf eine nicht gültige Adresse festgelegt **`delete`** . Dies dient dazu, die Wiederverwendung von veralteten Zeigerverweisen zu verhindern.

- Führt eine Klassenmember-Zeiger Initialisierung aus. Initialisiert automatisch Klassenmember des Zeiger Typs auf die **`nullptr`** Objekt Instanziierung (vor dem Ausführen des Konstruktors). Dadurch wird verhindert, dass nicht initialisierte Zeiger verwendet werden, die vom Konstruktor nicht explizit initialisiert werden. Die vom Compiler generierte Member-Zeiger Initialisierung wird so lange wie folgt aufgerufen:

  - Das Objekt wird nicht mit einem benutzerdefinierten (Benutzer definiert) zugeordnet.`operator new`

  - Das Objekt wird nicht als Teil eines Arrays zugeordnet (z. b. `new A[x]` ).

  - Die Klasse wird nicht verwaltet oder importiert.

  - Die-Klasse verfügt über einen benutzerdefinierten Standardkonstruktor.

  Ein Member muss ein Zeiger und keine Eigenschaft oder Konstante sein, um von der vom Compiler generierten Initialisierungsfunktion initialisiert zu werden.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Warnungen,/SDL und verbessern der Erkennung nicht initialisierter Variablen](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie den Ordner **C/C++** aus.

1. Wählen Sie auf der Seite **Allgemein** die Option in der Dropdown Liste SDL-über **Prüfungen** aus.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)
