---
title: STL/CLR-Container
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: bfdbbeb735f98f77046790e21c19dd2d21b9d5c6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544838"
---
# <a name="stlclr-containers"></a>STL/CLR-Container

Die STL/CLR-Bibliothek besteht aus Containern, die mit denen in der C++ Standard Bibliothek vergleichbar sind, aber innerhalb der verwalteten Umgebung des .NET Framework ausgeführt werden. Sie wird nicht mit der eigentlichen C++ Standard Bibliothek auf dem neuesten Stand gehalten und wird für Legacy Unterstützung verwaltet.

Dieses Dokument bietet eine Übersicht über die Container in STL/CLR, wie z. b. die Anforderungen für Container Elemente, die Elementtypen, die Sie in die Container einfügen können, und die Besitz Probleme mit den Elementen in den Containern. Gegebenenfalls werden Unterschiede zwischen der nativen C++ Standard Bibliothek und STL/CLR erwähnt.

## <a name="requirements-for-container-elements"></a>Anforderungen für Containerelemente

Alle Elemente, die in STL/CLR-Container eingefügt werden, müssen bestimmte Richtlinien einhalten. Weitere Informationen finden Sie unter [Anforderungen für STL/CLR-Container Elemente](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Gültige Container Elemente

STL/CLR-Container können einen von zwei Typen von Elementen enthalten:

- Handles für Verweis Typen.

- Verweistypen.

- Unboxing-Werttypen.

Sie können keine geachtelten Werttypen in einen der STL/CLR-Container einfügen.

### <a name="handles-to-reference-types"></a>Handles für Verweis Typen

Sie können ein Handle für einen Referenztyp in einen STL/CLR-Container einfügen. Ein Handle in C++ , das die CLR als Ziel hat, ist analog zu C++einem Zeiger im systemeigenen. Weitere Informationen finden Sie unter [handle to Object Operator (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie ein Handle für ein Employee-Objekt in einen [cliext:: Set](../dotnet/set-stl-clr.md)eingefügt wird.

```cpp
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>Verweistypen

Es ist auch möglich, einen Verweistyp (anstelle eines Handles für einen Verweistyp) in einen STL/CLR-Container einzufügen. Der Hauptunterschied besteht darin, dass beim Löschen eines Containers von Verweis Typen der Dekonstruktor für alle Elemente in diesem Container aufgerufen wird. In einem Container von Handles, die auf Typen verweisen, werden die dektoren für diese Elemente nicht aufgerufen.

#### <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie ein Employee-Objekt in eine `cliext::set`eingefügt wird.

```cpp
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Unboxing-Werttypen

Sie können auch einen Unboxing-Werttyp in einen STL/CLR-Container einfügen. Bei einem Unboxing-Werttyp handelt es sich um einen Werttyp, der nicht in einen Verweistyp *eingecheckt* wurde.

Ein Werttyp Element kann einer der Standard Werttypen sein, z. b. ein `int`, oder es kann ein benutzerdefinierter Werttyp, z. b. ein `value class`, sein. Weitere Informationen finden Sie unter [Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md) .

#### <a name="example"></a>Beispiel

Im folgenden Beispiel wird das erste Beispiel dahingehend geändert, dass die Employee-Klasse ein Werttyp ist. Dieser Werttyp wird dann wie im ersten Beispiel in eine `cliext::set` eingefügt.

```cpp
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

Wenn Sie versuchen, ein Handle für einen Werttyp in einen Container einzufügen, wird der [Compilerfehler C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) generiert.

### <a name="performance-and-memory-implications"></a>Auswirkungen auf Leistung und Arbeitsspeicher

Sie müssen mehrere Faktoren berücksichtigen, wenn Sie bestimmen, ob Handles verwendet werden sollen, um auf Typen oder Werttypen als Container Elemente zu verweisen. Wenn Sie sich für die Verwendung von Werttypen entscheiden, denken Sie daran, dass jedes Mal, wenn ein Element in den Container eingefügt wird, eine Kopie des Elements erstellt wird. Bei kleinen Objekten ist dies kein Problem, aber wenn die einzufügenden Objekte sehr groß sind, kann die Leistung beeinträchtigt werden. Wenn Sie Werttypen verwenden, ist es nicht möglich, ein Element gleichzeitig in mehreren Containern zu speichern, da jeder Container über eine eigene Kopie des Elements verfügt.

Wenn Sie stattdessen Handles verwenden, um auf Typen zu verweisen, kann sich die Leistung erhöhen, da es nicht erforderlich ist, eine Kopie des Elements zu erstellen, wenn es in den Container eingefügt wird. Anders als bei Werttypen kann auch das gleiche Element in mehreren Containern vorhanden sein. Wenn Sie sich jedoch für die Verwendung von Handles entscheiden, müssen Sie sicherstellen, dass das Handle gültig ist und dass das Objekt, auf das es verweist, nicht an anderer Stelle im Programm gelöscht wurde.

## <a name="ownership-issues-with-containers"></a>Besitz Probleme mit Containern

Container in STL/CLR arbeiten an der Wert Semantik. Jedes Mal, wenn Sie ein Element in einen Container einfügen, wird eine Kopie dieses Elements eingefügt. Wenn Sie Verweis ähnliche Semantik erhalten möchten, können Sie ein Handle für ein Objekt anstelle des Objekts selbst einfügen.

Wenn Sie die Clear-oder Erase-Methode eines Containers von handle-Objekten aufzurufen, werden die Objekte, auf die die Handles verweisen, nicht aus dem Arbeitsspeicher freigegeben. Sie müssen das Objekt entweder explizit löschen oder, da sich diese Objekte auf dem verwalteten Heap befinden, zulassen, dass der Garbage Collector den Speicher freigeben kann, sobald er feststellt, dass das Objekt nicht mehr verwendet wird.

## <a name="see-also"></a>Siehe auch

[C++ Standard Library Reference (C++-Standardbibliotheksreferenz)](../standard-library/cpp-standard-library-reference.md)
