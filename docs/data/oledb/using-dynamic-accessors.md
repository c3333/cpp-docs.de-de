---
title: Verwenden von dynamischen Accessoren
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: eea1c6199fed5a4e6e331c1c76f34b96090b709a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509415"
---
# <a name="using-dynamic-accessors"></a>Verwenden von dynamischen Accessoren

Dynamische Accessoren ermöglichen den Zugriff auf eine Datenquelle, wenn Sie das Datenbankschema (zugrunde liegende Struktur) nicht kennen. Die OLE DB Vorlagen Bibliothek bietet verschiedene Klassen, die Ihnen helfen.

Das [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) -Beispiel veranschaulicht, wie die dynamischen Accessorklassen zum Anzeigen von Spalten Informationen und zum dynamischen Erstellen von Accessoren verwendet werden.

## <a name="using-cdynamicaccessor"></a>Verwenden von CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ermöglicht den Zugriff auf eine Datenquelle, wenn Sie das Datenbankschema (die zugrunde liegende Struktur der Datenbank) nicht kennen. `CDynamicAccessor` Methoden erhalten Spalten Informationen, wie z. b. Spaltennamen, Anzahl und Datentyp. Mit diesen Spalten Informationen können Sie einen Accessor dynamisch zur Laufzeit erstellen. Die Spalten Informationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Verwenden Sie die [GetValue](./cdynamicaccessor-class.md#getvalue) -Methode, um Daten aus dem Puffer zu erhalten.

## <a name="example"></a>Beispiel

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>Verwenden von CDynamicStringAccessor

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) funktioniert wie [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), außer auf eine wichtige Weise. Während `CDynamicAccessor` Daten in dem vom Anbieter gemeldeten systemeigenen Format anfordert, `CDynamicStringAccessor` fordert den Anbieter auf, alle Daten, auf die vom Datenspeicher zugegriffen wird, als Zeichen folgen Daten abzurufen. Der Prozess ist besonders nützlich für einfache Aufgaben, bei denen keine Berechnung von Werten im Datenspeicher erforderlich ist, z. b. das Anzeigen oder Drucken der Inhalte des Daten Stores.

Verwenden `CDynamicStringAccessor` Sie-Methoden, um Spalten Informationen zu erhalten. Mit diesen Spalten Informationen können Sie einen Accessor dynamisch zur Laufzeit erstellen. Die Spalten Informationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Verwenden Sie [CDynamicStringAccessor:: GetString](./cdynamicstringaccessor-class.md#getstring) , um Daten aus dem Puffer zu erhalten, oder speichern Sie Sie mithilfe von [CDynamicStringAccessor:: SetString](./cdynamicstringaccessor-class.md#setstring)im Puffer.

## <a name="example"></a>Beispiel

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>Verwenden von CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) ähnelt [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), mit dem Unterschied, dass `CDynamicParameterAccessor` die durch Aufrufen der [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) -Schnittstelle festzulegenden Parameterinformationen erhält. Der Anbieter muss `ICommandWithParameters` unterstützen, damit der Consumer diese Klasse verwenden kann.

Die Parameterinformationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Verwenden Sie [CDynamicParameterAccessor:: GetParam](./cdynamicparameteraccessor-class.md#getparam) und [CDynamicParameterAccessor:: GetParamType](./cdynamicparameteraccessor-class.md#getparamtype), um Parameterdaten aus dem Puffer zu erhalten.

Ein Beispiel für die Verwendung dieser Klasse zum Ausführen einer SQL Server gespeicherten Prozedur und zum Ermitteln der Ausgabeparameter Werte finden Sie im Beispielcode [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) im [Microsoft vcsamples](https://github.com/Microsoft/VCSamples) -Repository auf GitHub.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Accessoren](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor-Klasse](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor-Klasse](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor-Klasse](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer-Beispiel](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
