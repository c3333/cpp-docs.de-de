---
title: TemplateInstantiation-Klasse
description: Der C++ Build Insights SDK TemplateInstantiation-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ba8fd10efc6a536c9160f10b19e19e17bfaaad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324223"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TemplateInstantiation` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `TemplateInstantiation` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[TemplateInstantiation](#template-instantiation)

### <a name="functions"></a>Functions

[Art](#kind)
[PrimaryTemplateSymbolKey](#primary-template-symbol-key)
[SpezialisierungSymbolKey](#specialization-symbol-key)

## <a name="kind"></a><a name="kind"></a>Art

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Code, der den Typ der Vorlageninstanziierung beschreibt, der durchgeführt wurde.

## <a name="primarytemplatesymbolkey"></a><a name="primary-template-symbol-key"></a>PrimaryTemplateSymbolKey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Bezeichner für den Vorlagentyp, der spezialisiert wurde. Dieser Bezeichner ist innerhalb eines Compiler-Front-End-Passes eindeutig.

## <a name="specializationsymbolkey"></a><a name="specialization-symbol-key"></a>SpezialisierungSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Bezeichner für den Typ der Spezialisierung. Dieser Bezeichner ist innerhalb eines Compiler-Front-End-Passes eindeutig.

## <a name="templateinstantiation"></a><a name="template-instantiation"></a>TemplateInstantiation

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) TEMPLATE_INSTANTIATION-Ereignis.

::: moniker-end
