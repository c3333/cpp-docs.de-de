---
title: Windows-Vorgänge (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: 99fce804ad30e01bdbaa99b1636a5238ff535f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371770"
---
# <a name="windows-operations-ccli"></a>Windows-Vorgänge (C++/CLI)

Veranschaulicht verschiedene Windows-spezifische Aufgaben mithilfe des Windows SDK.

In den folgenden Themen werden verschiedene Windows-Vorgänge veranschaulicht, die mit dem Windows SDK mit Visual C++ ausgeführt werden.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a>Stellen Sie fest, ob Shutdown gestartet wurde

Im folgenden Codebeispiel wird veranschaulicht, wie Sie ermitteln, ob die Anwendung oder .NET Framework derzeit beendet wird. Dies ist nützlich für den Zugriff auf statische Elemente in .NET Framework, da diese Konstrukte während des Herunterfahrens vom System abgeschlossen werden und nicht zuverlässig verwendet werden können. Wenn Sie <xref:System.Environment.HasShutdownStarted%2A> zuerst die Eigenschaft überprüfen, können Sie potenzielle Fehler vermeiden, indem Sie nicht auf diese Elemente zugreifen.

### <a name="example"></a>Beispiel

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a>Bestimmen des interaktiven Benutzerstatus

Im folgenden Codebeispiel wird veranschaulicht, wie Sie ermitteln, ob Code in einem benutzerinteraktiven Kontext ausgeführt wird. Wenn <xref:System.Environment.UserInteractive%2A> false ist, wird der Code als Dienstprozess oder innerhalb einer Webanwendung ausgeführt.

### <a name="example"></a>Beispiel

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a>Lesen von Daten aus der Windows-Registrierung

Im folgenden Codebeispiel wird der <xref:Microsoft.Win32.Registry.CurrentUser>-Schlüssel verwendet, um Daten aus der Windows-Registrierung zu lesen. Zuerst werden die Unterschlüssel mit der <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> Methode aufgezählt, und dann <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> wird der Unterschlüssel Identitäten mit der Methode geöffnet. Jeder Unterschlüssel wird wie ein Stammschlüssel durch die <xref:Microsoft.Win32.RegistryKey>-Klasse dargestellt. Schließlich werden mit dem neuen <xref:Microsoft.Win32.RegistryKey>-Objekt die Schlüssel/Wert-Paare aufgelistet.

### <a name="example"></a>Beispiel

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>Bemerkungen

Die <xref:Microsoft.Win32.Registry>-Klasse ist lediglich ein Container für statische Instanzen von <xref:Microsoft.Win32.RegistryKey>. Jede Instanz stellt einen Stammregistrierungsknoten dar. Die Instanzen sind <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> und <xref:Microsoft.Win32.Registry.Users>.

Die Objekte innerhalb der <xref:Microsoft.Win32.Registry>-Klasse sind nicht nur statisch, sondern auch schreibgeschützt. Darüber hinaus sind Instanzen der <xref:Microsoft.Win32.RegistryKey>-Klasse, die für den Zugriff auf den Inhalt der Registrierungsobjekte erstellt wurden, ebenfalls schreibgeschützt. Ein Beispiel für das Überschreiben dieses Verhaltens finden Sie unter [Gewusst wie: Schreiben von Daten in die Windows-Registrierung (C++/CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).

In der <xref:Microsoft.Win32.Registry>-Klasse stehen zwei weitere Objekte zur Verfügung: <xref:Microsoft.Win32.Registry.DynData> und <xref:Microsoft.Win32.Registry.PerformanceData>. Bei beiden Objekten handelt es sich um Instanzen der <xref:Microsoft.Win32.RegistryKey>-Klasse. Das <xref:Microsoft.Win32.Registry.DynData> Objekt enthält dynamische Registrierungsinformationen, die nur in Windows 98 und Windows Me unterstützt werden. Das <xref:Microsoft.Win32.Registry.PerformanceData>-Objekt dient dem Zugriff auf Informationen zu Leistungsindikatoren für Anwendungen, die das Leistungsüberwachungssystem von Windows verwenden. Der <xref:Microsoft.Win32.Registry.PerformanceData> Knoten stellt Informationen dar, die nicht tatsächlich in der Registrierung gespeichert sind und daher nicht mit Regedit.exe angezeigt werden können.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a>Lesen von Windows-Leistungsindikatoren

Einige Anwendungen und Windows-Subsysteme machen Leistungsdaten über das Windows-Leistungssystem verfügbar. Auf diese Leistungsindikatoren kann <xref:System.Diagnostics.PerformanceCounterCategory> <xref:System.Diagnostics.PerformanceCounter> mithilfe der und-Klassen zugegriffen werden, die sich im <xref:System.Diagnostics?displayProperty=fullName> Namespace befinden.

Im folgenden Codebeispiel werden diese Klassen zum Abrufen und Anzeigen eines Leistungsindikators verwendet, der von Windows aktualisiert wird, um den Prozentsatz der Zeit anzugeben, die der Prozessor ausgelastet ist.

> [!NOTE]
> Für dieses Beispiel benötigen Sie Administratorrechte, um es unter Windows Vista auszuführen.

### <a name="example"></a>Beispiel

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a>Abrufen von Text aus der Zwischenablage

Im folgenden Codebeispiel <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> wird die Memberfunktion verwendet, um einen Zeiger auf die <xref:System.Windows.Forms.IDataObject> Schnittstelle zurückzugeben. Diese Schnittstelle kann dann nach dem Format der Daten abgefragt und zum Abrufen der tatsächlichen Daten verwendet werden.

### <a name="example"></a>Beispiel

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a>Abrufen des aktuellen Benutzernamens

Das folgende Codebeispiel veranschaulicht den Abruf des aktuellen Benutzernamens (der Name des bei Windows angemeldeten Benutzers). Der Name wird <xref:System.Environment.UserName%2A> in der Zeichenfolge gespeichert, die im <xref:System.Environment> Namespace definiert ist.

### <a name="example"></a>Beispiel

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a>Abrufen der .NET Framework-Version

Im folgenden Codebeispiel wird veranschaulicht, wie die Version von <xref:System.Environment.Version%2A> .NET Framework mit der <xref:System.Version> Eigenschaft bestimmt wird, bei der es sich um einen Zeiger auf ein Objekt handelt, das die Versionsinformationen enthält.

### <a name="example"></a>Beispiel

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a>Abrufen des lokalen Computernamens

Im folgenden Codebeispiel wird der Abruf des lokalen Computernamens (der Name des Computers, wie er in einem Netzwerk angezeigt wird) veranschaulicht. Sie können dies <xref:System.Environment.MachineName%2A> erreichen, indem Sie <xref:System.Environment> die Zeichenfolge abrufen, die im Namespace definiert ist.

### <a name="example"></a>Beispiel

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a>Abrufen der Windows-Version

Im folgenden Codebeispiel wird veranschaulicht, wie die Plattform- und Versionsinformationen des aktuellen Betriebssystems abgerufen werden. Diese Informationen werden <xref:System.Environment.OSVersion%2A?displayProperty=fullName> in der Eigenschaft gespeichert und bestehen aus einer Enumeration, die die Windows-Version in groben Zügen beschreibt, und einem <xref:System.Environment.Version%2A> Objekt, das den genauen Build des Betriebssystems enthält.

### <a name="example"></a>Beispiel

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a>Abruf der seit dem Start verstrichenen Zeit

Im folgenden Codebeispiel wird veranschaulicht, wie Sie die Tickanzahl oder die Anzahl der Millisekunden bestimmen, die seit dem Start von Windows verstrichen sind. Dieser Wert wird <xref:System.Environment.TickCount%2A?displayProperty=fullName> im Member gespeichert und, da es sich um einen 32-Bit-Wert handelt, ungefähr alle 24,9 Tage auf Null zurückgesetzt.

### <a name="example"></a>Beispiel

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a>Speichern von Text in der Zwischenablage

Im folgenden Codebeispiel <xref:System.Windows.Forms.Clipboard> wird das <xref:System.Windows.Forms> im Namespace definierte Objekt zum Speichern einer Zeichenfolge verwendet. Dieses Objekt stellt zwei <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>Memberfunktionen bereit: und . Die Daten werden in der Zwischenablage <xref:System.Object> <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>gespeichert, indem jedes von abgeleitete Objekt an gesendet wird.

### <a name="example"></a>Beispiel

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a>Schreiben von Daten in die Windows-Registrierung

Im folgenden Codebeispiel <xref:Microsoft.Win32.Registry.CurrentUser> wird der Schlüssel verwendet, <xref:Microsoft.Win32.RegistryKey> um eine beschreibbare Instanz der Klasse zu erstellen, die dem **Softwareschlüssel** entspricht. Anschließend wird die <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>-Methode verwendet, um einen neuen Schlüssel zu erstellen und Schlüssel/Wert-Paare hinzuzufügen.

### <a name="example"></a>Beispiel

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>Bemerkungen

Sie können .NET Framework verwenden, um <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> auf die Registrierung mit <xref:Microsoft.Win32> den und-Klassen zuzugreifen, die beide im Namespace definiert sind. Die **Registry-Klasse** ist ein Container <xref:Microsoft.Win32.RegistryKey> für statische Instanzen der Klasse. Jede Instanz stellt einen Stammregistrierungsknoten dar. Die Instanzen sind <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> und <xref:Microsoft.Win32.Registry.Users>.

## <a name="related-sections"></a>Verwandte Abschnitte

<xref:System.Environment>

## <a name="see-also"></a>Siehe auch

[.NET Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
