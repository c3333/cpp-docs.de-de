---
title: Dateiverarbeitung und I-O (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
ms.openlocfilehash: a1cfdc4239506f22368753d8c37765e550d9b835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508931"
---
# <a name="file-handling-and-io-ccli"></a>Dateibehandlung und E/A (C++/CLI)

Veranschaulicht verschiedene Dateioperationen mit .NET Framework.

In den folgenden Themen wird die Verwendung von Klassen, die im <xref:System.IO>-Namespace definiert sind, zur Durchführung verschiedener Dateioperationen erläutert.

## <a name="enumerate-files-in-a-directory"></a><a name="enumerate"></a> Dateien in einem Verzeichnis aufzählen

Im folgenden Codebeispiel wird veranschaulicht, wie eine Liste von Dateien in einem Verzeichnis abgerufen wird. Zusätzlich werden die Unterverzeichnisse aufgelistet. Im folgenden Beispiel werden die <xref:System.IO.Directory.GetFiles%2A><xref:System.IO.Directory.GetFiles%2A>-Methode und <xref:System.IO.Directory.GetDirectories%2A>-Methode verwendet, um den Inhalt des Verzeichnisses C:\Windows anzuzeigen.

### <a name="example"></a>Beispiel

```cpp
// enum_files.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ folder = "C:\\";
   array<String^>^ dir = Directory::GetDirectories( folder );
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);
   for (int i=0; i<dir->Length; i++)
      Console::WriteLine(dir[i]);

   array<String^>^ file = Directory::GetFiles( folder );
   Console::WriteLine("--== Files inside '{0}' ==--", folder);
   for (int i=0; i<file->Length; i++)
      Console::WriteLine(file[i]);

   return 0;
}
```

## <a name="monitor-file-system-changes"></a><a name="monitor"></a> Überwachen von Datei System Änderungen

Im folgenden Codebeispiel <xref:System.IO.FileSystemWatcher> wird verwendet, um Ereignisse für Ereignisse zu registrieren, die Dateien entsprechen, die erstellt, geändert, gelöscht oder umbenannt werden. Anstatt ein Verzeichnis regelmäßig auf Änderungen an Dateien abzufragen, können Sie die-Klasse verwenden, <xref:System.IO.FileSystemWatcher> um Ereignisse auszulösen, wenn eine Änderung erkannt wird.

### <a name="example"></a>Beispiel

```cpp
// monitor_fs.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::IO;

ref class FSEventHandler
{
public:
    void OnChanged (Object^ source, FileSystemEventArgs^ e)
    {
        Console::WriteLine("File: {0} {1}",
               e->FullPath, e->ChangeType);
    }
    void OnRenamed(Object^ source, RenamedEventArgs^ e)
    {
        Console::WriteLine("File: {0} renamed to {1}",
                e->OldFullPath, e->FullPath);
    }
};

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();

   if(args->Length < 2)
   {
      Console::WriteLine("Usage: Watcher.exe <directory>");
      return -1;
   }

   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );
   fsWatcher->Path = args[1];
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>
              (NotifyFilters::FileName |
               NotifyFilters::Attributes |
               NotifyFilters::LastAccess |
               NotifyFilters::LastWrite |
               NotifyFilters::Security |
               NotifyFilters::Size );

    FSEventHandler^ handler = gcnew FSEventHandler();
    fsWatcher->Changed += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Created += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Deleted += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Renamed += gcnew RenamedEventHandler(
            handler, &FSEventHandler::OnRenamed);

    fsWatcher->EnableRaisingEvents = true;

    Console::WriteLine("Press Enter to quit the sample.");
    Console::ReadLine( );
}
```

## <a name="read-a-binary-file"></a><a name="read_binary"></a> Eine Binärdatei lesen

Im folgenden Codebeispiel wird das Lesen von Binärdaten aus einer Datei, mithilfe von zwei Klassen aus dem <xref:System.IO?displayProperty=fullName>-Namespace: <xref:System.IO.FileStream> und <xref:System.IO.BinaryReader> verdeutlicht. <xref:System.IO.FileStream> repräsentiert die eigentliche Datei. <xref:System.IO.BinaryReader> stellt eine Schnittstelle zum Stream für den Binärzugriff bereit.

Im Codebeispiel wird eine Datei namens "data.bin" gelesen, in der ganze Zahlen im Binärformat enthalten sind. Weitere Informationen zu dieser Art von Datei finden Sie unter Gewusst [wie: Schreiben einer Binärdatei (C++/CLI)](#write_binary).

### <a name="example"></a>Beispiel

```cpp
// binary_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "data.bin";
   try
   {
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);
      BinaryReader^ br = gcnew BinaryReader(fs);

      Console::WriteLine("contents of {0}:", fileName);
      while (br->BaseStream->Position < br->BaseStream->Length)
         Console::WriteLine(br->ReadInt32().ToString());

      fs->Close( );
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("File '{0}' not found", fileName);
      else
         Console::WriteLine("Exception: ({0})", e);
      return -1;
   }
   return 0;
}
```

## <a name="read-a-text-file"></a><a name="read_text"></a> Textdatei lesen

Im folgenden Codebeispiel wird veranschaulicht, wie eine Textdatei geöffnet und dann zeilenweise mithilfe der <xref:System.IO.StreamReader>-Klasse gelesen wird, die im <xref:System.IO?displayProperty=fullName>-Namespace definiert ist. Mit einer Instanz dieser Klasse wird eine Textdatei geöffnet und anschließend jede Zeile mithilfe der <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>-Methode abgerufen.

In diesem Codebeispiel wird eine Datei mit dem Namen textfile.txt gelesen, die Text enthält. Weitere Informationen zu dieser Art von Datei finden Sie unter Gewusst [wie: Schreiben einer Textdatei (C++/CLI)](#write_text).

### <a name="example"></a>Beispiel

```cpp
// text_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";
   try
   {
      Console::WriteLine("trying to open file {0}...", fileName);
      StreamReader^ din = File::OpenText(fileName);

      String^ str;
      int count = 0;
      while ((str = din->ReadLine()) != nullptr)
      {
         count++;
         Console::WriteLine("line {0}: {1}", count, str );
      }
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("file '{0}' not found", fileName);
      else
         Console::WriteLine("problem reading file '{0}'", fileName);
   }

   return 0;
}
```

## <a name="retrieve-file-information"></a><a name="retrieve"></a> Abrufen von Dateiinformationen

Im folgenden Codebeispiel wird die <xref:System.IO.FileInfo>-Klasse erläutert. Wenn der Name einer Datei bekannt ist, können Sie diese Klasse verwenden, um Informationen über die Datei abzurufen, z. B. Dateigröße, Verzeichnis, vollständiger Name, Datum und Uhrzeit der Erstellung sowie der letzten Änderung.

Mit diesem Code werden Dateiinformationen für Notepad.exe abgerufen.

### <a name="example"></a>Beispiel

```cpp
// file_info.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();
   if (args->Length < 2)
   {
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");
      return -1;
   }

   FileInfo^ fi = gcnew FileInfo( args[1] );

   Console::WriteLine("file size: {0}", fi->Length );

   Console::Write("File creation date:  ");
   Console::Write(fi->CreationTime.Month.ToString());
   Console::Write(".{0}", fi->CreationTime.Day.ToString());
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());

   Console::Write("Last access date:  ");
   Console::Write(fi->LastAccessTime.Month.ToString());
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());

   return 0;
}
```

## <a name="write-a-binary-file"></a><a name="write_binary"></a> Schreiben einer Binärdatei

Im folgenden Codebeispiel wird das Schreiben von Binärdaten in eine Datei veranschaulicht. Zwei Klassen des <xref:System.IO>-Namespace werden verwendet: <xref:System.IO.FileStream> und <xref:System.IO.BinaryWriter>. <xref:System.IO.FileStream> repräsentiert die eigentliche Datei, während <xref:System.IO.BinaryWriter> eine Schnittstelle zum Stream für den Binärzugriff bereitstellt.

Im folgenden Codebeispiel wird eine Datei erzeugt, die ganze Zahlen im Binärformat enthält. Diese Datei kann mit dem Code in Gewusst [wie: Lesen einer Binärdatei (C++/CLI)](#read_binary)gelesen werden.

### <a name="example"></a>Beispiel

```cpp
// binary_write.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   array<Int32>^ data = {1, 2, 3, 10000};

   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);
   BinaryWriter^ w = gcnew BinaryWriter(fs);

   try
   {
      Console::WriteLine("writing data to file:");
      for (int i=0; i<data->Length; i++)
      {
         Console::WriteLine(data[i]);
         w->Write(data[i]);
      }
   }
   catch (Exception^)
   {
     Console::WriteLine("data could not be written");
     fs->Close();
     return -1;
   }

   fs->Close();
   return 0;
}
```

## <a name="write-a-text-file"></a><a name="write_text"></a> Schreiben einer Textdatei

Im folgenden Codebeispiel wird veranschaulicht, wie eine Textdatei erstellt und in diese mithilfe der im <xref:System.IO.StreamWriter>-Namespace definierten <xref:System.IO>-Klasse geschrieben wird. Der Name der zu erstellenden Datei wird vom <xref:System.IO.StreamWriter>-Konstruktor übernommen. Wenn die Datei existiert, wird sie überschrieben (außer wenn Sie True als zweites <xref:System.IO.StringWriter>-Konstruktorargument übergeben).

Die Datei wird dann mithilfe der Funktionen <xref:System.IO.StreamWriter.Write%2A> und <xref:System.IO.TextWriter.WriteLine%2A> abgelegt.

### <a name="example"></a>Beispiel

```cpp
// text_write.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";

   StreamWriter^ sw = gcnew StreamWriter(fileName);
   sw->WriteLine("A text file is born!");
   sw->Write("You can use WriteLine");
   sw->WriteLine("...or just Write");
   sw->WriteLine("and do {0} output too.", "formatted");
   sw->WriteLine("You can also send non-text objects:");
   sw->WriteLine(DateTime::Now);
   sw->Close();
   Console::WriteLine("a new file ('{0}') has been written", fileName);

   return 0;
}
```

## <a name="see-also"></a>Weitere Informationen

[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Datei- und Stream-E/A](/dotnet/standard/io/index)<br/>
[System.IO-Namespace](/dotnet/api/system.io)
