---
title: Zugriffstastenklasse
ms.date: 11/04/2016
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 99747899e9264404244d66f3f0d18bee5d2b0967
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182706"
---
# <a name="accelerator-class"></a>Zugriffstastenklasse

Eine Zugriffstaste ist eine Hardwarefunktion, die für datenparallele Computervorgänge optimiert ist. Eine Zugriffstaste ist ein Gerät, das einem PCIe-Bus angefügt wird (wie einem GPU-Computer), oder es handelt sich um einen erweiterten Befehl, der auf der Haupt-CPU festgelegt ist.

## <a name="syntax"></a>Syntax

```cpp
class accelerator;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Accelerator-Konstruktor](#ctor)|Initialisiert eine neue Instanz der `accelerator`-Klasse.|
|[~ Accelerator-Debugging](#ctor)|Zerstört das `accelerator`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[create_view](#create_view)|Erstellt und gibt ein `accelerator_view`-Objekt auf dieser Zugriffstaste zurück.|
|[get_all](#get_all)|Gibt einen Vektor von `accelerator`-Objekten zurück, die alle verfügbaren Zugriffstasten darstellen.|
|[get_auto_selection_view](#get_auto_selection_view)|Gibt das `accelerator_view`-Objekt für die automatische Auswahl zurück.|
|[get_dedicated_memory](#get_dedicated_memory)|Gibt den dedizierten Arbeitsspeicher für das `accelerator`-Objekt in KB zurück.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Gibt die Standard [access_type](concurrency-namespace-enums-amp.md#access_type) für Puffer zurück, die auf dieser Zugriffstaste erstellt werden.|
|[get_default_view](#get_default_view)|Gibt das standardmäßige `accelerator_view`-Objekt zurück, das mit dem `accelerator`-Objekt verknüpft ist.|
|[get_description](#get_description)|Gibt eine kurze Beschreibung des `accelerator`-Geräts zurück.|
|[get_device_path](#get_device_path)|Gibt den Pfad des physischen Geräts zurück.|
|[get_has_display](#get_has_display)|Bestimmt, ob das `accelerator`-Objekt mit einer Anzeige verbunden ist.|
|[get_is_debug](#get_is_debug)|Bestimmt, für das `accelerator`-Objekt die DEBUG-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.|
|[get_is_emulated](#get_is_emulated)|Bestimmt, ob das `accelerator`-Objekt emuliert ist.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Bestimmt, ob das `accelerator`-Objekt freigegebenen Arbeitsspeicher unterstützt|
|[get_supports_double_precision](#get_supports_double_precision)|Bestimmt, ob das `accelerator`-Objekt mit einer Anzeige verbunden ist.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Bestimmt, ob das `accelerator`-Objekt über beschränkte Unterstützung für mathematische Funktionen mit doppelter Genauigkeit verfügt.|
|[get_version](#get_version)|Gibt die Version des `accelerator`-Objekts zurück.|
|[set_default](#set_default)|Gibt den Pfad der Standardzugriffstaste zurück.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Legt die Standard-CPU- [access_type](concurrency-namespace-enums-amp.md#access_type)für Arrays und implizite Speicher Belegungen für diese fest `accelerator` .|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator! =](#operator_neq)|Vergleicht dieses `accelerator` -Objekt mit einem anderen und gibt zurück, **`false`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`true`** .|
|[Operator =](#operator_eq)|Kopiert den Inhalt des angegebenen `accelerator`-Objekts in dieses Objekt.|
|[Operator = =](#operator_eq_eq)|Vergleicht dieses `accelerator` -Objekt mit einem anderen und gibt zurück, **`true`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`false`** .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Ruft eine Zeichenfolgenkonstante für die CPU-`accelerator` ab.|
|[dedicated_memory](#dedicated_memory)|Ruft den dedizierten Arbeitsspeicher für das `accelerator`-Objekt in KB ab.|
|[default_accelerator](#default_accelerator)|Ruft eine Zeichenfolgenkonstante für die standardmäßige `accelerator` ab.|
|[default_cpu_access_type](#default_cpu_access_type)|Ruft die Standard-CPU- [access_type](concurrency-namespace-enums-amp.md#access_type)für Arrays und implizite Speicher Belegungen für dieses ab oder legt diese fest `accelerator` .|
|[default_view](#default_view)|Ruft das standardmäßige `accelerator_view`-Objekt ab, das dem `accelerator`-Element zugeordnet ist.|
|[description](#description)|Ruft eine kurze Beschreibung des `accelerator`-Geräts ab.|
|[device_path](#device_path)|Ruft den Pfad des physischen Geräts ab.|
|[direct3d_ref](#direct3d_ref)|Ruft eine Zeichenfolgenkonstante für eine Direct3D-Verweis-`accelerator` ab.|
|[direct3d_warp](#direct3d_warp)|Ruft die Zeichen folgen Konstante für ein `accelerator` Objekt ab, das Sie zum Ausführen von C++ amp-Code auf Multi-Core-CPUs verwenden können, die Streaming SIMD Extensions (SSE) verwenden.|
|[has_display](#has_display)|Ruft einen booleschen Wert ab, der angibt, ob das `accelerator`-Objekt mit einer Anzeige verbunden ist.|
|[is_debug](#is_debug)|Gibt an, ob für das `accelerator`-Objekt die DEBUG-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.|
|[is_emulated](#is_emulated)|Gibt an, ob das `accelerator`-Objekt emuliert ist.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Gibt an, ob das `accelerator`-Objekt freigegebenen Arbeitsspeicher unterstützt.|
|[supports_double_precision](#supports_double_precision)|Gibt an, ob die Zugriffstaste mathematische Funktionen mit doppelter Genauigkeit unterstützt.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Gibt an, ob die Zugriffstaste über beschränkte Unterstützung für mathematische Funktionen mit doppelter Genauigkeit verfügt.|
|[version](#version)|Ruft die Version der `accelerator` ab.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`accelerator`

## <a name="remarks"></a>Bemerkungen

Eine Zugriffstaste ist eine Hardwarefunktion, die für datenparallele Computervorgänge optimiert ist. Eine Zugriffstaste ist häufig eine einzelne GPU, kann jedoch auch eine virtuelle hostseitige Entität wie ein DirectX REF-Gerät, ein WARP-Gerät (ein CPU-seitiges Gerät, das mithilfe von SSE-Anweisungen beschleunigt wird) oder die CPU selbst sein.

Sie können ein `accelerator`-Objekt erstellen, indem Sie die verfügbaren Geräte auflisten oder das Standardgerät, das Referenzgerät oder das WARP-Gerät abrufen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amprt. h

**Namespace:** Parallelität

## <a name="a-accelerator"></a><a name="dtor"></a></a>~ Accelerator

Zerstört das `accelerator`-Objekt.

```cpp
~accelerator();
```

### <a name="return-value"></a>Rückgabewert

## <a name="accelerator"></a><a name="ctor"></a>getreten

Initialisiert eine neue Instanz der [Accelerator-Klasse](accelerator-class.md).

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parameter

*_Device_path*<br/>
Der Pfad des physischen Geräts.

*_Other*<br/>
Die zu kopierende Zugriffstaste.

## <a name="cpu_accelerator"></a><a name="cpu_accelerator"></a>cpu_accelerator

Ruft eine Zeichen folgen Konstante für den CPU-Accelerator ab.

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a><a name="create_view"></a>create_view

Erstellt ein Objekt auf dieser Zugriffstaste und gibt `accelerator_view` es unter Verwendung des angegebenen Warteschlangen Modus zurück. Wenn der queuingmodus nicht angegeben wird, verwendet der neue `accelerator_view` den [queuing_mode:: immediate](concurrency-namespace-enums-amp.md#queuing_mode) queuingmodus.

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parameter

*qmode*<br/>
Der queuingmodus.

### <a name="return-value"></a>Rückgabewert

Ein neues- `accelerator_view` Objekt auf dieser Zugriffstaste unter Verwendung des angegebenen Warteschlangen Modus.

## <a name="dedicated_memory"></a><a name="dedicated_memory"></a>dedicated_memory

Ruft den dedizierten Arbeitsspeicher für das `accelerator`-Objekt in KB ab.

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a><a name="default_accelerator"></a>default_accelerator

Ruft eine Zeichenfolgenkonstante für die standardmäßige `accelerator` ab.

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a><a name="default_cpu_access_type"></a>default_cpu_access_type

Der Standard-CPU- [access_type](concurrency-namespace-enums-amp.md#access_type)für Arrays und implizite Speicher Belegungen, die für dieses erstellt wurden `accelerator` .

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a><a name="default_view"></a>default_view

Ruft die standardacceleransichts Ansicht ab, die dem zugeordnet ist `accelerator` .

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a><a name="description"></a>Beschreibung

Ruft eine kurze Beschreibung des `accelerator`-Geräts ab.

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a><a name="device_path"></a>device_path

Ruft den Pfad der Zugriffstaste ab. Der Pfad ist im System eindeutig.

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a><a name="direct3d_ref"></a>direct3d_ref

Ruft eine Zeichen folgen Konstante für einen Direct3D Reference Accelerator ab.

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a><a name="direct3d_warp"></a>direct3d_warp

Ruft die Zeichen folgen Konstante für ein- `accelerator` Objekt ab, das Sie zum Ausführen des C++ amp Codes auf Multikern-CPUs mit Streaming SIMD Extensions (SSE) verwenden können.

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a><a name="get_all"></a>get_all

Gibt einen Vektor von `accelerator`-Objekten zurück, die alle verfügbaren Zugriffstasten darstellen.

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Rückgabewert

Der Vektor der verfügbaren Accelerators

## <a name="get_auto_selection_view"></a><a name="get_auto_selection_view"></a>get_auto_selection_view

Gibt das accelerator_view-Objekt zur automatischen Auswahl zurück, das, sofern als parallel_for_each-Ziel angegeben, im accelerator_view-Ziel resultiert, damit der parallel_for_each-Kernels von der Laufzeit automatisch ausgewählt wird. Für alle anderen Zwecke ist das von dieser Methode zurückgegebene accelerator_view-Objekt, mit dem accelerator_view-Standardobjekt der Standardzugriffstaste identisch.

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Rückgabewert

Das accelerator_view-Objekt zur automatischen Auswahl.

## <a name="get_dedicated_memory"></a><a name="get_dedicated_memory"></a>get_dedicated_memory

Gibt den dedizierten Arbeitsspeicher für das `accelerator`-Objekt in KB zurück.

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>Rückgabewert

Der dedizierte Arbeitsspeicher für den `accelerator` in Kilobyte.

## <a name="get_default_cpu_access_type"></a><a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

Ruft das standardmäßige CPU-access_type-Objekt für die Puffer zurück, die auf dieser Zugriffstaste erstellt werden.

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>Rückgabewert

Das standardmäßige CPU-access_type-Objekt für die Puffer, die auf dieser Zugriffstaste erstellt werden.

## <a name="get_default_view"></a><a name="get_default_view"></a>get_default_view

Gibt das standardmäßige `accelerator_view`-Objekt zurück, das mit dem `accelerator`-Objekt verknüpft ist.

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>Rückgabewert

Das Standard `accelerator_view` Objekt, das zugeordnet ist `accelerator` .

## <a name="get_description"></a><a name="get_description"></a>get_description

Gibt eine kurze Beschreibung des `accelerator`-Geräts zurück.

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>Rückgabewert

Eine kurze Beschreibung des `accelerator` Geräts.

## <a name="get_device_path"></a><a name="get_device_path"></a>get_device_path

Gibt den Pfad der Zugriffstaste zurück. Der Pfad ist im System eindeutig.

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>Rückgabewert

Der systemweite eindeutige Geräte instanzpfad.

## <a name="get_has_display"></a><a name="get_has_display"></a>get_has_display

Gibt einen booleschen Wert zurück, der angibt, ob die `accelerator` an eine Anzeige ausgeben kann.

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das `accelerator` an eine Anzeige ausgeben kann, andernfalls **`false`** .

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Bestimmt, für das `accelerator`-Objekt die DEBUG-Ebene für eine umfangreiche Fehlerberichterstattung aktiviert ist.

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`** Wenn die `accelerator` debugschicht für eine umfangreiche Fehlerberichterstattung aktiviert ist. Andernfalls **`false`** .

