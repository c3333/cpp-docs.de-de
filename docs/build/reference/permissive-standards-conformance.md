---
title: /permissive- (Übereinstimmung mit Standards)
description: Referenzhandbuch für die Compileroption Microsoft C++ /permissive- (Standards conformance).
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337402"
---
# <a name="permissive--standards-conformance"></a>/permissive- (Übereinstimmung mit Standards)

Geben Sie dem Compiler den Standardkonformitätsmodus an. Verwenden Sie diese Option, um Konformitätsprobleme im Code zu identifizieren und zu beheben, um sie sowohl korrekter als auch tragbarer zu gestalten.

## <a name="syntax"></a>Syntax

> **/permissive-**

## <a name="remarks"></a>Bemerkungen

Diese Option wird in Visual Studio 2017 und höher unterstützt.

Sie können die Option **/permissive-** compiler verwenden, um das standardkonforme Compilerverhalten anzugeben. Diese Option deaktiviert freizügiges Verhalten und legt die [/Zc-Compileroptionen](zc-conformance.md) für die strikte Konformität fest. In der IDE wird durch diese Option auch der IntelliSense-Modul dazu verwendet, nicht konformen Code zu unterstreichen.

Standardmäßig wird die Option **/permissive-** in neuen Projekten festgelegt, die von Visual Studio 2017 Version 15.5 und höher erstellt wurden. In früheren Versionen ist es nicht standardmäßig festgelegt. Wenn die Option festgelegt ist, generiert der Compiler Diagnosefehler oder Warnungen, wenn nicht standardmäßige Sprachkonstrukte im Code erkannt werden, einschließlich einiger häufiger Fehler im Code vor C++11.

Die **Option /permissive-** ist mit fast allen Headerdateien der neuesten Windows Kits kompatibel, z. B. dem Software Development Kit (SDK) oder dem Windows Driver Kit (WDK), beginnend im Windows Fall Creators SDK (10.0.16299.0). Ältere Versionen des SDK können aus verschiedenen Gründen der Quellcodeübereinstimmung unter **/permissive nicht** kompiliert werden. Der Compiler und SDKs werden auf verschiedenen Release-Timelines ausgeliefert, daher gibt es noch einige Probleme. Informationen zu bestimmten Headerdateiproblemen finden Sie unter [Windows-Headerprobleme](#windows-header-issues) unten.

Die Option **/permissive-** legt die Optionen [/Zc:referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc:strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)und [/Zc:rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) auf konformes Verhalten fest. Diese Optionen sind standardmäßig nicht konformes Verhalten. Sie können bestimmte **/Zc-Optionen** nach **/permissive-** in der Befehlszeile übergeben, um dieses Verhalten zu überschreiben.

In Versionen des Compilers ab Visual Studio 2017 Version 15.3 legt die Option **/permissive-** die Option [/Zc:ternary](zc-ternary.md) fest. Der Compiler implementiert auch mehr Anforderungen für die zweiphasige Namenssuche. Wenn die Option **/permissive-** festgelegt ist, analysiert der Compiler Funktions- und Klassenvorlagendefinitionen und identifiziert abhängige und nicht abhängige Namen, die in den Vorlagen verwendet werden. In dieser Version wird nur eine Namensabhängigkeitsanalyse durchgeführt.

Umweltspezifische Erweiterungen und Sprachbereiche, die der Standard bis zur Implementierung überlässt, sind von **/permissive-** nicht betroffen. Beispielsweise werden die Microsoft-spezifische `__declspec`, Aufrufkonvention und strukturierte Ausnahmebehandlungsschlüsselwörter sowie Compilerspezifische Pragma-Direktiven oder Attribute vom Compiler nicht im **/permissive-Modus** gekennzeichnet.

Die Option **/permissive-** verwendet die Konformitätsunterstützung in der aktuellen Compilerversion, um zu bestimmen, welche Sprachkonstrukte nicht konform sind. Die Option bestimmt nicht, ob ihr Code einer bestimmten Version des C++-Standards entspricht. Um die gesamte implementierte Compilerunterstützung für den neuesten Entwurfsstandard zu aktivieren, verwenden Sie die Option [/std:latest.](std-specify-language-standard-version.md) Um die Compilerunterstützung auf den aktuell implementierten C++17-Standard zu beschränken, verwenden Sie die Option [/std:c++17.](std-specify-language-standard-version.md) Um die Compilerunterstützung auf eine engere Übereinstimmung mit dem C++14-Standard zu beschränken, verwenden Sie die Option [/std:c++14,](std-specify-language-standard-version.md) die die Standardeinstellung ist.

Nicht der gesamte C++11-, C++14- oder C++17-Standardcode wird vom MSVC-Compiler in allen Versionen von Visual Studio 2017 unterstützt. Abhängig von der Version von Visual Studio erkennt die Option **/permissive-** möglicherweise keine Probleme in Bezug auf einige Aspekte der zweiphasigen Namenssuche, indem ein nicht-const-Verweis auf einen temporären Verweis gebunden wird, das Kopieren init als direktes Init behandelt, mehrere benutzerdefinierte Konvertierungen in der Initialisierung oder alternative Token für logische Operatoren und andere nicht unterstützte Konformitätsbereiche ermöglicht. Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md). Um das Beste aus **/permissive-** herausholen, aktualisieren Sie Visual Studio auf die neueste Version.

