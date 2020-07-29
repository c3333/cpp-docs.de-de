---
title: _get_purecall_handler, _set_purecall_handler
ms.date: 11/04/2016
api_name:
- _set_purecall_handler
- _set_purecall_handler_m
- _get_purecall_handler
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_purecall_handler
- _set_purecall_handler_m
- set_purecall_handler_m
- set_purecall_handler
- stdlib/_set_purecall_handler
- stdlib/_get_purecall_handler
- _get_purecall_handler
helpviewer_keywords:
- _set_purecall_handler function
- set_purecall_handler function
- purecall_handler
- set_purecall_handler_m function
- _purecall_handler
- _set_purecall_handler_m function
- _get_purecall_handler function
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
ms.openlocfilehash: 9f21258fa1f6ecd2d1717b00ef2cecaee9c865e2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216946"
---
# <a name="_get_purecall_handler-_set_purecall_handler"></a>_get_purecall_handler, _set_purecall_handler

Ruft den Handler für einen rein virtuellen Funktionsaufruf ab oder legt diesen fest.

## <a name="syntax"></a>Syntax

```cpp
typedef void (__cdecl* _purecall_handler)(void);
_purecall_handler __cdecl _get_purecall_handler(void);
_purecall_handler __cdecl _set_purecall_handler(
   _purecall_handler function
);
```

### <a name="parameters"></a>Parameter

*function*<br/>
Die aufzurufende Funktion, wenn eine rein virtuelle Funktion aufgerufen wird. Eine **_purecall_handler** Funktion muss einen void-Rückgabetyp aufweisen.

## <a name="return-value"></a>Rückgabewert

Der vorherige **_purecall_handler**. Gibt zurück, **`nullptr`** Wenn kein vorheriger Handler vorhanden war.

## <a name="remarks"></a>Bemerkungen

Die Funktionen **_get_purecall_handler** und **_set_purecall_handler** sind Microsoft-spezifisch und gelten nur für C++-Code.

Ein Aufruf an eine rein virtuelle Funktion ist ein Fehler, da sie keine Implementierung hat. Standardmäßig generiert der Compiler einen Code, um eine Fehlerhandlerfunktion aufzurufen, wenn eine reine virtuelle Funktion aufgerufen wird, womit das Programm beendet wird. Sie können Ihre eigene Fehlerhandlerfunktion für rein virtuelle Funktionsaufrufe installieren, um sie für das Debuggen und für Berichtszwecke abzufangen. Um einen eigenen Fehlerhandler zu verwenden, erstellen Sie eine Funktion, die über die **_purecall_handler** Signatur verfügt, und verwenden Sie **_set_purecall_handler** , um Sie als aktuellen Handler festzulegen.

Da für jeden Prozess nur ein **_purecall_handler** vorhanden ist, wirkt sich das, wenn Sie **_set_purecall_handler** aufgerufen haben, sofort auf alle Threads aus. Der letzte Aufrufer in einem beliebigen Thread legt den Handler fest.

Um das Standardverhalten wiederherzustellen, wenden Sie **_set_purecall_handler** mit einem- **`nullptr`** Argument an.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_get_purecall_handler** **_set_purecall_handler**|\<cstdlib> oder \<stdlib.h>|

Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```cpp
// _set_purecall_handler.cpp
// compile with: /W1
#include <tchar.h>
#include <stdio.h>
#include <stdlib.h>

class CDerived;
class CBase
{
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function(void) = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase
{
public:
   CDerived() : CBase(this) {};   // C4355
   virtual void function(void) {};
};

CBase::~CBase()
{
   m_pDerived -> function();
}

void myPurecallHandler(void)
{
   printf("In _purecall_handler.");
   exit(0);
}

int _tmain(int argc, _TCHAR* argv[])
{
   _set_purecall_handler(myPurecallHandler);
   CDerived myDerived;
}
```

```Output
In _purecall_handler.
```

## <a name="see-also"></a>Weitere Informationen

[Fehlerbehandlung](../../c-runtime-library/error-handling-crt.md)<br/>
[_purecall](purecall.md)<br/>