## <a name="get_is_emulated"></a><a name="get_is_emulated"></a>get_is_emulated

Bestimmt, ob das `accelerator`-Objekt emuliert ist.

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der `accelerator` emuliert wird. Andernfalls **`false`** .

## <a name="get_supports_cpu_shared_memory"></a><a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

Gibt einen booleschen Wert zurück, der angibt, ob die Zugriffstaste Arbeitsspeicher unterstützt, auf den sowohl die Zugriffstaste als auch die CPU zugreifen können.

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zugriffstaste CPU Shared Memory unterstützt. andernfalls **`false`** .

## <a name="get_supports_double_precision"></a><a name="get_supports_double_precision"></a>get_supports_double_precision

Gibt einen booleschen Wert zurück, der angibt, ob die Zugriffstaste mathematische Zeichen mit doppelter Genauigkeit unterstützt, einschließlich "Multiplizieren multiplizieren (FMA)", "Division", "gegenseitiger **`int`** " und**`double`**

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zugriffstaste math mit doppelter Genauigkeit unterstützt. andernfalls **`false`** .

## <a name="get_supports_limited_double_precision"></a><a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

Gibt einen booleschen Wert zurück, der angibt, ob die Zugriffstaste eine begrenzte Unterstützung für mathematische Zeichen mit doppelter Genauigkeit aufweist. Wenn für die Zugriffstaste nur eingeschränkte Unterstützung besteht, wird das Multiplizieren von Multiplikations-Add (FMA), Division, gegenseitiger und Umwandlung zwischen **`int`** und **`double`** nicht unterstützt.

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Zugriffstaste nur eine begrenzte Unterstützung für die mathematische Genauigkeit aufweist; andernfalls **`false`** .

