---
title: Boxing (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- boxing, C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
ms.openlocfilehash: 6221087b60e76e3a2648366c4efebc4105f0ab58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544669"
---
# <a name="boxing--ccli-and-ccx"></a>Boxing (C++/CLI und C++/CX)

Die Konvertierung von Werttypen in Objekte wird als *Boxing* bezeichnet, und die Konvertierung von Objekten in Werttypen als *Unboxing*.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

## <a name="windows-runtime"></a>Windows-Runtime

C++/CX unterstützt eine Kurzsyntax für Boxing-Werttypen und Unboxing-Verweistypen. Ein Werttyp mittels Boxing konvertiert, wenn sie einer Variable des Typs `Object` zugewiesen wird. Eine `Object`-Variable wird mittels Unboxing konvertiert, wenn sie einer Werttypvariable zugeordnet ist und der Unboxing-Typ in Klammern angegeben wird; d. h., wenn die Objektvariable in einen Werttyp umgewandelt wird.

```cpp
  Platform::Object^
  object_variable  = value_variable;
value_variable = (value_type) object_variable;
```

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/ZW`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird ein `DateTime`-Wert mittels Boxing und Unboxing konvertiert. Zunächst ruft das Beispiel einen `DateTime`-Wert ab, der das aktuelle Datum und die Uhrzeit darstellt, und weist ihm eine `DateTime`-Variable zu. Anschließend wird `DateTime` durch Zuweisen zu einer `Object`-Variablen mittels Boxing konvertiert. Schließlich wird der Boxing-Wert mittels Unboxing zurückkonvertiert, indem ihm eine andere `DateTime`-Variable zugewiesen wird.

Um das Beispiel zu testen, erstellen Sie ein `BlankApplication`-Projekt, ersetzen Sie die `BlankPage::OnNavigatedTo()`-Methode, und geben Sie dann bei der schließenden Klammer Haltepunkte und die Zuweisung zur Variablen `str1` an. Wenn im Beispiel die schließende Klammer erreicht wird, untersuchen Sie `str1`.

```cpp
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)
{
    using namespace Windows::Globalization::DateTimeFormatting;

    Windows::Foundation::DateTime dt, dtAnother;
    Platform::Object^ obj1;

    Windows::Globalization::Calendar^ c =
        ref new Windows::Globalization::Calendar;
    c->SetToNow();
    dt = c->GetDateTime();
    auto dtf = ref new DateTimeFormatter(
                           YearFormat::Full,
                           MonthFormat::Numeric,
                           DayFormat::Default,
                           DayOfWeekFormat::None);
    String^ str1 = dtf->Format(dt);
    OutputDebugString(str1->Data());
    OutputDebugString(L"\r\n");

    // Box the value type and assign to a reference type.
    obj1 = dt;
    // Unbox the reference type and assign to a value type.
    dtAnother = (Windows::Foundation::DateTime) obj1;

    // Format the DateTime for display.
    String^ str2 = dtf->Format(dtAnother);
    OutputDebugString(str2->Data());
}
```

Weitere Informationen finden Sie unter [Boxing (C++/CX)](../cppcx/boxing-c-cx.md).

## <a name="common-language-runtime"></a>Common Language Runtime

Der Compiler konvertiert Werttypen durch Boxing in <xref:System.Object>. Dies ist möglich durch eine compiler-definierte Konvertierung zur Konvertierung von Werttypen in <xref:System.Object>.

Mit Boxing und Unboxing können Werttypen wie Objekte behandelt werden. Werttypen, einschließlich Strukturtypen und integrierten Typen wie int, können in und aus dem Typ <xref:System.Object> konvertiert werden.

Weitere Informationen finden Sie unter

- [Vorgehensweise: Explizites Anfordern von Boxing](../dotnet/how-to-explicitly-request-boxing.md)

- [Vorgehensweise: Verwenden von gcnew zum Erstellen von Werttypen und für implizites Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)

- [Vorgehensweise: Unboxing](../dotnet/how-to-unbox.md)

- [Standardumwandlungen und implizites Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Beispiel zeigt wie implizites Boxing funktioniert.

```cpp
// vcmcppv2_explicit_boxing2.cpp
// compile with: /clr
using namespace System;

ref class A {
public:
   void func(System::Object^ o){Console::WriteLine("in A");}
};

value class V {};

interface struct IFace {
   void func();
};

value class V1 : public IFace {
public:
   virtual void func() {
      Console::WriteLine("Interface function");
   }
};

value struct V2 {
   // conversion operator to System::Object
   static operator System::Object^(V2 v2) {
      Console::WriteLine("operator System::Object^");
      return (V2^)v2;
   }
};

void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}
void func1(V2^){Console::WriteLine("in func1(V2^)");}

void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}

int main() {
   // example 1 simple implicit boxing
   Int32^ bi = 1;
   Console::WriteLine(bi);

   // example 2 calling a member with implicit boxing
   Int32 n = 10;
   Console::WriteLine("xx = {0}", n.ToString());

   // example 3 implicit boxing for function calls
   A^ a = gcnew A;
   a->func(n);

   // example 4 implicit boxing for WriteLine function call
   V v;
   Console::WriteLine("Class {0} passed using implicit boxing", v);
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing

   // example 5 casting to a base with implicit boxing
   V1 v1;
   IFace ^ iface = v1;
   iface->func();

   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching
   V2 v2;
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing
                // Will call void func1(System::Object^);

   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)
}
```

```Output
1

xx = 10

in A

Class V passed using implicit boxing

Class V passed with forced boxing

Interface function

in func1(V2^)

in func2(System::ValueType^)

in func2(System::ValueType^)
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)