### <a name="how-to-fix-your-code"></a>So beheben Sie Ihren Code

Hier sind einige Beispiele für Code, der als nicht konform erkannt wird, wenn Sie **/permissive-** verwenden, zusammen mit vorgeschlagenen Möglichkeiten, die Probleme zu beheben.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Verwenden der Standardeinstellung als Bezeichner im systemeigenen Code

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Nachschlagen von Mitgliedern in abhängiger Basis

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>Verwendung qualifizierter Namen in Mitgliedserklärungen

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Initialisieren mehrerer Gewerkschaftsmitglieder in einem Memberinitialisierer

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>Regeln für die Suche nach namen verborgenen Freunden

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Verwenden von bereichsgebundenen Enumerungen in Arraygrenzen

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Verwendung für jeden in systemeigenem Code

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>Verwendung von ATL-Attributen

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>Mehrdeutige bedingte Operatorargumente

In Versionen des Compilers vor Visual Studio 2017 Version 15.3 akzeptierte der `?:` Compiler Argumente an den bedingten Operator (oder ternären Operator), die vom Standard als mehrdeutig betrachtet werden. Im **/permissive-Modus** gibt der Compiler jetzt eine oder mehrere Diagnosen aus, wenn in früheren Versionen ohne Diagnose kompiliert wurde.

Häufige Fehler, die sich aus dieser Änderung ergeben können, sind:

- Fehler C2593: 'Operator ?' ist mehrdeutig

- Fehler C2679: binär '?': Es wurde kein Operator gefunden, der einen rechten Operanden vom Typ 'B' annimmt (oder es gibt keine akzeptable Konvertierung)

- Fehler C2678: binär '?': kein Operator gefunden, der einen linken Operanden vom Typ 'A' nimmt (oder es gibt keine akzeptable Konvertierung)

- Fehler C2446: ':': keine Konvertierung von 'B' in 'A'

Ein typisches Codemuster, das dieses Problem verursachen kann, ist, wenn eine Klasse C sowohl einen nicht expliziten Konstruktor eines anderen Typs T als auch einen nicht expliziten Konvertierungsoperator für Typ T bereitstellt. Im vorliegenden Fall sind sowohl die Konvertierung des zweiten Arguments in den Typ des dritten Arguments als auch die Konvertierung des dritten Arguments in den Typ des zweiten Arguments gültige Konvertierungen. Da beide gültig sind, ist sie gemäß dem Standard mehrdeutig.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

Es gibt eine wichtige Ausnahme von diesem allgemeinen Muster, wenn T einen der `const char *` `const char16_t *`null-terminierten Zeichenfolgentypen (z. B. , , usw.) darstellt und das eigentliche Argument für `?:` ein Zeichenfolgenliteral des entsprechenden Typs ist. C++17 hat die Semantik von C++14 geändert. Daher wird der Code in Beispiel 2 unter **/std:c++14** akzeptiert und unter **/std:c++17** abgelehnt, wenn **/Zc:ternary** oder **/permissive-** verwendet wird.

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

Ein weiterer Fall, in dem Fehler angezeigt werden, ist in bedingten Operatoren mit einem Argument vom Typ `void`. Dieser Fall kann in ASSERT-ähnlichen Makros üblich sein.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Möglicherweise werden auch Fehler in der Vorlagenmetaprogrammierung angezeigt, bei denen sich die Ergebnistypen des bedingten Operators unter **/Zc:ternary** und **/permissive-** ändern können. Eine Möglichkeit, dieses Problem zu beheben, besteht darin, [std::remove_reference](../../standard-library/remove-reference-class.md) für den resultierenden Typ zu verwenden.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Zwei-Phasen-Namenssuche

Wenn die Option **/permissive-** festgelegt ist, analysiert der Compiler Funktions- und Klassenvorlagendefinitionen und identifiziert abhängige und nicht abhängige Namen, die in Vorlagen verwendet werden, wie es für die zweiphasige Namenssuche erforderlich ist. In Visual Studio 2017 Version 15.3 wird eine Namensabhängigkeitsanalyse durchgeführt. Insbesondere nicht abhängige Namen, die nicht im Kontext einer Vorlagendefinition deklariert werden, verursachen eine Diagnosemeldung, wie dies von den ISO C++-Standards gefordert wird. In Visual Studio 2017 Version 15.7 wird auch die Bindung nicht abhängiger Namen durchgeführt, die eine argumentabhängige Suche im Definitionskontext erfordern.

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