## <a name="get_version"></a><a name="get_version"></a>get_version

Gibt die Version des `accelerator`-Objekts zurück.

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Rückgabewert

Die Version der `accelerator`.

## <a name="has_display"></a><a name="has_display"></a>has_display

Ruft einen booleschen Wert ab, der angibt, ob die `accelerator` an eine Anzeige ausgeben kann.

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Ruft einen booleschen Wert ab, der angibt, ob die `accelerator` debugschicht für eine umfangreiche Fehlerberichterstattung aktiviert ist.

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a><a name="is_emulated"></a>is_emulated

Ruft einen booleschen Wert ab, der angibt, ob der `accelerator` emuliert wird.

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator"></a><a name="operator_neq"></a>Operator! =

Vergleicht dieses `accelerator` -Objekt mit einem anderen und gibt zurück, **`false`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`true`** .

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `accelerator` Objekt, das mit diesem verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`false`**, wenn die beiden- `accelerator` Objekte identisch sind, andernfalls **`true`** .

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Kopiert den Inhalt des angegebenen `accelerator`-Objekts in dieses Objekt.

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `accelerator`-Objekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `accelerator`-Objekt.

## <a name="operator"></a><a name="operator_eq_eq"></a>Operator = =

Vergleicht dieses `accelerator` -Objekt mit einem anderen und gibt zurück, **`true`** Wenn Sie identisch sind; andernfalls wird zurückgegeben **`false`** .

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `accelerator` Objekt, das mit diesem verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn das andere `accelerator` Objekt mit diesem-Objekt identisch ist, `accelerator` andernfalls **`false`** .

