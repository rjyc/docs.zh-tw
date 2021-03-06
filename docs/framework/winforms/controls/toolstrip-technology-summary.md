---
title: "ToolStrip 技術摘要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "功能表 [Windows Form], 技術摘要"
  - "狀態列, 技術摘要"
  - "工具列 [Windows Form], 技術摘要"
  - "ToolStrip 控制項 [Windows Forms], 技術摘要"
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# ToolStrip 技術摘要
本主題提供有關 `ToolStrip` 控制項及支援這些控制項之類別的摘要資訊。  
  
 `ToolStrip` 控制項以及與其相關聯的類別提供了完整的解決方案，可用於建立工具列、 狀態列和功能表。  
  
## 命名空間  
 <xref:System.Windows.Forms?displayProperty=fullName>  
  
## 背景  
 有了 `ToolStrip` 控制項以及與其相關聯的類別，您可以建立具有一致且專業的外觀和行為的進階工具列功能。   `ToolStrip` 控制項和類別透過先前的控制項提供下列改良功能：  
  
-   更一致的事件模型。  
  
-   更一致的設計階段行為，其中包含工作清單和項目集合編輯器。  
  
-   使用 `ToolStripManager` 和 `ToolStripRenderer` 來自訂轉譯。  
  
-   以 `ToolStripContainer` 和 `ToolStripPanel` 來進行內建浮動定位 \(共用停駐時工具區域內的水平或垂直空間\)。  
  
-   設計階段和執行階段具有 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> 屬性的項目重新排列。  
  
-   項目重新配置到具有 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> 屬性的溢位功能表。  
  
-   具有 `ToolStripContainer` 、 `ToolStripPanel` 與 `ToolStripContentPanel` 的完全可設定之控制位置。  
  
-   傳統的 `ToolStrip` 之裝載，或使用 `ToolStripControlHost` 的自訂控制項。  
  
-   合併使用 `ToolStripPanel` 的 `ToolStrip` 控制項。  
  
 `ToolStrip` 是 `MenuStrip`、`ContextMenuStrip` 和 `StatusStrip` 的可擴充基底類別。  這些控制項是 <xref:System.Windows.Forms.ToolStripItem> 容器，它們繼承了一般行為和事件處理、擴充以便讓每個實作處理適合它的行為。  衍生自 <xref:System.Windows.Forms.ToolStripItem> 的控制項如下表所示。  基底 `ToolStrip` 類別處理繪製、 使用者輸入，以及這些控制項的拖放事件。  
  
 `ToolStrip` 、 `MenuStrip` 、 `ContextMenuStrip` 和 `StatusStrip` 控制項取代先前的工具列、 功能表、捷徑功能表和狀態列控制項，雖然這些控制項是被保留來確保回溯相容性。  
  
## ToolStrip 類別簡介  
 下表顯示依技術領域分組的 ToolStrip 類別。  
  
|技術範圍|類別|  
|----------|--------|  
|工具列、 狀態和功能表容器|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|ToolStrip 項目|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|位置|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|展示和轉譯|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## ToolStrip 設計階段功能  
 <xref:System.Windows.Forms.ToolStrip> 家族控制項提供一組豐富的工具和範本，它能夠就地編輯和定義使用者介面的基礎，讓您可以快速建立實用的應用程式。  
  
### 工作對話方塊  
 在 Visual Studio 中，按一下設計工具中控制項上的智慧標籤會顯示工作清單中，以便存取許多常用的命令。  
  
