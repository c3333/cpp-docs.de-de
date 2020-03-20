---
title: call_in_appdomain-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- call_in_appdomain
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
ms.openlocfilehash: da0f2bc1a503226e41198871e6dc48ace7a86854
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545372"
---
# <a name="call_in_appdomain-function"></a>call_in_appdomain-Funktion

Führt eine Funktion in einer angegebenen Anwendungsdomäne aus.

## <a name="syntax"></a>Syntax

```
template <typename ArgType1, ...typename ArgTypeN>
void call_in_appdomain(
   DWORD appdomainId,
   void (*voidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
template <typename RetType, typename ArgType1, ...typename ArgTypeN>
RetType call_in_appdomain(
   DWORD appdomainId,
   RetType (*nonvoidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
```

#### <a name="parameters"></a>Parameter

*AppDomainID*<br/>
Die AppDomain, in der die Funktion aufgerufen werden soll.

*voidFunc*<br/>
Zeiger auf eine `void` Funktion, die N Parameter annimmt (0 < = N < = 15).

*nonvoidFunc*<br/>
Zeiger auf eine nicht`void` Funktion, die N Parameter annimmt (0 < = N < = 15).

*arg1... argN*<br/>
Null bis 15 Parameter, die an `voidFunc` oder `nonvoidFunc` in der anderen Anwendungsdomäne übermittelt werden sollen.

## <a name="return-value"></a>Rückgabewert

Das Ergebnis der Ausführung `voidFunc` oder `nonvoidFunc` in der angegebenen Anwendungsdomäne.

## <a name="remarks"></a>Hinweise

Die Argumente der an `call_in_appdomain` über gebenden Funktion dürfen keine CLR-Typen sein.

## <a name="example"></a>Beispiel

```cpp
// msl_call_in_appdomain.cpp
// compile with: /clr

// Defines two functions: one takes a parameter and returns nothing,
// the other takes no parameters and returns an int.  Calls both
// functions in the default appdomain and in a newly-created
// application domain using call_in_appdomain.

#include <msclr\appdomain.h>

using namespace System;
using namespace msclr;

void PrintCurrentDomainName( char* format )
{
   String^ s = gcnew String(format);
   Console::WriteLine( s, AppDomain::CurrentDomain->FriendlyName );
}

int GetDomainId()
{
   return AppDomain::CurrentDomain->Id;
}

int main()
{
   AppDomain^ appDomain1 = AppDomain::CreateDomain( "First Domain" );

   call_in_appdomain( AppDomain::CurrentDomain->Id,
                   &PrintCurrentDomainName,
                   (char*)"default appdomain: {0}" );
   call_in_appdomain( appDomain1->Id,
                   &PrintCurrentDomainName,
                   (char*)"in appDomain1: {0}" );

   int id;
   id = call_in_appdomain( AppDomain::CurrentDomain->Id, &GetDomainId );
   Console::WriteLine( "default appdomain id = {0}", id );
   id = call_in_appdomain( appDomain1->Id, &GetDomainId );
   Console::WriteLine( "appDomain1 id = {0}", id );
}
```

## <a name="output"></a>Ausgabe

```
default appdomain: msl_call_in_appdomain.exe
in appDomain1: First Domain
default appdomain id = 1
appDomain1 id = 2
```

## <a name="requirements"></a>Voraussetzungen

**Header Datei** \<msclr\appdomain.h >

**Namespace** -msclr
