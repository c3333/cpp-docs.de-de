---
title: com::ptr-Klasse
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 8a3223543dfa6c1b5b45fef2780cd11b558eab84
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078969"
---
# <a name="comptr-class"></a>com::ptr-Klasse

Ein Wrapper für ein COM-Objekt, das als Member einer CLR-Klasse verwendet werden kann.  Der Wrapper automatisiert auch die Lebensdauer Verwaltung des COM-Objekts und gibt alle im Besitz befindlichen Verweise auf das Objekt frei, wenn sein Dekonstruktor aufgerufen wird. Analog zur [CComPtr-Klasse](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntax

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parameter

*_interface_type*<br/>
COM-Schnittstelle.

## <a name="remarks"></a>Bemerkungen

Eine `com::ptr` kann auch als lokale Funktions Variable verwendet werden, um verschiedene com-Aufgaben zu vereinfachen und die Lebensdauer Verwaltung zu automatisieren.

Eine `com::ptr` kann nicht direkt als Funktionsparameter verwendet werden. Verwenden Sie stattdessen einen nach [Verfolgungs Verweis Operator](../extensions/tracking-reference-operator-cpp-component-extensions.md) oder einen [handle-to-Object-Operator (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) .

Eine `com::ptr` kann nicht direkt von einer Funktion zurückgegeben werden. Verwenden Sie stattdessen ein handle.

## <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen.  Das Aufrufen der öffentlichen Methoden der-Klasse führt zu Aufrufen des enthaltenen `IXMLDOMDocument` Objekts.  Das Beispiel erstellt eine Instanz eines XML-Dokuments, füllt sie mit einem einfachen XML-Code auf und führt einen vereinfachten Durchlauf der Knoten in der analysierten Dokumentstruktur aus, um den XML-Code in der Konsole auszugeben.

```cpp
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|---------|-----------|
|[ptr::ptr](#ptr)|Erstellt eine `com::ptr` zum Einschließen eines COM-Objekts.|
|[ptr::~ptr](#tilde-ptr)|Zerstört eine `com::ptr`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|---------|-----------|
|[ptr::Attach](#attach)|Fügt ein COM-Objekt an eine `com::ptr`an.|
|[ptr::CreateInstance](#createInstance)|Erstellt eine Instanz eines COM-Objekts in einer `com::ptr`.|
|[ptr::Detach](#detach)|Gibt den Besitz des COM-Objekts an und gibt einen Zeiger auf das-Objekt zurück.|
|[ptr::GetInterface](#getInterface)|Erstellt eine Instanz eines COM-Objekts in einer `com::ptr`.|
|[ptr::QueryInterface](#queryInterface)|Fragt das eigene COM-Objekt für eine Schnittstelle ab und fügt das Ergebnis an einen anderen `com::ptr`an.|
|[ptr::Release](#release)|Gibt alle eigenen Verweise auf dem COM-Objekt frei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|---------|-----------|
|[PTR:: Operator-&gt;](#operator-arrow)|Member Access-Operator, der zum Aufrufen von Methoden für das eigene COM-Objekt verwendet wird.|
|[ptr::operator=](#operator-assign)|Fügt ein COM-Objekt an eine `com::ptr`an.|
|[PTR:: Operator&nbsp;bool](#operator-bool)|Operator für die Verwendung von `com::ptr` in einem bedingten Ausdruck.|
|[ptr::operator!](#operator-logical-not)|-Operator, um zu bestimmen, ob das eigene COM-Objekt ungültig ist.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header Datei** \<msclr\com\ptr.h >

**Namespace** msclr:: com

## <a name="ptrptr"></a><a name="ptr"></a>PTR::p TR

Gibt einen Zeiger auf das eigene COM-Objekt zurück.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein COM-Schnittstellenzeiger.

### <a name="remarks"></a>Bemerkungen

Der Konstruktor ohne Argument weist dem zugrunde liegenden Objekt Handle `nullptr` zu. Zukünftige Aufrufe des `com::ptr` überprüfen das interne Objekt und schlagen im Hintergrund fehl, bis ein Objekt erstellt oder angefügt wird.

Der Konstruktor mit einem Argument fügt dem COM-Objekt einen Verweis hinzu, gibt jedoch nicht den Verweis des Aufrufers frei, sodass der Aufrufer `Release` für das COM-Objekt abrufen muss, um die Kontrolle zu erhalten. Wenn der Dekonstruktor des `com::ptr`aufgerufen wird, gibt er automatisch seine Verweise auf das COM-Objekt frei.

Das übergeben von `NULL` an diesen Konstruktor ist mit dem Aufruf der No-Argument-Version identisch.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Es veranschaulicht die Verwendung beider Versionen des Konstruktors.

```cpp
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrptr"></a><a name="tilde-ptr"></a>PTR:: ~ PTR

Zerstört eine `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Bemerkungen

Bei der Zerstörung gibt der `com::ptr` alle Verweise, die er besitzt, auf sein com-Objekt frei. Vorausgesetzt, dass keine anderen Verweise auf das COM-Objekt gespeichert sind, wird das COM-Objekt gelöscht und sein Speicher freigegeben.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen.  In der `main`-Funktion werden die beiden Dekonstruktoren von `XmlDocument` Objekten aufgerufen, wenn Sie aus dem Bereich des `try`-Blocks gehen, was dazu führt, dass der zugrunde liegende `com::ptr` Dekonstruktor aufgerufen wird und alle im Besitz befindlichen Verweise auf das COM-Objekt freigegeben werden.

```cpp
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrattach"></a><a name="attach"></a>PTR:: Attach

Fügt ein COM-Objekt an eine `com::ptr`an.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Der anzufügende com-Schnittstellen Zeiger.

### <a name="exceptions"></a>Ausnahmen

Wenn das `com::ptr` bereits einen Verweis auf ein COM-Objekt besitzt, löst `Attach` <xref:System.InvalidOperationException>aus.

### <a name="remarks"></a>Bemerkungen

Ein Aufruf von `Attach` verweist auf das COM-Objekt, gibt den Verweis des Aufrufers jedoch nicht frei.

Wenn `NULL` an `Attach` übergeben wird, wird keine Aktion ausgeführt.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Die `ReplaceDocument` Member-Funktion ruft zuerst `Release` für jedes Objekt auf, das bereits im Besitz ist, und ruft dann `Attach` auf, um ein neues Dokument Objekt anzufügen

```cpp
// comptr_attach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>PTR:: kreatone Stance

Erstellt eine Instanz eines COM-Objekts in einer `com::ptr`.

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>Parameter

*progid*<br/>
Eine `ProgID`-Zeichenfolge.

*pouter*<br/>
Zeiger auf die IUnknown-Schnittstelle des aggregierten Objekts (das steuernde IUnknown). Wenn `pouter` nicht angegeben ist, wird `NULL` verwendet.

*cls_context*<br/>
Der Kontext, in dem der Code, mit dem das neu erstellte Objekt verwaltet wird, ausgeführt wird. Die Werte werden aus der `CLSCTX` Enumeration entnommen. Wenn `cls_context` nicht angegeben ist, wird der Wert CLSCTX_ALL verwendet.

*rclsid*<br/>
`CLSID` den Daten und dem Code zugeordnet, die zum Erstellen des Objekts verwendet werden.

### <a name="exceptions"></a>Ausnahmen

Wenn das `com::ptr` bereits einen Verweis auf ein COM-Objekt besitzt, löst `CreateInstance` <xref:System.InvalidOperationException>aus.

Diese Funktion ruft `CoCreateInstance` auf und verwendet <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>, um alle Fehler `HRESULT` in eine entsprechende Ausnahme zu konvertieren.

### <a name="remarks"></a>Bemerkungen

in `CreateInstance` wird `CoCreateInstance` verwendet, um eine neue Instanz des angegebenen Objekts zu erstellen, die entweder von einer ProgID oder einer CLSID identifiziert wird. Der `com::ptr` verweist auf das neu erstellte Objekt und gibt bei der Zerstörung automatisch alle im Besitz befindlichen Verweise frei.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Die Klassenkonstruktoren verwenden zwei verschiedene Formen von `CreateInstance`, um das Dokument Objekt entweder aus einer ProgID oder einer CLSID plus einer CLSCTX zu erstellen.

```cpp
// comptr_createinstance.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="ptrdetach"></a><a name="detach"></a>PTR::D Etach

Gibt den Besitz des COM-Objekts an und gibt einen Zeiger auf das-Objekt zurück.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Rückgabewert

Der Zeiger auf das COM-Objekt.

Wenn kein Objekt im Besitz ist, wird NULL zurückgegeben.

### <a name="exceptions"></a>Ausnahmen

Intern wird `QueryInterface` für das eigene COM-Objekt aufgerufen, und alle Fehler `HRESULT` werden von <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>in eine Ausnahme konvertiert.

### <a name="remarks"></a>Bemerkungen

`Detach` fügt dem Aufrufer zuerst einen Verweis auf das COM-Objekt hinzu und gibt dann alle Verweise frei, die sich im Besitz des `com::ptr`befinden.  Der Aufrufer muss das zurückgegebene Objekt schließlich freigeben, um es zu zerstören.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen.  Die `DetachDocument` Member-Funktion ruft `Detach` auf, um den Besitz des COM-Objekts zu übertragen und einen Zeiger auf den Aufrufer zurückzugeben.

```cpp
// comptr_detach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

## <a name="ptrgetinterface"></a><a name="getInterface"></a>PTR:: GetInterface

Gibt einen Zeiger auf das eigene COM-Objekt zurück.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das eigene COM-Objekt.

### <a name="exceptions"></a>Ausnahmen

Intern wird `QueryInterface` für das eigene COM-Objekt aufgerufen, und alle Fehler `HRESULT` werden von <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>in eine Ausnahme konvertiert.

### <a name="remarks"></a>Bemerkungen

Der `com::ptr` fügt einen Verweis auf das COM-Objekt im Auftrag des Aufrufers hinzu und behält seinen eigenen Verweis auf das COM-Objekt. Der Aufrufer muss letztendlich den Verweis auf das zurückgegebene Objekt freigeben oder nie zerstört werden.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Die `GetDocument` Member-Funktion verwendet `GetInterface`, um einen Zeiger auf das COM-Objekt zurückzugeben.

```cpp
// comptr_getinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>PTR:: QueryInterface

Fragt das eigene COM-Objekt für eine Schnittstelle ab und fügt das Ergebnis an einen anderen `com::ptr`an.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parameter

*other*<br/>
Der `com::ptr`, der die-Schnittstelle erhält.

### <a name="exceptions"></a>Ausnahmen

Intern wird `QueryInterface` für das eigene COM-Objekt aufgerufen, und alle Fehler `HRESULT` werden von <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>in eine Ausnahme konvertiert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode zum Erstellen eines COM-Wrappers für eine andere Schnittstelle des COM-Objekts, das im Besitz des aktuellen Wrappers ist. Diese Methode ruft `QueryInterface` über das eigene COM-Objekt auf, um einen Zeiger auf eine bestimmte Schnittstelle des COM-Objekts anzufordern, und fügt den zurückgegebenen Schnittstellen Zeiger an die Pass-in-`com::ptr`an.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Die `WriteTopLevelNode` Member-Funktion verwendet `QueryInterface`, um eine lokale `com::ptr` mit einem `IXMLDOMNode` auszufüllen, und übergibt dann den `com::ptr` (durch nach Verfolgungs Verweis) an eine private Member-Funktion, die die Name-und Text-Eigenschaften des Knotens in die Konsole schreibt.

```cpp
// comptr_queryinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into our document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="ptrrelease"></a><a name="release"></a>PTR:: Release

Gibt alle eigenen Verweise auf dem COM-Objekt frei.

```cpp
void Release();
```

### <a name="remarks"></a>Bemerkungen

Durch Aufrufen dieser Funktion werden alle im Besitz befindlichen Verweise auf das COM-Objekt freigegeben, und das interne Handle wird auf das COM-Objekt festgelegt, `nullptr`  Wenn keine anderen Verweise auf das COM-Objekt vorhanden sind, wird das Objekt zerstört.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen.  Die `ReplaceDocument` Member-Funktion verwendet `Release`, um jedes vorherige Dokument Objekt freizugeben, bevor das neue Dokument angefügt wird.

```cpp
// comptr_release.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>PTR:: Operator-&gt;

Member Access-Operator, der zum Aufrufen von Methoden für das eigene COM-Objekt verwendet wird.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Rückgabewert

Eine `smart_com_ptr` für das COM-Objekt.

### <a name="exceptions"></a>Ausnahmen

Intern wird `QueryInterface` für das eigene COM-Objekt aufgerufen, und alle Fehler `HRESULT` werden von <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>in eine Ausnahme konvertiert.

### <a name="remarks"></a>Bemerkungen

Mit diesem Operator können Sie Methoden des eigenen com-Objekts aufzurufen. Es wird ein temporäres `smart_com_ptr` zurückgegeben, das automatisch seine eigenen `AddRef` und `Release`behandelt.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Die `WriteDocument`-Funktion verwendet `operator->`, um den `get_firstChild`-Member des Document-Objekts aufzurufen.

```cpp
// comptr_op_member.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="ptroperator"></a><a name="operator-assign"></a>PTR:: Operator =

Fügt ein COM-Objekt an eine `com::ptr`an.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Der anzufügende com-Schnittstellen Zeiger.

### <a name="return-value"></a>Rückgabewert

Ein nach Verfolgungs Verweis auf den `com::ptr`.

### <a name="exceptions"></a>Ausnahmen

Wenn das `com::ptr` bereits einen Verweis auf ein COM-Objekt besitzt, löst `operator=` <xref:System.InvalidOperationException>aus.

### <a name="remarks"></a>Bemerkungen

Das Zuweisen eines COM-Objekts zu einem `com::ptr` verweist auf das COM-Objekt, gibt den Verweis des Aufrufers jedoch nicht frei.

Dieser Operator hat denselben Effekt wie `Attach`.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen.  Die `ReplaceDocument` Member-Funktion ruft zuerst `Release` für jedes Objekt auf, das bereits im Besitz ist, und verwendet dann `operator=`, um ein neues Dokument Objekt anzufügen.

```cpp
// comptr_op_assign.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>PTR:: Operator bool

Operator für die Verwendung von `com::ptr` in einem bedingten Ausdruck.

```cpp
operator bool();
```

### <a name="return-value"></a>Rückgabewert

`true`, wenn das besitzende com-Objekt gültig ist. Andernfalls `false`.

### <a name="remarks"></a>Bemerkungen

Das eigene COM-Objekt ist gültig, wenn es nicht `nullptr`ist.

Dieser Operator konvertiert in `_detail_class::_safe_bool`, der sicherer als `bool` ist, weil er nicht in einen ganzzahligen Typ konvertiert werden kann.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen. Die `CreateInstance` Member-Funktion verwendet `operator bool`, nachdem das neue Dokument Objekt erstellt wurde, um zu bestimmen, ob es gültig ist und in die Konsole schreibt, wenn dies der Fall ist.

```cpp
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="ptroperator"></a><a name="operator-logical-not"></a>PTR:: Operator!

-Operator, um zu bestimmen, ob das eigene COM-Objekt ungültig ist.

```cpp
bool operator!();
```

### <a name="return-value"></a>Rückgabewert

`true`, wenn das besitzende com-Objekt ungültig ist. Andernfalls `false`.

### <a name="remarks"></a>Bemerkungen

Das eigene COM-Objekt ist gültig, wenn es nicht `nullptr`ist.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die eine `com::ptr` verwendet, um den privaten Member `IXMLDOMDocument`-Objekts zu umschließen.  Die `CreateInstance` Member-Funktion verwendet `operator!`, um zu bestimmen, ob ein Dokument Objekt bereits im Besitz ist, und erstellt nur dann eine neue Instanz, wenn das Objekt ungültig ist.

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```
