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
ms.openlocfilehash: 35633449c4c01f5c103dcd54b81c0d6aa7c08cdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364408"
---
# <a name="data-access-using-adonet-ccli"></a>Datenzugriff mit ADO.NET (C++/CLI)

ADO.NET ist die .NET Framework-API für den Datenzugriff und bietet Leistung und Benutzerfreundlichkeit, die von früheren Datenzugriffslösungen nicht erreicht wurden. In diesem Abschnitt werden einige der Probleme beschrieben, die ADO.NET betreffen, die für Visual C++-Benutzer eindeutig sind, z. B. das Marshallen systemeigener Typen.

ADO.NET läuft unter der Common Language Runtime (CLR). Daher muss jede Anwendung, die mit ADO.NET interagiert, auch auf die CLR abzielen. Dies bedeutet jedoch nicht, dass systemeigene Anwendungen ADO.NET nicht verwenden können. In diesen Beispielen wird veranschaulicht, wie sie mit einer ADO.NET Datenbank aus systemeigenem Code interagieren.

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>Marshal ANSI Strings für ADO.NET

Veranschaulicht, wie einer Datenbank`char *`eine systemeigene Zeichenfolge ( <xref:System.String?displayProperty=fullName> ) hinzugefügt wird und wie eine aus einer Datenbank zu einer systemeigenen Zeichenfolge gemarshallt wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass <xref:System.Data.DataTable> erstellt, um mit einem ADO.NET Objekt zu interagieren. Beachten Sie, dass es sich `class` bei dieser `ref class` Klasse `value class`um ein systemeigenes C++ handelt (im Vergleich zu einem oder ). Dies ist erforderlich, da wir diese Klasse aus systemeigenem Code verwenden möchten und Sie keine verwalteten Typen in systemeigenem Code verwenden können. Diese Klasse wird für die CLR erstellt, wie `#pragma managed` die Direktive vor der Klassendeklaration zeigt. Weitere Informationen zu dieser Direktive finden Sie unter [Verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Beachten Sie den privaten Member `gcroot<DataTable ^> table`der DatabaseClass-Klasse: . Da systemeigene Typen keine `gcroot` verwalteten Typen enthalten können, ist das Schlüsselwort erforderlich. Weitere Informationen `gcroot`zu finden Sie unter [Gewusst wie: Erklären von Handles in systemeigenen Typen](../dotnet/how-to-declare-handles-in-native-types.md).

Der Rest des Codes in diesem Beispiel ist systemeigener C++-Code, wie die `#pragma unmanaged` vorangehende `main`Direktive zeigt. In diesem Beispiel erstellen wir eine neue Instanz von DatabaseClass und rufen deren Methoden auf, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass systemeigene C++-Zeichenfolgen als Werte für die Datenbankspalte StringCol übergeben werden. Innerhalb von DatabaseClass werden diese Zeichenfolgen mithilfe der im <xref:System.Runtime.InteropServices?displayProperty=fullName> Namespace gefundenen Marshallingfunktionalität in verwaltete Zeichenfolgen gemarshallt. Insbesondere wird <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> die Methode verwendet, `char *` <xref:System.String>um a <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> zu a zu <xref:System.String> marshallen, und die Methode wird verwendet, um a zu einer `char *`zu marshallen.

> [!NOTE]
> Der von <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> ihnen zugewiesene Speicher <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> muss `GlobalFree`durch Aufrufen von entweder oder zugewiesen werden.

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

- Um den Code aus der Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei mit dem Namen adonet_marshal_string_native.cpp, und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>Marshal BSTR Strings für ADO.NET

Veranschaulicht, wie einer Datenbank`BSTR`eine COM-Zeichenfolge ( <xref:System.String?displayProperty=fullName> ) hinzugefügt wird `BSTR`und wie eine aus einer Datenbank zu einer gemarshallt wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass <xref:System.Data.DataTable> erstellt, um mit einem ADO.NET Objekt zu interagieren. Beachten Sie, dass es sich `class` bei dieser `ref class` Klasse `value class`um ein systemeigenes C++ handelt (im Vergleich zu einem oder ). Dies ist erforderlich, da wir diese Klasse aus systemeigenem Code verwenden möchten und Sie keine verwalteten Typen in systemeigenem Code verwenden können. Diese Klasse wird für die CLR erstellt, wie `#pragma managed` die Direktive vor der Klassendeklaration zeigt. Weitere Informationen zu dieser Direktive finden Sie unter [Verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Beachten Sie den privaten Member `gcroot<DataTable ^> table`der DatabaseClass-Klasse: . Da systemeigene Typen keine `gcroot` verwalteten Typen enthalten können, ist das Schlüsselwort erforderlich. Weitere Informationen `gcroot`zu finden Sie unter [Gewusst wie: Erklären von Handles in systemeigenen Typen](../dotnet/how-to-declare-handles-in-native-types.md).

Der Rest des Codes in diesem Beispiel ist systemeigener C++-Code, wie die `#pragma unmanaged` vorangehende `main`Direktive zeigt. In diesem Beispiel erstellen wir eine neue Instanz von DatabaseClass und rufen deren Methoden auf, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass COM-Zeichenfolgen als Werte für die Datenbankspalte StringCol übergeben werden. Innerhalb von DatabaseClass werden diese Zeichenfolgen mithilfe der im <xref:System.Runtime.InteropServices?displayProperty=fullName> Namespace gefundenen Marshallingfunktionalität in verwaltete Zeichenfolgen gemarshallt. Insbesondere wird <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> die Methode verwendet, `BSTR` <xref:System.String>um a <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> zu a zu <xref:System.String> marshallen, und die Methode wird verwendet, um a zu einer `BSTR`zu marshallen.

> [!NOTE]
> Der von <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> ihnen zugewiesene Speicher <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> muss `SysFreeString`durch Aufrufen von entweder oder zugewiesen werden.

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

- Um den Code aus der Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei mit dem Namen adonet_marshal_string_native.cpp, und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>Marshal Unicode Strings für ADO.NET

Veranschaulicht, wie eine systemeigene`wchar_t *`Unicode-Zeichenfolge ( ) <xref:System.String?displayProperty=fullName> zu einer Datenbank hinzugefügt wird und wie eine aus einer Datenbank zu einer systemeigenen Unicode-Zeichenfolge gemarshallt wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass <xref:System.Data.DataTable> erstellt, um mit einem ADO.NET Objekt zu interagieren. Beachten Sie, dass es sich `class` bei dieser `ref class` Klasse `value class`um ein systemeigenes C++ handelt (im Vergleich zu einem oder ). Dies ist erforderlich, da wir diese Klasse aus systemeigenem Code verwenden möchten und Sie keine verwalteten Typen in systemeigenem Code verwenden können. Diese Klasse wird für die CLR erstellt, wie `#pragma managed` die Direktive vor der Klassendeklaration zeigt. Weitere Informationen zu dieser Direktive finden Sie unter [Verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Beachten Sie den privaten Member `gcroot<DataTable ^> table`der DatabaseClass-Klasse: . Da systemeigene Typen keine `gcroot` verwalteten Typen enthalten können, ist das Schlüsselwort erforderlich. Weitere Informationen `gcroot`zu finden Sie unter [Gewusst wie: Erklären von Handles in systemeigenen Typen](../dotnet/how-to-declare-handles-in-native-types.md).

Der Rest des Codes in diesem Beispiel ist systemeigener C++-Code, wie die `#pragma unmanaged` vorangehende `main`Direktive zeigt. In diesem Beispiel erstellen wir eine neue Instanz von DatabaseClass und rufen deren Methoden auf, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass Unicode C++-Zeichenfolgen als Werte für die Datenbankspalte StringCol übergeben werden. Innerhalb von DatabaseClass werden diese Zeichenfolgen mithilfe der im <xref:System.Runtime.InteropServices?displayProperty=fullName> Namespace gefundenen Marshallingfunktionalität in verwaltete Zeichenfolgen gemarshallt. Insbesondere wird <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> die Methode verwendet, `wchar_t *` <xref:System.String>um a <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> zu a zu <xref:System.String> marshallen, und die Methode wird verwendet, um a zu einer `wchar_t *`zu marshallen.

> [!NOTE]
> Der von <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> ihnen zugewiesene Speicher <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> muss `GlobalFree`durch Aufrufen von entweder oder zugewiesen werden.

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

- Um den Code aus der Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei mit dem Namen adonet_marshal_string_wide.cpp, und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>Marschall a VARIANT für ADO.NET

Veranschaulicht, wie eine `VARIANT` Systemazuzmutter zu <xref:System.Object?displayProperty=fullName> einer Datenbank hinzugefügt `VARIANT`und eine aus einer Datenbank zu einer systemeigenen gemarshallt wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass <xref:System.Data.DataTable> erstellt, um mit einem ADO.NET Objekt zu interagieren. Beachten Sie, dass es sich `class` bei dieser `ref class` Klasse `value class`um ein systemeigenes C++ handelt (im Vergleich zu einem oder ). Dies ist erforderlich, da wir diese Klasse aus systemeigenem Code verwenden möchten und Sie keine verwalteten Typen in systemeigenem Code verwenden können. Diese Klasse wird für die CLR erstellt, wie `#pragma managed` die Direktive vor der Klassendeklaration zeigt. Weitere Informationen zu dieser Direktive finden Sie unter [Verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Beachten Sie den privaten Member `gcroot<DataTable ^> table`der DatabaseClass-Klasse: . Da systemeigene Typen keine `gcroot` verwalteten Typen enthalten können, ist das Schlüsselwort erforderlich. Weitere Informationen `gcroot`zu finden Sie unter [Gewusst wie: Erklären von Handles in systemeigenen Typen](../dotnet/how-to-declare-handles-in-native-types.md).

Der Rest des Codes in diesem Beispiel ist systemeigener C++-Code, wie die `#pragma unmanaged` vorangehende `main`Direktive zeigt. In diesem Beispiel erstellen wir eine neue Instanz von DatabaseClass und rufen deren Methoden auf, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass systemeigene `VARIANT` Typen als Werte für die Datenbankspalte ObjectCol übergeben werden. Innerhalb von DatabaseClass werden diese `VARIANT` Typen mithilfe der im <xref:System.Runtime.InteropServices?displayProperty=fullName> Namespace gefundenen Marshallingfunktionalität zu verwalteten Objekten gemarshallt. Insbesondere wird <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> die Methode verwendet, `VARIANT` <xref:System.Object>um a <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> zu einem zu <xref:System.Object> marshallen, und die Methode wird verwendet, um eine zu einer `VARIANT`zu marshallen.

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

- Um den Code aus der Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei mit dem Namen adonet_marshal_variant.cpp, und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>Marshall a SAFEARRAY für ADO.NET

Veranschaulicht, wie eine `SAFEARRAY` systemeigene Datei zu einer Datenbank hinzugefügt und `SAFEARRAY`ein verwaltetes Array aus einer Datenbank zu einem systemeigenen gemarshallt wird.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Klasse DatabaseClass <xref:System.Data.DataTable> erstellt, um mit einem ADO.NET Objekt zu interagieren. Beachten Sie, dass es sich `class` bei dieser `ref class` Klasse `value class`um ein systemeigenes C++ handelt (im Vergleich zu einem oder ). Dies ist erforderlich, da wir diese Klasse aus systemeigenem Code verwenden möchten und Sie keine verwalteten Typen in systemeigenem Code verwenden können. Diese Klasse wird für die CLR erstellt, wie `#pragma managed` die Direktive vor der Klassendeklaration zeigt. Weitere Informationen zu dieser Direktive finden Sie unter [Verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md).

Beachten Sie den privaten Member `gcroot<DataTable ^> table`der DatabaseClass-Klasse: . Da systemeigene Typen keine `gcroot` verwalteten Typen enthalten können, ist das Schlüsselwort erforderlich. Weitere Informationen `gcroot`zu finden Sie unter [Gewusst wie: Erklären von Handles in systemeigenen Typen](../dotnet/how-to-declare-handles-in-native-types.md).

Der Rest des Codes in diesem Beispiel ist systemeigener C++-Code, wie die `#pragma unmanaged` vorangehende `main`Direktive zeigt. In diesem Beispiel erstellen wir eine neue Instanz von DatabaseClass und rufen deren Methoden auf, um eine Tabelle zu erstellen und einige Zeilen in der Tabelle aufzufüllen. Beachten Sie, dass systemeigene `SAFEARRAY` Typen als Werte für die Datenbankspalte ArrayIntsCol übergeben werden. Innerhalb von DatabaseClass werden diese `SAFEARRAY` Typen mithilfe der im <xref:System.Runtime.InteropServices?displayProperty=fullName> Namespace gefundenen Marshallingfunktionalität zu verwalteten Objekten gemarshallt. Insbesondere wird <xref:System.Runtime.InteropServices.Marshal.Copy%2A> die Methode verwendet, um a `SAFEARRAY` zu einem verwalteten <xref:System.Runtime.InteropServices.Marshal.Copy%2A> Array von Ganzzahlen zu marshallen, `SAFEARRAY`und die Methode wird verwendet, um ein verwaltetes Array von Ganzzahlen zu einem zu marshallen.

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

- Um den Code aus der Befehlszeile zu kompilieren, speichern Sie das Codebeispiel in einer Datei mit dem Namen adonet_marshal_safearray.cpp, und geben Sie die folgende Anweisung ein:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>.NET Framework-Sicherheit

Informationen zu Sicherheitsproblemen im Zusammenhang mit ADO.NET finden Sie unter [Sichern ADO.NET Anwendungen](/dotnet/framework/data/adonet/securing-ado-net-applications).

## <a name="related-sections"></a>Verwandte Abschnitte

|`Section`|BESCHREIBUNG|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Bietet einen Überblick über ADO.NET, eine Gruppe von Klassen, die Datenzugriffsdienste für den .NET-Programmierer verfügbar machen.|

## <a name="see-also"></a>Siehe auch

[.NET Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Interoperabilität von nativem Code und .NET](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Interoperabilität](/dotnet/framework/interop/index)
