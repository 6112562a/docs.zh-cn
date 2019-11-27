---
title: 字符数据类型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346392"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="9365c-102">字符数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9365c-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="9365c-103">Visual Basic 提供了用于处理可打印和可显示字符的*字符数据类型*。</span><span class="sxs-lookup"><span data-stu-id="9365c-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="9365c-104">虽然这两种方法都处理 Unicode 字符，但 `Char` 会保留一个字符，而 `String` 包含无数个字符。</span><span class="sxs-lookup"><span data-stu-id="9365c-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="9365c-105">有关显示 Visual Basic 数据类型的并行比较的表，请参阅[数据类型](../../../../visual-basic/language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9365c-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="9365c-106">Char 类型</span><span class="sxs-lookup"><span data-stu-id="9365c-106">Char Type</span></span>  
 <span data-ttu-id="9365c-107">`Char` 的数据类型是单个双字节（16位） Unicode 字符。</span><span class="sxs-lookup"><span data-stu-id="9365c-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="9365c-108">如果变量始终只存储一个字符，则将其声明为 `Char`。</span><span class="sxs-lookup"><span data-stu-id="9365c-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="9365c-109">例如：</span><span class="sxs-lookup"><span data-stu-id="9365c-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="9365c-110">`Char` 或 `String` 变量中的每个可能值都是 Unicode 字符集中的一个*码位*或字符代码。</span><span class="sxs-lookup"><span data-stu-id="9365c-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="9365c-111">Unicode 字符包含基本 ASCII 字符集、各种其他字母数字、重音、货币符号、分数、音调符号和数学符号以及技术符号。</span><span class="sxs-lookup"><span data-stu-id="9365c-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9365c-112">Unicode 字符集为*代理项对*保留了 D800 到 DFFF （55296到 55551 decimal）的代码点，这需要 2 16 位值来表示单个码位。</span><span class="sxs-lookup"><span data-stu-id="9365c-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="9365c-113">`Char` 变量不能包含代理项对，`String` 使用两个位置来保存这两个位置对。</span><span class="sxs-lookup"><span data-stu-id="9365c-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="9365c-114">有关详细信息，请参阅[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="9365c-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="9365c-115">字符串类型</span><span class="sxs-lookup"><span data-stu-id="9365c-115">String Type</span></span>  
 <span data-ttu-id="9365c-116">`String` 的数据类型是由零个或多个双字节（16位） Unicode 字符组成的序列。</span><span class="sxs-lookup"><span data-stu-id="9365c-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="9365c-117">如果变量可以包含无限数量的字符，则将其声明为 `String`。</span><span class="sxs-lookup"><span data-stu-id="9365c-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="9365c-118">例如：</span><span class="sxs-lookup"><span data-stu-id="9365c-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="9365c-119">有关详细信息，请参阅[String 数据类型](../../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="9365c-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9365c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9365c-120">See also</span></span>

- [<span data-ttu-id="9365c-121">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="9365c-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="9365c-122">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="9365c-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="9365c-123">Visual Basic 中的泛型类型</span><span class="sxs-lookup"><span data-stu-id="9365c-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9365c-124">值类型和引用类型</span><span class="sxs-lookup"><span data-stu-id="9365c-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="9365c-125">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="9365c-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="9365c-126">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="9365c-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="9365c-127">类型字符</span><span class="sxs-lookup"><span data-stu-id="9365c-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
