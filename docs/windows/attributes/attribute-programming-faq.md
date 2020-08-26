---
title: Fragen und Antworten zur attributierten Programmierung
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 70fbcc47884214fb998eb63ebfe50e445dbe95b8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843143"
---
# <a name="attribute-programming-faq"></a>Fragen und Antworten zur attributierten Programmierung

In diesem Thema werden die folgenden häufig gestellten Fragen beantwortet:

- [Was ist ein HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [Wann muss ich den Parameternamen für ein Attribut angeben?](#vcconattributeprogrammmingfaqanchor2)

- [Kann ich Kommentare in einem Attribut Block verwenden?](#vcconattributeprogrammmingfaqanchor3)

- [Wie interagieren Attribute mit Vererbung?](#vcconattributeprogrammmingfaqanchor4)

- [Wie kann ich Attribute in einem nicht attributierten ATL-Projekt verwenden?](#vcconattributeprogrammmingfaqanchor5)

- [Wie kann ich eine IDL-Datei in einem attributierten Projekt verwenden?](#vcconattributeprogrammmingfaqanchor6)

- [Kann ich Code ändern, der von einem Attribut eingefügt wird?](#vcconattributeprogrammmingfaqanchor7)

- [Wie kann ich eine attributierte Schnittstelle deklarieren?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [Kann ich Attribute für eine Klasse verwenden, die von einer Klasse abgeleitet ist, die ebenfalls Attribute verwendet?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a> Was ist ein HRESULT?

Ein HRESULT ist ein einfacher Datentyp, der häufig als Rückgabewert von Attributen und ATL im Allgemeinen verwendet wird. In der folgenden Tabelle werden die verschiedenen Werte beschrieben. Weitere Werte sind in der Header Datei Winerror. h enthalten.

|Name|BESCHREIBUNG|Wert|
|----------|-----------------|-----------|
|S_OK|Vorgang erfolgreich|0x00000000|
|E_UNEXPECTED|Unerwarteter Fehler.|0x8000FFFF|
|E_NOTIMPL|Nicht implementiert|0x80004001|
|E_OUTOFMEMORY|Fehler beim Zuordnen des erforderlichen Arbeitsspeichers.|0x8007000E|
|E_INVALIDARG|Mindestens ein Argument ist ungültig.|0x80070057|
|E_NOINTERFACE|Schnittstelle nicht unterstützt.|0x80004002|
|E_POINTER|Ungültiger Zeiger|0x80004003|
|E_HANDLE|Ungültiges Handle|0x80070006|
|E_ABORT|Vorgang abgebrochen|0x80004004|
|E_FAIL|Nicht spezifizierter Fehler|0x80004005|
|E_ACCESSDENIED|Allgemeiner Zugriffs Verweigerungs Fehler|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a> Wann muss ich den Parameternamen für ein Attribut angeben?

In den meisten Fällen hat der Parameter den Namen, wenn das Attribut über einen einzelnen Parameter verfügt. Dieser Name ist nicht erforderlich, wenn Sie das-Attribut in Ihren Code einfügen. Beispielsweise die folgende Verwendung des [aggregierbare](aggregatable.md) -Attributs:

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

ist exakt identisch mit:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

Die folgenden Attribute verfügen jedoch über einzelne, unbenannte Parameter:

:::row:::
   :::column span="":::
      [`call_as`](call-as.md)\
      [`case`](case-cpp.md)\
      [`cpp_quote`](cpp-quote.md)\
      [`default`](default-cpp.md)\
      [`defaultvalue`](defaultvalue.md)\
      [`defaultvtable`](defaultvtable.md)\
      [`emitidl`](emitidl.md)\
      [`entry`](entry.md)\
      [`first_is`](first-is.md)
   :::column-end:::
   :::column span="":::
      [`helpcontext`](helpcontext.md)\
      [`helpfile`](helpfile.md)\
      [`helpstring`](helpstring.md)\
      [`helpstringcontext`](helpstringcontext.md)\
      [`helpstringdll`](helpstringdll.md)\
      [`id`](id.md)\
      [`iid_is`](iid-is.md)\
      [`import`](import.md)
   :::column-end:::
   :::column span="":::
      [`importlib`](importlib.md)\
      [`include`](include-cpp.md)\
      [`includelib`](includelib-cpp.md)\
      [`last_is`](last-is.md)\
      [`length_is`](length-is.md)\
      [`max_is`](max-is.md)\
      [`no_injected_text`](no-injected-text.md)\
      [`pointer_default`](pointer-default.md)
   :::column-end:::
   :::column span="":::
      [`pragma`](pragma.md)\
      [`restricted`](restricted.md)\
      [`size_is`](size-is.md)\
      [`source`](source-cpp.md)\
      [`switch_is`](switch-is.md)\
      [`switch_type`](switch-type.md)\
      [`transmit_as`](transmit-as.md)\
      [`wire_marshal`](wire-marshal.md)
   :::column-end:::
:::row-end:::

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a> Kann ich Kommentare in einem Attribut Block verwenden?

Sie können in einem Attribut Block sowohl einzeilige als auch mehrzeilige Kommentare verwenden. Sie können jedoch keinen Kommentar Stil innerhalb der Klammern verwenden, die die Parameter für ein Attribut verwenden.

Folgendes ist zulässig:

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

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a> Wie interagieren Attribute mit Vererbung?

Sie können sowohl attributierte als auch nicht attributierte Klassen von anderen Klassen erben, die selbst attributiert werden können. Das Ergebnis der Ableitung von einer attributierten Klasse ist das gleiche wie das Ableiten von dieser Klasse, nachdem der Attribut Anbieter den Code transformiert hat. Attribute werden nicht über die C++-Vererbung an abgeleitete Klassen übertragen. Ein Attribut Anbieter wandelt Code nur in der Nähe seiner Attribute um.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a> Wie kann ich Attribute in einem nicht attributierten ATL-Projekt verwenden?

Möglicherweise verfügen Sie über ein nicht attributiertes ATL-Projekt, das über eine IDL-Datei verfügt, und Sie möchten mit dem Hinzufügen von attributierten Objekten beginnen. Verwenden Sie in diesem Fall den **Assistenten zum Hinzufügen von Klassen** , um den Code bereitzustellen.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a> Wie kann ich eine IDL-Datei in einem attributierten Projekt verwenden?

Möglicherweise verfügen Sie über eine IDL-Datei, die Sie in Ihrem ATL-attributierten Projekt verwenden möchten. In diesem Fall verwenden Sie das [importidl](importidl.md) -Attribut, kompilieren Sie die IDL-Datei in eine h-Datei (siehe die [Eigenschaften Seiten der Seite](../../build/reference/midl-property-pages.md) im Dialogfeld **Eigenschaften Seiten** des Projekts), und fügen Sie dann die. h-Datei in Ihr Projekt ein.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a> Kann ich Code ändern, der von einem Attribut eingefügt wird?

Einige Attribute fügen Code in Ihr Projekt ein. Der eingefügte Code kann mit der [/FX](../../build/reference/fx-merge-injected-code.md) -Compileroption angezeigt werden. Es ist auch möglich, Code aus der eingefügten Datei zu kopieren und in den Quellcode einzufügen. Dies ermöglicht es Ihnen, das Verhalten des Attributs zu ändern. Möglicherweise müssen Sie jedoch auch andere Teile des Codes ändern.

Das folgende Beispiel ist das Ergebnis des Kopierens von injiziertem Code in eine Quell Code Datei:

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> Wie kann ich eine attributierte Schnittstelle deklarieren?

Wenn Sie eine vorwärts Deklaration einer attributierten Schnittstelle erstellen, müssen Sie die gleichen Attribute auf die vorwärts Deklaration anwenden, die Sie auf die tatsächliche Schnittstellen Deklaration anwenden. Sie müssen auch das [Export](export.md) -Attribut auf Ihre vorwärts Deklaration anwenden.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> Kann ich Attribute für eine Klasse verwenden, die von einer Klasse abgeleitet ist, die ebenfalls Attribute verwendet?

Nein, das Verwenden von Attributen für eine Klasse, die von einer Klasse abgeleitet ist, die ebenfalls Attribute verwendet, wird nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen

[C++-Attribute für COM und .NET](cpp-attributes-com-net.md)
