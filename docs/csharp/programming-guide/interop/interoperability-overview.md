---
title: 互操作性概述（C# 编程指南）
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 0bd53d97cec4370adc78fc715b1cea5ee5a3fd6f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2018
ms.locfileid: "44208791"
---
# <a name="interoperability-overview-c-programming-guide"></a>互操作性概述（C# 编程指南）
本主题描述在 C# 托管代码和非托管代码之间实现互操作性的方法。  
  
## <a name="platform-invoke"></a>平台调用  
 平台调用是一项服务，它使托管代码能够调用动态链接库 (DLL) 中实现的非托管函数，例如 Microsoft Win32 API 中的非托管函数。 此服务定位并调用导出的函数，并根据需要跨交互操作边界封送其自变量（整数、字符串、数组、结构等）。  
  
 有关详细信息，请参阅[使用非托管 DLL 函数](../../../framework/interop/consuming-unmanaged-dll-functions.md)和[如何：使用平台调用播放波形文件](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)。  
  
> [!NOTE]
>  [公共语言运行时](../../../standard/clr.md) (CLR) 管理对系统资源的访问。 调用 CLR 外部的非托管代码将避开这种安全机制，因此会带来安全风险。 例如，非托管代码可能直接调用非托管代码中的资源，从而避开 CLR 安全机制。 有关详细信息，请参阅 [ .NET 中的安全性](../../../standard/security/index.md)。  
  
## <a name="c-interop"></a>C++ 互操作  
 可使用 C++ interop（又称为 It Just Works (IJW)）包装本机 C++ 类，以便用 C# 或其他 .NET Framework 语言编写的代码可以使用此类。 为此，请编写 C++ 代码来包装本机 DLL 或 COM 组件。 与其他 .NET Framework 语言不同，[!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] 具有互操作性支持，可使托管和非托管代码放置在同一个应用程序（甚至同一个文件）中。 然后使用 **/clr** 编译器开关生成托管程序集，以便生成 C++ 代码。 最后，在 C# 项目中添加一个对该程序集的引用，并像使用其他托管类那样使用被包装对象。  
  
## <a name="exposing-com-components-to-c"></a>向 C# 公开 COM 组件  
 可以使用 C# 项目中的 COM 组件。 常规步骤如下所示：  
  
1.  找到要使用的 COM 组件并注册。 使用 regsvr32.exe 注册或注销 COM DLL。  
  
2.  向项目添加对 COM 组件或类型库的引用。  
  
     添加引用时，Visual Studio 使用 [Tlbimp.exe（类型库导入程序）](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)。此程序需要使用类型库作为输入，以输出 .NET Framework 互操作程序集。 该程序集又称为运行时可调用包装器 (RCW)，其中包含包装类型库中的 COM 类和接口的托管类和接口。 Visual Studio 向项目添加对生成程序集的引用。  
  
3.  创建在 RCW 中定义的类的实例。 这会创建 COM 对象的实例。  
  
4.  像使用其他托管对象那样使用该对象。 当垃圾回收对该对象进行回收后，COM 对象的实例也会从内存中释放出来。  
  
 有关详细信息，请参阅[向 .NET Framework 公开 COM 组件](../../../../docs/framework/interop/exposing-com-components.md)。  
  
## <a name="exposing-c-to-com"></a>向 COM 公开 C#  
 COM 客户端可以使用已经正确公开的 C# 类型。 公开 C# 类型的基本步骤如下所示：  
  
1.  在 C# 项目中添加互操作特性。  
  
     可通过修改 Visual C# 项目属性使程序集 COM 可见。 有关详细信息，请参阅[“程序集信息”对话框](/visualstudio/ide/reference/assembly-information-dialog-box)。  
  
2.  生成 COM 类型库并对它进行注册以供 COM 使用。  
  
     可修改 Visual C# 项目属性以自动注册 COM 互操作的 C# 程序集。 Visual Studio 通过 `/tlb` 命令行开关使用 [Regasm.exe（程序集注册工具）](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)。此工具使用托管组件作为输入，以生成类型库。 此类型库描述程序集中的 `public` 类型并添加注册表项，以便 COM 客户端可以创建托管类。  
  
 有关详细信息，请参阅[向 COM 公开 .NET Framework 组件](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)和 [COM 类示例](../../../csharp/programming-guide/interop/example-com-class.md)。  
  
## <a name="see-also"></a>请参阅

- [Improving Interop Performance](https://msdn.microsoft.com/library/ms998551.aspx)（提高互操作性能）  
- [COM 和 .NET 之间的互操作性简介](https://msdn.microsoft.com/library/office/bb610378.aspx)  
- [Visual Basic 中的 COM 互操作简介](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
- [托管代码与非托管代码之间的封送处理](../../../../docs/framework/interop/interop-marshaling.md)  
- [与非托管代码交互操作](../../../../docs/framework/interop/index.md)  
- [C# 编程指南](../../../csharp/programming-guide/index.md)
