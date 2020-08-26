---
title: Umwandlung von Typen (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 5e51f9e100be2096494e10aca38232dbd1576f40
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843481"
---
# <a name="casting-ccx"></a>Umwandlung von Typen (C++/CX)

Vier verschiedene Umwandlungs Operatoren gelten für Windows-Runtime Typen: [static_cast Operator](../cpp/static-cast-operator.md), [dynamic_cast-Operator](../cpp/dynamic-cast-operator.md), **safe_cast-Operator**und reinterpret_cast- [Operator](../cpp/reinterpret-cast-operator.md). **safe_cast** und lösen **`static_cast`** eine Ausnahme aus, wenn die Konvertierung nicht ausgeführt werden kann. [static_cast Operator](../cpp/static-cast-operator.md) führt außerdem eine Typüberprüfung zur Kompilierzeit durch. **`dynamic_cast`** Gibt zurück **`nullptr`** , wenn der Typ nicht konvertiert werden kann. Obwohl **`reinterpret_cast`** einen Wert ungleich NULL zurückgibt, ist er möglicherweise ungültig. Aus diesem Grund wird empfohlen, dass Sie nicht verwenden, **`reinterpret_cast`** es sei denn, Sie wissen, dass die Umwandlung erfolgreich ist. Außerdem wird empfohlen, keine Umwandlungen im C-Stil in Ihrem C++/CX-Code zu verwenden, da Sie mit identisch sind **`reinterpret_cast`** .

Der Compiler und die Laufzeit führen ebenfalls implizite Umwandlungen aus – beispielsweise bei Boxingvorgängen, wenn ein Werttyp oder ein integrierter Datentyp als Argumente an eine Methode mit dem Parametertyp `Object^`übergeben werden. Theoretisch sollte eine implizite Umwandlung zur Laufzeit nie Ausnahmen verursachen. Wenn der Compiler eine implizite Konvertierung nicht ausführen kann, löst dies einen Fehler zur Kompilierzeit aus.

Windows-Runtime ist eine Abstraktion über com, bei der HRESULT-Fehlercodes anstelle von Ausnahmen verwendet werden. Im Allgemeinen gibt [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) einen COM-Fehler auf niedriger Ebene bei E_NOINTERFACE an.

## <a name="static_cast"></a>static_cast

Eine **`static_cast`** wird zum Zeitpunkt der Kompilierung geprüft, um zu bestimmen, ob zwischen den beiden Typen eine Vererbungs Beziehung besteht. Die Umwandlung verursacht einen Compilerfehler, wenn die Typen nicht verknüpft sind.

Ein **`static_cast`** für eine Verweis Klasse bewirkt auch, dass eine Lauf Zeit Überprüfung ausgeführt wird. Ein-Wert **`static_cast`** für eine Verweis Klasse kann die Kompilierzeit Überprüfung bestehen, kann jedoch zur Laufzeit weiterhin fehlschlagen. in diesem Fall wird eine ausgelöst `Platform::InvalidCastException` . Im Allgemeinen müssen Sie diese Ausnahmen nicht behandeln, da sie fast immer Programmierfehler angeben, die Sie in der Regel während der Entwicklung und der Testphase beheben können.

Verwenden **`static_cast`** Sie, wenn der Code explizit eine Beziehung zwischen den beiden Typen deklariert und Sie daher sicher sind, dass die Umwandlung funktioniert.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

Der **safe_cast** -Operator ist Teil Windows-Runtime. Er führt eine Laufzeittypüberprüfung aus und löst `Platform::InvalidCastException` aus, wenn die Konvertierung fehlschlägt. Verwenden Sie **safe_cast** , wenn ein Laufzeitfehler eine Ausnahme Bedingung angibt. Der Hauptzweck von **safe_cast** ist die Identifizierung von Programmierfehlern während der Entwicklungs-und Testphasen an dem Punkt, an dem Sie auftreten. Sie müssen die Ausnahme nicht behandeln, da der Ausnahmefehler selbst den Fehlerpunkt identifiziert.

Verwenden Sie safe_cast, wenn der Code nicht die Beziehung deklariert, aber Sie sicher sind, dass die Umwandlung funktioniert.

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamic_cast"></a>dynamic_cast

Verwenden Sie **`dynamic_cast`** , wenn Sie ein Objekt (genauer gesagt, einen hat **^** ) in einen stärker abgeleiteten Typ umwandeln. Sie erwarten, dass das Zielobjekt manchmal ist **`nullptr`** oder dass die Umwandlung fehlschlägt, und Sie möchten diese Bedingung als regulären Codepfad anstelle einer Ausnahme behandeln. Beispielsweise verwendet die-Methode in "App. xamp. cpp" in der Projektvorlage " **leere app" (universelle Windows-APP)** , `OnLaunched` **`dynamic_cast`** um zu testen, ob das App-Fenster über Inhalt verfügt. Es ist kein Fehler, wenn kein Inhalt vorhanden ist; es ist eine erwartete Bedingung. `Windows::Current::Content` ist ein `Windows::UI::XAML::UIElement` und die Konvertierung erfolgt in einen `Windows::UI.XAML::Controls::Frame`, der ein besser abgeleiteter Typ in der Vererbungshierarchie ist.

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();
        // ...
    }
}
```

Eine andere Verwendung von **`dynamic_cast`** ist das Überprüfen eines `Object^` , um zu bestimmen, ob es einen geachtelten Werttyp enthält. In diesem Fall versuchen Sie `dynamic_cast<Platform::Box>` oder `dynamic_cast<Platform::IBox>`.

## <a name="dynamic_cast-and-tracking-references-"></a>dynamic_cast und Nachverfolgungsverweise (%)

Sie können auch **`dynamic_cast`** auf einen nach Verfolgungs Verweis anwenden, aber in diesem Fall verhält sich die Umwandlung wie **safe_cast**. Sie löst `Platform::InvalidCastException` bei einem Fehler eine aus, da ein nach Verfolgungs Verweis keinen Wert von aufweisen kann **`nullptr`** .

## <a name="reinterpret_cast"></a>reinterpret_cast

Es wird empfohlen, nicht [reinterpret_cast](../cpp/reinterpret-cast-operator.md) zu verwenden, da weder eine Kompilierzeitüberprüfung noch eine Laufzeitüberprüfung ausgeführt wird. Im ungünstigsten Fall **`reinterpret_cast`** ermöglicht es, dass Programmierungs Fehler zur Entwicklungszeit nicht erkannt werden und zu geringfügigen oder schwerwiegenden Fehlern im Verhalten des Programms führen. Daher wird empfohlen, **`reinterpret_cast`** nur in den seltenen Fällen zu verwenden, wenn Sie eine Umwandlung zwischen nicht verknüpften Typen durchführen müssen und Sie wissen, dass die Umwandlung erfolgreich ist. Ein Beispiel für eine seltene Verwendung ist das Konvertieren eines Windows-Runtime Typs in den zugrunde liegenden ABI-Typ – Dies bedeutet, dass Sie die Verweis Zählung für das Objekt übernehmen. Hierzu wird empfohlen, den intelligenten [ComPtr Class](../cpp/com-ptr-t-class.md) -Zeiger verwenden. Andernfalls müssen Sie Release auf der Schnittstelle ausdrücklich aufrufen. Das folgende Beispiel veranschaulicht, wie eine Verweisklasse zu `IInspectable*`umgewandelt werden kann.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Wenn Sie verwenden, **`reinterpret_cast`** um von der onewindows-Runtime-Schnittstelle in eine andere zu konvertieren, wird das-Objekt zweimal freigegeben. Verwenden Sie daher diese Umwandlung nur, wenn Sie eine Schnittstelle für eine nicht-C + +-Komponenten Erweiterung konvertieren.

## <a name="abi-types"></a>ABI-Typen

- ABI-Typen befinden sich im Windows SDK in Headern. Praktischerweise sind die Header nach Namespaces benannt – z. B. `windows.storage.h`.

- ABI-Typen befinden sich in einer speziellen Namespace-ABI – z. B. `ABI::Windows::Storage::Streams::IBuffer*`.

- Konvertierungen zwischen einem Windows-Runtime Schnittstellentyp und seinem entsprechenden ABI-Typ sind immer sicher – `IBuffer^` d `ABI::IBuffer*` . h. auf.

- Eine Windows-Runtime Lauf Zeit Klasse sollte immer in `IInspectable*` oder Ihre Standardschnittstelle konvertiert werden, wenn dies bekannt ist.

- Nachdem Sie die Konvertierung in ABI-Typen durchgeführt haben, verfügen Sie über die Lebensdauer des Typs und müssen den COM-Regeln folgen. Wir empfehlen zum Vereinfachen der Lebensdauerverwaltung von ABI-Zeigern, `WRL::ComPtr` zu verwenden.

In der folgenden Tabelle werden die Fälle zusammengefasst, in denen Sie sicher verwendet werden kann **`reinterpret_cast`** . In jedem Fall ist die Umwandlung in beide Richtungen sicher.

| Umwandlung von, Umwandlung in | Umwandlung in, Cast from |
|--|--|
| `HSTRING` | `String^` |
| `HSTRING*` | `String^*` |
| `IInspectable*` | `Object^` |
| `IInspectable**` | `Object^*` |
| `IInspectable-derived-type*` | `same-interface-from-winmd^` |
| `IInspectable-derived-type**` | `same-interface-from-winmd^*` |
| `IDefault-interface-of-RuntimeClass*` | `same-RefClass-from-winmd^` |
| `IDefault-interface-of-RuntimeClass**` | `same-RefClass-from-winmd^*` |

## <a name="see-also"></a>Weitere Informationen

- [Typensystem](../cppcx/type-system-c-cx.md)
- [C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)
- [Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
