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
ms.openlocfilehash: e494285f33cf282d7b7515aac374ec86ef3036b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372491"
---
# <a name="comptr-class"></a>com::ptr-Klasse

Ein Wrapper für ein COM-Objekt, das als Member einer CLR-Klasse verwendet werden kann.  Der Wrapper automatisiert auch die Lebensdauerverwaltung des COM-Objekts und gibt alle eigenen Verweise auf das Objekt frei, wenn sein Destruktor aufgerufen wird. Analog zur [CComPtr-Klasse](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntax

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parameter

*_interface_type*<br/>
COM-Schnittstelle.

## <a name="remarks"></a>Bemerkungen

A `com::ptr` kann auch als lokale Funktionsvariable verwendet werden, um verschiedene COM-Aufgaben zu vereinfachen und die Lebensdauerverwaltung zu automatisieren.

A `com::ptr` kann nicht direkt als Funktionsparameter verwendet werden; Verwenden Sie stattdessen einen [Tracking-Referenzoperator](../extensions/tracking-reference-operator-cpp-component-extensions.md) oder einen [Handle-to-Objektoperator ( .](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

A `com::ptr` kann nicht direkt von einer Funktion zurückgegeben werden. verwenden Sie stattdessen ein Handle.

## <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet.  Das Aufrufen der öffentlichen Methoden der Klasse `IXMLDOMDocument` führt zu Aufrufen des enthaltenen Objekts.  Das Beispiel erstellt eine Instanz eines XML-Dokuments, füllt es mit einfachem XML aus und führt eine vereinfachte Durchgang der Knoten in der analysierten Dokumentstruktur durch, um die XML-Datei in der Konsole zu drucken.

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

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|---------|-----------|
|[ptr::ptr](#ptr)|Erstellt ein, `com::ptr` um ein COM-Objekt umzuschließen.|
|[ptr::-ptr](#tilde-ptr)|Zerstört eine `com::ptr`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|---------|-----------|
|[ptr::Attach](#attach)|Fügt ein COM-Objekt `com::ptr`an eine an.|
|[ptr::CreateInstance](#createInstance)|Erstellt eine Instanz eines COM-Objekts innerhalb einer `com::ptr`.|
|[ptr::Detach](#detach)|Gibt den Besitz des COM-Objekts auf und gibt einen Zeiger auf das Objekt zurück.|
|[ptr::GetInterface](#getInterface)|Erstellt eine Instanz eines COM-Objekts innerhalb einer `com::ptr`.|
|[ptr::QueryInterface](#queryInterface)|Fragt das eigene COM-Objekt nach einer Schnittstelle `com::ptr`ab und fügt das Ergebnis an eine andere an.|
|[ptr::Release](#release)|Gibt alle eigenen Verweise auf das COM-Objekt frei.|

### <a name="public-operators"></a>Öffentliche Betreiber

|Name|BESCHREIBUNG|
|---------|-----------|
|[ptr::operator-&gt;](#operator-arrow)|Memberzugriffsoperator, der zum Aufrufen von Methoden für das eigene COM-Objekt verwendet wird.|
|[ptr::operator=](#operator-assign)|Fügt ein COM-Objekt `com::ptr`an eine an.|
|[ptr::operator&nbsp;bool](#operator-bool)|Operator für `com::ptr` die Verwendung in einem bedingten Ausdruck.|
|[ptr::operator!](#operator-logical-not)|Operator, um zu ermitteln, ob das im Besitz befindliche COM-Objekt ungültig ist.|

## <a name="requirements"></a>Anforderungen

**Headerdatei** \<msclr-com-ptr.h>

**Namespace** msclr::com

## <a name="ptrptr"></a><a name="ptr"></a>ptr::ptr

Gibt einen Zeiger auf das im Besitz befindliche COM-Objekt zurück.

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

Der No-Argument-Konstruktor `nullptr` weist dem zugrunde liegenden Objekthandle zu. Zukünftige Aufrufe `com::ptr` an die überprüfen das interne Objekt und schlagen stillschweigend fehl, bis ein Objekt erstellt oder angefügt wird.

Der Konstruktor mit einem Argument fügt einen Verweis auf das COM-Objekt hinzu, gibt den `Release` Verweis des Aufrufers jedoch nicht frei, sodass der Aufrufer das COM-Objekt aufrufen muss, um die Steuerung wirklich aufzugeben. Wenn `com::ptr`der Destruktor von aufgerufen wird, werden seine Verweise automatisch auf das COM-Objekt freigegeben.

Die `NULL` Übergabe an diesen Konstruktor entspricht dem Aufrufen der No-Argument-Version.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Es zeigt die Verwendung beider Versionen des Konstruktors.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>ptr::-ptr

Zerstört eine `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Bemerkungen

Bei der `com::ptr` Zerstörung gibt der alle Verweise auf sein COM-Objekt frei. Unter der Annahme, dass keine weiteren Verweise auf das COM-Objekt vorhanden sind, wird das COM-Objekt gelöscht und sein Speicher freigegeben.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet.  In `main` der Funktion `XmlDocument` werden die Destruktoren der beiden Objekte aufgerufen, `try` wenn sie den `com::ptr` Bereich des Blocks nicht mehr haben, was dazu führt, dass der zugrunde liegende Destruktor aufgerufen wird, wodurch alle eigenen Verweise auf das COM-Objekt freigegeben werden.

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

## <a name="ptrattach"></a><a name="attach"></a>ptr::Attach

Fügt ein COM-Objekt `com::ptr`an eine an.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Der anzufügende COM-Schnittstellenzeiger.

### <a name="exceptions"></a>Ausnahmen

Wenn `com::ptr` der bereits einen Verweis auf `Attach` ein <xref:System.InvalidOperationException>COM-Objekt besitzt, wird ausgelöst.

### <a name="remarks"></a>Bemerkungen

Ein Aufruf, auf `Attach` das COM-Objekt zu verweisen, gibt jedoch nicht den Verweis des Aufrufers darauf frei.

Durch `NULL` `Attach` das Durchlaufen der Ergebnisse wird keine Aktion ergriffen.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Die `ReplaceDocument` Memberfunktion `Release` ruft zuerst ein zuvor `Attach` im Besitz befindliches Objekt auf und ruft dann auf, um ein neues Dokumentobjekt anzufügen.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>ptr::CreateInstance

Erstellt eine Instanz eines COM-Objekts innerhalb einer `com::ptr`.

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

*Progid*<br/>
Eine `ProgID`-Zeichenfolge.

*pouter*<br/>
Zeiger auf die IUnknown-Schnittstelle des Aggregatobjekts (die steuernde IUnknown). Wenn `pouter` nicht angegeben, `NULL` wird verwendet.

*cls_context*<br/>
Kontext, in dem der Code ausgeführt wird, der das neu erstellte Objekt verwaltet. Die Werte werden `CLSCTX` der Enumeration entnommen. Wenn `cls_context` nicht angegeben, wird der Wert CLSCTX_ALL verwendet.

*rclsid*<br/>
`CLSID`daten und code zugeordnet sind, die zum Erstellen des Objekts verwendet werden.

### <a name="exceptions"></a>Ausnahmen

Wenn `com::ptr` der bereits einen Verweis auf `CreateInstance` ein <xref:System.InvalidOperationException>COM-Objekt besitzt, wird ausgelöst.

Diese Funktion `CoCreateInstance` ruft <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> auf und `HRESULT` verwendet, um jeden Fehler in eine entsprechende Ausnahme zu konvertieren.

### <a name="remarks"></a>Bemerkungen

`CreateInstance`verwendet, `CoCreateInstance` um eine neue Instanz des angegebenen Objekts zu erstellen, die entweder aus einer ProgID oder einer CLSID identifiziert wird. Die `com::ptr` Verweise auf das neu erstellte Objekt und geben automatisch alle eigenen Verweise nach Zerstörung frei.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Die Klassenkonstruktoren verwenden zwei `CreateInstance` verschiedene Formen, um das Dokumentobjekt entweder aus einer ProgID oder aus einer CLSID plus einem CLSCTX zu erstellen.

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

## <a name="ptrdetach"></a><a name="detach"></a>ptr::Detach

Gibt den Besitz des COM-Objekts auf und gibt einen Zeiger auf das Objekt zurück.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Rückgabewert

Der Zeiger auf das COM-Objekt.

Wenn kein Objekt im Besitz ist, wird NULL zurückgegeben.

### <a name="exceptions"></a>Ausnahmen

Intern `QueryInterface` wird das im Besitz befindliche `HRESULT` COM-Objekt aufgerufen, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>und jeder Fehler wird in eine Ausnahme von konvertiert.

### <a name="remarks"></a>Bemerkungen

`Detach`fügt zunächst einen Verweis auf das COM-Objekt im Namen des `com::ptr`Aufrufers hinzu und gibt dann alle Verweise frei, die im Besitz der .  Der Aufrufer muss das zurückgegebene Objekt letztendlich freigeben, um es zu zerstören.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet.  Die `DetachDocument` Memberfunktion `Detach` ruft auf, den Besitz des COM-Objekts aufzugeben und einen Zeiger an den Aufrufer zurückzugeben.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>ptr::GetInterface

Gibt einen Zeiger auf das im Besitz befindliche COM-Objekt zurück.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das eigene COM-Objekt.

### <a name="exceptions"></a>Ausnahmen

Intern `QueryInterface` wird das im Besitz befindliche `HRESULT` COM-Objekt aufgerufen, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>und jeder Fehler wird in eine Ausnahme von konvertiert.

### <a name="remarks"></a>Bemerkungen

Der `com::ptr` fügt im Namen des Aufrufers einen Verweis auf das COM-Objekt hinzu und behält auch seinen eigenen Verweis auf das COM-Objekt bei. Der Aufrufer muss den Verweis auf das zurückgegebene Objekt letztendlich freigeben, da er nie zerstört wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Die `GetDocument` Memberfunktion `GetInterface` verwendet, um einen Zeiger auf das COM-Objekt zurückzugeben.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>ptr::QueryInterface

Fragt das eigene COM-Objekt nach einer Schnittstelle `com::ptr`ab und fügt das Ergebnis an eine andere an.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parameter

*Andere*<br/>
Die, `com::ptr` die die Schnittstelle erhält.

### <a name="exceptions"></a>Ausnahmen

Intern `QueryInterface` wird das im Besitz befindliche `HRESULT` COM-Objekt aufgerufen, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>und jeder Fehler wird in eine Ausnahme von konvertiert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen COM-Wrapper für eine andere Schnittstelle des COM-Objekts zu erstellen, das dem aktuellen Wrapper gehört. Diese Methode `QueryInterface` ruft über das eigene COM-Objekt auf, um einen Zeiger auf eine bestimmte Schnittstelle des `com::ptr`COM-Objekts anzufordern, und fügt den zurückgegebenen Schnittstellenzeiger an den übergebenen an.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Die `WriteTopLevelNode` Memberfunktion `QueryInterface` verwendet, `com::ptr` um `IXMLDOMNode` ein lokales `com::ptr` mit einem zu füllen und übergibt dann die (durch Nachverfolgungsreferenz) an eine private Memberfunktion, die den Namen und die Texteigenschaften des Knotens in die Konsole schreibt.

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

## <a name="ptrrelease"></a><a name="release"></a>ptr::Release

Gibt alle eigenen Verweise auf das COM-Objekt frei.

```cpp
void Release();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion aufrufen, werden alle eigenen Verweise auf `nullptr`das COM-Objekt freigegeben und das interne Handle auf das COM-Objekt auf festgelegt.  Wenn keine anderen Verweise auf das COM-Objekt vorhanden sind, wird es zerstört.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet.  Die `ReplaceDocument` Memberfunktion `Release` verwendet, um alle vorherigen Dokumentobjekte freizugeben, bevor das neue Dokument angefügt wird.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>ptr::operator-&gt;

Memberzugriffsoperator, der zum Aufrufen von Methoden für das eigene COM-Objekt verwendet wird.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Rückgabewert

A `smart_com_ptr` zum COM-Objekt.

### <a name="exceptions"></a>Ausnahmen

Intern `QueryInterface` wird das im Besitz befindliche `HRESULT` COM-Objekt aufgerufen, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>und jeder Fehler wird in eine Ausnahme von konvertiert.

### <a name="remarks"></a>Bemerkungen

Mit diesem Operator können Sie Methoden des eigenen COM-Objekts aufrufen. Es gibt `smart_com_ptr` ein Temporär `AddRef` zurück, das automatisch seine eigenen und `Release`verarbeitet.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Die `WriteDocument` Funktion `operator->` verwendet, `get_firstChild` um den Member des Dokumentobjekts aufzurufen.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>ptr::operator=

Fügt ein COM-Objekt `com::ptr`an eine an.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parameter

*_right*<br/>
Der anzufügende COM-Schnittstellenzeiger.

### <a name="return-value"></a>Rückgabewert

Eine Tracking-Referenz `com::ptr`auf der .

### <a name="exceptions"></a>Ausnahmen

Wenn `com::ptr` der bereits einen Verweis auf `operator=` ein <xref:System.InvalidOperationException>COM-Objekt besitzt, wird ausgelöst.

### <a name="remarks"></a>Bemerkungen

Das Zuweisen eines COM-Objekts zu einem `com::ptr` Verweis auf das COM-Objekt, gibt jedoch keinen Verweis des Aufrufers darauf frei.

Dieser Operator hat den `Attach`gleichen Effekt wie .

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet.  Die `ReplaceDocument` Memberfunktion `Release` ruft zuerst ein zuvor `operator=` im Besitz befindliches Objekt auf und wird dann zum Anfügen eines neuen Dokumentobjekts verwendet.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>ptr::operator bool

Operator für `com::ptr` die Verwendung in einem bedingten Ausdruck.

```cpp
operator bool();
```

### <a name="return-value"></a>Rückgabewert

`true`wenn das im Besitz befindliche COM-Objekt gültig ist; `false` andernfalls.

### <a name="remarks"></a>Bemerkungen

Das im Besitz befindliche COM-Objekt `nullptr`ist gültig, wenn es sich nicht handelt.

Dieser Operator konvertiert `_detail_class::_safe_bool` in die `bool` sicherer ist, als weil er nicht in einen integralen Typ konvertiert werden kann.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet. Die `CreateInstance` Memberfunktion `operator bool` verwendet nach dem Erstellen des neuen Dokumentobjekts, um zu bestimmen, ob es gültig ist, und schreibt in die Konsole, falls dies der Bedarf ist.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>ptr::Operator!

Operator, um zu ermitteln, ob das im Besitz befindliche COM-Objekt ungültig ist.

```cpp
bool operator!();
```

### <a name="return-value"></a>Rückgabewert

`true`wenn das im Besitz befindliche COM-Objekt ungültig ist; `false` andernfalls.

### <a name="remarks"></a>Bemerkungen

Das im Besitz befindliche COM-Objekt `nullptr`ist gültig, wenn es sich nicht handelt.

### <a name="example"></a>Beispiel

In diesem Beispiel wird eine CLR-Klasse implementiert, die ein `com::ptr` zum Umschließen des privaten Memberobjekts `IXMLDOMDocument` verwendet.  Die `CreateInstance` Memberfunktion `operator!` verwendet, um zu bestimmen, ob ein Dokumentobjekt bereits im Besitz ist, und erstellt nur dann eine neue Instanz, wenn das Objekt ungültig ist.

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
