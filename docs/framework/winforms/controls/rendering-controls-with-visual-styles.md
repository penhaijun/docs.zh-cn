---
title: 使用视觉样式呈现控件
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: a7f2d810567d37021d5d4473204d9950d6834b9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540899"
---
# <a name="rendering-controls-with-visual-styles"></a>使用视觉样式呈现控件
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 使用操作系统中受支持的视觉样式为呈现控件和其他 Windows 用户界面 (UI) 元素提供支持。 本主题讨论 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中对使用操作系统当前视觉样式的呈现控件和其他 UI 元素提供的多种级别的支持。  
  
## <a name="rendering-classes-for-common-controls"></a>公共控件的呈现类  
 呈现控件是指绘制控件的用户界面。 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间提供了用来呈现某些公共 Windows 窗体控件的 <xref:System.Windows.Forms.ControlPaint> 类。 但是，此类以经典 Windows 样式绘制的控件，当在启用了视觉样式的应用程序中绘制自定义控件时，难以维护 UI 体验的一致性。  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]包括中的类<xref:System.Windows.Forms?displayProperty=nameWithType>呈现的部件和状态以视觉样式的公共控件的命名空间。 每个这样的类都包括使用操作系统当前视觉样式绘制控件和特定状态控件部件的 `static` 方法。  
  
 其中一些类旨在绘制相关控件，而不考虑视觉样式是否可用。 如果启用了视觉样式，类成员将使用视觉样式绘制相关控件；如果禁用了视觉样式，类成员将以经典 Windows 样式绘制控件。 这些类包括：  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 视觉样式可用时，其他类才能绘制相关控件，如果禁用了视觉样式，则类成员会引发异常。 这些类包括：  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 有关使用这些类绘制控件的详细信息，请参阅 [How to: Use a Control Rendering Class](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md)。  
  
## <a name="visual-style-element-and-rendering-classes"></a>视觉样式元素和呈现类  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> 命名空间包含用于绘制和获取视觉样式支持的任何控件或 UI 元素信息的类。 支持的控件包括在 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间中具有呈现类的公共控件（请参阅上一节）以及诸如选项卡控件和 rebar 控件的其他控件。 其他受支持的 UI 元素包括“开始”  菜单、任务栏和 Windows 非工作区的各部分。  
  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> 命名空间的主要类为 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 和 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>。 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 是一个基础类，用于标识视觉样式支持的任何控件或用户界面元素。 除了 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 本身，<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> 命名空间包含许多 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 嵌套类，这些类具有为视觉样式支持的控件、控件部件或其他 UI 元素的状态返回 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 的 `static` 属性。  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 提供一些方法，这些方法可以绘制和获取由操作系统当前视觉样式定义的每个 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> 的信息。 可以检索的元素信息包括其默认大小、背景类型和颜色定义。 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 包装来自 Windows Platform SDK 的 Windows Shell 部分的视觉样式 (UxTheme) API 的功能。 有关详细信息，请参阅[使用 Windows XP 视觉样式](https://msdn.microsoft.com/library/ms997649.aspx)。  
  
 有关使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 和 <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>的详细信息，请参阅 [How to: Render a Visual Style Element](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md)。  
  
## <a name="enabling-visual-styles"></a>启用视觉样式  
 若要为针对 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本 1.0 编写的应用程序启用视觉样式，程序员必须将应用清单包含进来。该清单指定使用 ComCtl32.dll 版本 6 或更高版本绘制控件。 使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本 1.1 或更高版本生成的应用可以使用 <xref:System.Windows.Forms.Application> 类的 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法。  
  
## <a name="checking-for-visual-styles-support"></a>检查视觉样式支持  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> 类的 <xref:System.Windows.Forms.Application> 属性指示当前应用程序是否正在使用视觉样式绘制控件。 绘制自定义控件时，可以检查 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> 的值来确定是否应使用视觉样式呈现控件。 下表列出了 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> 返回 `true`必须存在的四个条件。  
  
|条件|说明|  
|---------------|-----------|  
|操作系统支持视觉样式。|若要单独验证这种情况，请使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> 类的 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> 属性。|  
|用户已在操作系统中启用视觉样式。|若要单独验证这种情况，请使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> 类的 <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> 属性。|  
|应用程序中已启用视觉样式。|可以通过调用 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法或使用指定用 ComCtl32.dll 版本 6 或更高版本绘制控件的应用程序清单来启用应用程序中的视觉样式。|  
|正在使用视觉样式来绘制应用程序窗口的工作区。|若要单独验证这种情况，请使用 <xref:System.Windows.Forms.Application> 类的 <xref:System.Windows.Forms.Application.VisualStyleState%2A> 属性，验证它是否具有 <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType> 值。|  
  
 若要确定用户何时启用或禁用视觉样式，或何时从一种视觉样式切换到另种，请检查 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> 或 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> 事件处理程序中的 <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> 值。  
  
> [!IMPORTANT]
>  如果想要在用户启用或切换视觉样式时使用 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 来呈现控件或 UI 元素，请确保在处理 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件而非 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> 事件时这样做。 处理 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> 时如果使用 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>类，则会引发异常。  
  
## <a name="see-also"></a>请参阅  
 [自定义控件的绘制和呈现](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)
