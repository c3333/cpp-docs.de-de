---
title: 'Gewusst wie: Marshallen von Strukturen mit PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: e132505ef536a79c67afdd76443c2637c08f923b
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008756"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Gewusst wie: Marshallen von Strukturen mit PInvoke

In diesem Dokument wird erläutert, wie Native Funktionen, die Strukturen im C-Stil akzeptieren, mithilfe von P/Aufruf von verwalteten Funktionen aufgerufen werden können. Es wird empfohlen, dass Sie die C++-Interop-Features anstelle von p/aufrufen verwenden, da p/aufrufen wenig Kompilierzeit-Fehlerberichterstattung bereitstellt, nicht typsicher ist und nicht typsicher sein kann. wenn die nicht verwaltete API als DLL gepackt ist und der Quellcode nicht verfügbar ist, ist p/aufrufen die einzige Option. Andernfalls sehen Sie sich die folgenden Dokumente an:

- [Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Gewusst wie: Mars Hallen von Zeichen folgen mit PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

Standardmäßig werden Native und verwaltete Strukturen im Arbeitsspeicher unterschiedlich angeordnet, sodass das Übergeben von Strukturen über die verwaltete/nicht verwaltete Grenze zusätzliche Schritte erfordert, um die Datenintegrität beizubehalten.

Dieses Dokument erläutert die Schritte, die erforderlich sind, um verwaltete Entsprechungen von systemeigenen Strukturen zu definieren, und wie die resultierenden Strukturen an nicht verwaltete Funktionen übermittelt werden können. In diesem Dokument wird davon ausgegangen, dass einfache Strukturen – diejenigen, die keine Zeichen folgen oder Zeiger – enthalten, verwendet werden. Informationen zur nicht blitfähigen Interoperabilität finden Sie unter [using C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). Beim P/Aufruf dürfen keine nicht blitfähigen Typen als Rückgabewert angegeben werden. Blitfähige Typen haben die gleiche Darstellung in verwaltetem und nicht verwaltetem Code. Weitere Informationen finden Sie unter [blitfähige und nicht blitfähige Typen](/dotnet/framework/interop/blittable-and-non-blittable-types).

Das Marshalling von einfachen, blitfähigen Strukturen über die verwaltete/nicht verwaltete Grenze erfordert zunächst, dass verwaltete Versionen der einzelnen nativen Strukturen definiert werden. Diese Strukturen können einen beliebigen rechtlichen Namen aufweisen. Es gibt keine Beziehung zwischen der nativen und der verwalteten Version der beiden anderen Strukturen als dem Datenlayout. Daher ist es wichtig, dass die verwaltete Version Felder enthält, die dieselbe Größe und in derselben Reihenfolge wie die systemeigene Version haben. (Es gibt keinen Mechanismus, um sicherzustellen, dass die verwaltete und die systemeigene Version der Struktur äquivalent sind, sodass Inkompatibilitäten erst zur Laufzeit offensichtlich werden. Es ist Aufgabe des Programmierers, sicherzustellen, dass die beiden Strukturen über das gleiche Datenlayout verfügen.)

Da die Member verwalteter Strukturen manchmal zu Leistungs Zwecken neu angeordnet werden, muss das-Attribut verwendet werden, <xref:System.Runtime.InteropServices.StructLayoutAttribute> um anzugeben, dass die Struktur sequenziell angeordnet ist. Es ist auch eine gute Idee, die Struktur Verpackungs Einstellung explizit auf die gleiche festzulegen, die von der systemeigenen Struktur verwendet wird. (Obwohl Visual C++ standardmäßig eine 8-Byte-Struktur Komprimierung für beide verwalteten Code verwendet.)

1. Verwenden Sie als nächstes <xref:System.Runtime.InteropServices.DllImportAttribute> zum Deklarieren von Einstiegspunkten, die allen nicht verwalteten Funktionen entsprechen, die die Struktur akzeptieren, aber verwenden Sie die verwaltete Version der Struktur in den Funktions Signaturen, bei der es sich um einen Punkt handelt, wenn Sie für beide Versionen der Struktur denselben Namen verwenden.

1. Nun kann verwalteter Code die verwaltete Version der Struktur an die nicht verwalteten Funktionen übergeben, als wären Sie tatsächlich verwaltete Funktionen. Diese Strukturen können als Wert oder als Verweis weitergegeben werden, wie im folgenden Beispiel gezeigt.

## <a name="unmanaged-and-a-managed-modules"></a>Nicht verwaltete und verwaltete Module

Der folgende Code besteht aus einem nicht verwalteten und einem verwalteten Modul. Das nicht verwaltete Modul ist eine DLL, die eine Struktur namens "Location" definiert, und eine Funktion mit dem Namen "GetDistance", die zwei Instanzen der Standortstruktur akzeptiert. Das zweite Modul ist eine verwaltete Befehlszeilen Anwendung, die die GetDistance-Funktion importiert, Sie jedoch in Bezug auf eine verwaltete Entsprechung der Standortstruktur "MLocation" definiert. In der Praxis würde der gleiche Name wahrscheinlich für beide Versionen der Struktur verwendet werden. Hier wird jedoch ein anderer Name verwendet, um zu veranschaulichen, dass der DllImport-Prototyp in Bezug auf die verwaltete Version definiert ist.

Beachten Sie, dass kein Teil der DLL für den verwalteten Code mit der herkömmlichen #include-Direktive verfügbar gemacht wird. Tatsächlich wird nur zur Laufzeit auf die dll zugegriffen, sodass Probleme mit Funktionen, die mit DllImport importiert werden, zum Zeitpunkt der Kompilierung nicht erkannt werden.

### <a name="example-unmanaged-dll-module"></a>Beispiel: nicht verwaltetes dll-Modul

```cpp
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}
```

### <a name="example-managed-command-line-application-module"></a>Beispiel: Modul für verwaltete Befehlszeilen Anwendung

```cpp
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>Siehe auch

[Verwenden von explizitem PInvoke in C++ (DllImport-Attribut)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
