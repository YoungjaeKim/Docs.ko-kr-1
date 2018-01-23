---
uid: identity/overview/extensibility/change-primary-key-for-users-in-aspnet-identity
title: "ASP.NET Identity에서 사용자에 대 한 기본 키를 변경 합니다. | Microsoft Docs"
author: tfitzmac
description: "Visual Studio 2013에서 기본 웹 응용 프로그램 사용자 계정에 대 한 키에 대 한 문자열 값을 사용합니다. ASP.NET Id를 사용 하면의 형식을 변경 하는 중..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 09/30/2014
ms.topic: article
ms.assetid: 44925849-5762-4504-a8cd-8f0cd06f6dc3
ms.technology: 
ms.prod: .net-framework
msc.legacyurl: /identity/overview/extensibility/change-primary-key-for-users-in-aspnet-identity
msc.type: authoredcontent
ms.openlocfilehash: 79812efb4de2461fad3765d6005bbd20393e62b2
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2017
---
<a name="change-primary-key-for-users-in-aspnet-identity"></a><span data-ttu-id="0dfe7-104">ASP.NET Identity에서 사용자에 대 한 기본 키를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-104">Change Primary Key for Users in ASP.NET Identity</span></span>
====================
<span data-ttu-id="0dfe7-105">으로 [Tom FitzMacken](https://github.com/tfitzmac)</span><span class="sxs-lookup"><span data-stu-id="0dfe7-105">by [Tom FitzMacken](https://github.com/tfitzmac)</span></span>

> <span data-ttu-id="0dfe7-106">Visual Studio 2013에서 기본 웹 응용 프로그램 사용자 계정에 대 한 키에 대 한 문자열 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-106">In Visual Studio 2013, the default web application uses a string value for the key for user accounts.</span></span> <span data-ttu-id="0dfe7-107">ASP.NET Id를 사용 하면 데이터 요구 사항을 충족 하기 위해 키 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-107">ASP.NET Identity enables you to change the type of the key to meet your data requirements.</span></span> <span data-ttu-id="0dfe7-108">예를 들어 키의 형식 문자열에서 정수로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-108">For example, you can change the type of the key from a string to an integer.</span></span>
> 
> <span data-ttu-id="0dfe7-109">이 항목에서는 기본 웹 응용 프로그램 및 사용자 계정 키를 정수로 변경 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-109">This topic shows how to start with the default web application and change the user account key to an integer.</span></span> <span data-ttu-id="0dfe7-110">프로젝트에서 모든 유형의 키를 구현 하기 위해 수정에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-110">You can use the same modifications to implement any type of key in your project.</span></span> <span data-ttu-id="0dfe7-111">기본 웹 응용 프로그램에서 이러한 변경을 수행 하는 방법을 보여 줍니다 하지만 사용자 지정된 응용 프로그램에 비슷한 수정 사항을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-111">It shows how to make these changes in the default web application, but you could apply similar modifications to a customized application.</span></span> <span data-ttu-id="0dfe7-112">MVC 또는 Web Forms에서 작업할 때 필요한 변경 사항을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-112">It shows the changes needed when working with MVC or Web Forms.</span></span>
> 
> ## <a name="software-versions-used-in-the-tutorial"></a><span data-ttu-id="0dfe7-113">자습서에서 사용 되는 소프트웨어 버전</span><span class="sxs-lookup"><span data-stu-id="0dfe7-113">Software versions used in the tutorial</span></span>
> 
> 
> - <span data-ttu-id="0dfe7-114">Visual Studio 2013 업데이트 2 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="0dfe7-114">Visual Studio 2013 with Update 2 (or later)</span></span>
> - <span data-ttu-id="0dfe7-115">ASP.NET Identity 2.1 이상</span><span class="sxs-lookup"><span data-stu-id="0dfe7-115">ASP.NET Identity 2.1 or later</span></span>


<span data-ttu-id="0dfe7-116">이 자습서의 단계를 수행 하려면 Visual Studio 2013 업데이트 2 (또는 이상) 및 ASP.NET 웹 응용 프로그램 템플릿에서 만든 웹 응용 프로그램이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-116">To perform the steps in this tutorial, you must have Visual Studio 2013 Update 2 (or later), and a web application created from the ASP.NET Web Application template.</span></span> <span data-ttu-id="0dfe7-117">업데이트 3에서 변경 하는 템플릿.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-117">The template changed in Update 3.</span></span> <span data-ttu-id="0dfe7-118">이 항목에서는 업데이트 2와 업데이트 3에서 서식 파일을 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-118">This topic shows how to change the template in Update 2 and Update 3.</span></span>

<span data-ttu-id="0dfe7-119">이 항목에는 다음과 같은 단원이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-119">This topic contains the following sections:</span></span>

- [<span data-ttu-id="0dfe7-120">Id 사용자 클래스에서 키의 형식 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-120">Change the type of the key in the Identity user class</span></span>](#userclass)
- [<span data-ttu-id="0dfe7-121">키 유형을 사용 하는 사용자 지정 된 Id 클래스 추가</span><span class="sxs-lookup"><span data-stu-id="0dfe7-121">Add customized Identity classes that use the key type</span></span>](#customclass)
- [<span data-ttu-id="0dfe7-122">키 유형을 사용 하는 상황에 맞는 클래스 및 사용자 관리자 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-122">Change the context class and user manager to use the key type</span></span>](#context)
- [<span data-ttu-id="0dfe7-123">시작 키 유형을 사용 하는 구성 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-123">Change start-up configuration to use the key type</span></span>](#startup)
- [<span data-ttu-id="0dfe7-124">MVC 업데이트 2에 대 한 키 형식을 전달할 AccountController 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-124">For MVC with Update 2, change the AccountController to pass the key type</span></span>](#mvcupdate2)
- [<span data-ttu-id="0dfe7-125">MVC 업데이트 3에 대 한 키 형식을 전달할 AccountController 및 ManageController 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-125">For MVC with Update 3, change the AccountController and ManageController to pass the key type</span></span>](#mvcupdate3)
- [<span data-ttu-id="0dfe7-126">업데이트 2의 Web Forms에 대 한 키 형식을 전달할 계정 페이지를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-126">For Web Forms with Update 2, change Account pages to pass the key type</span></span>](#webformsupdate2)
- [<span data-ttu-id="0dfe7-127">업데이트 3 Web Forms에 대 한 키 형식을 전달할 계정 페이지를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-127">For Web Forms with Update 3, change Account pages to pass the key type</span></span>](#webformsupdate3)
- [<span data-ttu-id="0dfe7-128">응용 프로그램 실행</span><span class="sxs-lookup"><span data-stu-id="0dfe7-128">Run application</span></span>](#run)
- [<span data-ttu-id="0dfe7-129">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="0dfe7-129">Other resources</span></span>](#other)

<a id="userclass"></a>
## <a name="change-the-type-of-the-key-in-the-identity-user-class"></a><span data-ttu-id="0dfe7-130">Id 사용자 클래스에서 키의 형식 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-130">Change the type of the key in the Identity user class</span></span>

<span data-ttu-id="0dfe7-131">ASP.NET 웹 응용 프로그램 템플릿에서 만들어진 프로젝트에 ApplicationUser 클래스는 정수를 사용 하 여 사용자 계정에 대 한 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-131">In your project created from the ASP.NET Web Application template, specify that the ApplicationUser class uses an integer for the key for user accounts.</span></span> <span data-ttu-id="0dfe7-132">IdentityModels.cs, 변경의 형식을 갖는 IdentityUser 상속할 ApplicationUser 클래스 **int** TKey 제네릭 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-132">In IdentityModels.cs, change the ApplicationUser class to inherit from IdentityUser that has a type of **int** for the TKey generic parameter.</span></span> <span data-ttu-id="0dfe7-133">아직 구현 하지는 세 가지 사용자 지정 된 클래스의 이름을 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-133">You also pass the names of three customized class which you have not implemented yet.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample1.cs?highlight=1-2)]

<span data-ttu-id="0dfe7-134">키의 형식 변경 하지만 기본적으로 응용 프로그램의 나머지 부분은 여전히 가정 키는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-134">You have changed the type of the key, but, by default, the rest of the application still assumes the key is a string.</span></span> <span data-ttu-id="0dfe7-135">명시적으로 문자열로 가정 하는 코드에서 키의 형식을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-135">You must explicitly indicate the type of the key in code that assumes a string.</span></span>

<span data-ttu-id="0dfe7-136">에 **ApplicationUser** 클래스, 변경의 **GenerateUserIdentityAsync** 메서드 아래 강조 표시 된 코드에 나와 있는 것 처럼 int를 포함 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-136">In the **ApplicationUser** class, change the **GenerateUserIdentityAsync** method to include int, as shown in the highlighted code below.</span></span> <span data-ttu-id="0dfe7-137">이 변경 내용을 업데이트 3 템플릿 사용 하 여 Web Forms 프로젝트에 대 한 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-137">This change is not necessary for Web Forms projects with the Update 3 template.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample2.cs?highlight=2)]

<a id="customclass"></a>
## <a name="add-customized-identity-classes-that-use-the-key-type"></a><span data-ttu-id="0dfe7-138">키 유형을 사용 하는 사용자 지정 된 Id 클래스 추가</span><span class="sxs-lookup"><span data-stu-id="0dfe7-138">Add customized Identity classes that use the key type</span></span>

<span data-ttu-id="0dfe7-139">IdentityUserRole, IdentityUserClaim, IdentityUserLogin, IdentityRole, UserStore, RoleStore, 등의 다른 Id 클래스는 여전히 문자열 키를 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-139">The other Identity classes, such as IdentityUserRole, IdentityUserClaim, IdentityUserLogin, IdentityRole, UserStore, RoleStore, are still set up to use a string key.</span></span> <span data-ttu-id="0dfe7-140">키에 대 한 정수를 지정 하는 이러한 클래스의 새 버전을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-140">Create new versions of these classes that specify an integer for the key.</span></span> <span data-ttu-id="0dfe7-141">이러한 클래스에 구현 코드를 제공할 필요가 없습니다, 주로 방금 int 키로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-141">You do not need to provide much implementation code in these classes, you are primarily just setting int as the key.</span></span>

<span data-ttu-id="0dfe7-142">IdentityModels.cs 파일에 다음 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-142">Add the following classes to your IdentityModels.cs file.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample3.cs)]

<a id="context"></a>
## <a name="change-the-context-class-and-user-manager-to-use-the-key-type"></a><span data-ttu-id="0dfe7-143">키 유형을 사용 하는 상황에 맞는 클래스 및 사용자 관리자 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-143">Change the context class and user manager to use the key type</span></span>

<span data-ttu-id="0dfe7-144">IdentityModels.cs의 정의 변경는 **ApplicationDbContext** 클래스를 사용 하 여 새 클래스를 사용자 지정 및 **int** 강조 표시 된 코드에 표시 된 키에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-144">In IdentityModels.cs, change the definition of the **ApplicationDbContext** class to use your new customized classes and an **int** for the key, as shown in the highlighted code.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample4.cs?highlight=1-2)]

<span data-ttu-id="0dfe7-145">ThrowIfV1Schema 매개 변수는 생성자에 더 이상 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-145">The ThrowIfV1Schema parameter is no longer valid in the constructor.</span></span> <span data-ttu-id="0dfe7-146">생성자를 변경 하 여 ThrowIfV1Schema 값을 전달 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-146">Change the constructor so it does not pass a ThrowIfV1Schema value.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample5.cs)]

<span data-ttu-id="0dfe7-147">IdentityConfig.cs을 열고 변경는 **ApplicationUserManger** 데이터 유지를 위한 클래스를 저장 하는 새 사용자를 사용 하는 클래스 및 **int** 키에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-147">Open IdentityConfig.cs, and change the **ApplicationUserManger** class to use your new user store class for persisting data and an **int** for the key.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample6.cs?highlight=1,3,12,14,32,37,48)]

<span data-ttu-id="0dfe7-148">업데이트 3 템플릿을 ApplicationSignInManager 클래스를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-148">In the Update 3 template, you must change the ApplicationSignInManager class.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample7.cs?highlight=1)]

<a id="startup"></a>
## <a name="change-start-up-configuration-to-use-the-key-type"></a><span data-ttu-id="0dfe7-149">시작 키 유형을 사용 하는 구성 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-149">Change start-up configuration to use the key type</span></span>

<span data-ttu-id="0dfe7-150">Startup.Auth.cs, 아래 강조 표시 된 대로 OnValidateIdentity 코드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-150">In Startup.Auth.cs, replace the OnValidateIdentity code, as highlighted below.</span></span> <span data-ttu-id="0dfe7-151">GetUserIdCallback 정의 문자열 값 구문 분석 하는 정수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-151">Notice that the getUserIdCallback definition, parses the string value into an integer.</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample8.cs?highlight=7-12)]

<span data-ttu-id="0dfe7-152">프로젝트의 제네릭 구현을 인식 하지 못합니다는 **GetUserId** 메서드를 버전 2.1에는 ASP.NET Identity NuGet 패키지를 업데이트 해야 할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="0dfe7-152">If your project does not recognize the generic implementation of the **GetUserId** method, you may need to update the ASP.NET Identity NuGet package to version 2.1</span></span>

<span data-ttu-id="0dfe7-153">ASP.NET Identity에서 사용 하는 인프라 클래스를 많이 변경 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-153">You have made a lot of changes to the infrastructure classes used by ASP.NET Identity.</span></span> <span data-ttu-id="0dfe7-154">프로젝트 컴파일 시도 하면 많은 오류를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-154">If you try compiling the project, you will notice a lot of errors.</span></span> <span data-ttu-id="0dfe7-155">다행히 나머지 오류가 모두 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-155">Fortunately, the remaining errors are all similar.</span></span> <span data-ttu-id="0dfe7-156">Id 클래스는 키에 대 한 정수 하는데 컨트롤러 (또는 Web Form)는 문자열 값을 전달 하는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-156">The Identity class expects an integer for the key, but the controller (or Web Form) is passing a string value.</span></span> <span data-ttu-id="0dfe7-157">각각의 경우에서 호출 하 여 문자열 및 정수 변환 해야 **GetUserId&lt;int&gt;**합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-157">In each case, you need to convert from a string to and integer by calling **GetUserId&lt;int&gt;**.</span></span> <span data-ttu-id="0dfe7-158">컴파일 오류 목록을 통해 작업 하거나 아래에 변경 내용에 따라 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-158">You can either work through the error list from compilation or follow the changes below.</span></span>

<span data-ttu-id="0dfe7-159">나머지 변경을 Visual Studio에 설치 된 업데이트를 만드는 프로젝트의 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-159">The remaining changes depend on the type of project you are creating and which update you have installed in Visual Studio.</span></span> <span data-ttu-id="0dfe7-160">다음 링크를 통해 관련 섹션으로 직접 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-160">You can go directly to the relevant section through the following links</span></span>

- [<span data-ttu-id="0dfe7-161">MVC 업데이트 2에 대 한 키 형식을 전달할 AccountController 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-161">For MVC with Update 2, change the AccountController to pass the key type</span></span>](#mvcupdate2)
- [<span data-ttu-id="0dfe7-162">MVC 업데이트 3에 대 한 키 형식을 전달할 AccountController 및 ManageController 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-162">For MVC with Update 3, change the AccountController and ManageController to pass the key type</span></span>](#mvcupdate3)
- [<span data-ttu-id="0dfe7-163">업데이트 2의 Web Forms에 대 한 키 형식을 전달할 계정 페이지를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-163">For Web Forms with Update 2, change Account pages to pass the key type</span></span>](#webformsupdate2)
- [<span data-ttu-id="0dfe7-164">업데이트 3 Web Forms에 대 한 키 형식을 전달할 계정 페이지를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-164">For Web Forms with Update 3, change Account pages to pass the key type</span></span>](#webformsupdate3)

<a id="mvcupdate2"></a>
## <a name="for-mvc-with-update-2-change-the-accountcontroller-to-pass-the-key-type"></a><span data-ttu-id="0dfe7-165">MVC 업데이트 2에 대 한 키 형식을 전달할 AccountController 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-165">For MVC with Update 2, change the AccountController to pass the key type</span></span>

<span data-ttu-id="0dfe7-166">AccountController.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-166">Open the AccountController.cs file.</span></span> <span data-ttu-id="0dfe7-167">다음 메서드를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-167">You need to change the following methods.</span></span>

<span data-ttu-id="0dfe7-168">**ConfirmEmail** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-168">**ConfirmEmail** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample9.cs?highlight=1,3)]

<span data-ttu-id="0dfe7-169">**한 연결을 끊을** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-169">**Disassociate** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample10.cs?highlight=5,9)]

<span data-ttu-id="0dfe7-170">**Manage(ManageUserViewModel)** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-170">**Manage(ManageUserViewModel)** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample11.cs?highlight=11,17,41)]

<span data-ttu-id="0dfe7-171">**LinkLoginCallback** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-171">**LinkLoginCallback** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample12.cs?highlight=10)]

<span data-ttu-id="0dfe7-172">**RemoveAccountList** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-172">**RemoveAccountList** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample13.cs?highlight=3)]

<span data-ttu-id="0dfe7-173">**HasPassword** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-173">**HasPassword** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample14.cs?highlight=3)]

<span data-ttu-id="0dfe7-174">이제 수 [응용 프로그램을 실행](#run) 새 사용자를 등록 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-174">You can now [run the application](#run) and register a new user.</span></span>

<a id="mvcupdate3"></a>
## <a name="for-mvc-with-update-3-change-the-accountcontroller-and-managecontroller-to-pass-the-key-type"></a><span data-ttu-id="0dfe7-175">MVC 업데이트 3에 대 한 키 형식을 전달할 AccountController 및 ManageController 변경</span><span class="sxs-lookup"><span data-stu-id="0dfe7-175">For MVC with Update 3, change the AccountController and ManageController to pass the key type</span></span>

<span data-ttu-id="0dfe7-176">AccountController.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-176">Open the AccountController.cs file.</span></span> <span data-ttu-id="0dfe7-177">다음 메서드를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-177">You need to change the following method.</span></span>

<span data-ttu-id="0dfe7-178">**ConfirmEmail** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-178">**ConfirmEmail** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample15.cs?highlight=1,3)]

<span data-ttu-id="0dfe7-179">**SendCode** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-179">**SendCode** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample16.cs?highlight=4)]

<span data-ttu-id="0dfe7-180">ManageController.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-180">Open the ManageController.cs file.</span></span> <span data-ttu-id="0dfe7-181">다음 메서드를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-181">You need to change the following methods.</span></span>

<span data-ttu-id="0dfe7-182">**인덱스** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-182">**Index** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample17.cs?highlight=15-17)]

<span data-ttu-id="0dfe7-183">**RemoveLogin** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-183">**RemoveLogin** methods</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample18.cs?highlight=3,13,17)]

<span data-ttu-id="0dfe7-184">**AddPhoneNumber** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-184">**AddPhoneNumber** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample19.cs?highlight=9)]

<span data-ttu-id="0dfe7-185">**EnableTwoFactorAuthentication** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-185">**EnableTwoFactorAuthentication** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample20.cs?highlight=3-4)]

<span data-ttu-id="0dfe7-186">**DisableTwoFactorAuthentication** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-186">**DisableTwoFactorAuthentication** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample21.cs?highlight=3-4)]

<span data-ttu-id="0dfe7-187">**VerifyPhoneNumber** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-187">**VerifyPhoneNumber** methods</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample22.cs?highlight=4,18,21)]

<span data-ttu-id="0dfe7-188">**RemovePhoneNumber** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-188">**RemovePhoneNumber** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample23.cs?highlight=3,8)]

<span data-ttu-id="0dfe7-189">**ChangePassword** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-189">**ChangePassword** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample24.cs?highlight=10,13)]

<span data-ttu-id="0dfe7-190">**SetPassword** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-190">**SetPassword** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample25.cs?highlight=5,8)]

<span data-ttu-id="0dfe7-191">**ManageLogins** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-191">**ManageLogins** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample26.cs?highlight=7,12)]

<span data-ttu-id="0dfe7-192">**LinkLoginCallback** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-192">**LinkLoginCallback** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample27.cs?highlight=8)]

<span data-ttu-id="0dfe7-193">**HasPassword** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-193">**HasPassword** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample28.cs?highlight=3)]

<span data-ttu-id="0dfe7-194">**HasPhoneNumber** 메서드</span><span class="sxs-lookup"><span data-stu-id="0dfe7-194">**HasPhoneNumber** method</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample29.cs?highlight=3)]

<span data-ttu-id="0dfe7-195">이제 수 [응용 프로그램을 실행](#run) 새 사용자를 등록 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-195">You can now [run the application](#run) and register a new user.</span></span>

<a id="webformsupdate2"></a>
## <a name="for-web-forms-with-update-2-change-account-pages-to-pass-the-key-type"></a><span data-ttu-id="0dfe7-196">업데이트 2의 Web Forms에 대 한 키 형식을 전달할 계정 페이지를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-196">For Web Forms with Update 2, change Account pages to pass the key type</span></span>

<span data-ttu-id="0dfe7-197">업데이트 2의 Web Forms에 대 한 다음 페이지를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-197">For Web Forms with Update 2, you need to change the following pages.</span></span>

<span data-ttu-id="0dfe7-198">**Confirm.aspx.cx**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-198">**Confirm.aspx.cx**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample30.cs?highlight=8)]

<span data-ttu-id="0dfe7-199">**RegisterExternalLogin.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-199">**RegisterExternalLogin.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample31.cs?highlight=36)]

<span data-ttu-id="0dfe7-200">**Manage.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-200">**Manage.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample32.cs?highlight=3,22,47,52,69,85,93,98)]

<span data-ttu-id="0dfe7-201">이제 수 [응용 프로그램을 실행](#run) 새 사용자를 등록 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-201">You can now [run the application](#run) and register a new user.</span></span>

<a id="webformsupdate3"></a>
## <a name="for-web-forms-with-update-3-change-account-pages-to-pass-the-key-type"></a><span data-ttu-id="0dfe7-202">업데이트 3 Web Forms에 대 한 키 형식을 전달할 계정 페이지를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-202">For Web Forms with Update 3, change Account pages to pass the key type</span></span>

<span data-ttu-id="0dfe7-203">업데이트 3 Web Forms에 대 한 다음 페이지를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-203">For Web Forms with Update 3, you need to change the following pages.</span></span>

<span data-ttu-id="0dfe7-204">**Confirm.aspx.cx**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-204">**Confirm.aspx.cx**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample33.cs?highlight=8)]

<span data-ttu-id="0dfe7-205">**RegisterExternalLogin.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-205">**RegisterExternalLogin.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample34.cs?highlight=36)]

<span data-ttu-id="0dfe7-206">**Manage.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-206">**Manage.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample35.cs?highlight=11,27,32,34,82,87,99,108)]

<span data-ttu-id="0dfe7-207">**VerifyPhoneNumber.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-207">**VerifyPhoneNumber.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample36.cs?highlight=8,23,27)]

<span data-ttu-id="0dfe7-208">**AddPhoneNumber.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-208">**AddPhoneNumber.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample37.cs?highlight=7)]

<span data-ttu-id="0dfe7-209">**ManagePassword.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-209">**ManagePassword.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample38.cs?highlight=11,47,50,68)]

<span data-ttu-id="0dfe7-210">**ManageLogins.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-210">**ManageLogins.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample39.cs?highlight=16,23,32,41,45)]

<span data-ttu-id="0dfe7-211">**TwoFactorAuthenticationSignIn.aspx.cs**</span><span class="sxs-lookup"><span data-stu-id="0dfe7-211">**TwoFactorAuthenticationSignIn.aspx.cs**</span></span>

[!code-csharp[Main](change-primary-key-for-users-in-aspnet-identity/samples/sample40.cs?highlight=14-15,29,53)]

<a id="run"></a>
## <a name="run-application"></a><span data-ttu-id="0dfe7-212">응용 프로그램 실행</span><span class="sxs-lookup"><span data-stu-id="0dfe7-212">Run application</span></span>

<span data-ttu-id="0dfe7-213">모든 기본 웹 응용 프로그램 템플릿에 필요한 변경 사항을 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-213">You have finished all of the required changes to the default Web Application template.</span></span> <span data-ttu-id="0dfe7-214">응용 프로그램을 실행 하 고 새 사용자를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-214">Run the application and register a new user.</span></span> <span data-ttu-id="0dfe7-215">사용자를 등록 한 후 AspNetUsers 테이블에는 정수 Id 열에 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-215">After registering the user, you will notice that the AspNetUsers table has an Id column that is an integer.</span></span>

![새 기본 키](change-primary-key-for-users-in-aspnet-identity/_static/image1.png)

<span data-ttu-id="0dfe7-217">이전에 만든 ASP.NET Identity 테이블 서로 다른 기본 키가 있는 경우 일부 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-217">If you have previously created the ASP.NET Identity tables with a different primary key, you need to make some additional changes.</span></span> <span data-ttu-id="0dfe7-218">가능 하면 기존 데이터베이스를 삭제 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-218">If possible, just delete the existing database.</span></span> <span data-ttu-id="0dfe7-219">웹 응용 프로그램을 실행 하 고 새 사용자를 추가 하는 경우 데이터베이스와 올바른 디자인 다시 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-219">The database will be re-created with the correct design when you run the web application and add a new user.</span></span> <span data-ttu-id="0dfe7-220">삭제할 수 없는 경우, 테이블을 변경 하려면 code first 마이그레이션 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-220">If deletion is not possible, run code first migrations to change the tables.</span></span> <span data-ttu-id="0dfe7-221">그러나 새 정수 기본 키 되지 설정 됩니다는 데이터베이스에서 SQL IDENTITY 속성으로.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-221">However, the new integer primary key will not be set up as a SQL IDENTITY property in the database.</span></span> <span data-ttu-id="0dfe7-222">Id 열의 ID로 수동으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0dfe7-222">You must manually set the Id column as an IDENTITY.</span></span>

<a id="other"></a>
## <a name="other-resources"></a><span data-ttu-id="0dfe7-223">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="0dfe7-223">Other resources</span></span>

- [<span data-ttu-id="0dfe7-224">ASP.NET Id에 대 한 사용자 지정 저장소 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="0dfe7-224">Overview of Custom Storage Providers for ASP.NET Identity</span></span>](overview-of-custom-storage-providers-for-aspnet-identity.md)
- [<span data-ttu-id="0dfe7-225">ASP.NET Id로 기존 웹 사이트 SQL 멤버 자격에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="0dfe7-225">Migrating an Existing Website from SQL Membership to ASP.NET Identity</span></span>](../migrations/migrating-an-existing-website-from-sql-membership-to-aspnet-identity.md)
- [<span data-ttu-id="0dfe7-226">멤버 자격 및 ASP.NET Identity에 대 한 사용자 프로필에 대 한 유니버설 공급자 데이터 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="0dfe7-226">Migrating Universal Provider Data for Membership and User Profiles to ASP.NET Identity</span></span>](../migrations/migrating-universal-provider-data-for-membership-and-user-profiles-to-aspnet-identity.md)
- <span data-ttu-id="0dfe7-227">[샘플 응용 프로그램](https://aspnet.codeplex.com/SourceControl/latest#Samples/Identity/ChangePK/readme.txt) 변경 된 기본 키가 있는</span><span class="sxs-lookup"><span data-stu-id="0dfe7-227">[Sample application](https://aspnet.codeplex.com/SourceControl/latest#Samples/Identity/ChangePK/readme.txt) with changed primary key</span></span>