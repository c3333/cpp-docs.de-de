---
title: :::no-loc(this):::-Zeiger
description: 'Der :::no-loc(this)::: -Zeiger ist ein vom Compiler generierter Zeiger auf das aktuelle-Objekt in nicht statischen Element Funktionen.'
ms.date: 01/22/2020
f1_keywords:
- :::no-loc(this):::_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- 'pointers, to :::no-loc(class)::: instance'
- ':::no-loc(this)::: pointer'
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- ':::no-loc(this):::'
- ':::no-loc(class):::'
- ':::no-loc(struct):::'
- ':::no-loc(union):::'
- ':::no-loc(sizeof):::'
- ':::no-loc(const):::'
- ':::no-loc(volatile):::'
ms.openlocfilehash: c851beaba7fe1091ffd7827714f90307303058c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225825"
---
# <a name="no-locthis-pointer"></a>:::no-loc(this):::-Zeiger

Der **`:::no-loc(this):::`** Zeiger ist ein Zeiger, auf den nur innerhalb der nicht statischen Member-Funktionen eines- **`:::no-loc(class):::`** ,-oder-Typs zugegriffen werden kann **`:::no-loc(struct):::`** **`:::no-loc(union):::`** . Er zeigt auf das Objekt, für das die Memberfunktion aufgerufen wird. Statische Member-Funktionen verfügen nicht über einen- **`:::no-loc(this):::`** Zeiger.

## <a name="syntax"></a>Syntax

```cpp
:::no-loc(this):::
:::no-loc(this):::->member-identifier
```

## <a name="remarks"></a>Bemerkungen

Der Zeiger eines Objekts **`:::no-loc(this):::`** ist nicht Teil des Objekts selbst. Das Ergebnis einer- **`:::no-loc(sizeof):::`** Anweisung für das-Objekt wird nicht berücksichtigt. Wenn eine nicht statische Member-Funktion für ein Objekt aufgerufen wird, übergibt der Compiler die Adresse des Objekts als verborgenes Argument an die Funktion. Folgender Funktionsaufruf kann beispielsweise:

```cpp
myDate.setMonth( 3 );
```

kann wie folgt interpretiert werden:

```cpp
setMonth( &myDate, 3 );
```

Die Adresse des Objekts ist innerhalb der Member-Funktion als Zeiger verfügbar **`:::no-loc(this):::`** . Die meisten **`:::no-loc(this):::`** Zeiger Verwendungen sind implizit. Es ist jedoch nicht erforderlich, eine explizite zu verwenden, **`:::no-loc(this):::`** Wenn auf Member von verwiesen wird :::no-loc(class)::: . Beispiel:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   :::no-loc(this):::->month = mn;      // are equivalent
   (*:::no-loc(this):::).month = mn;
}
```

Der-Ausdruck **`*:::no-loc(this):::`** wird häufig verwendet, um das aktuelle-Objekt aus einer Member-Funktion zurückzugeben:

```cpp
return *:::no-loc(this):::;
```

Der **`:::no-loc(this):::`** Zeiger wird auch verwendet, um sich gegen den selbst Verweis zu schützen:

```cpp
if (&Object != :::no-loc(this):::) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Da der **`:::no-loc(this):::`** Zeiger nicht änderbar ist, sind Zuweisungen zum **`:::no-loc(this):::`** Zeiger nicht zulässig. Frühere Implementierungen von C++ ermöglichten die Zuweisung zu **`:::no-loc(this):::`** .

Gelegentlich wird der **`:::no-loc(this):::`** Zeiger direkt verwendet – z. b., um selbstreferenzielle Daten zu bearbeiten :::no-loc(struct)::: , wobei die Adresse des aktuellen-Objekts erforderlich ist.

## <a name="example"></a>Beispiel

