---
title: Concurrency::direct3d-Namespace-Funktionen (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375934"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d-Namespace-Funktionen (AMP)

||||
|-|-|-|
|[Abs](#abs)|[Klemme](#clamp)|[Countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[Imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[wütend](#mad)|[make_array](#make_array)|[Lärm](#noise)|
|[Bogenmaß](#radians)|[rcp](#rcp)|[Reversebits](#reversebits)|
|[Sättigen](#saturate)|[Zeichen](#sign)|[smoothstep](#smoothstep)|
|[Schritt](#step)|[Umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Anforderungen

**Header:** amp.h **Namespace:** Parallelität

## <a name="abs"></a><a name="abs"></a>Abs

Gibt den absoluten Wert des Arguments zurück.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt den absoluten Wert des Arguments zurück.

## <a name="clamp"></a><a name="clamp"></a>Klemme

Berechnet den Wert des angegebenen ersten Arguments, das an einen Bereich gebunden ist, der vom zweiten und dritten angegebenen Argument definiert wird.

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Der zu bindende Wert

*_Min*<br/>
Die untere Grenze des gebundenen Bereichs.

*_Max*<br/>
Die obere Grenze des gebundenen Bereichs.

### <a name="return-value"></a>Rückgabewert

Der gebundene Wert von `_X`.

## <a name="countbits"></a><a name="countbits"></a>Countbits

Zählt die Anzahl der festgelegten Bits in _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Nicht signierter Ganzzahlwert

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der gesetzten Bits in _X zurück.

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

Erstellt ein [accelerator_view](accelerator-view-class.md) Objekts von einem Zeiger auf eine Direct3D-Geräteschnittstelle.

## <a name="syntax"></a>Syntax

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parameter

*_Accelerator*<br/>
Die Zugriffstaste, auf der das neue accelerator_view-Objekt erstellt werden soll.

*_D3D_device*<br/>
Der Zeiger auf die Schnittstelle eines Direct3D-Geräts.

*_Disable_timeout*<br/>
Ein boolescher Parameter, der angibt, ob das Timeout für das neu erstellte accelerator_view-Objekt deaktiviert werden sollte. Dies entspricht dem D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT-Flag für die Erstellung von Direct3D-Geräten und wird verwendet, um anzugeben, ob das Betriebssystem Arbeitslasten zulässt, deren Ausführung mehr als 2 Sekunden dauert, ohne das Gerät über den Windows-TDR-Mechanismus (Timeout Detection and Recovery) zurückzusetzen. Die Verwendung dieses Flags wird empfohlen, wenn Sie zeitintensive Aufgaben im accelerator_view-Objekt ausführen müssen.

*_Qmode*<br/>
Die [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) für die neu erstellten accelerator_view verwendet werden. Der Standardwert dieses Parameters ist `queuing_mode_automatic`.

## <a name="return-value"></a>Rückgabewert

Das `accelerator_view`-Objekt, das über die übergebene Direct3D-Geräteschnittstelle erstellt wurde.

## <a name="remarks"></a>Bemerkungen

Diese Funktion erstellt ein neues `accelerator_view`-Objekt von einem vorhandenen Zeiger auf eine Direct3D-Geräteschnittstelle. Wenn der Funktionsaufruf folgt, wird der Verweiszähler des Parameters mit einem `AddRef`-Aufruf der Schnittstelle erhöht. Sie können das Objekt sicher freigeben, wenn es im DirectX-Code nicht mehr benötigt wird. Wenn der Methodenaufruf fehlschlägt, wird ein [runtime_exception](runtime-exception-class.md) ausgelöst.

Das `accelerator_view`-Objekt, das Sie mit dieser Funktion erstellen, ist threadsicher. Sie müssen die gleichzeitige Verwendung des `accelerator_view`-Objekts synchronisieren. Die unsynchronisierte gleichzeitige Verwendung des `accelerator_view`-Objekts und die unformatierte ID3D11Device-Schnittstelle verursachen ein nicht definiertes Verhalten.

Die C++-AMP-Laufzeit stellt detaillierte Fehlerinformationen im Debugmodus mithilfe der D3D-Debugebene bereit, wenn Sie das `D3D11_CREATE_DEVICE_DEBUG`-Flag verwenden.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

Ruft eine Sperre für eine "accelerator_view" ab, um D3D-Vorgänge in Ressourcen, die gemeinsam mit der "accelerator_view" genutzt werden, sicher ausführen zu können. Die "accelerator_view" und alle C++ AMP-Ressourcen, die dieser "accelerator_view" intern zugeordnet sind, werden gesperrt, wenn Vorgänge ausgeführt werden, und blockieren, während ein anderer Thread die D3D-Zugriffssperre inne hat. Diese Sperre ist nicht rekursiv: Es ist nicht definiertes Verhalten, diese Funktion von einem Thread aufzurufen, der bereits die Sperre besitzt. Es ist nicht definiertes Verhalten, Vorgänge für die "accelerator_view" oder Datencontainer auszuführen, die der "accelerator_view" vom Thread zugeordnet sind, der die D3D-Zugriffssperre besitzt. Siehe auch: "scoped_d3d_access_lock", eine RAII-Formatklasse für eine bereichsbasierte D3D-Zugriffssperre.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parameter

*_Av*<br/>
Die zu sperrende "accelerator_view".

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

Versuch, ohne Blockierung die D3D-Zugriffssperre für eine accelerator_view abzurufen.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parameter

*_Av*<br/>
Die zu sperrende "accelerator_view".

### <a name="return-value"></a>Rückgabewert

"true", wenn die Sperre abgerufen wurde, oder "false", wenn sie durch einen anderen Thread verwendet wird.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

Gibt die D3D-Zugriffssperre für die angegebene accelerator_view frei. Wenn der aufrufende Thread nicht die Sperre für "accelerator_view" hat, sind die Ergebnisse nicht definiert.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parameter

*_Av*<br/>
Die „accelerator_view“, für die die Sperre aufgehoben werden soll.

## <a name="firstbithigh"></a><a name="firstbithigh"></a>firstbithigh

Ruft den Speicherort des ersten festgelegten Bits in _X ab, beginnend mit dem höchsten Bit und arbeitet sich weiter bis zum niedrigsten Bit.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Der Speicherort des ersten festgelegten Bits

## <a name="firstbitlow"></a><a name="firstbitlow"></a>firstbitlow

Ruft den Speicherort des ersten festgelegten Bits in _X ab, beginnend mit dem niederwertigsten Bit und arbeitet sich weiter bis zum höchsten Bit.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Gibt den Speicherort des ersten festgelegten Bits zurück

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

Rufen Sie die Direct3D-Pufferschnittstelle ab, die dem angegebenen Array zugrunde liegt.

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>Parameter

*Value_type*<br/>
Der Typ der Elemente im Array.

*_Rank*<br/>
Der Rang des Arrays.

*_Array*<br/>
Ein Array auf einem Direct3D-accelerator_view_Objekt, für das die zugrunde liegende Direct3D-Pufferschnittstelle zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Der IUnknown-Schnittstellenzeiger entspricht dem Direct3D-Puffer, der dem Array zugrunde liegt.

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

Holen Sie sich die D3D-Geräteschnittstelle, die einem accelerator_view zugrunde liegt.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parameter

*Av*<br/>
Die D3D-accelerator_view, für die die zugrunde liegende D3D-Geräteschnittstelle zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Der `IUnknown` Schnittstellenzeiger des D3D-Geräts, das dem accelerator_view zugrunde liegt.

## <a name="imax"></a><a name="imax"></a>Imax

Festlegung des höchsten numerischen Werts der Argumente

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Rückgabe des höchsten numerischen Werts der Argumente

## <a name="imin"></a><a name="imin"></a>imin

Festlegung des niedrigsten numerischen Werts der Argumente

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Rückgabe des niedrigsten numerischen Werts der Argumente

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

Gibt ein boolesches Flag zurück, das angibt, ob Timeout für die angegebene "accelerator_view" deaktiviert ist. Dies entspricht dem D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT-Flag für Direct3D-Geräteerstellung.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parameter

*_Accelerator_view*<br/>
Die "accelerator_view", für die die deaktivierte Timeouteinstellung, abgefragt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein boolesches Flag, das angibt, ob Timeout für die angegebene "accelerator_view" deaktiviert ist.

## <a name="mad"></a><a name="mad"></a>wütend

Berechnet das Produkt des ersten und zweiten angegebenen Arguments und fügt dann das dritte angegebene Argument hinzu.

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Das erste angegebene Argument.

*_Y*<br/>
Das zweite angegebene Argument.

*_Z*<br/>
Das dritte angegebene Argument.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis `_X` \* `_Y`  +  `_Z`von .

## <a name="make_array"></a><a name="make_array"></a>make_array

Erstellt ein Array aus dem Schnittstellenzeiger eines Direct3D-Puffers.

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>Parameter

*Value_type*<br/>
Der Elementtyp des zu erstellenden Arrays.

*_Rank*<br/>
Der Rang des zu erstellenden Arrays.

*_Extent*<br/>
Ein Wertebereich, der die Form des Arrayaggregats beschreibt.

*_Rv*<br/>
Eine D3D-Zugriffstastenansicht, in der das Array erstellt werden soll.

*_D3D_buffer*<br/>
IUnknown-Schnittstellenzeiger des D3D-Puffers zum Erstellen des Arrays.

### <a name="return-value"></a>Rückgabewert

Ein mithilfe des angegebenen Direct3D-Puffers erstelltes Array.

## <a name="noise"></a><a name="noise"></a>Lärm

Generiert einen Zufallswert mit dem Perlin-Rauschalgorithmus

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert, aus dem Perlin-Rauschen erzeugt werden soll

### <a name="return-value"></a>Rückgabewert

Gibt den Perlin-Rauschwert innerhalb eines Bereichs zwischen -1 und 1 zurück

## <a name="radians"></a><a name="radians"></a>Bogenmaß

Konvertiert _X von Grad in Bogenmaß

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgaben _X von Grad in Bogenmaß konvertiert

## <a name="rcp"></a><a name="rcp"></a>Rcp

Berechnet den Kehrwert des angegebenen Arguments mithilfe einer schnellen Näherung.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Der Wert, für den der Kehrwert berechnet werden soll.

### <a name="return-value"></a>Rückgabewert

Der Kehrwert des angegebenen Arguments.

## <a name="reversebits"></a><a name="reversebits"></a>Reversebits

Kehrt die Reihenfolge der Bits in _X um

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Nicht signierter Ganzzahlwert

### <a name="return-value"></a>Rückgabewert

Gibt den Wert zurück, wobei die Bitreihenfolge in _X

## <a name="saturate"></a><a name="saturate"></a>Sättigen

Bindet _X im Bereich zwischen 0 und 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Rückgaben _X im Bereich von 0 bis 1 eingeklemmt

## <a name="sign"></a><a name="sign"></a>Zeichen

Bestimmt das Vorzeichen des angegebenen Arguments.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Das Vorzeichen des Arguments.

## <a name="smoothstep"></a><a name="smoothstep"></a>smoothstep

Gibt eine glatte Hermite-Interpolation zwischen 0 und 1 zurück, wenn _X im Bereich [_Min, _Max] liegt.

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Min*<br/>
Gleitkommawert

*_Max*<br/>
Gleitkommawert

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt 0 zurück, wenn _X kleiner als _Min ist; 1 wenn _X größer ist als _Max; Andernfalls liegt ein Wert zwischen 0 und 1, wenn _X im Bereich [_Min, _Max] liegt.

## <a name="step"></a><a name="step"></a>Schritt

Vergleicht zwei Werte und gibt, je nachdem welcher Wert größer ist, 0 oder 1 zurück

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_Y*<br/>
Gleitkommawert

*_x*<br/>
Gleitkommawert

### <a name="return-value"></a>Rückgabewert

Gibt 1 zurück, wenn die _X größer oder gleich _Y ist; andernfalls, 0

## <a name="umax"></a><a name="umax"></a>Umax

Festlegung des höchsten numerischen Werts der Argumente

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Rückgabe des höchsten numerischen Werts der Argumente

## <a name="umin"></a><a name="umin"></a>umin

Festlegung des niedrigsten numerischen Werts der Argumente

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parameter

*_x*<br/>
Ganzzahliger Wert

*_Y*<br/>
Ganzzahliger Wert

### <a name="return-value"></a>Rückgabewert

Rückgabe des niedrigsten numerischen Werts der Argumente

## <a name="see-also"></a>Siehe auch

[Concurrency::direct3d-Namespace](concurrency-direct3d-namespace.md)
