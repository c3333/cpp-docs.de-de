---
title: C++-Stack-Semantik für Referenztypen
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: 886d0d16d8b81364078db5604ab10d8dcc3fa561
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197838"
---
# <a name="c-stack-semantics-for-reference-types"></a>C++-Stack-Semantik für Referenztypen

Vor Visual Studio 2005 konnte eine Instanz eines Verweis Typs nur mit dem-Operator erstellt werden **`new`** , der das Objekt auf dem Heap der Garbage Collection erstellt hat. Allerdings können Sie jetzt eine Instanz eines Verweis Typs mit derselben Syntax erstellen, die Sie zum Erstellen einer Instanz eines systemeigenen Typs auf dem Stapel verwenden. Daher müssen Sie [ref New, gcnew,](../extensions/ref-new-gcnew-cpp-component-extensions.md) nicht verwenden, um ein Objekt eines Verweis Typs zu erstellen. Wenn das Objekt den Gültigkeitsbereich verlässt, ruft der Compiler den Dekonstruktor des Objekts auf.

## <a name="remarks"></a>Bemerkungen

Wenn Sie eine Instanz eines Verweis Typs mithilfe der Stapel Semantik erstellen, erstellt der Compiler intern die Instanz auf dem Heap der Garbage Collection (mithilfe von **`gcnew`** ).

Wenn die Signatur oder der Rückgabetyp einer Funktion eine Instanz eines by-Value-Verweis Typs enthält, wird die Funktion in den Metadaten als spezielle Behandlung (mit "mudreq") markiert. Diese besondere Behandlung wird zurzeit nur von Visual C++ Clients bereitgestellt. andere Sprachen unterstützen derzeit nicht die Verwendung von Funktionen oder Daten, die Verweis Typen verwenden, die mit der Stapel Semantik erstellt wurden.

Ein Grund für **`gcnew`** die Verwendung von (dynamische Zuordnung) anstelle von Stapel Semantik wäre, wenn der Typ keinen Destruktor aufweist. Außerdem wäre die Verwendung von Verweis Typen, die mit der Stapel Semantik in Funktions Signaturen erstellt wurden, nicht möglich, wenn Sie möchten, dass ihre Funktionen von anderen Sprachen als Visual C++ genutzt werden.

Der Compiler generiert keinen Kopierkonstruktor für einen Referenztyp. Daher müssen Sie, wenn Sie eine Funktion definieren, die einen per-Wert-Verweistyp in der Signatur verwendet, einen Kopierkonstruktor für den Verweistyp definieren. Ein Kopierkonstruktor für einen Verweistyp weist eine Signatur der folgenden Form auf: `R(R%){}` .

Der Compiler generiert keinen Standard Zuweisungs Operator für einen Referenztyp. Mit einem Zuweisungs Operator können Sie ein Objekt mithilfe der Stapel Semantik erstellen und es mit einem vorhandenen Objekt initialisieren, das mithilfe der Stapel Semantik erstellt wurde. Ein Zuweisungs Operator für einen Verweistyp verfügt über eine Signatur der folgenden Form: `void operator=( R% ){}` .

Wenn der Destruktor ihres Typs wichtige Ressourcen freigibt und Sie die Stapel Semantik für Verweis Typen verwenden, müssen Sie den Destruktor nicht explizit (oder den-Befehl) aufzurufen **`delete`** . Weitere Informationen zu Debuggern in Verweis Typen finden Sie unter Vorgehens [Weise: definieren und Verarbeiten von Klassen und Strukturen (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Ein vom Compiler generierter Zuweisungs Operator befolgt die üblichen Standardregeln für C++ mit den folgenden Ergänzungen:

- Alle nicht statischen Datenmember, deren Typ ein Handle für einen Referenztyp ist, werden flach kopiert (wie z. b. ein nicht statischer Datenmember, dessen Typ ein Zeiger ist).

- Ein nicht statischer Datenmember, dessen Typ ein Werttyp ist, wird flach kopiert.

- Alle nicht statischen Datenmember, deren Typ eine Instanz eines Verweis Typs ist, rufen einen Aufruf des Kopierkonstruktors des Verweis Typs auf.

Der Compiler stellt außerdem einen `%` unären Operator bereit, um eine Instanz eines Verweis Typs, der mithilfe der Stapel Semantik erstellt wurde, in den zugrunde liegenden Handle-Typ zu konvertieren.

Die folgenden Referenztypen sind für die Verwendung mit der Stapel Semantik nicht verfügbar:

- [delegate (Komponentenerweiterungen für C++)](../extensions/delegate-cpp-component-extensions.md)

- [Arrays](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Im folgenden Codebeispiel wird veranschaulicht, wie Instanzen von Verweis Typen mit Stapel Semantik deklariert werden, wie der Zuweisungs Operator und der Kopierkonstruktor funktionieren und wie ein nach Verfolgungs Verweis mit einem Referenztyp initialisiert wird, der mithilfe der Stapel Semantik erstellt wurde.

### <a name="code"></a>Code

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>Output

```Output
98
98
98
13
13
```

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md)
