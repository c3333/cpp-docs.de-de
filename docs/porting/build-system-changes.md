---
title: VCBuild im Vergleich zu MSBuild
description: Das Visual Studio C++ -Buildsystem wurde in Visual Studio 2010 von VCBuild in MSBuild geändert.
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: ce3eb9e51a103aa54b74c7b5b4f775eb402269f1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076951"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild im Vergleich zu MSBuild: buildsystemänderungen in Visual Studio 2010

Das MSBuild-System C++ für Projekte wurde in Visual Studio 2010 eingeführt. In Visual Studio 2008 und früheren Versionen wurde das VCBuild-System verwendet. Bestimmte Dateitypen und Konzepte, die von VCBuild abhängen, sind entweder nicht vorhanden oder werden in MSBuild anders dargestellt. In diesem Artikel werden die Unterschiede im aktuellen Buildsystem behandelt. Um ein Visual Studio 2008-Projekt in MSBuild zu konvertieren, müssen Sie Visual Studio 2010 verwenden. Nachdem das Projekt konvertiert wurde, sollten Sie die neueste Version von Visual Studio verwenden, um ein Upgrade auf die aktuelle IDE und das aktuelle Compilertoolset auszuführen. Weitere Informationen, einschließlich Informationen zum Abrufen von Visual Studio 2010, finden Sie unter [Anweisungen für Visual Studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

In den folgenden Abschnitten werden die Änderungen von VCBuild zu MSBuild zusammengefasst. Wenn Ihr VCBuild-Projekt über benutzerdefinierte Buildregeln oder Makros verfügt, die nicht von MSBuild erkannt werden, finden Sie weitere Informationen unter [Visual Studio-Projekte C++ ](../build/creating-and-managing-visual-cpp-projects.md) , um zu erfahren, wie diese Anweisungen in das MSBuild-System übersetzt Die anfängliche Konvertierung von VCBuild in MSBuild ist nur ein Zwischenschritt. Es ist nicht erforderlich, dass die Projektdatei vollständig korrekt ist oder das Programm ohne Fehler kompiliert wird. Sie verwenden Visual Studio 2010 nur zum Konvertieren des Projekts in das MSBuild-Format, damit das Projekt in der aktuellen Version von Visual Studio funktioniert.

## <a name="vcproj-is-now-vcxproj"></a>VCPROJ ist nun VCXPROJ

Projektdateien verwenden nicht mehr die VCPROJ-Erweiterung. Visual Studio 2010 konvertiert Projektdateien, die von einer früheren Version von Visual C++ erstellt wurden, automatisch in das MSBuild-Format, in dem die vcxproj-Erweiterung für Projektdateien verwendet wird.

## <a name="vsprops-is-now-props"></a>VSPROPS ist nun PROPS

In Visual Studio 2008 und früheren Versionen ist ein *Projekteigenschaften Blatt* eine XML-basierte Datei mit der Dateinamenerweiterung ". vsprops". Mit einem Projekteigenschaftenblatt können Sie Parameter für Buildtools festlegen, z. B. Compiler oder Linker, und benutzerdefinierte Makros erstellen. In MSBuild ist die Dateinamenerweiterung für ein Projekteigenschaften Blatt.-Eigenschaften.

## <a name="custom-build-rules-and-rules-files"></a>Benutzerdefinierte Buildregeln und rules-Dateien

In Visual Studio 2008 und früheren Versionen ist eine *Regeldatei* eine XML-basierte Datei mit der Dateinamenerweiterung. Rules. Mit Regeldateien können Sie benutzerdefinierte Buildregeln definieren und diese in den Buildvorgang eines C++-Projekts in Visual Studio integrieren. Mit benutzerdefinierten Buildregeln, die mehreren Erweiterungen zugeordnet sein können, können Sie Eingabedateien an ein Tool übergeben, das mindestens eine Ausgabedatei erstellt.

Im MSBuild-System werden benutzerdefinierte Buildregeln durch drei Dateitypen,. XML,.-Eigenschaften und. targets, anstelle einer Rules-Datei dargestellt. Wenn eine. Rules-Datei, die mit einer früheren Version von Visual C++ erstellt wurde, zu Visual Studio 2010 migriert wird, werden äquivalente XML-,.-Eigenschaften-und Targets-Dateien in Ihrem Projekt erstellt und mit der ursprünglichen Rules-Datei gespeichert.

> [!IMPORTANT]
> In Visual Studio 2010 wird die Erstellung neuer Regeln von der IDE nicht unterstützt. Aus diesem Grund ist die einfachste Möglichkeit, eine Regeldatei aus einem Projekt zu verwenden, das mit einer früheren Version von Visual C++ erstellt wurde, das Projekt zu Visual Studio 2010 zu migrieren.

## <a name="inheritance-macros"></a>Vererbungs Makros

In Visual Studio 2008 und früheren Versionen gibt das **$ (erben)** -Makro die Reihenfolge an, in der geerbte Eigenschaften in der Befehlszeile angezeigt werden, die vom Projektbuildsystem erstellt wird. Mit dem Makro **$(NoInherit)** werden alle Vorkommnisse von „$(Inherit)“ ignoriert und Eigenschaften, die andernfalls geerbt werden würden, werden nicht geerbt. Durch das Makro „$(Inherit)“ werden beispielsweise Dateien, die mithilfe der Compileroption [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md) (/I (Zusätzliche Includeverzeichnisse)) festgelegt werden, an die Befehlszeile angefügt.

In Visual Studio 2010 wird die Vererbung unterstützt, indem der Wert einer Eigenschaft als Verkettung eines oder mehrerer Literalwerte und Eigenschafts Makros angegeben wird. Die Makros **$(Inherit)** und **$(NoInherit)** werden nicht unterstützt.

Im folgenden Beispiel wird einer Eigenschaft auf einer Eigenschaftenseite eine durch Semikolons getrennte Liste zugewiesen. Die Liste besteht aus der Verkettung des Literals *\<Wert>* und des Werts der `MyProperty`-Eigenschaft, auf den mithilfe der Makronotation **$(** <em>MyProperty</em> **)** zugegriffen wird.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>vcxproj. User-Dateien

Benutzerdateien (VCXPROJ.USER) speichern benutzerspezifische Eigenschaften, z. B. Debug- und Bereitstellungseinstellungen. Die Datei " *vcxproj. User* " gilt für alle Projekte eines bestimmten Benutzers.

## <a name="vcxprojfilters-file"></a>vcxproj. Filters-Datei

Wenn **Projektmappen-Explorer** zum Hinzufügen einer Datei zu einem Projekt verwendet wird, definiert die Filterdatei ( *. vcxproj. Filters*), wo in der **Projektmappen-Explorer** Strukturansicht die Datei hinzugefügt wird, basierend auf der Dateinamenerweiterung.

## <a name="vc-directories-settings"></a>Einstellungen für VC + +-Verzeichnisse

Die Einstellungen von Visual C++-Verzeichnissen werden auf der [Eigenschaftenseite für VC++-Verzeichnisse](../ide/vcpp-directories-property-page.md) festgelegt. In Visual Studio 2008 und früheren Versionen werden Verzeichnisse pro Benutzer angewendet, und die Liste der ausgeschlossenen Verzeichnisse wird in der Datei " *SYSINCL. dat* " angegeben.

Sie können die VC++-Verzeichniseinstellungen nicht ändern, wenn Sie [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) in der Befehlszeile ausführen. Außerdem können Sie die Einstellungen nicht ändern, indem Sie das Menü **Extras** öffnen, auf **Einstellungen importieren/exportieren** klicken und dann die Option **Alle Einstellungen zurücksetzen** auswählen.

So migrieren Sie die Einstellungen für VC + +-Verzeichnisse aus einer *VSSETTINGS* -Datei, die von einer früheren Version von Visual Studio erstellt wurde:

1. Öffnen Sie **das Menü** Extras, und klicken Sie auf **Einstellungen importieren und exportieren** .
2. **Ausgewählte Umgebungseinstellungen importieren**
3. Folgen Sie den Anweisungen im Assistenten.

## <a name="see-also"></a>Weitere Informationen

[MSBuild on the Command Line – C++ (C++: MSBuild in der Befehlszeile)](../build/msbuild-visual-cpp.md)
