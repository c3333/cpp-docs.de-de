---
title: /Zc:twoPhase- (Zweiphasennamenssuche deaktivieren)
description: 'Erläutert, wie/Zc: twophase die zweiphasige Namenssuche deaktiviert, wenn/permissive-angegeben wird.'
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: 3464759793a2dd243024a9f3f52263f76514033a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438638"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase- (Zweiphasennamenssuche deaktivieren)

Die **/Zc: twophase-** Option unter **/permissive-** weist den Compiler an, das ursprüngliche, nicht konforme Microsoft C++ -Compilerverhalten zum Analysieren und Instanziieren von Klassen Vorlagen und Funktions Vorlagen zu verwenden.

## <a name="syntax"></a>Syntax

> **/Zc: twophase-**

## <a name="remarks"></a>Bemerkungen

Visual Studio 2017 Version 15,3 und höher: unter [/permissive-](permissive-standards-conformance.md)verwendet der Compiler die zweiphasige Namenssuche für die Vorlagen Namensauflösung. Wenn Sie auch **/Zc: twophase**angeben, kehrt der Compiler auf seine vorherige, nicht konforme Klassen Vorlage und die Namensauflösung und das Ersetzungs Verhalten der Funktions Vorlage zurück. Wenn **/permissive-** nicht angegeben wird, ist das nicht konforme Verhalten der Standardwert.

Die Windows SDK-Header Dateien in Version 10.0.15063.0 (Creators Update oder RS2) und früher funktionieren nicht im Übereinstimmungs Modus. **/Zc: twophase:** ist erforderlich, um Code für diese SDK-Versionen zu kompilieren, wenn Sie **/permissive-** verwenden. Versionen der Windows SDK, die mit Version 10.0.15254.0 (Fall Creators Update oder RS3) beginnen, funktionieren ordnungsgemäß im Konformitäts Modus. Sie benötigen nicht die Option **/Zc: twophase-** .

Verwenden Sie **/Zc: twophase-** , wenn Ihr Code erfordert, dass das alte Verhalten ordnungsgemäß kompiliert wird. In Erwägung gezogen, den Code so zu aktualisieren, dass er dem Standard entspricht.

### <a name="compiler-behavior-under-zctwophase-"></a>Compilerverhalten unter/Zc: twophase-

Standardmäßig oder in Visual Studio 2017, Version 15,3 und höher, wenn Sie sowohl **/permissive-** als auch **/Zc: twophase**angeben, verwendet der Compiler dieses Verhalten:

- Sie analysiert nur die Vorlagen Deklaration, den Klassen Kopf und die Basisklassen Liste. Der Vorlagen Text wird als Tokenstream aufgezeichnet. Funktions Texte, Initialisierer, Standardargumente oder noaußer-Argumente werden nicht analysiert. Die Klassen Vorlage wird bei einem vorläufigen Typ Pseudo instanziiert, um zu überprüfen, ob die Deklarationen in der Klassen Vorlage korrekt sind. Beachten Sie diese Klassen Vorlage:

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   Die Vorlagen Deklaration, die `template <typename T>`, die Klasse Head `class Derived`und die `public Base<T>` der Basisklassen Liste werden analysiert, aber der Vorlagen Text wird als Tokenstream aufgezeichnet.

- Beim Analysieren einer Funktions Vorlage analysiert der Compiler nur die Funktions Signatur. Der Funktions Text wird nicht analysiert. Stattdessen wird er als Tokenstream aufgezeichnet.

Wenn der Vorlagen Text daher Syntax Fehler aufweist, die Vorlage jedoch nie instanziiert wird, werden die Fehler vom Compiler nicht diagnostiziert.

Ein weiterer Effekt dieses Verhaltens ist die Überladungs Auflösung. Ein nicht standardmäßiges Verhalten tritt auf, wenn der Tokenstream an der instanziierungssite erweitert wird. Symbole, die nicht in der Vorlagen Deklaration sichtbar waren, werden möglicherweise zum Zeitpunkt der Instanziierung sichtbar. Dies bedeutet, dass Sie an der Überladungs Auflösung teilnehmen können. Es kann sein, dass Vorlagen Verhalten auf der Grundlage von Code ändern, der in der Vorlagen Definition nicht sichtbar ist, im Gegensatz zum Standard.

Betrachten Sie z. B. diesen Code:

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

Hier ist die Ausgabe, wenn Sie den Standardmodus, den Konformitäts Modus und den Konformitäts Modus mit **/Zc: twophase-Compileroptionen** verwenden:

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

Bei der Kompilierung im Übereinstimmungs Modus unter **/permissive-** druckt dieses Programm "`Standard two-phase`", da die zweite Überladung von `func` nicht sichtbar ist, wenn der Compiler die Vorlage erreicht. Wenn Sie **/Zc: twophase-** hinzufügen, druckt das Programm "`Microsoft one-phase`". Die Ausgabe entspricht dem Wert, wenn Sie **/permissive-** nicht angeben.

*Abhängige Namen* sind Namen, die von einem Vorlagen Parameter abhängen. Diese Namen weisen das Suchverhalten auf, das unter **/Zc: twophase-** nicht anders ist. Im Übereinstimmungs Modus sind abhängige Namen nicht an der Stelle der Vorlagen Definition gebunden. Stattdessen sucht der Compiler diese, wenn die Vorlage instanziiert wird. Bei Funktionsaufrufen mit einem abhängigen Funktionsnamen wird der Name an Funktionen gebunden, die in der Vorlagen Definition an der Aufruf site sichtbar sind. Zusätzliche über Ladungen aus der Argument abhängigen Suche werden hinzugefügt, sowohl am Punkt der Vorlagen Definition als auch am Punkt der Vorlagen Instanziierung.

