---
title: 如何：将程序集安装到全局程序集缓存
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972869"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="4f12c-102">如何：将程序集安装到全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="4f12c-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="4f12c-103">全局程序集缓存 (GAC) 存储由多个应用程序共享的程序集。</span><span class="sxs-lookup"><span data-stu-id="4f12c-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="4f12c-104">使用以下任一组件将程序集安装到[全局程序集缓存](gac.md)中：</span><span class="sxs-lookup"><span data-stu-id="4f12c-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="4f12c-105">Windows 安装程序</span><span class="sxs-lookup"><span data-stu-id="4f12c-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="4f12c-106">全局程序集缓存工具</span><span class="sxs-lookup"><span data-stu-id="4f12c-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="4f12c-107">可以只将强名称程序集安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="4f12c-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="4f12c-108">有关如何创建强名称程序集的信息，请参阅[如何：使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="4f12c-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="4f12c-109">Windows Installer</span></span>

<span data-ttu-id="4f12c-110">建议使用 [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)（即 Windows 安装引擎）将程序集添加到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="4f12c-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="4f12c-111">Windows Installer 可提供全局程序集缓存中程序集的引用计数，还具有其他优点。</span><span class="sxs-lookup"><span data-stu-id="4f12c-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="4f12c-112">若要创建 Windows Installer 的安装程序包，请使用[适用于 Visual Studio 2017 的 WiX 工具集扩展](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="4f12c-113">全局程序集缓存工具</span><span class="sxs-lookup"><span data-stu-id="4f12c-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="4f12c-114">可以使用 [.NET 全局程序集实用程序 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 将程序集添加到全局程序集缓存，并查看全局程序集缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="4f12c-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4f12c-115">Gacutil.exe 仅用于开发目的。</span><span class="sxs-lookup"><span data-stu-id="4f12c-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="4f12c-116">请勿用于将生产程序集安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="4f12c-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="4f12c-117">使用 gacutil.exe 在 GAC 中安装程序集的语法如下：</span><span class="sxs-lookup"><span data-stu-id="4f12c-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="4f12c-118">在此命令中，\<assembly name> 是要在全局程序集缓存中安装的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="4f12c-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="4f12c-119">如果 gacutil.exe 不在系统路径中，则使用 [VS 开发人员命令提示符\<版本>](../tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f12c-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="4f12c-120">下面的示例将文件名为 hello.dll 的程序集安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="4f12c-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="4f12c-121">在 .NET Framework 的早期版本中，可以使用 Shfusion.dll Windows 外壳扩展通过将程序集拖到“文件资源管理器”来安装这些程序集。</span><span class="sxs-lookup"><span data-stu-id="4f12c-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="4f12c-122">从 .NET Framework 4 开始，Shfusion.dll 已过时。</span><span class="sxs-lookup"><span data-stu-id="4f12c-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f12c-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="4f12c-123">See also</span></span>

- [<span data-ttu-id="4f12c-124">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="4f12c-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="4f12c-125">如何：从全局程序集缓存中删除程序集</span><span class="sxs-lookup"><span data-stu-id="4f12c-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="4f12c-126">Gacutil.exe（全局程序集缓存工具）</span><span class="sxs-lookup"><span data-stu-id="4f12c-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="4f12c-127">如何：使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="4f12c-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)