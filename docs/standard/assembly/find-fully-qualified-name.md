---
title: 如何：查找程序集的完全限定名
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 4fc670adc80a6f4ce7b36074185dcd3bb85fbc67
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991315"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="8366e-102">如何：查找程序集的完全限定名</span><span class="sxs-lookup"><span data-stu-id="8366e-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="8366e-103">若要在全局程序集缓存中查找某个 .NET Framework 程序集的完全限定名，请使用全局程序集缓存工具 ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md))。</span><span class="sxs-lookup"><span data-stu-id="8366e-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="8366e-104">请参阅[如何：查看全局程序集缓存的内容](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="8366e-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="8366e-105">对于 .NET Core 程序集，以及对于不在全局程序集缓存中的 .NET Framework 程序集，可以通过多种方式获取完全限定的程序集名称：</span><span class="sxs-lookup"><span data-stu-id="8366e-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="8366e-106">可使用代码将信息输出到控制台或变量，或者使用 [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) 检查程序集的元数据（其中包含了完全限定名）。</span><span class="sxs-lookup"><span data-stu-id="8366e-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="8366e-107">如果应用程序已加载程序集，则可检索 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 属性的值在以获取完全限定名。</span><span class="sxs-lookup"><span data-stu-id="8366e-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="8366e-108">可以使用该程序集中定义的 <xref:System.Type> 的 <xref:System.Type.Assembly> 属性来检索对 <xref:System.Reflection.Assembly> 对象的引用。</span><span class="sxs-lookup"><span data-stu-id="8366e-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="8366e-109">说明如示例所示。</span><span class="sxs-lookup"><span data-stu-id="8366e-109">The example provides an illustration.</span></span>

- <span data-ttu-id="8366e-110">如果知道程序集的文件系统路径，则可调用 `static` (C#) 或 `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法获取完全限定的程序集名称。</span><span class="sxs-lookup"><span data-stu-id="8366e-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="8366e-111">下面是一个简单的示例。</span><span class="sxs-lookup"><span data-stu-id="8366e-111">The following is a simple example.</span></span>

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- <span data-ttu-id="8366e-112">可使用 [Ildasm.exe（IL 反汇编程序）](../../framework/tools/ildasm-exe-il-disassembler.md)检查包含完全限定名的程序集元数据。</span><span class="sxs-lookup"><span data-stu-id="8366e-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="8366e-113">有关设置程序集属性（如版本、区域性和程序集名称）的详细信息，请参阅[设置程序集属性](set-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="8366e-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="8366e-114">有关为程序集提供强名称的详细信息，请参阅[创建并使用强名称程序集](create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="8366e-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="8366e-115">示例</span><span class="sxs-lookup"><span data-stu-id="8366e-115">Example</span></span>

<span data-ttu-id="8366e-116">下例演示了如何向控制台显示包含指定类的程序集的完全限定名。</span><span class="sxs-lookup"><span data-stu-id="8366e-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="8366e-117">它使用 <xref:System.Type.Assembly?displayProperty=nameWithType> 属性从该程序集中定义的类型检索对程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="8366e-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="8366e-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="8366e-118">See also</span></span>

- [<span data-ttu-id="8366e-119">程序集名称</span><span class="sxs-lookup"><span data-stu-id="8366e-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="8366e-120">创建程序集</span><span class="sxs-lookup"><span data-stu-id="8366e-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="8366e-121">创建和使用具有强名称的程序集</span><span class="sxs-lookup"><span data-stu-id="8366e-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="8366e-122">全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="8366e-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="8366e-123">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="8366e-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="8366e-124">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="8366e-124">Program with assemblies</span></span>](program.md)