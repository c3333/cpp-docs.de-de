---
title: Fragen und Antworten zur attributierten Programmierung
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376060"
---
# <a name="attribute-programming-faq"></a>Fragen und Antworten zur attributierten Programmierung

In diesem Thema werden die folgenden häufig gestellten Fragen beantwortet:

- [Was ist ein HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Wann muss ich den Parameternamen für ein Attribut angeben?](#vcconattributeprogrammmingfaqanchor2)

- [Kann ich Kommentare in einem Attributblock verwenden?](#vcconattributeprogrammmingfaqanchor3)

- [Wie interagieren Attribute mit vererbung?](#vcconattributeprogrammmingfaqanchor4)

- [Wie kann ich Attribute in einem nicht attributierten ATL-Projekt verwenden?](#vcconattributeprogrammmingfaqanchor5)

- [Wie kann ich eine .idl-Datei in einem attributierten Projekt verwenden?](#vcconattributeprogrammmingfaqanchor6)

- [Kann ich Code ändern, der von einem Attribut eingefügt wird?](#vcconattributeprogrammmingfaqanchor7)

- [Wie kann ich eine attributierte Schnittstelle weiterleiten?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Kann ich Attribute für eine Klasse verwenden, die von einer Klasse abgeleitet wurde, die auch Attribute verwendet?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>Was ist ein HRESULT?

Ein HRESULT ist ein einfacher Datentyp, der häufig als Rückgabewert nach Attributen und ATL im Allgemeinen verwendet wird. In der folgenden Tabelle werden die verschiedenen Werte beschrieben. Weitere Werte sind in der Headerdatei winerror.h enthalten.

|Name|BESCHREIBUNG|Wert|
|----------|-----------------|-----------|
|S_OK|Vorgang erfolgreich|0x00000000|
|E_UNEXPECTED|Unerwarteter Fehler|0x8000FFFF|
|E_NOTIMPL|Nicht implementiert.|0x80004001|
|E_OUTOFMEMORY|Fehler beim Zuweisen des erforderlichen Speichers|0x8007000E|
|E_INVALIDARG|Mindestens ein Argument ist ungültig|0x80070057|
|E_NOINTERFACE|Schnittstelle nicht unterstützt.|0x80004002|
|E_POINTER|Ungültiger Zeiger|0x80004003|
|E_HANDLE|Ungültiges Handle|0x80070006|
|E_ABORT|Operation abgebrochen|0x80004004|
|E_FAIL|Nicht spezifizierter Fehler|0x80004005|
|E_ACCESSDENIED|Allgemeiner Zugriffsverweigerungsfehler|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>Wann muss ich den Parameternamen für ein Attribut angeben?

Wenn das Attribut in den meisten Fällen über einen einzelnen Parameter verfügt, wird dieser Parameter benannt. Dieser Name ist beim Einfügen des Attributs in den Code nicht erforderlich. Die folgende Verwendung des [aggregatierbaren](aggregatable.md) Attributs ist z. B.:

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

ist genau das gleiche wie:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Die folgenden Attribute weisen jedoch einzelne, unbenannte Parameter auf:

||||
|-|-|-|
|[call_as](call-as.md)|[Fall](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[Standard](default-cpp.md)|[Defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[Eintrag](entry.md)|[first_is](first-is.md)|
|[Helpcontext](helpcontext.md)|[Helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[Importieren](import.md)|[importlib](importlib.md)|
|[gehören dazu](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[Beschränkt](restricted.md)|
|[size_is](size-is.md)|[Quelle](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>Kann ich Kommentare in einem Attributblock verwenden?

Sie können sowohl einzeilige als auch mehrzeilige Kommentare innerhalb eines Attributblocks verwenden. Sie können jedoch keine der beiden Kommentare innerhalb der Klammern verwenden, in denen die Parameter zu einem Attribut gehalten werden.

Folgendes ist erlaubt:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

Folgendes ist nicht zulässig:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>Wie interagieren Attribute mit vererbung?

Sie können sowohl attributierte als auch nicht attributierte Klassen von anderen Klassen erben, die selbst zugeordnet werden können oder nicht. Das Ergebnis der Ableitung von einer attributierten Klasse ist das gleiche wie das Ableiten von dieser Klasse, nachdem der Attributanbieter seinen Code transformiert hat. Attribute werden nicht durch C++-Vererbung an abgeleitete Klassen übertragen. Ein Attributanbieter transformiert Code nur in der Nähe seiner Attribute.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>Wie kann ich Attribute in einem nicht attributierten ATL-Projekt verwenden?

Möglicherweise verfügen Sie über ein nicht attributiertes ATL-Projekt mit einer .idl-Datei, und Sie möchten möglicherweise mit dem Hinzufügen attributierter Objekte beginnen. Verwenden Sie in diesem Fall den Assistenten zum Hinzufügen von **Klassen,** um den Code bereitzustellen.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>Wie kann ich eine .idl-Datei in einem attributierten Projekt verwenden?

Möglicherweise verfügen Sie über eine .idl-Datei, die Sie in Ihrem ATL-Attributprojekt verwenden möchten. In diesem Fall verwenden Sie das [importidl-Attribut,](importidl.md) kompilieren die .idl-Datei in eine .h-Datei (siehe [die MIDL-Eigenschaftenseiten](../../build/reference/midl-property-pages.md) im Dialogfeld **Eigenschaftenseiten** des Projekts) und fügen dann die .h-Datei in Ihr Projekt ein.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>Kann ich Code ändern, der von einem Attribut eingefügt wird?

Einige Attribute fügen Code in Ihr Projekt ein. Sie können den eingefügten Code mit der Compileroption [/Fx](../../build/reference/fx-merge-injected-code.md) anzeigen. Es ist auch möglich, Code aus der eingefügten Datei zu kopieren und in den Quellcode einzufügen. Auf diese Weise können Sie das Verhalten des Attributs ändern. Möglicherweise müssen Sie jedoch auch andere Teile des Codes ändern.

Das folgende Beispiel ist das Ergebnis des Kopierens von eingefügtem Code in eine Quellcodedatei:

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>Wie kann ich eine attributierte Schnittstelle weiterleiten?

Wenn Sie eine Vorwärtsdeklaration einer attributierten Schnittstelle vornehmen möchten, müssen Sie dieselben Attribute auf die Vorwärtsdeklaration anwenden, die Sie auf die tatsächliche Schnittstellendeklaration anwenden. Sie müssen auch das [Exportattribut](export.md) auf Ihre Vorwärtsdeklaration anwenden.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>Kann ich Attribute für eine Klasse verwenden, die von einer Klasse abgeleitet wurde, die auch Attribute verwendet?

Nein, die Verwendung von Attributen für eine Klasse, die von einer Klasse abgeleitet wurde, die auch Attribute verwendet, wird nicht unterstützt.

## <a name="see-also"></a>Siehe auch

[C++-Attribute für COM und .NET](cpp-attributes-com-net.md)
