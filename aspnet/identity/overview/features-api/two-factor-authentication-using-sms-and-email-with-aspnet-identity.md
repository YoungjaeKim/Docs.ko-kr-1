---
uid: identity/overview/features-api/two-factor-authentication-using-sms-and-email-with-aspnet-identity
title: "SMS 및 전자 메일을 사용 하 여 ASP.NET Identity와 2 단계 인증 | Microsoft Docs"
author: HaoK
description: "이 자습서에서는 SMS 및 전자 메일을 사용 하 여 2 단계 인증 (2FA)을 설정 하는 방법을 보여줍니다. 이 문서 Rick Anderson에 의해 작성 되었으므로 ( @RickAndMSFT ) Pr.,..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 09/15/2015
ms.topic: article
ms.assetid: 053e23c4-13c9-40fa-87cb-3e9b0823b31e
ms.technology: 
ms.prod: .net-framework
msc.legacyurl: /identity/overview/features-api/two-factor-authentication-using-sms-and-email-with-aspnet-identity
msc.type: authoredcontent
ms.openlocfilehash: ecb1fc693063995a3a05a7af5db64554c9f595e2
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2017
---
<a name="two-factor-authentication-using-sms-and-email-with-aspnet-identity"></a><span data-ttu-id="34d54-104">SMS 및 전자 메일을 사용 하 여 ASP.NET Identity와 2 단계 인증</span><span class="sxs-lookup"><span data-stu-id="34d54-104">Two-factor authentication using SMS and email with ASP.NET Identity</span></span>
====================
<span data-ttu-id="34d54-105">여 [Hao 둘러싼](https://github.com/HaoK), [Pranav Rastogi](https://github.com/rustd), [Rick Anderson](https://github.com/Rick-Anderson), [Suhas Joshi](https://github.com/suhasj)</span><span class="sxs-lookup"><span data-stu-id="34d54-105">by [Hao Kung](https://github.com/HaoK), [Pranav Rastogi](https://github.com/rustd), [Rick Anderson](https://github.com/Rick-Anderson), [Suhas Joshi](https://github.com/suhasj)</span></span>

> <span data-ttu-id="34d54-106">이 자습서에서는 SMS 및 전자 메일을 사용 하 여 2 단계 인증 (2FA)을 설정 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-106">This tutorial will show you how to set up Two-factor authentication (2FA) using SMS and email.</span></span>
> 
> <span data-ttu-id="34d54-107">이 문서 Rick Anderson에 의해 작성 되었으므로 ([@RickAndMSFT](https://twitter.com/#!/RickAndMSFT)), Pranav Rastogi ([@rustd](https://twitter.com/rustd)), Hao 둘러싼 및 Suhas Joshi 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-107">This article was written by Rick Anderson ([@RickAndMSFT](https://twitter.com/#!/RickAndMSFT)), Pranav Rastogi ([@rustd](https://twitter.com/rustd)), Hao Kung, and Suhas Joshi.</span></span> <span data-ttu-id="34d54-108">NuGet 샘플 Hao 둘러싼 주로 썼습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-108">The NuGet sample was written primarily by Hao Kung.</span></span>


<span data-ttu-id="34d54-109">이 항목에서는 다음에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-109">This topic covers the following:</span></span>

- [<span data-ttu-id="34d54-110">Identity 샘플 빌드</span><span class="sxs-lookup"><span data-stu-id="34d54-110">Building the Identity sample</span></span>](#build)
- [<span data-ttu-id="34d54-111">2 단계 인증에 대 한 SMS를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-111">Set up SMS for Two-factor authentication</span></span>](#SMS)
- [<span data-ttu-id="34d54-112">2 단계 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="34d54-112">Enable Two-factor authentication</span></span>](#enable2)
- [<span data-ttu-id="34d54-113">2 단계 인증 공급자를 등록 하는 방법</span><span class="sxs-lookup"><span data-stu-id="34d54-113">How to register a Two-factor authentication provider</span></span>](#reg)
- [<span data-ttu-id="34d54-114">공유 및 로컬 로그인 계정을 결합합니다</span><span class="sxs-lookup"><span data-stu-id="34d54-114">Combine social and local login accounts</span></span>](#combine)
- [<span data-ttu-id="34d54-115">무차별 암호 대입 공격 으로부터 계정 잠금</span><span class="sxs-lookup"><span data-stu-id="34d54-115">Account lockout from brute force attacks</span></span>](#lock)

<a id="build"></a>

## <a name="building-the-identity-sample"></a><span data-ttu-id="34d54-116">Identity 샘플 빌드</span><span class="sxs-lookup"><span data-stu-id="34d54-116">Building the Identity sample</span></span>

<span data-ttu-id="34d54-117">이 섹션으로 작업 하는 예제를 다운로드 하려면 NuGet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-117">In this section, you'll use NuGet to download a sample we will work with.</span></span> <span data-ttu-id="34d54-118">설치 하 고 실행 하 여 시작 [Visual Studio Express 2013 for Web](https://go.microsoft.com/fwlink/?LinkId=299058) 또는 [Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=306566)합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-118">Start by installing and running [Visual Studio Express 2013 for Web](https://go.microsoft.com/fwlink/?LinkId=299058) or [Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=306566).</span></span> <span data-ttu-id="34d54-119">Visual Studio 설치 [2013 업데이트 2](https://go.microsoft.com/fwlink/?LinkId=390521) 이상.</span><span class="sxs-lookup"><span data-stu-id="34d54-119">Install Visual Studio [2013 Update 2](https://go.microsoft.com/fwlink/?LinkId=390521) or higher.</span></span>

> [!NOTE]
> <span data-ttu-id="34d54-120">경고: Visual Studio를 설치 해야 [2013 업데이트 2](https://go.microsoft.com/fwlink/?LinkId=390521) 이 자습서를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-120">Warning: You must install Visual Studio [2013 Update 2](https://go.microsoft.com/fwlink/?LinkId=390521) to complete this tutorial.</span></span>


1. <span data-ttu-id="34d54-121">새 ***빈*** ASP.NET 웹 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-121">Create a new ***empty*** ASP.NET Web project.</span></span>
2. <span data-ttu-id="34d54-122">패키지 관리자 콘솔에서 다음을 입력 하면 다음 명령이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-122">In the Package Manager Console, enter the following the following commands:</span></span>  
  
    `Install-Package SendGrid`  
    `Install-Package -Prerelease Microsoft.AspNet.Identity.Samples`  
  
 <span data-ttu-id="34d54-123">이 자습서에서는 [SendGrid](http://sendgrid.com/) 전자 메일을 보내는 및 [Twilio](https://www.twilio.com/) 또는 [ASPSMS](https://www.aspsms.com/asp.net/identity/testcredits/) sms 문자 보내기에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-123">In this tutorial, we'll use [SendGrid](http://sendgrid.com/) to send email and [Twilio](https://www.twilio.com/) or [ASPSMS](https://www.aspsms.com/asp.net/identity/testcredits/) for sms texting.</span></span> <span data-ttu-id="34d54-124">`Identity.Samples` 패키지와 사용할 코드를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-124">The `Identity.Samples` package installs the code we will be working with.</span></span>
3. <span data-ttu-id="34d54-125">설정의 [SSL을 사용 하도록 프로젝트](../../../mvc/overview/security/create-an-aspnet-mvc-5-app-with-facebook-and-google-oauth2-and-openid-sign-on.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-125">Set the [project to use SSL](../../../mvc/overview/security/create-an-aspnet-mvc-5-app-with-facebook-and-google-oauth2-and-openid-sign-on.md).</span></span>
4. <span data-ttu-id="34d54-126">*선택적*:의 지침에 따라 내 [전자 메일 확인 자습서](account-confirmation-and-password-recovery-with-aspnet-identity.md) SendGrid 후크 다음 응용 프로그램을 실행 하 고 전자 메일 계정을 등록 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-126">*Optional*: Follow the instructions in my [Email confirmation tutorial](account-confirmation-and-password-recovery-with-aspnet-identity.md) to hook up SendGrid and then run the app and register an email account.</span></span>
5. <span data-ttu-id="34d54-127">* 옵션: * 샘플에서 데모 전자 메일 링크 확인 코드를 제거 (의 `ViewBag.Link` 계정 컨트롤러의 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-127">*Optional: *Remove the demo email link confirmation code from the sample (The `ViewBag.Link` code in the account controller.</span></span> <span data-ttu-id="34d54-128">참조는 `DisplayEmail` 및 `ForgotPasswordConfirmation` 작업 메서드 및 razor 뷰가).</span><span class="sxs-lookup"><span data-stu-id="34d54-128">See the `DisplayEmail` and `ForgotPasswordConfirmation` action methods and razor views ).</span></span>
6. <span data-ttu-id="34d54-129">* 옵션: * 제거는 `ViewBag.Status` 코드와 관리 및 계정 컨트롤러에서는 *Views\Account\VerifyCode.cshtml* 및 *Views\Manage\VerifyPhoneNumber.cshtml* razor 뷰.</span><span class="sxs-lookup"><span data-stu-id="34d54-129">*Optional: *Remove the `ViewBag.Status` code from the Manage and Account controllers and from the *Views\Account\VerifyCode.cshtml* and *Views\Manage\VerifyPhoneNumber.cshtml* razor views.</span></span> <span data-ttu-id="34d54-130">유지할 수 있습니다는 `ViewBag.Status` 이 앱에 연결 및 전자 메일 및 SMS 메시지를 보낼 필요 없이 로컬에서 작동 하는 방법을 테스트 하려면 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-130">Alternatively, you can keep the `ViewBag.Status` display to test how this app works locally without having to hook up and send email and SMS messages.</span></span>

> [!NOTE]
> <span data-ttu-id="34d54-131">경고:이 샘플의 보안 설정을 변경 하면 프로덕션 응용 프로그램의 변경 내용을 명시적으로 지정 하는 보안 감사를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-131">Warning: If you change any of the security settings in this sample, productions apps will need to undergo a security audit that explicitly calls out the changes made.</span></span>


<a id="SMS"></a>

## <a name="set-up-sms-for-two-factor-authentication"></a><span data-ttu-id="34d54-132">2 단계 인증에 대 한 SMS를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-132">Set up SMS for Two-factor authentication</span></span>

<span data-ttu-id="34d54-133">이 자습서에서는 Twilio 또는 ASPSMS 중 하나를 사용 하기 위한 지침을 제공 하지만 다른 SMS 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-133">This tutorial provides instructions for using either Twilio or ASPSMS but you can use any other SMS provider.</span></span>

1. <span data-ttu-id="34d54-134">**SMS 공급자를 사용 하 여 사용자 계정 만들기**</span><span class="sxs-lookup"><span data-stu-id="34d54-134">**Creating a User Account with an SMS provider**</span></span>  
  
 <span data-ttu-id="34d54-135">만들기는 [Twilio](https://www.twilio.com/try-twilio) 또는 [ASPSMS](https://www.aspsms.com/asp.net/identity/testcredits/) 계정.</span><span class="sxs-lookup"><span data-stu-id="34d54-135">Create a [Twilio](https://www.twilio.com/try-twilio) or an [ASPSMS](https://www.aspsms.com/asp.net/identity/testcredits/) account.</span></span>
2. <span data-ttu-id="34d54-136">**추가 패키지 설치 또는 서비스 참조 추가**</span><span class="sxs-lookup"><span data-stu-id="34d54-136">**Installing additional packages or adding service references**</span></span>  
  
 <span data-ttu-id="34d54-137">Twilio:</span><span class="sxs-lookup"><span data-stu-id="34d54-137">Twilio:</span></span>  
 <span data-ttu-id="34d54-138">패키지 관리자 콘솔에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-138">In the Package Manager Console, enter the following command:</span></span>  
    `Install-Package Twilio`  
  
 <span data-ttu-id="34d54-139">ASPSMS:</span><span class="sxs-lookup"><span data-stu-id="34d54-139">ASPSMS:</span></span>  
 <span data-ttu-id="34d54-140">다음 서비스 참조를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-140">The following service reference needs to be added:</span></span>  
  
    ![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image1.png)  
  
 <span data-ttu-id="34d54-141">주소:</span><span class="sxs-lookup"><span data-stu-id="34d54-141">Address:</span></span>  
    `https://webservice.aspsms.com/aspsmsx2.asmx?WSDL`  
  
 <span data-ttu-id="34d54-142">네임스페이스:</span><span class="sxs-lookup"><span data-stu-id="34d54-142">Namespace:</span></span>  
    `ASPSMSX2`
3. <span data-ttu-id="34d54-143">**SMS 공급자 사용자 자격 증명을 파악**</span><span class="sxs-lookup"><span data-stu-id="34d54-143">**Figuring out SMS Provider User credentials**</span></span>  
  
 <span data-ttu-id="34d54-144">Twilio:</span><span class="sxs-lookup"><span data-stu-id="34d54-144">Twilio:</span></span>  
 <span data-ttu-id="34d54-145">**대시보드** 복사 Twilio 계정 탭의 **계정 SID** 및 **인증 토큰**합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-145">From the **Dashboard** tab of your Twilio account, copy the **Account SID** and **Auth token**.</span></span>  
  
 <span data-ttu-id="34d54-146">ASPSMS:</span><span class="sxs-lookup"><span data-stu-id="34d54-146">ASPSMS:</span></span>  
 <span data-ttu-id="34d54-147">계정 설정을에서으로 이동 **사용자 키로** 자체 정의 함께 복사 및 **암호**합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-147">From your account settings, navigate to **Userkey** and copy it together with your self-defined **Password**.</span></span>  
  
 <span data-ttu-id="34d54-148">변수이 값이 나중에 저장할 `SMSAccountIdentification` 및 `SMSAccountPassword` 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-148">We will later store these values in the variables `SMSAccountIdentification` and `SMSAccountPassword` .</span></span>
4. <span data-ttu-id="34d54-149">**SenderID 지정 / 송신자**</span><span class="sxs-lookup"><span data-stu-id="34d54-149">**Specifying SenderID / Originator**</span></span>  
  
 <span data-ttu-id="34d54-150">Twilio:</span><span class="sxs-lookup"><span data-stu-id="34d54-150">Twilio:</span></span>  
 <span data-ttu-id="34d54-151">**숫자** 탭, Twilio 전화 번호를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-151">From the **Numbers** tab, copy your Twilio phone number.</span></span>  
  
 <span data-ttu-id="34d54-152">ASPSMS:</span><span class="sxs-lookup"><span data-stu-id="34d54-152">ASPSMS:</span></span>  
 <span data-ttu-id="34d54-153">내에서 **잠금 해제 보낸 사람** 메뉴를 사용 하거나 하나 이상의 보낸 사람을 잠금 해제 (모든 네트워크에서 지원 되지 않음)에 영숫자 보낸 사람이 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-153">Within the **Unlock Originators** Menu, unlock one or more Originators or choose an alphanumeric Originator (Not supported by all networks).</span></span>  
  
 <span data-ttu-id="34d54-154">변수이 값이 나중에 저장할 `SMSAccountFrom` 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-154">We will later store this value in the variable `SMSAccountFrom` .</span></span>
5. <span data-ttu-id="34d54-155">**응용 프로그램에 SMS 공급자 자격 증명 전송**</span><span class="sxs-lookup"><span data-stu-id="34d54-155">**Transferring SMS provider credentials into app**</span></span>  
  
 <span data-ttu-id="34d54-156">자격 증명 및 보낸 사람에 게 전화 번호가 응용 프로그램에 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-156">Make the credentials and sender phone number available to the app:</span></span>

    [!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample1.cs)]

    > [!WARNING]
    > <span data-ttu-id="34d54-157">보안-소스 코드에서 중요 한 데이터 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-157">Security - Never store sensitive data in your source code.</span></span> <span data-ttu-id="34d54-158">계정 및 자격 증명은 위의 예제를 단순하게 유지 하기 위해 코드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-158">The account and credentials are added to the code above to keep the sample simple.</span></span> <span data-ttu-id="34d54-159">Jon Atten 참조 [ASP.NET MVC: 소스 제어의 개인 설정 확장 유지](http://typecastexception.com/post/2014/04/06/ASPNET-MVC-Keep-Private-Settings-Out-of-Source-Control.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-159">See Jon Atten's [ASP.NET MVC: Keep Private Settings Out of Source Control](http://typecastexception.com/post/2014/04/06/ASPNET-MVC-Keep-Private-Settings-Out-of-Source-Control.aspx).</span></span>
6. <span data-ttu-id="34d54-160">**SMS 공급자에 데이터 전송의 구현**</span><span class="sxs-lookup"><span data-stu-id="34d54-160">**Implementation of data transfer to SMS provider**</span></span>  
  
 <span data-ttu-id="34d54-161">구성에서 `SmsService` 클래스에 *앱\_Start\IdentityConfig.cs* 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-161">Configure the `SmsService`  class in the *App\_Start\IdentityConfig.cs* file.</span></span>  
  
 <span data-ttu-id="34d54-162">사용 되는 SMS 공급자에 따라 활성화 중 하나는 **Twilio** 또는 **ASPSMS** 섹션:</span><span class="sxs-lookup"><span data-stu-id="34d54-162">Depending on the used SMS provider activate either the **Twilio** or the **ASPSMS** section:</span></span> 

    [!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample2.cs)]
7. <span data-ttu-id="34d54-163">응용 프로그램을 실행 하 고 이전에 등록 하는 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-163">Run the app and log in with the account you previously registered.</span></span>
8. <span data-ttu-id="34d54-164">활성화 하는 사용자 ID, 클릭는 `Index` 의 동작 메서드에 `Manage` 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-164">Click on your User ID, which activates the `Index` action method in `Manage` controller.</span></span>  
  
    ![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image2.png)
9. <span data-ttu-id="34d54-165">추가 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-165">Click Add.</span></span>  
  
    ![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image3.png)
10. <span data-ttu-id="34d54-166">몇 초 후에 확인 코드를 있는 문자 메시지를 받아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-166">In a few seconds you will get a text message with the verification code.</span></span> <span data-ttu-id="34d54-167">입력 하 고 키를 눌러 **전송**합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-167">Enter it and press **Submit**.</span></span>  
  
    ![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image4.png)
11. <span data-ttu-id="34d54-168">관리 보기 표시 전화 번호가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-168">The Manage view shows your phone number was added.</span></span>  
  
    ![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image5.png)

### <a name="examine-the-code"></a><span data-ttu-id="34d54-169">코드 검사</span><span class="sxs-lookup"><span data-stu-id="34d54-169">Examine the code</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample3.cs?highlight=2)]

<span data-ttu-id="34d54-170">`Index` 의 동작 메서드에 `Manage` 컨트롤러 이전 작업에 따라 상태 메시지를 설정 하 고 로컬 암호를 변경 하거나 로컬 계정을 추가에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-170">The `Index` action method in `Manage` controller sets the status message based on your previous action and provides links to change your local password or add a local account.</span></span> <span data-ttu-id="34d54-171">`Index` 메서드는 또한 상태 표시 또는 2FA 사용자 전화 번호, 외부 로그인, 2FA 사용 하도록 설정 하 고 2FA 메서드 (나중에 설명)이이 브라우저에 대 한를 기억 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-171">The `Index` method also displays the state or your 2FA phone number, external logins, 2FA enabled, and remember 2FA method for this browser(explained later).</span></span> <span data-ttu-id="34d54-172">제목 표시줄에 사용자 ID (전자 메일)를 클릭 하는 메시지를 전달 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-172">Clicking on your user ID (email) in the title bar doesn't pass a message.</span></span> <span data-ttu-id="34d54-173">클릭 하 고 **전화 번호: 제거** 패스를 연결할 `Message=RemovePhoneSuccess` 쿼리 문자열로 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-173">Clicking on the **Phone Number : remove** link passes `Message=RemovePhoneSuccess` as a query string.</span></span>  
  
`https://localhost:44300/Manage?Message=RemovePhoneSuccess`

<span data-ttu-id="34d54-174">[![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image6.png)]</span><span class="sxs-lookup"><span data-stu-id="34d54-174">[![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image6.png)]</span></span>

<span data-ttu-id="34d54-175">`AddPhoneNumber` 동작 메서드 SMS 메시지를 받을 수 있는 전화 번호를 입력 하는 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-175">The `AddPhoneNumber` action method displays a dialog box to enter a phone number that can receive SMS messages.</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample4.cs)]

![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image7.png)

<span data-ttu-id="34d54-176">클릭 하는 **확인 코드를 보낼** 단추 HTTP POST에 전화 번호를 게시 `AddPhoneNumber` 동작 메서드.</span><span class="sxs-lookup"><span data-stu-id="34d54-176">Clicking on the **Send verification code** button posts the phone number to the HTTP POST `AddPhoneNumber` action method.</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample5.cs?highlight=12)]

<span data-ttu-id="34d54-177">`GenerateChangePhoneNumberTokenAsync` 메서드 SMS 메시지에 설정할 수 있는 보안 토큰을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-177">The `GenerateChangePhoneNumberTokenAsync` method generates the security token which will be set in the SMS message.</span></span> <span data-ttu-id="34d54-178">문자열로 된 토큰은 전송 SMS 서비스를 구성한 경우 &quot;보안 코드는 &lt;토큰&gt;&quot;합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-178">If the SMS service has been configured, the token is sent as the string &quot;Your security code is &lt;token&gt;&quot;.</span></span> <span data-ttu-id="34d54-179">`SmsService.SendAsync` 앱의 리디렉션 다음 메서드를 비동기적으로 호출 되는 `VerifyPhoneNumber` 동작 메서드 (다음과 같은 대화 상자가 표시 됨), 확인 코드를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-179">The `SmsService.SendAsync` method to is called asynchronously, then the app is redirected to the `VerifyPhoneNumber` action method (which displays the following dialog), where you can enter the verification code.</span></span>

![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image8.png)

<span data-ttu-id="34d54-180">코드는 HTTP POST에 게시 되는 코드를 입력 하 고 제출을 클릭 한 후 `VerifyPhoneNumber` 동작 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-180">Once you enter the code and click submit, the code is posted to the HTTP POST `VerifyPhoneNumber` action method.</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample6.cs)]

<span data-ttu-id="34d54-181">`ChangePhoneNumberAsync` 메서드 게시 된 보안 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-181">The `ChangePhoneNumberAsync` method checks the posted security code.</span></span> <span data-ttu-id="34d54-182">전화 번호를 추가 코드가 정확한 경우는 `PhoneNumber` 필드는 `AspNetUsers` 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-182">If the code is correct, the phone number is added to the `PhoneNumber` field of the `AspNetUsers` table.</span></span> <span data-ttu-id="34d54-183">이 호출이 성공 하는 경우는 `SignInAsync` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-183">If that call is successful, the `SignInAsync` method is called:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample7.cs)]

<span data-ttu-id="34d54-184">`isPersistent` 매개 변수는 인증 세션이 여러 요청 간에 지속 되는지 여부를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-184">The `isPersistent` parameter sets whether the authentication session is persisted across multiple requests.</span></span>

<span data-ttu-id="34d54-185">새 보안 스탬프를 생성 되 고에 저장 된 보안 프로필을 변경 하면는 `SecurityStamp` 필드는 *AspNetUsers* 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-185">When you change your security profile, a new security stamp is generated and stored in the `SecurityStamp` field of the *AspNetUsers* table.</span></span> <span data-ttu-id="34d54-186">단는 `SecurityStamp` 필드는 보안 쿠키와에서 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-186">Note, the `SecurityStamp` field is different from the security cookie.</span></span> <span data-ttu-id="34d54-187">보안 쿠키에 저장 되지 않습니다는 `AspNetUsers` 테이블 (또는 Identity DB의 다른 곳).</span><span class="sxs-lookup"><span data-stu-id="34d54-187">The security cookie is not stored in the `AspNetUsers` table (or anywhere else in the Identity DB).</span></span> <span data-ttu-id="34d54-188">사용 하 여 보안 쿠키 토큰 자체 서명 [DPAPI](https://msdn.microsoft.com/en-us/library/system.security.cryptography.protecteddata.aspx) 와 만들어집니다는 `UserId, SecurityStamp` 및 만료 시간 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-188">The security cookie token is self-signed using [DPAPI](https://msdn.microsoft.com/en-us/library/system.security.cryptography.protecteddata.aspx) and is created with the `UserId, SecurityStamp` and expiration time information.</span></span>

<span data-ttu-id="34d54-189">쿠키 미들웨어 각 요청에 대해 쿠키를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-189">The cookie middleware checks the cookie on each request.</span></span> <span data-ttu-id="34d54-190">`SecurityStampValidator` 에서 메서드는 `Startup` 클래스 DB에 도달 하 고 보안 스탬프를 주기적으로 확인 된 지정 된 대로 `validateInterval`합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-190">The `SecurityStampValidator` method in the `Startup` class hits the DB and checks security stamp periodically, as specified with the `validateInterval`.</span></span> <span data-ttu-id="34d54-191">이 보안 프로필을 변경 하지 않는 한 (샘플)에서 30 분 마다만 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-191">This only happens every 30 minutes (in our sample) unless you change your security profile.</span></span> <span data-ttu-id="34d54-192">30 분 간격 데이터베이스에 대 한 왕복을 최소화 하기 위해 선택 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-192">The 30 minute interval was chosen to minimize trips to the database.</span></span>

<span data-ttu-id="34d54-193">`SignInAsync` 보안 프로필에 변경 될 때 호출 될 메서드에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-193">The `SignInAsync` method needs to be called when any change is made to the security profile.</span></span> <span data-ttu-id="34d54-194">데이터베이스 업데이트는 보안 프로필이 변경 될 때는 `SecurityStamp` 필드 및 호출 하지 않고는 `SignInAsync` 로그인 머무는 것 메서드 *만* 다음 OWIN 파이프라인에 될 때까지 데이터베이스에 도달 (의 `validateInterval`).</span><span class="sxs-lookup"><span data-stu-id="34d54-194">When the security profile changes, the database is updates the `SecurityStamp` field, and without calling the `SignInAsync` method you would stay logged in *only* until the next time the OWIN pipeline hits the database (the `validateInterval`).</span></span> <span data-ttu-id="34d54-195">변경 하 여 테스트할 수 있습니다는 `SignInAsync` 즉시 반환 하는 메서드 및 쿠키 설정 `validateInterval` 5 초에 30 분에서 속성:</span><span class="sxs-lookup"><span data-stu-id="34d54-195">You can test this by changing the `SignInAsync` method to return immediately, and setting the cookie `validateInterval` property from 30 minutes to 5 seconds:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample8.cs?highlight=3)]

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample9.cs?highlight=20-21)]

<span data-ttu-id="34d54-196">위의 코드 변경 내용으로 보안 프로필을 변경할 수 있습니다 (의 상태를 변경 하 여 예를 들어 **두 개의 요소 사용**) 및 5 초에서 로그인 됩니다 때는 `SecurityStampValidator.OnValidateIdentity` 메서드가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-196">With the above code changes, you can change your security profile (for example, by changing the state of **Two Factor Enabled**) and you will be logged out in 5 seconds when the `SecurityStampValidator.OnValidateIdentity` method fails.</span></span> <span data-ttu-id="34d54-197">반환 행은 제거는 `SignInAsync` 메서드를 변경 하는 다른 보안 프로필을 확인 하 고 기록 되지 것입니다 있습니다. `SignInAsync` 메서드는 새 보안 쿠키를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-197">Remove the return line in the `SignInAsync` method, make another security profile change and you will not be logged out. The `SignInAsync` method generates a new security cookie.</span></span>

<a id="enable2"></a>

## <a name="enable-two-factor-authentication"></a><span data-ttu-id="34d54-198">2 단계 인증을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="34d54-198">Enable two-factor authentication</span></span>

<span data-ttu-id="34d54-199">샘플 응용 프로그램에서 (2FA) 2 단계 인증을 사용 하도록 UI를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-199">In the sample app, you need to use the UI to enable two-factor authentication (2FA).</span></span> <span data-ttu-id="34d54-200">2FA를 활성화 하려면 탐색 모음에서 사용자 ID (전자 메일 별칭)을 클릭 합니다.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image9.png)</span><span class="sxs-lookup"><span data-stu-id="34d54-200">To enable 2FA, click on your user ID (email alias) in the navigation bar.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image9.png)</span></span>  
<span data-ttu-id="34d54-201">Enable 2FA 클릭 합니다.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image10.png)</span><span class="sxs-lookup"><span data-stu-id="34d54-201">Click on enable 2FA.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image10.png)</span></span> <span data-ttu-id="34d54-202">로그 아웃 한 다음 다시 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-202">Log out, then log back in.</span></span> <span data-ttu-id="34d54-203">전자 메일을 활성화 한 경우 (참조 내 [이전 자습서](account-confirmation-and-password-recovery-with-aspnet-identity.md)), SMS 또는 2FA에 대 한 전자 메일을 선택할 수 있습니다.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image11.png)</span><span class="sxs-lookup"><span data-stu-id="34d54-203">If you've enabled email (see my [previous tutorial](account-confirmation-and-password-recovery-with-aspnet-identity.md)), you can select the SMS or email for 2FA.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image11.png)</span></span> <span data-ttu-id="34d54-204">확인 코드 페이지 (SMS 또는 전자 메일)에서 코드를 입력할 수 있는 표시 됩니다.![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image12.png)</span><span class="sxs-lookup"><span data-stu-id="34d54-204">The Verify Code page is displayed where you can enter the code (from SMS or email).![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image12.png)</span></span> <span data-ttu-id="34d54-205">클릭 하 고 **저장이 브라우저** 확인란 있습니다 2FA를 사용 하 여 해당 컴퓨터와 브라우저를 사용 하 여 로그온 하에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-205">Clicking on the **Remember this browser** check box will exempt you from needing to use 2FA to log on with that computer and browser.</span></span> <span data-ttu-id="34d54-206">2FA를 사용 하도록 설정 하 고 클릭 하 고 **저장이 브라우저** 을 제공 합니다 강력한 2FA 보호 된 컴퓨터에 액세스할 수 없는 상태로 회원님의 계정에 액세스 하려고 하는 악의적인 사용자 로부터 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-206">Enabling 2FA and clicking on the **Remember this browser** will provide you with strong 2FA protection from malicious users trying to access your account, as long as they don't have access to your computer.</span></span> <span data-ttu-id="34d54-207">정기적으로 사용 하는 모든 개인 컴퓨터에서이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-207">You can do this on any private machine you regularly use.</span></span> <span data-ttu-id="34d54-208">설정 하 여 **저장이 브라우저**, 있습니다 2FA의 강화 된 보안에서 정기적으로 사용 하지 않는 컴퓨터를 가져오고에 2FA 자신의 컴퓨터에 통과 하지 않아도 되는 편의성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-208">By setting **Remember this browser**, you get the added security of 2FA from computers you don't regularly use, and you get the convenience on not having to go through 2FA on your own computers.</span></span> 

<a id="reg"></a>
## <a name="how-to-register-a-two-factor-authentication-provider"></a><span data-ttu-id="34d54-209">2 단계 인증 공급자를 등록 하는 방법</span><span class="sxs-lookup"><span data-stu-id="34d54-209">How to register a Two-factor authentication provider</span></span>

<span data-ttu-id="34d54-210">새 MVC 프로젝트를 만들 때의 *IdentityConfig.cs* 2 단계 인증 공급자를 등록 하려면 다음 코드를 포함 하는 파일:</span><span class="sxs-lookup"><span data-stu-id="34d54-210">When you create a new MVC project, the *IdentityConfig.cs* file contains the following code to register a Two-factor authentication provider:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample10.cs?highlight=22-35)]

## <a name="add-a-phone-number-for-2fa"></a><span data-ttu-id="34d54-211">2FA 전화 번호를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-211">Add a phone number for 2FA</span></span>

<span data-ttu-id="34d54-212">`AddPhoneNumber` 의 동작 메서드에 `Manage` 컨트롤러는 보안 토큰을 생성 하 고 보냅니다 하에 전화 번호를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-212">The `AddPhoneNumber` action method in the `Manage` controller generates a security token and sends it to the phone number you have provided.</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample11.cs)]

<span data-ttu-id="34d54-213">리디렉션합니다. 토큰을 보낸 후의 `VerifyPhoneNumber` 동작 메서드에 2FA SMS 등록 하는 코드를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-213">After sending the token, it redirects to the `VerifyPhoneNumber` action method, where you can enter the code to register SMS for 2FA.</span></span> <span data-ttu-id="34d54-214">SMS 2FA 전화 번호를 확인 하기 전 까지는 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-214">SMS 2FA is not used until you have verified the phone number.</span></span>

## <a name="enabling-2fa"></a><span data-ttu-id="34d54-215">2FA를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="34d54-215">Enabling 2FA</span></span>

<span data-ttu-id="34d54-216">`EnableTFA` 동작 메서드를 사용 하면 2FA:</span><span class="sxs-lookup"><span data-stu-id="34d54-216">The `EnableTFA` action method enables 2FA:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample12.cs)]

<span data-ttu-id="34d54-217">참고는 `SignInAsync` enable 2FA 보안 프로필에 대 한 변경 이므로 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-217">Note the `SignInAsync` must be called because enable 2FA is a change to the security profile.</span></span> <span data-ttu-id="34d54-218">2FA 활성화 되 면 사용자 사용 해야 합니다 2FA 로그인, (SMS 및 샘플에 대 한 전자 메일)가 등록 2FA 방법을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-218">When 2FA is enabled, the user will need to use 2FA to log in, using the 2FA approaches they have registered (SMS and email in the sample).</span></span>

<span data-ttu-id="34d54-219">QR 코드 생성기 같은 더 많은 2FA 공급자를 추가 하거나 소유권을 작성할 수 있습니다 (참조 [ASP.NET Identity와 Google 인증자를 사용 하 여](http://www.beabigrockstar.com/blog/using-google-authenticator-asp-net-identity/)).</span><span class="sxs-lookup"><span data-stu-id="34d54-219">You can add more 2FA providers such as QR code generators or you can write you own (See [Using Google Authenticator with ASP.NET Identity](http://www.beabigrockstar.com/blog/using-google-authenticator-asp-net-identity/)).</span></span>

> [!NOTE]
> <span data-ttu-id="34d54-220">2FA 코드를 사용 하 여 생성 된 [일회용 암호 알고리즘 시간 기반](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm) 및 코드는 6 분 후에 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-220">The 2FA codes are generated using [Time-based One-time Password Algorithm](http://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm) and codes are valid for six minutes.</span></span> <span data-ttu-id="34d54-221">사용자가 코드를 입력 하는 데 6 분 넘게을 수행 하는 경우 잘못 된 코드 오류 메시지가 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-221">If you take more than six minutes to enter the code, you'll get an Invalid code error message.</span></span>


<a id="combine"></a>

## <a name="combine-social-and-local-login-accounts"></a><span data-ttu-id="34d54-222">공유 및 로컬 로그인 계정을 결합합니다</span><span class="sxs-lookup"><span data-stu-id="34d54-222">Combine social and local login accounts</span></span>

<span data-ttu-id="34d54-223">사용자 전자 메일 링크를 클릭 하 여 로컬 및 소셜 계정을 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-223">You can combine local and social accounts by clicking on your email link.</span></span> <span data-ttu-id="34d54-224">다음 순서로 &quot; RickAndMSFT@gmail.com &quot; 처음에 로컬 로그인으로 만들면 하지만 로컬 로그인을 추가 다음에서 첫 번째로, 소셜 로그로 계정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-224">In the following sequence &quot;RickAndMSFT@gmail.com&quot; is first created as a local login, but you can create the account as a social log in first, then add a local login.</span></span>

![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image13.png)

<span data-ttu-id="34d54-225">클릭는 **관리** 링크 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-225">Click on the **Manage** link.</span></span> <span data-ttu-id="34d54-226">이 계정에 연결 된 참고 0 외부 (소셜 로그인)</span><span class="sxs-lookup"><span data-stu-id="34d54-226">Note the 0 external (social logins) associated with this account.</span></span>

![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image14.png)

<span data-ttu-id="34d54-227">서비스에서 다른 로그에 대 한 링크를 클릭 하 고 응용 프로그램 요청을 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-227">Click the link to another log in service and accept the app requests.</span></span> <span data-ttu-id="34d54-228">두 개의 계정을 결합 되어, 두 계정으로 로그온 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-228">The two accounts have been combined, you will be able to log on with either account.</span></span> <span data-ttu-id="34d54-229">경우에 대비 다운 되는 인증 서비스에서 소셜의 로그 또는 쓰지만 대개은 स ॅ स 소셜 계정으로 로컬 계정을 추가 하려면 사용자가 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-229">You might want your users to add local accounts in case their social log in authentication service is down, or more likely they have lost access to their social account.</span></span>

<span data-ttu-id="34d54-230">다음 그림에서는 Tom는 소셜 로그인 (에서 볼 수 있는 **외부 로그인: 1** 페이지에 표시).</span><span class="sxs-lookup"><span data-stu-id="34d54-230">In the following image, Tom is a social log in (which you can see from the **External Logins: 1** shown on the page).</span></span>

![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image15.png)

<span data-ttu-id="34d54-231">클릭 하면 **암호** 동일한 계정에 연결 된 로컬 로그에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-231">Clicking on **Pick a password** allows you to add a local log on associated with the same account.</span></span>

![](two-factor-authentication-using-sms-and-email-with-aspnet-identity/_static/image16.png)

<a id="lock"></a>

## <a name="account-lockout-from-brute-force-attacks"></a><span data-ttu-id="34d54-232">무차별 암호 대입 공격 으로부터 계정 잠금</span><span class="sxs-lookup"><span data-stu-id="34d54-232">Account lockout from brute force attacks</span></span>

<span data-ttu-id="34d54-233">사용자 잠금 사용 하 여 사전 공격 으로부터 응용 프로그램에 계정을 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-233">You can protect the accounts on your app from dictionary attacks by enabling user lockout.</span></span> <span data-ttu-id="34d54-234">다음 코드에 `ApplicationUserManager Create` 메서드 구성 잠금:</span><span class="sxs-lookup"><span data-stu-id="34d54-234">The following code in the `ApplicationUserManager Create` method configures lock out:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample13.cs)]

<span data-ttu-id="34d54-235">위의 코드에만 2 단계 인증에 대 한 잠금 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-235">The code above enables lockout for two factor authentication only.</span></span> <span data-ttu-id="34d54-236">변경 하 여 로그인에 대 한 잠금을 설정할 수 있습니다 하는 동안 `shouldLockout` true로는 `Login` 계정 컨트롤러의 메서드를 권장 설정 하지 로그인에 대 한 잠금을 사용 하면 계정에 취약 하기 때문에 [DOS](http://en.wikipedia.org/wiki/Denial-of-service_attack) 로그인 공격입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-236">While you can enable lock out for logins by changing `shouldLockout` to true in the `Login` method of the account controller, we recommend you not enable lock out for logins because it makes the account susceptible to [DOS](http://en.wikipedia.org/wiki/Denial-of-service_attack) login attacks.</span></span> <span data-ttu-id="34d54-237">잠금에서 만든 관리자 계정에 대 한 샘플 코드에서 비활성화 된 `ApplicationDbInitializer Seed` 메서드:</span><span class="sxs-lookup"><span data-stu-id="34d54-237">In the sample code, lockout is disabled for the admin account created in the `ApplicationDbInitializer Seed` method:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample14.cs?highlight=19)]

## <a name="requiring-a-user-to-have-a-validated-email-account"></a><span data-ttu-id="34d54-238">유효성이 검사 된 전자 메일 계정이 사용자 요구</span><span class="sxs-lookup"><span data-stu-id="34d54-238">Requiring a user to have a validated email account</span></span>

<span data-ttu-id="34d54-239">다음 코드에 사용자를를 로그인 할 수 전에 유효성이 검사 된 전자 메일 계정이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-239">The following code requires a user to have a validated email account before they can log in:</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample15.cs?highlight=8-17)]

## <a name="how-signinmanager-checks-for-2fa-requirement"></a><span data-ttu-id="34d54-240">SignInManager는 2FA 요구 사항에 대해 확인 하는 방법</span><span class="sxs-lookup"><span data-stu-id="34d54-240">How SignInManager checks for 2FA requirement</span></span>

<span data-ttu-id="34d54-241">로컬 로그인와 소셜 로그인 2FA을 사용할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-241">Both the local log in and social log in check to see if 2FA is enabled.</span></span> <span data-ttu-id="34d54-242">2FA 사용 하는 경우는 `SignInManager` 로그온 메서드 반환 `SignInStatus.RequiresVerification`, 사용자 리디렉션됩니다는 `SendCode` 동작 메서드에 있는 시퀀스의 로그를 완료 하려면 코드를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-242">If 2FA is enabled, the `SignInManager` logon method returns `SignInStatus.RequiresVerification`, and the user will be redirected to the `SendCode` action method, where they will have to enter the code to complete the log in sequence.</span></span> <span data-ttu-id="34d54-243">사용자에 게 RememberMe 있으면 사용자가 로컬 쿠키에 설정 되어는 `SignInManager` 돌아갑니다 `SignInStatus.Success` 2FA를 수행 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-243">If the user has RememberMe is set on the users local cookie, the `SignInManager` will return `SignInStatus.Success` and they will not have to go through 2FA.</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample16.cs?highlight=20-22)]

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample17.cs?highlight=10-11,17-18)]

<span data-ttu-id="34d54-244">다음 코드는 `SendCode` 동작 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-244">The following code shows the `SendCode` action method.</span></span> <span data-ttu-id="34d54-245">A [SelectListItem](https://msdn.microsoft.com/en-us/library/system.web.mvc.selectlistitem.aspx) 사용자에 대해 사용 하도록 설정 하는 모든 2FA 메서드를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-245">A [SelectListItem](https://msdn.microsoft.com/en-us/library/system.web.mvc.selectlistitem.aspx) is created with all the 2FA methods enabled for the user.</span></span> <span data-ttu-id="34d54-246">[SelectListItem](https://msdn.microsoft.com/en-us/library/system.web.mvc.selectlistitem.aspx) 에 전달 되는 [DropDownListFor](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.dropdownlist.aspx) 도우미 사용자 (일반적으로 전자 메일 및 SMS) 2FA 접근 방식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-246">The [SelectListItem](https://msdn.microsoft.com/en-us/library/system.web.mvc.selectlistitem.aspx) is passed to the [DropDownListFor](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.dropdownlist.aspx) helper, which allows the user to select the 2FA approach (typically email and SMS).</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample18.cs)]

<span data-ttu-id="34d54-247">2FA 방법은 사용자가 게시 되 면는 `HTTP POST SendCode` 동작 메서드가 호출 되는 `SignInManager` 보냅니다에 2FA 코드 및 사용자가 리디렉션되는 `VerifyCode` 로그인을 완료 하는 코드를 입력할 수 있는 작업 메서드.</span><span class="sxs-lookup"><span data-stu-id="34d54-247">Once the user posts the 2FA approach, the `HTTP POST SendCode` action method is called, the `SignInManager` sends the 2FA code, and the user is redirected to the `VerifyCode` action method where they can enter the code to complete the log in.</span></span>

[!code-csharp[Main](two-factor-authentication-using-sms-and-email-with-aspnet-identity/samples/sample19.cs?highlight=3,13-14,18)]

## <a name="2fa-lockout"></a><span data-ttu-id="34d54-248">2FA 잠금</span><span class="sxs-lookup"><span data-stu-id="34d54-248">2FA Lockout</span></span>

<span data-ttu-id="34d54-249">로그인 암호 시도 실패에 계정 잠금에 설정할 수 있지만 해당 접근 방식을 통해 사용자의 로그인에 취약 [DOS](http://en.wikipedia.org/wiki/Denial-of-service_attack) 잠금을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-249">Although you can set account lockout on login password attempt failures, that approach makes your login susceptible to [DOS](http://en.wikipedia.org/wiki/Denial-of-service_attack) lockouts.</span></span> <span data-ttu-id="34d54-250">계정 잠금 2FA에만 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-250">We recommend you use account lockout only with 2FA.</span></span> <span data-ttu-id="34d54-251">경우는 `ApplicationUserManager` 가 만들어지면 샘플 코드에서는 설정 2FA 잠금 및 `MaxFailedAccessAttemptsBeforeLockout` 5입니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-251">When the `ApplicationUserManager` is created, the sample code sets 2FA lockout and `MaxFailedAccessAttemptsBeforeLockout` to five.</span></span> <span data-ttu-id="34d54-252">사용자가 로컬 계정 또는 소셜 계정) (통해 로그인 하 고 2FA에서 연결 시도가 실패할된 때마다 저장 된 최대 시도 횟수에 도달 하면 사용자가 잠길 5 분 (잠금 시간 초과 설정할 수 있습니다 `DefaultAccountLockoutTimeSpan`).</span><span class="sxs-lookup"><span data-stu-id="34d54-252">Once a user logs in (through local account or social account), each failed attempt at 2FA is stored, and if the maximum attempts is reached, the user is locked out for five minutes (you can set the lock out time with `DefaultAccountLockoutTimeSpan`).</span></span>

<a id="addRes"></a>

## <a name="additional-resources"></a><span data-ttu-id="34d54-253">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="34d54-253">Additional Resources</span></span>

- <span data-ttu-id="34d54-254">[ASP.NET Identity 권장 리소스](../getting-started/aspnet-identity-recommended-resources.md) Id 블로그, 비디오, 자습서 및 좋은의 전체 목록은 지금 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-254">[ASP.NET Identity Recommended Resources](../getting-started/aspnet-identity-recommended-resources.md) Complete list of Identity blogs, videos, tutorials and great SO links.</span></span>
- <span data-ttu-id="34d54-255">[Facebook, Twitter, LinkedIn 및 Google OAuth2 로그온 된 MVC 5 앱](../../../mvc/overview/security/create-an-aspnet-mvc-5-app-with-facebook-and-google-oauth2-and-openid-sign-on.md) 사용자 테이블에 프로필 정보를 추가 하는 방법도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-255">[MVC 5 App with Facebook, Twitter, LinkedIn and Google OAuth2 Sign-on](../../../mvc/overview/security/create-an-aspnet-mvc-5-app-with-facebook-and-google-oauth2-and-openid-sign-on.md) also shows how to add profile information to the users table.</span></span>
- <span data-ttu-id="34d54-256">[ASP.NET MVC 및 Id 2.0: 기본 사항을 이해](http://typecastexception.com/post/2014/04/20/ASPNET-MVC-and-Identity-20-Understanding-the-Basics.aspx) John Atten 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-256">[ASP.NET MVC and Identity 2.0: Understanding the Basics](http://typecastexception.com/post/2014/04/20/ASPNET-MVC-and-Identity-20-Understanding-the-Basics.aspx) by John Atten.</span></span>
- [<span data-ttu-id="34d54-257">계정 확인 및 ASP.NET Id와 암호 복구</span><span class="sxs-lookup"><span data-stu-id="34d54-257">Account Confirmation and Password Recovery with ASP.NET Identity</span></span>](account-confirmation-and-password-recovery-with-aspnet-identity.md)
- [<span data-ttu-id="34d54-258">ASP.NET Id 소개</span><span class="sxs-lookup"><span data-stu-id="34d54-258">Introduction to ASP.NET Identity</span></span>](../getting-started/introduction-to-aspnet-identity.md)
- <span data-ttu-id="34d54-259">[ASP.NET Identity 2.0.0의 RTM 발표](https://blogs.msdn.com/b/webdev/archive/2014/03/20/test-announcing-rtm-of-asp-net-identity-2-0-0.aspx) Pranav Rastogi 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-259">[Announcing RTM of ASP.NET Identity 2.0.0](https://blogs.msdn.com/b/webdev/archive/2014/03/20/test-announcing-rtm-of-asp-net-identity-2-0-0.aspx) by Pranav Rastogi.</span></span>
- <span data-ttu-id="34d54-260">[ASP.NET Id 2.0: 계정 유효성 검사 및 2 단계 인증을 설정](http://typecastexception.com/post/2014/04/20/ASPNET-Identity-20-Setting-Up-Account-Validation-and-Two-Factor-Authorization.aspx) John Atten 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="34d54-260">[ASP.NET Identity 2.0: Setting Up Account Validation and Two-Factor Authorization](http://typecastexception.com/post/2014/04/20/ASPNET-Identity-20-Setting-Up-Account-Validation-and-Two-Factor-Authorization.aspx) by John Atten.</span></span>