Die zweistufige Suche besteht aus zwei Teilen: der Suche nach nicht abhängigen Namen während der Vorlagen Definition und der Suche nach abhängigen Namen während der Instanziierung der Vorlage. Unter **/Zc: twophase-** führt der Compiler die Argument abhängige Suche nicht getrennt von der nicht qualifizierten Suche aus. Das heißt, es wird kein zweiphasenlookup durchzuführen, daher können sich die Ergebnisse der Überladungs Auflösung unterscheiden.

Hier ist ein weiteres Beispiel angegeben:

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

Bei der Kompilierung ohne **/permissive-** gibt dieser Code Folgendes aus:

```Output
func(int)
NS::func(NS::S)
```

Bei der Kompilierung mit **/permissive-** , aber ohne **/Zc: twophase-** , druckt dieser Code Folgendes:

```Output
func(long)
NS::func(NS::S)
```

Bei der Kompilierung mit " **/permissive-** " und " **/Zc: twophase**" gibt dieser Code Folgendes aus:

```Output
func(int)
NS::func(NS::S)
```

Im Übereinstimmungs Modus unter **/permissive-** wird der-Aufruf`tfunc(1729)` in die `void func(long)` Überladung aufgelöst. Es wird nicht in die `void func(int)` Überladung aufgelöst, wie unter **/Zc: twophase-** . Dies liegt daran, dass die nicht qualifizierte `func(int)` nach der Definition der Vorlage deklariert wird und nicht durch eine Argument abhängige Suche gefunden wird. `void func(S)` jedoch an einer Argument abhängigen Suche beteiligt ist, wird Sie dem Überladungs Satz für den Aufrufen `tfunc(s)`hinzugefügt, auch wenn Sie nach der Vorlagen Funktion deklariert wird.

### <a name="update-your-code-for-two-phase-conformance"></a>Aktualisieren des Codes für die zweistufige Konformität

Ältere Versionen des Compilers benötigen nicht die Schlüsselwörter `template` und `typename` überall C++ , wo der Standard Sie benötigt. Diese Schlüsselwörter werden an manchen Stellen benötigt, um zu unterscheiden, wie Compiler einen abhängigen Namen während der ersten Phase der Suche analysieren sollten. Beispiel:

`T::Foo<a || b>(c);`

Ein konformer Compiler analysiert `Foo` als Variable im Bereich der `T`. Dies bedeutet, dass dieser Code ein logischer or-Ausdruck mit `T::foo < a` als Linker Operand ist und `b > (c)` als rechter Operand. Wenn Sie `Foo` als Funktions Vorlage verwenden möchten, müssen Sie angeben, dass es sich um eine Vorlage handelt, indem Sie das `template`-Schlüsselwort hinzufügen:

`T::template Foo<a || b>(c);`

In Versionen von Visual Studio 2017 Version 15,3 und höher, wenn **/permissive-** und **/Zc: twophase-** angegeben sind, lässt der Compiler diesen Code ohne das `template`-Schlüsselwort zu. Er interpretiert den Code als einen aufrufsvorgang für eine Funktions Vorlage mit einem Argument `a || b`, da nur Vorlagen auf begrenzte Weise analysiert werden. Der obige Code wird in der ersten Phase überhaupt nicht analysiert. In der zweiten Phase ist ausreichend Kontext vorhanden, um zu erkennen, dass `T::Foo` eine Vorlage anstelle einer Variablen ist, sodass der Compiler die Verwendung des Schlüssel Worts nicht erzwingt.

Dieses Verhalten kann auch angezeigt werden, indem das Schlüsselwort `typename` vor Namen in Funktions Vorlagen Texten, Initialisierern, Standardargumenten und noaußer-Argumenten entfernt wird. Beispiel:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Wenn Sie das Schlüsselwort `typename` im Funktions Rumpf nicht verwenden, wird dieser Code unter **/permissive-/Zc: twophase-** , aber nicht allein unter **/permissive-** kompiliert. Das `typename`-Schlüsselwort ist erforderlich, um anzugeben, dass die `TYPE` abhängig ist. Da der Text nicht unter " **/Zc: twophase**" analysiert wird, ist das Schlüsselwort für den Compiler nicht erforderlich. Im **/permissive-** -Übereinstimmungs Modus generiert Code ohne das `typename`-Schlüsselwort Fehler. Wenn Sie Ihren Code in Visual Studio 2017, Version 15,3 und höher, in Konformität migrieren möchten, fügen Sie das `typename`-Schlüsselwort ein, wo es fehlt.

Beachten Sie auch dieses Codebeispiel:

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

Unter **/permissive-/Zc: twophase** und in älteren Compilern benötigt der Compiler nur das `template`-Schlüsselwort in Zeile 2. Im Übereinstimmungs Modus benötigt der Compiler jetzt auch das `template`-Schlüsselwort in Zeile 4, um anzugeben, dass `T::X<T>` eine Vorlage ist. Suchen Sie nach Code, dem dieses Schlüsselwort fehlt, und stellen Sie es bereit, damit der Code dem Standard entspricht.

Weitere Informationen zu Konformitäts Problemen finden [Nonstandard Behavior](../../cpp/nonstandard-behavior.md) [ C++ Sie unter Verbesserungen der Konformität in Visual Studio](../../overview/cpp-conformance-improvements.md) und nicht dem Standard entsprechende Verhalten.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf der Eigenschaftenseite auf **Konfigurationseigenschaften** > **C/C++**  > **Befehlszeile**.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** so, dass Sie **/Zc: twophase** einschließt, und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[/Zc (Übereinstimmung)](zc-conformance.md)