-   [MenuStrip 工作對話方塊](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [ToolStrip 工作對話方塊](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [ContextMenuStrip 工作對話方塊](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [StatusStrip 工作對話方塊](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [ToolStripContainer 工作對話方塊](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### 項目集合編輯器  
 在 Visual Studio 中，當您按一下工作清單上的 \[編輯項目\] ，或以滑鼠右鍵按一下控制項，然後選取快顯功能表中的 \[編輯項目\]，控制項的集合編輯器會隨即出現。  集合編輯器可讓您新增、 移除和重新排列控制項包含的項目。  您也可以檢視和變更控制項與控制項項目的屬性。  
  
-   [MenuStrip 項目集合編輯器](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [StatusStrip 項目集合編輯器](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [ContextMenuStrip 項目集合編輯器](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [ToolStrip Items 項目集合編輯器](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## 裝載控制項  
 <xref:System.Windows.Forms.ToolStripControlHost> 類別會提供內建的包裝函式給 <xref:System.Windows.Forms.ToolStripComboBox> 、 <xref:System.Windows.Forms.ToolStripTextBox> 和 <xref:System.Windows.Forms.ToolStripProgressBar> 控制項。  您也可以裝載任何其他現有或者 <xref:System.Windows.Forms.ToolStripControlHost> 中的 COM 控制項。  
  
 如需控制項裝載的範例，請參閱[如何：使用 ToolStripControlHost 為 Windows Form 控制項換行](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md)。  
  
## 正在轉譯  
 <xref:System.Windows.Forms.ToolStrip> 類別會實作明顯不同於其他的 Windows Form 控制項的轉譯配置。  透過這種配置，您可以輕鬆地套用樣式和主題。  
  
 要套用樣式到 <xref:System.Windows.Forms.ToolStrip> 和它所包含的所有 <xref:System.Windows.Forms.ToolStripItem> 物件，您不必針對每個項目處理 <xref:System.Windows.Forms.ToolStripItem.Paint> 事件。  相反地，您可以把 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 屬性設定為 <xref:System.Windows.Forms.ToolStripRenderMode> 以外任何一個 <xref:System.Windows.Forms.ToolStripRenderMode> 的值。  或者，您可以把 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 直接設定成繼承自 <xref:System.Windows.Forms.ToolStripRenderer> 類別的任何類別。  設定這個屬性會自動設定 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>。  
  
 您可以將相同的樣式套用至多個相同的應用程式中的 <xref:System.Windows.Forms.ToolStrip> 物件，這可以藉由把 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 設定為 <xref:System.Windows.Forms.ToolStripRenderMode>以及分別把 <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> 或 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> 屬性設定為您想要的 <xref:System.Windows.Forms.ToolStripManagerRenderMode> 或 <xref:System.Windows.Forms.ToolStripRenderer> 值。  
  
 如需呈現的範例，請參閱[如何：建立和設定 Windows Form 中的 ToolStrip 控制項自訂產生器](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)。  
  
## 樣式和主題  
 <xref:System.Windows.Forms.ToolStrip> 以及關聯的類別可讓您輕鬆支援視覺化樣式和自訂外觀，而且不需要覆寫 <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> 方法的每個項目。  使用 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 和 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 屬性。  
  
## 浮動定位和停駐  
 您可以浮動定位、停駐或絕對定位 <xref:System.Windows.Forms.ToolStrip> 控制項。  <xref:System.Windows.Forms.ToolStrip> 項目由容器中的 <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> 來配置版面。  
  
 *浮動定位*是工具列共用水平或垂直空間的能力。  Windows Form 的 <xref:System.Windows.Forms.ToolStripContainer> 可以反過來有個面板，它可以在表單的左邊、 右邊、 上方和下方，並且用來定位和浮動定位 <xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項。  如果您將多個 <xref:System.Windows.Forms.ToolStrip> 控制項放在左邊或右邊 <xref:System.Windows.Forms.ToolStripContainer>，它們會垂直堆疊。  如果您將它們放在頂端或底端 <xref:System.Windows.Forms.ToolStripContainer>，它們會水平堆疊。  您可以使用 <xref:System.Windows.Forms.ToolStripContainer> 的中央 <xref:System.Windows.Forms.ToolStripContentPanel>來定位在表單上的傳統控制項。  
  
 任何或所有 <xref:System.Windows.Forms.ToolStripContainer> 控制項可直接在設計階段選取，而且可以刪除。  <xref:System.Windows.Forms.ToolStripContainer> 可展開及摺疊，並且可以使用它所包含的控制項調整大小。  
  
 *「停駐」*\(Docking\) 是在表單的左邊、 右邊、 上方，或底部指定控制項的簡單位置。  
  
 透過停駐來浮動定位的優點在於 <xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項可以與其他控制項共用水平或垂直空間。  
  
 大部分的 <xref:System.Windows.Forms.ToolStrip> 控制項能夠如同其他控制項被定位到表單，而不使用浮動定位。  您也可以藉由將 <xref:System.Windows.Forms.ToolStrip> 控制項從它的 <xref:System.Windows.Forms.ToolStripContainer> 移出並且將 `Dock` 屬性設定為 `None`， 來指定它放置在表單的任意位置上，或者藉由個別設定 <xref:System.Windows.Forms.Control.Location%2A> 屬性來指定它的絕對位置。  請參閱[如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md)。  
  
 使用一或多個 <xref:System.Windows.Forms.ToolStripPanel> 控制項來獲得更大的彈性，特別是針對多重文件介面 \(MDI\) 應用程式，或如果您不需要 <xref:System.Windows.Forms.ToolStripContainer>。  <xref:System.Windows.Forms.ToolStripPanel> 提供一個可停駐空間來定位及浮動定位除了傳統控制項的 <xref:System.Windows.Forms.ToolStrip> 控制項。  根據預設，<xref:System.Windows.Forms.ToolStripPanel> 不會出現在設計工具 \[工具箱\]  中，但您可以把它放在那裡，只需要在 \[工具箱\] 按一下滑鼠右鍵，然後按一下 \[選擇項目\]。  您也以程式設計方式存取與 <xref:System.Windows.Forms.ToolStripPanel> 相似的任何其他類別。  
  
 <xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.StatusStrip> 讓項目溢位。  這與在 Microsoft Office 工具列上那些項目的使用方式類似。  
  
## 請參閱  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)