```cpp
// :::no-loc(this):::_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

:::no-loc(class)::: Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( :::no-loc(const)::: Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( :::no-loc(const)::: Buf &otherbuf )
{
    if( &otherbuf != :::no-loc(this)::: )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *:::no-loc(this):::;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-no-locthis-pointer"></a>Der Typ des :::no-loc(this)::: Zeigers.

Der **`:::no-loc(this):::`** Zeigertyp kann in der Funktionsdeklaration durch die **`:::no-loc(const):::`** -und- **`:::no-loc(volatile):::`** Schlüsselwörter geändert werden. Um eine Funktion mit einem dieser Attribute zu deklarieren, fügen Sie das Schlüsselwort (e) nach der Funktions Argumentliste hinzu.

Sehen Sie sich ein Beispiel an:

```cpp
// type_of_:::no-loc(this):::_pointer1.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

Der vorangehende Code deklariert eine Member-Funktion, `X` , in der der **`:::no-loc(this):::`** Zeiger als **`:::no-loc(const):::`** Zeiger auf ein- **`:::no-loc(const):::`** Objekt behandelt wird. Es können Kombinationen von *CV-mod-List-* Optionen verwendet werden, aber Sie ändern immer das Objekt, auf das der **`:::no-loc(this):::`** Zeiger zeigt, nicht den Zeiger selbst. In der folgenden Deklaration `X` wird eine Funktion deklariert, bei der der **`:::no-loc(this):::`** Zeiger ein **`:::no-loc(const):::`** Zeiger auf ein- **`:::no-loc(const):::`** Objekt ist:

```cpp
// type_of_:::no-loc(this):::_pointer2.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

Der Typ von **`:::no-loc(this):::`** in einer Member-Funktion wird durch die folgende Syntax beschrieben. Die *CV-qualifiziererliste* wird vom Deklarator der Element Funktion bestimmt. Der Wert kann **`:::no-loc(const):::`** oder **`:::no-loc(volatile):::`** (oder beides) sein. * :::no-loc(class)::: -Type* ist der Name des :::no-loc(class)::: :

[*CV-Qualifizierer-List*] * :::no-loc(class)::: -Typ* ** \* :::no-loc(const)::: :::no-loc(this)::: **

Dies bedeutet, dass der **`:::no-loc(this):::`** Zeiger immer ein :::no-loc(const)::: Zeiger ist. Sie kann nicht neu zugewiesen werden.  Die **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** in der Deklaration der Element Funktion verwendeten-oder-Qualifizierer gelten für die- :::no-loc(class)::: Instanz **`:::no-loc(this):::`** , auf die der Zeiger verweist, im Gültigkeitsbereich dieser Funktion.

In der folgenden Tabelle wird näher erläutert, wie diese Modifizierer funktionieren.

### <a name="semantics-of-no-locthis-modifiers"></a>Semantik von :::no-loc(this)::: modifiziererzeichen

|Modifizierer|Bedeutung|
|--------------|-------------|
|**`:::no-loc(const):::`**|Elementdaten können nicht geändert werden. Es können keine Element Funktionen aufgerufen werden, die nicht sind **`:::no-loc(const):::`** .|
|**`:::no-loc(volatile):::`**|Elementdaten werden jedes Mal aus dem Arbeitsspeicher geladen, wenn darauf zugegriffen wird. Deaktiviert bestimmte Optimierungen.|

Es ist ein Fehler, ein- **`:::no-loc(const):::`** Objekt an eine Member-Funktion zu übergeben, die nicht ist **`:::no-loc(const):::`** .

Ebenso ist es auch ein Fehler, ein- **`:::no-loc(volatile):::`** Objekt an eine Member-Funktion zu übergeben, die nicht ist **`:::no-loc(volatile):::`** .

Member-Funktionen, die als deklarierte Element **`:::no-loc(const):::`** Daten nicht geändert werden können – in solchen Funktionen **`:::no-loc(this):::`** ist der Zeiger ein Zeiger auf ein- **`:::no-loc(const):::`** Objekt.

> [!NOTE]
> Con :::no-loc(struct)::: ORS und de :::no-loc(struct)::: ORS können nicht als oder deklariert werden **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** . Sie können jedoch für-oder-Objekte aufgerufen werden **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** .

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