## <a name="set_default"></a><a name="set_default"></a>set_default

Legt die Standardzugriffstaste fest, die für jeden Vorgang verwendet werden soll, der die Standardzugriffstaste implizit verwendet. Diese Methode ist nur erfolgreich, wenn die von der Laufzeit ausgewählte Standardzugriffstaste nicht bereits in einem Vorgang verwendet wurde, der die Standardzugriffstaste implizit verwendet

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parameter

*_Path*<br/>
Der Pfad zur Zugriffstaste.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der-Befehl beim Festlegen der Standard Zugriffstaste erfolgreich ist. Andernfalls **`false`** .

## <a name="set_default_cpu_access_type"></a><a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

Legen Sie die Standard-CPU-access_type für Arrays fest, die auf dieser Zugriffstaste erstellt werden, oder für implizite Speicher Belegungen als Teil der array_views, auf die Sie Diese Methode ist nur erfolgreich, wenn die default_cpu_access_type für die Zugriffstaste nicht bereits durch einen vorherigen Aufrufen dieser Methode überschrieben wurde und die für diese Zugriffstaste default_cpu_access_type ausgewählte Laufzeit noch nicht für die Zuordnung eines Arrays verwendet wurde, oder für eine implizite Speicher Belegung, die auf eine array_view zugreift, die auf dieser Zugriffstaste zugreift.

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parameter

*_Default_cpu_access_type*<br/>
Das Standard-CPU-access_type-Objekt, das für array/array_view-Speicherbelegungen auf dieser Zugriffstaste verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der angibt, ob das Standard-CPU-access_type-Objekt für die Zugriffstaste erfolgreich festgelegt wurde.

## <a name="supports_cpu_shared_memory"></a><a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

Ruft einen booleschen Wert ab, der angibt, ob das `accelerator`-Objekt freigegebenen Arbeitsspeicher unterstützt.

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a><a name="supports_double_precision"></a>supports_double_precision

Ruft einen booleschen Wert ab, der angibt, ob die Zugriffstaste mathematische Zeichen mit doppelter Genauigkeit unterstützt.

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a><a name="supports_limited_double_precision"></a>supports_limited_double_precision

Ruft einen booleschen Wert ab, der angibt, ob die Zugriffstaste eine begrenzte Unterstützung für mathematische Zeichen mit doppelter Genauigkeit aufweist. Wenn für die Zugriffstaste nur eingeschränkte Unterstützung besteht, wird das Multiplizieren von Multiplikations-Add (FMA), Division, gegenseitiger und Umwandlung zwischen **`int`** und **`double`** nicht unterstützt.

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a><a name="version"></a>-Version

Ruft die Version der `accelerator` ab.

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
