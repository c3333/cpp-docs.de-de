---
title: /GENPROFILE, /FASTGENPROFILE (Profilerstellung instrumentierenden Build generieren)
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: 19ddf56d92cc2d8fbbfaf635c8e1602443e35b5b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825784"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE (Profilerstellung instrumentierenden Build generieren)

Gibt die Generierung einer PGD-Datei durch den Linker an, um die profilgesteuerte Optimierung (PGO) zu unterstützen. **/GENPROFILE** und **/FASTGENPROFILE** verwenden unterschiedliche Standardparameter. Verwenden Sie **/GENPROFILE** , um Genauigkeit gegenüber Geschwindigkeit und Speicherauslastung bei der Profilerstellung zu bevorzugen. Verwenden Sie **/FASTGENPROFILE** , um eine geringere Speicherauslastung und Geschwindigkeit gegenüber der Genauigkeit zu bevorzugen.

## <a name="syntax"></a>Syntax

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **exakte**|**noexact**] | **memmax =**_#_|**memmin =**_#_| [**Pfad**|**nopath** ] | [**trackeh** |**notrackeh** ] | **PGD =**_Dateiname_}] \
> **/FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [ **exakte**|**noexact**] | **memmax =**_#_|**memmin =**_#_| [**Pfad**|**nopath** ] | [**trackeh** |**notrackeh** ] | **PGD =**_Dateiname_}]

### <a name="arguments"></a>Argumente

Eines der folgenden Argumente kann für **/GENPROFILE** oder **/FASTGENPROFILE**angegeben werden. Die hier aufgelisteten Argumente, getrennt durch ein**|** senkrechter Strich (), schließen sich gegenseitig aus. Verwenden Sie ein Komma (**,**) zum Trennen von Optionen.

**COUNTER32** &#124; **COUNTER64**<br/>
Verwenden Sie **COUNTER32** , um die Verwendung von 32-Bit-Test Zählern anzugeben, und **COUNTER64** , um 64-Bit-testindikatoren anzugeben. Wenn Sie **/GENPROFILE**angeben, ist der Standardwert **COUNTER64**. Wenn Sie **/FASTGENPROFILE**angeben, ist der Standardwert **COUNTER32**.

**Exakte** &#124; **noexact**<br/>
Verwenden Sie **Exact** , um Thread sichere, Interlocked Inkremente für Tests anzugeben. **Noexact** gibt ungeschützte Inkrement-Vorgänge für Tests an. Der Standardwert ist **noexact**.

**Memmax**=*Wert*, **memmin**=-*Wert*<br/>
Verwenden Sie **memmax** und **memmin** , um die maximalen und minimalen Reservierungs Größen für Trainingsdaten im Arbeitsspeicher anzugeben. Der Wert entspricht der Größe des in Bytes zu reservierenden Arbeitsspeichers. Standardmäßig werden diese Werte über eine interne Heuristik bestimmt.

**Pfad** &#124; **nopath** <br/>
Verwenden Sie **path** , um einen separaten Satz von PGO-Indikatoren für jeden eindeutigen Pfad zu einer Funktion anzugeben. Verwenden Sie **nopath** , um nur einen Satz von Indikatoren für die einzelnen Funktionen anzugeben. Wenn Sie **/GENPROFILE**angeben, ist der Standard **Pfad** . Wenn Sie **/FASTGENPROFILE**angeben, lautet der Standardwert **nopath** .

**Trackeh** &#124; **notrackeh** <br/>
Gibt an, ob zusätzliche Indikatoren verwendet werden sollen, um eine genaue Anzahl beizubehalten, wenn während des Trainings Ausnahmen ausgelöst werden. Verwenden Sie **trackeh** , um zusätzliche Indikatoren für eine genaue Anzahl anzugeben. Verwenden Sie **notrackeh** , um einzelne Indikatoren für Code anzugeben, der keine Ausnahmebehandlung verwendet oder keine Ausnahmen in ihren Trainingsszenarien findet.  Wenn Sie **/GENPROFILE**angeben, lautet der Standardwert **trackeh** . Wenn Sie **/FASTGENPROFILE**angeben, lautet der Standardwert **notrackeh** .

**PGD**=*Dateiname*<br/>
Gibt einen Basisdateinamen für die PGD-Datei an. Standardmäßig wird vom Linker der Name der ausführbaren Basisbilddatei mit der Erweiterung PGD verwendet.

## <a name="remarks"></a>Bemerkungen

Die Optionen **/GENPROFILE** und **/FASTGENPROFILE** weisen den Linker an, die Instrumentations Datei zu generieren, die zum unterstützen von Anwendungs Schulungen für die Profil gesteuerte Optimierung (PGO) benötigt wird. Diese Optionen sind neu in Visual Studio 2015. Bevorzugen Sie diese Optionen für die veralteten **/LTCG: PGINSTRUMENT**-, **/PGD** -und **/POGOSAFEMODE** -Optionen und die Umgebungsvariablen **PogoSafeMode**, **VCPROFILE_ALLOC_SCALE** und **VCPROFILE_PATH** . Die vom Anwendungstraining generierten Informationen zur Profilerstellung werden als Eingabe verwendet, um während der Builderstellung Zieloptimierungen für vollständige Programme durchzuführen. Sie können zusätzliche Optionen festlegen, um die verschiedenen Features für die Profilerstellung während des App-Trainings und der App-Erstellung hinsichtlich der Leistung zu steuern. Die von **/GENPROFILE** angegebenen Standardoptionen führen zu den genauesten Ergebnissen, insbesondere für große, komplexe Multithread-apps. Die **/FASTGENPROFILE** -Option verwendet unterschiedliche Standardwerte für einen geringeren Speicherbedarf und eine schnellere Leistung während des Trainings, auf Kosten der Genauigkeit.

Profil Erstellungs Informationen werden aufgezeichnet, wenn Sie die instrumentierte app ausführen, nachdem Sie mithilfe von **/GENPROFILE** of **/FASTGENPROFILE**erstellt haben. Diese Informationen werden aufgezeichnet, wenn Sie die [/UserProfile angegeben](useprofile.md) -Linkeroption angeben, um den Profil Erstellungs Schritt auszuführen, und dann zum Ausführen des optimierten Buildschritts verwendet werden. Weitere Informationen zum Trainieren Ihrer APP und Details zu den gesammelten Daten finden Sie unter [Profil gesteuerte Optimierungen](../profile-guided-optimizations.md).

Sie müssen auch **/LTCG** angeben, wenn Sie **/GENPROFILE** oder **/FASTGENPROFILE**angeben.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaften Seite für die**Linker** > **Linkerbefehlszeile** der **Configuration Properties** > 

1. Geben Sie im Feld **zusätzliche Optionen** die Optionen und Argumente für **/GENPROFILE** oder **/FASTGENPROFILE** ein. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)<br/>
[/LTCG (Link-Zeitcodegenerierung)](ltcg-link-time-code-generation.md)<br/>
