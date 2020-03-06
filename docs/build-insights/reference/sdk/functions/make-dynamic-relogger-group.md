---
title: Makedynamikreloggergroup
description: Die C++ Funktionsreferenz für das Build Insights SDK makedynamikreloggergroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334397"
---
# <a name="makedynamicreloggergroup"></a>Makedynamikreloggergroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeDynamicReloggerGroup`-Funktion wird zum Erstellen einer dynamischen der reloggersitzung-Gruppe verwendet. Mitglieder einer der reloggersitzung-Gruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablauf Verfolgung verarbeitet wurden.

## <a name="syntax"></a>Syntax

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parameter

*reloggers*\
Ein Vektor von [irelogger](../other-types/irelogger-class.md) -Zeigern, die in der Gruppe dynamischer der reloggersitzung enthalten sind. Diese Zeiger können RAW, `std::unique_ptr`oder `std::shared_ptr`sein. [Ianalyzer](../other-types/ianalyzer-class.md) -Zeiger werden aufgrund einer Vererbungs Beziehung auch als `IRelogger` Zeiger betrachtet.

### <a name="return-value"></a>Rückgabewert

Eine dynamische der reloggersitzung-Gruppe. Verwenden Sie das Schlüsselwort " **Auto** ", um den Rückgabewert aufzuzeichnen.

## <a name="remarks"></a>Bemerkungen

Im Unterschied zu statischen der reloggersitzung-Gruppen müssen die Mitglieder einer Gruppe dynamischer der reloggersitzung zum Zeitpunkt der Kompilierung nicht bekannt sein. Sie können Gruppenmitglieder zur Laufzeit basierend auf der Programm Eingabe oder basierend auf anderen Werten, die zum Zeitpunkt der Kompilierung unbekannt sind, mithilfe von der reloggersitzung gruppieren. Im Unterschied zu statischen der reloggersitzung-Gruppen weisen [irelogger](../other-types/irelogger-class.md) -Zeiger in einer dynamischen der reloggersitzung-Gruppe polymorphe Verhalten auf, und virtuelle Funktionsaufrufe werden ordnungsgemäß weitergeleitet. Diese Flexibilität ergibt sich aus einer möglicherweise langsameren Ereignis Verarbeitungszeit. Wenn alle Gruppenmitglieder von der reloggersitzung zum Zeitpunkt der Kompilierung bekannt sind und Sie kein polymorphes Verhalten benötigen, sollten Sie die Verwendung einer statischen der reloggersitzung-Gruppe in Erwägung gezogen. Wenn Sie eine statische der reloggersitzung-Gruppe verwenden möchten, müssen Sie stattdessen [makestatikreloggergroup](make-static-relogger-group.md) aufrufen.

Eine Gruppe dynamischer der reloggersitzung kann in einer Gruppe statischer der reloggersitzung gekapselt werden. Sie übergeben die Adresse an [makestatikreloggergroup](make-static-relogger-group.md). Verwenden Sie dieses Verfahren, um dynamische der reloggersitzung-Gruppen an Funktionen wie z. b. [relog](relog.md)zu übergeben, die nur statische der reloggersitzung-Gruppen akzeptieren.

::: moniker-end
