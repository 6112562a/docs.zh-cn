---
title: 创建 Game1 类
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: c96fa846d11947af03faec26dd6de99e0aeec052
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452792"
---
# <a name="creating-the-game1-class"></a>创建 Game1 类
在所有的 Microsoft XNA 项目中，Game1 类都派生自 [Microsoft.Xna.Framework.Game](https://docs.microsoft.com/previous-versions/windows/xna/bb197040%28v%3dxnagamestudio.41%29) 类，后者提供了 XNA 游戏的基本图形设备初始化、游戏逻辑和呈现代码。 Game1 类相对简单，因为大部分工作是在 GamePiece 和 GamePieceCollection 类中完成的。  
  
## <a name="creating-the-code"></a>创建代码  
 该类的私有成员包括用于保存游戏块的 GamePieceCollection 对象、[GraphicsDeviceManager](https://docs.microsoft.com/previous-versions/windows/xna/bb197317%28v%3dxnagamestudio.41%29) 对象和用于呈现游戏块的 [SpriteBatch](https://docs.microsoft.com/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29)。  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 在游戏初始化期间，这些对象被实例化。  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 调用 [LoadContent](https://docs.microsoft.com/previous-versions/windows/xna/bb975766%28v%3dxnagamestudio.41%29) 方法时，会创建游戏块并将其分配给 GamePieceCollection 对象。 有以下两种类型的游戏块。 略微更改这些游戏块的缩放比例，以便小块和大块同时存在。  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 游戏运行时，XNA Framework 会反复调用 [Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) 方法。 [Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) 方法会对游戏块集合调用 **ProcessInertia** 和 **UpdateFromMouse** 方法。 [创建 GamePieceCollection 类](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中介绍了这些方法。  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 游戏运行时，XNA Framework 也会反复调用 [Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) 方法。 [Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) 方法通过调用 GamePieceCollection 对象的 Draw 方法来呈现游戏块。 [创建 GamePieceCollection 类](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)中介绍了这些方法。  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>请参阅  
 [控制和惯性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [在 XNA 应用程序中使用控制和惯性](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [创建 GamePiece 类](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [创建 GamePieceCollection 类](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [完整代码清单](../../../docs/framework/common-client-technologies/full-code-listings.md)