Wenn Sie ein Legacyverhalten für die zweiphasige Suche wünschen, ansonsten aber **/permissive-** Verhalten wünschen, fügen Sie die Option **/Zc:twoPhase-** hinzu.

### <a name="windows-header-issues"></a>Probleme mit dem Windows-Header

Die Option **/permissive-** ist zu streng für Versionen der Windows Kits vor Windows Fall Creators Update SDK (10.0.16299.0) oder dem Windows Driver Kit (WDK) Version 1709. Wir empfehlen Ihnen, auf die neuesten Versionen der Windows-Kits zu aktualisieren, um **/permissive-** in Ihrem Windows- oder Gerätetreibercode zu verwenden.

Bestimmte Headerdateien im Windows April 2018 Update SDK (10.0.17134.0), dem Windows Fall Creators Update SDK (10.0.16299.0) oder dem Windows Driver Kit (WDK) 1709 haben immer noch Probleme, die sie mit der Verwendung von **/permissive-** unvereinbar machen. Um diese Probleme zu umgehen, empfehlen wir, dass Sie die Verwendung dieser Header auf die Quellcodedateien beschränken, die sie benötigen, und die Option **/permissive-** entfernen, wenn Sie diese spezifischen Quellcodedateien kompilieren.

Diese WinRT WRL-Header, die im Windows April 2018 Update SDK (10.0.17134.0) veröffentlicht wurden, sind nicht mit **/permissive-** bereinigt. Um diese Probleme zu umgehen, verwenden Sie entweder nicht **/permissive-**, oder verwenden Sie **/permissive-** mit **/Zc:twoPhase-** wenn Sie mit diesen Headern arbeiten:

- Probleme in winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problem in winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Diese Benutzermodus-Header, die im Windows April 2018 Update SDK (10.0.17134.0) veröffentlicht wurden, sind nicht mit **/permissive-** bereinigt. Um diese Probleme zu umgehen, verwenden Sie **/permissive-** nicht, wenn Sie mit diesen Headern arbeiten:

- Probleme in um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Ausgabe in um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Probleme in um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Diese Probleme sind spezifisch für Benutzermodusheader im Windows Fall Creators Update SDK (10.0.16299.0):

- Problem in um/Query.h

   Bei Verwendung des **/permissive-** `tagRESTRICTION` Compiler-Switches wird die Struktur aufgrund des case(RTOr)-Members 'oder' nicht kompiliert.

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   Um dieses Problem zu beheben, kompilieren Sie Dateien, die Query.h enthalten, ohne die Option **/permissive-.**

- Ausgabe in um/cellularapi_oem.h

   Bei Verwendung des **/permissive-** Compiler-Schalters `enum UICCDATASTOREACCESSMODE` verursacht die Vorwärtsdeklaration eine Warnung:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Die Vorwärtsdeklaration der nicht scoped enum ist eine Microsoft-Erweiterung. Um dieses Problem zu beheben, kompilieren Sie Dateien, die cellularapi_oem.h ohne die Option **/permissive-** enthalten, oder verwenden Sie die Option [/wd,](compiler-option-warning-level.md) um die Warnung C4471 zum Schweigen zu bringen.

- Problem in um/omscript.h

   In C++03 ist eine Konvertierung von einem Zeichenfolgenliteral in BSTR (das ist ein typedef in 'wchar_t *') veraltet, aber zulässig. In C++11 ist die Konvertierung nicht mehr zulässig.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Um dieses Problem zu beheben, kompilieren Sie Dateien, die omscript.h enthalten, ohne die Option **/permissive-** oder verwenden Sie stattdessen **/Zc:strictStrings-.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

Verwenden Sie in Visual Studio 2017 Version 15.5 und höher wie folgt:

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** Ihres Projekts.

1. Wählen Sie die Eigenschaftenseite **"Konfigurationseigenschaften** > **C/C++** > **Language"** aus.

1. Ändern Sie den **Eigenschaftswert des Konformitätsmodus** in **Ja (/permissive-)**. Wählen Sie **OK** oder **Übernehmen,** um Ihre Änderungen zu speichern.

Verwenden Sie in Versionen vor Visual Studio 2017 Version 15.5 dieses Verfahren:

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** Ihres Projekts.

1. Wählen Sie die Eigenschaftenseite **"Konfigurationseigenschaften** > **C/C++** > **Befehlszeile"** aus.

1. Geben Sie die Option **/permissive-** compiler in das Feld **Zusätzliche Optionen** ein. Wählen Sie **OK** oder **Übernehmen,** um Ihre Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)\
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)
