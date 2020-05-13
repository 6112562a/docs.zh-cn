---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo 方法
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: a6c32b72c5924399aeb13d56ddf9242fe7990f35
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379326"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="23d37-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo 方法</span><span class="sxs-lookup"><span data-stu-id="23d37-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="23d37-103">检索泛型字典映射。</span><span class="sxs-lookup"><span data-stu-id="23d37-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="23d37-104">语法</span><span class="sxs-lookup"><span data-stu-id="23d37-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="23d37-105">参数</span><span class="sxs-lookup"><span data-stu-id="23d37-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="23d37-106">弄指向包含泛型字典映射的[ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)对象地址的指针。</span><span class="sxs-lookup"><span data-stu-id="23d37-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="23d37-107">有关详细信息，请参阅“备注”部分。</span><span class="sxs-lookup"><span data-stu-id="23d37-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="23d37-108">备注</span><span class="sxs-lookup"><span data-stu-id="23d37-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="23d37-109">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="23d37-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="23d37-110">该映射由两个顶级部分组成：</span><span class="sxs-lookup"><span data-stu-id="23d37-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="23d37-111">一个[目录](#Directory)，其中包含此映射中包含的所有字典的相对虚拟地址（RVA）。</span><span class="sxs-lookup"><span data-stu-id="23d37-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="23d37-112">一个字节对齐的[堆](#Heap)，其中包含对象实例化信息。</span><span class="sxs-lookup"><span data-stu-id="23d37-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="23d37-113">在最后一个目录输入后立即开始。</span><span class="sxs-lookup"><span data-stu-id="23d37-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="23d37-114">目录</span><span class="sxs-lookup"><span data-stu-id="23d37-114">The Directory</span></span>

<span data-ttu-id="23d37-115">目录中的每个条目引用堆内的偏移量；也就是说，它是相对于堆开始的偏移量。</span><span class="sxs-lookup"><span data-stu-id="23d37-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="23d37-116">单独条目的值不一定是唯一的；在堆中多个目录条目有可能指向相同的偏移量。</span><span class="sxs-lookup"><span data-stu-id="23d37-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="23d37-117">泛型字典映射的目录部分具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="23d37-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="23d37-118">前 4 个字节包含字典条目的数量（也就是说，字典中的相对虚拟地址数）。</span><span class="sxs-lookup"><span data-stu-id="23d37-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="23d37-119">我们将此值称为*N*。如果设置了高位，则按相对虚拟地址（升序）对项进行排序。</span><span class="sxs-lookup"><span data-stu-id="23d37-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="23d37-120">*N*目录项跟随。</span><span class="sxs-lookup"><span data-stu-id="23d37-120">The *N* directory entries follow.</span></span> <span data-ttu-id="23d37-121">每个条目由 8 个字节（两个 4 字节段）构成：</span><span class="sxs-lookup"><span data-stu-id="23d37-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="23d37-122">字节 0-3：RVA；字典的相对虚拟地址。</span><span class="sxs-lookup"><span data-stu-id="23d37-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="23d37-123">字节 4-7：偏移量；相对于堆开始的偏移量。</span><span class="sxs-lookup"><span data-stu-id="23d37-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="23d37-124">堆</span><span class="sxs-lookup"><span data-stu-id="23d37-124">The Heap</span></span>

<span data-ttu-id="23d37-125">可用流读取器计算堆的大小，计算方法是目录大小 + 4 再减去流的长度。</span><span class="sxs-lookup"><span data-stu-id="23d37-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="23d37-126">换言之：</span><span class="sxs-lookup"><span data-stu-id="23d37-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="23d37-127">其中，目录大小为 `N * 8`。</span><span class="sxs-lookup"><span data-stu-id="23d37-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="23d37-128">在堆上每个实例化信息项的格式为：</span><span class="sxs-lookup"><span data-stu-id="23d37-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="23d37-129">此实例化信息项的长度（采用压缩 ECMA 元数据格式，以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="23d37-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="23d37-130">该值不包括此长度信息。</span><span class="sxs-lookup"><span data-stu-id="23d37-130">The value excludes this length information.</span></span>

- <span data-ttu-id="23d37-131">采用压缩 ECMA 元数据格式的泛型实例化类型或*T*的数目。</span><span class="sxs-lookup"><span data-stu-id="23d37-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="23d37-132">*T*类型，每个类型都以 ECMA 类型签名格式表示。</span><span class="sxs-lookup"><span data-stu-id="23d37-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="23d37-133">包含每个堆元素的长度使目录部分实现简单排序，而不对堆造成影响。</span><span class="sxs-lookup"><span data-stu-id="23d37-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="23d37-134">要求</span><span class="sxs-lookup"><span data-stu-id="23d37-134">Requirements</span></span>

<span data-ttu-id="23d37-135">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23d37-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="23d37-136">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23d37-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="23d37-137">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23d37-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="23d37-138">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23d37-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="23d37-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="23d37-139">See also</span></span>

- [<span data-ttu-id="23d37-140">ICorDebugSymbolProvider2 接口</span><span class="sxs-lookup"><span data-stu-id="23d37-140">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="23d37-141">调试接口</span><span class="sxs-lookup"><span data-stu-id="23d37-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
