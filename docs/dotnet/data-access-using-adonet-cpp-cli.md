---
title: Datenzugriff mit ADO.NET (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
ms.openlocfilehash: 3f3980c98890382e77d9d89db2944bebf7b12319
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211059"
---
# <a name="data-access-using-adonet-ccli"></a>Datenzugriff mit ADO.NET (C++/CLI)

ADO.net ist die .NET Framework-API für den Datenzugriff und bietet Leistungsfähigkeit und Benutzerfreundlichkeit, die von früheren Datenzugriffs Lösungen nicht erreicht wird. In diesem Abschnitt werden einige der Probleme im Zusammenhang mit ADO.net beschrieben, die für Visual C++ Benutzer spezifisch sind, z. b. das Marshalling von systemeigenen Typen.

ADO.net wird unter der Common Language Runtime (CLR) ausgeführt. Daher muss jede Anwendung, die mit ADO.NET interagiert, auch auf die CLR abzielen. Dies bedeutet jedoch nicht, dass native Anwendungen ADO.net nicht verwenden können. In diesen Beispielen wird veranschaulicht, wie Sie mit einer ADO.net-Datenbank aus nativem Code interagieren.

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>Mars Hall Zeichen für ADO.net

Veranschaulicht, wie eine systemeigene Zeichenfolge ( `char *` ) zu einer Datenbank hinzugefügt wird und wie ein <xref:System.String?displayProperty=fullName> aus einer Datenbank in eine systemeigene Zeichenfolge gemarshallt wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass erstellt, um mit einem ADO.net- <xref:System.Data.DataTable> Objekt zu interagieren. Beachten Sie, dass diese Klasse eine native C++ **`class`** (im Vergleich zu **`ref class`** oder **`value class`** ) ist. Dies ist erforderlich, da wir diese Klasse aus nativem Code verwenden möchten, und Sie können keine verwalteten Typen in nativem Code verwenden. Diese Klasse wird für die CLR als Ziel kompiliert, wie dies durch die- `#pragma managed` Direktive vor der Klassen Deklaration angegeben wird. Weitere Informationen zu dieser Direktive finden Sie unter [verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Notieren Sie sich den privaten Member der DatabaseClass-Klasse: `gcroot<DataTable ^> table` . Da Native Typen keine verwalteten Typen enthalten können, `gcroot` ist das Schlüsselwort erforderlich. Weitere Informationen zu `gcroot` finden Sie unter Gewusst [wie: Deklarieren von Handles in](../dotnet/how-to-declare-handles-in-native-types.md)systemeigenen Typen.

Der Rest des Codes in diesem Beispiel ist System eigener C++-Code, wie von der `#pragma unmanaged` vorangehenden-Direktive angegeben `main` . In diesem Beispiel wird eine neue Instanz von DatabaseClass erstellt und die zugehörigen Methoden aufgerufen, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass systemeigene C++-Zeichen folgen als Werte für die Daten Bank Spalte StringCol übergeben werden. In DatabaseClass werden diese Zeichen folgen mithilfe der Marshallingfunktionen im-Namespace an verwaltete Zeichen folgen gemarshallt <xref:System.Runtime.InteropServices?displayProperty=fullName> . Insbesondere <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> wird die-Methode verwendet, um einen in ein zu Mars Hallen `char *` <xref:System.String> , und die-Methode <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> wird verwendet, um einen <xref:System.String> in ein zu Mars Hallen `char *` .

> [!NOTE]
> Der durch zugeordnete Arbeitsspeicher muss aufgehoben <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> werden, indem entweder oder aufgerufen wird <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> `GlobalFree` .

```cpp
// adonet_marshal_string_native.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(char *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringAnsi(
            (IntPtr)stringColValue);
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("StringCol",
            Type::GetType("System.String"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(char *dataColumn, char **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringAnsi(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a char *.
            values[i] = (char *)Marshal::StringToHGlobalAnsi(
                (String ^)rows[i][columnStr]).ToPointer();
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();
    db->AddRow("This is string 1.");
    db->AddRow("This is string 2.");

    // Now retrieve the rows and display their contents.
    char *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        "StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        cout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalAnsi.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>Kompilieren des Codes

- Um den Code über die Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei namens "adonet_marshal_string_native. cpp", und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>Mars Hallen von BSTR-Zeichen folgen für ADO.net

Veranschaulicht das Hinzufügen einer com-Zeichenfolge ( `BSTR` ) zu einer Datenbank und das Marshalling <xref:System.String?displayProperty=fullName> von Daten aus einer Datenbank zu einer `BSTR` .

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass erstellt, um mit einem ADO.net- <xref:System.Data.DataTable> Objekt zu interagieren. Beachten Sie, dass diese Klasse eine native C++ **`class`** (im Vergleich zu **`ref class`** oder **`value class`** ) ist. Dies ist erforderlich, da wir diese Klasse aus nativem Code verwenden möchten, und Sie können keine verwalteten Typen in nativem Code verwenden. Diese Klasse wird für die CLR als Ziel kompiliert, wie dies durch die- `#pragma managed` Direktive vor der Klassen Deklaration angegeben wird. Weitere Informationen zu dieser Direktive finden Sie unter [verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Notieren Sie sich den privaten Member der DatabaseClass-Klasse: `gcroot<DataTable ^> table` . Da Native Typen keine verwalteten Typen enthalten können, `gcroot` ist das Schlüsselwort erforderlich. Weitere Informationen zu `gcroot` finden Sie unter Gewusst [wie: Deklarieren von Handles in](../dotnet/how-to-declare-handles-in-native-types.md)systemeigenen Typen.

Der Rest des Codes in diesem Beispiel ist System eigener C++-Code, wie von der `#pragma unmanaged` vorangehenden-Direktive angegeben `main` . In diesem Beispiel wird eine neue Instanz von DatabaseClass erstellt und die zugehörigen Methoden aufgerufen, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass com-Zeichen folgen als Werte für die Daten Bank Spalte StringCol übergeben werden. In DatabaseClass werden diese Zeichen folgen mithilfe der Marshallingfunktionen im-Namespace an verwaltete Zeichen folgen gemarshallt <xref:System.Runtime.InteropServices?displayProperty=fullName> . Insbesondere <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> wird die-Methode verwendet, um einen in ein zu Mars Hallen `BSTR` <xref:System.String> , und die-Methode <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> wird verwendet, um einen <xref:System.String> in ein zu Mars Hallen `BSTR` .

> [!NOTE]
> Der durch zugeordnete Arbeitsspeicher muss aufgehoben <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> werden, indem entweder oder aufgerufen wird <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> `SysFreeString` .

``` cpp
// adonet_marshal_string_bstr.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(BSTR stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringBSTR(
            (IntPtr)stringColValue);
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("StringCol",
            Type::GetType("System.String"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(BSTR dataColumn, BSTR *values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringBSTR(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a BSTR.
            values[i] = (BSTR)Marshal::StringToBSTR(
                (String ^)rows[i][columnStr]).ToPointer();
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();

    BSTR str1 = SysAllocString(L"This is string 1.");
    db->AddRow(str1);

    BSTR str2 = SysAllocString(L"This is string 2.");
    db->AddRow(str2);

    // Now retrieve the rows and display their contents.
    BSTR values[MAXCOLS];
    BSTR str3 = SysAllocString(L"StringCol");
    int len = db->GetValuesForColumn(
        str3, values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToBSTR.
        SysFreeString(values[i]);
    }

    SysFreeString(str1);
    SysFreeString(str2);
    SysFreeString(str3);
    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>Kompilieren des Codes

- Um den Code über die Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei namens "adonet_marshal_string_native. cpp", und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>Marshal-Unicode-Zeichen folgen für ADO.net

Veranschaulicht das Hinzufügen einer systemeigenen Unicode-Zeichenfolge ( `wchar_t *` ) zu einer Datenbank und das Mars Hallen einer <xref:System.String?displayProperty=fullName> aus einer Datenbank in eine systemeigene Unicode-Zeichenfolge.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass erstellt, um mit einem ADO.net- <xref:System.Data.DataTable> Objekt zu interagieren. Beachten Sie, dass diese Klasse eine native C++ **`class`** (im Vergleich zu **`ref class`** oder **`value class`** ) ist. Dies ist erforderlich, da wir diese Klasse aus nativem Code verwenden möchten, und Sie können keine verwalteten Typen in nativem Code verwenden. Diese Klasse wird für die CLR als Ziel kompiliert, wie dies durch die- `#pragma managed` Direktive vor der Klassen Deklaration angegeben wird. Weitere Informationen zu dieser Direktive finden Sie unter [verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Notieren Sie sich den privaten Member der DatabaseClass-Klasse: `gcroot<DataTable ^> table` . Da Native Typen keine verwalteten Typen enthalten können, `gcroot` ist das Schlüsselwort erforderlich. Weitere Informationen zu `gcroot` finden Sie unter Gewusst [wie: Deklarieren von Handles in](../dotnet/how-to-declare-handles-in-native-types.md)systemeigenen Typen.

Der Rest des Codes in diesem Beispiel ist System eigener C++-Code, wie von der `#pragma unmanaged` vorangehenden-Direktive angegeben `main` . In diesem Beispiel wird eine neue Instanz von DatabaseClass erstellt und die zugehörigen Methoden aufgerufen, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass Unicode-C++ Zeichenfolgen als Werte für die Daten Bank Spalte StringCol übergeben werden. In DatabaseClass werden diese Zeichen folgen mithilfe der Marshallingfunktionen im-Namespace an verwaltete Zeichen folgen gemarshallt <xref:System.Runtime.InteropServices?displayProperty=fullName> . Insbesondere <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> wird die-Methode verwendet, um einen in ein zu Mars Hallen `wchar_t *` <xref:System.String> , und die-Methode <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> wird verwendet, um einen <xref:System.String> in ein zu Mars Hallen `wchar_t *` .

> [!NOTE]
> Der durch zugeordnete Arbeitsspeicher muss aufgehoben <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> werden, indem entweder oder aufgerufen wird <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> `GlobalFree` .

```cpp
// adonet_marshal_string_wide.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(wchar_t *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringUni(
            (IntPtr)stringColValue);
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("StringCol",
            Type::GetType("System.String"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringUni(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a wchar_t *.
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(
                (String ^)rows[i][columnStr]).ToPointer();
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();
    db->AddRow(L"This is string 1.");
    db->AddRow(L"This is string 2.");

    // Now retrieve the rows and display their contents.
    wchar_t *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalUni.
        GlobalFree(values[i]);
    }

    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>Kompilieren des Codes

- Um den Code über die Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei namens "adonet_marshal_string_wide. cpp", und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>Marshalling einer Variante für ADO.net

Veranschaulicht, wie eine native `VARIANT` zu einer Datenbank hinzugefügt wird und wie eine <xref:System.Object?displayProperty=fullName> aus einer Datenbank in eine systemeigene gemarshallt wird `VARIANT` .

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass erstellt, um mit einem ADO.net- <xref:System.Data.DataTable> Objekt zu interagieren. Beachten Sie, dass diese Klasse eine native C++ **`class`** (im Vergleich zu **`ref class`** oder **`value class`** ) ist. Dies ist erforderlich, da wir diese Klasse aus nativem Code verwenden möchten, und Sie können keine verwalteten Typen in nativem Code verwenden. Diese Klasse wird für die CLR als Ziel kompiliert, wie dies durch die- `#pragma managed` Direktive vor der Klassen Deklaration angegeben wird. Weitere Informationen zu dieser Direktive finden Sie unter [verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Notieren Sie sich den privaten Member der DatabaseClass-Klasse: `gcroot<DataTable ^> table` . Da Native Typen keine verwalteten Typen enthalten können, `gcroot` ist das Schlüsselwort erforderlich. Weitere Informationen zu `gcroot` finden Sie unter Gewusst [wie: Deklarieren von Handles in](../dotnet/how-to-declare-handles-in-native-types.md)systemeigenen Typen.

Der Rest des Codes in diesem Beispiel ist System eigener C++-Code, wie von der `#pragma unmanaged` vorangehenden-Direktive angegeben `main` . In diesem Beispiel wird eine neue Instanz von DatabaseClass erstellt und die zugehörigen Methoden aufgerufen, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass Native `VARIANT` Typen als Werte für die Daten Bank Spalte ObjectCol ausgegeben werden. In DatabaseClass werden diese `VARIANT` Typen mithilfe der Marshallingfunktionen, die im-Namespace gefunden werden, an verwaltete Objekte gemarshallt <xref:System.Runtime.InteropServices?displayProperty=fullName> . Insbesondere <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> wird die-Methode verwendet, um einen in ein zu Mars Hallen `VARIANT` <xref:System.Object> , und die-Methode <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> wird verwendet, um eine <xref:System.Object> in eine zu Mars Hallen `VARIANT` .

```cpp
// adonet_marshal_variant.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(VARIANT *objectColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(
            IntPtr(objectColValue));
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",
            Type::GetType("System.Object"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringUni(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed object
            // to a VARIANT.
            Marshal::GetNativeVariantForObject(
                rows[i][columnStr], IntPtr(&values[i]));
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();

    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");
    VARIANT v1;
    v1.vt = VT_BSTR;
    v1.bstrVal = bstr1;
    db->AddRow(&v1);

    int i = 42;
    VARIANT v2;
    v2.vt = VT_I4;
    v2.lVal = i;
    db->AddRow(&v2);

    // Now retrieve the rows and display their contents.
    VARIANT values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"ObjectCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        switch (values[i].vt)
        {
            case VT_BSTR:
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;
                break;
            case VT_I4:
                cout << "ObjectCol: " << values[i].lVal << endl;
                break;
            default:
                break;
        }

    }

    SysFreeString(bstr1);
    delete db;

    return 0;
}
```

```Output
ObjectCol: This is a BSTR in a VARIANT.
ObjectCol: 42
```

### <a name="compiling-the-code"></a>Kompilieren des Codes

- Um den Code über die Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei namens "adonet_marshal_variant. cpp", und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>Mars Hallen eines SAFEARRAY für ADO.net

Veranschaulicht das Hinzufügen einer nativen `SAFEARRAY` zu einer Datenbank und das Mars Hallen eines verwalteten Arrays aus einer Datenbank in eine systemeigene `SAFEARRAY` .

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass erstellt, um mit einem ADO.net- <xref:System.Data.DataTable> Objekt zu interagieren. Beachten Sie, dass diese Klasse eine native C++ **`class`** (im Vergleich zu **`ref class`** oder **`value class`** ) ist. Dies ist erforderlich, da wir diese Klasse aus nativem Code verwenden möchten, und Sie können keine verwalteten Typen in nativem Code verwenden. Diese Klasse wird für die CLR als Ziel kompiliert, wie dies durch die- `#pragma managed` Direktive vor der Klassen Deklaration angegeben wird. Weitere Informationen zu dieser Direktive finden Sie unter [verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Notieren Sie sich den privaten Member der DatabaseClass-Klasse: `gcroot<DataTable ^> table` . Da Native Typen keine verwalteten Typen enthalten können, `gcroot` ist das Schlüsselwort erforderlich. Weitere Informationen zu `gcroot` finden Sie unter Gewusst [wie: Deklarieren von Handles in](../dotnet/how-to-declare-handles-in-native-types.md)systemeigenen Typen.

Der Rest des Codes in diesem Beispiel ist System eigener C++-Code, wie von der `#pragma unmanaged` vorangehenden-Direktive angegeben `main` . In diesem Beispiel wird eine neue Instanz von DatabaseClass erstellt und die zugehörigen Methoden aufgerufen, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass Native `SAFEARRAY` Typen als Werte für die Daten Bank Spalte ArrayIntsCol übergeben werden. In DatabaseClass werden diese `SAFEARRAY` Typen mithilfe der Marshallingfunktionen, die im-Namespace gefunden werden, an verwaltete Objekte gemarshallt <xref:System.Runtime.InteropServices?displayProperty=fullName> . Insbesondere wird die-Methode verwendet, um <xref:System.Runtime.InteropServices.Marshal.Copy%2A> einen `SAFEARRAY` in ein verwaltetes Array von ganzen Zahlen zu Mars Hallen, und die-Methode <xref:System.Runtime.InteropServices.Marshal.Copy%2A> wird verwendet, um ein verwaltetes Array von ganzen Zahlen zu einem zu Mars Hallen `SAFEARRAY` .

```cpp
// adonet_marshal_safearray.cpp
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll
#include <comdef.h>
#include <gcroot.h>
#include <iostream>
using namespace std;

#using <System.Data.dll>
using namespace System;
using namespace System::Data;
using namespace System::Runtime::InteropServices;

#define MAXCOLS 100

#pragma managed
class DatabaseClass
{
public:
    DatabaseClass() : table(nullptr) { }

    void AddRow(SAFEARRAY *arrayIntsColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        int len = arrayIntsColValue->rgsabound[0].cElements;
        array<int> ^arr = gcnew array<int>(len);

        int *pData;
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);
        Marshal::Copy(IntPtr(pData), arr, 0, len);
        SafeArrayUnaccessData(arrayIntsColValue);

        row["ArrayIntsCol"] = arr;
        table->Rows->Add(row);
    }

    void CreateAndPopulateTable()
    {
        // Create a simple DataTable.
        table = gcnew DataTable("SampleTable");

        // Add a column of type String to the table.
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",
            Type::GetType("System.Int32[]"));
        table->Columns->Add(column1);
    }

    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringUni(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed array
            // of Int32s to a SAFEARRAY of type VT_I4.
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);
            int *pData;
            SafeArrayAccessData(values[i], (void **)&pData);
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,
                IntPtr(pData), 10);
            SafeArrayUnaccessData(values[i]);
        }

        return len;
    }

private:
    // Using gcroot, you can use a managed type in
    // a native class.
    gcroot<DataTable ^> table;
};

#pragma unmanaged
int main()
{
    // Create a table and add a few rows to it.
    DatabaseClass *db = new DatabaseClass();
    db->CreateAndPopulateTable();

    // Create a standard array.
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

    // Create a SAFEARRAY.
    SAFEARRAY *psa;
    psa = SafeArrayCreateVector(VT_I4, 0, 10);

    // Copy the data from the original array to the SAFEARRAY.
    int *pData;
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);
    memcpy(pData, &originalArray, 40);
    SafeArrayUnaccessData(psa);
    db->AddRow(psa);

    // Now retrieve the rows and display their contents.
    SAFEARRAY *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"ArrayIntsCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        int *pData;
        SafeArrayAccessData(values[i], (void **)&pData);
        for (int j = 0; j < 10; j++)
        {
            cout << pData[j] << " ";
        }
        cout << endl;
        SafeArrayUnaccessData(values[i]);

        // Deallocate the memory allocated using
        // SafeArrayCreateVector.
        SafeArrayDestroy(values[i]);
    }

    SafeArrayDestroy(psa);
    delete db;

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="compiling-the-code"></a>Kompilieren des Codes

- Um den Code über die Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei namens "adonet_marshal_safearray. cpp", und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework-Sicherheit

Informationen zu Sicherheitsproblemen, die ADO.net betreffen, finden Sie unter [Sichern von ADO.NET-Anwendungen](/dotnet/framework/data/adonet/securing-ado-net-applications).

## <a name="related-sections"></a>Verwandte Abschnitte

|`Section`|BESCHREIBUNG|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Bietet eine Übersicht über ADO.net, eine Reihe von Klassen, die Datenzugriffs Dienste für .NET-Programmierer verfügbar machen.|

## <a name="see-also"></a>Weitere Informationen

[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Native und .NET-Interoperabilität](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Interoperabilität](/dotnet/framework/interop/index)
