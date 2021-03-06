﻿---
title: '常見的郵件核准案例: Exchange Online Help'
TOCTitle: 常見的郵件核准案例
ms:assetid: 5c13a07e-c21d-4502-a9f9-fb801197e1dd
ms:mtpsurl: https://technet.microsoft.com/zh-tw/library/Dd298007(v=EXCHG.150)
ms:contentKeyID: 50473287
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 常見的郵件核准案例

 

_**適用版本：** Exchange Online, Exchange Server 2013_

_**上次修改主題的時間：** 2014-09-29_

您的組織可能需要以符合法律或規範需求，或以實作特定商務工作流程核准特定類型的郵件。以下是一些您可以使用Exchange設定的常見案例的範例：

  - 範例 1 ︰ 避免給大型通訊群組的郵件衝擊

  - 範例 2： 將郵件轉寄給寄件者經理進行核准

  - 範例 3： 設定郵件核准鏈結

  - 範例 4： 將符合其中一個幾項準則的郵件轉寄

  - 範例 5 ︰ 轉寄郵件包含敏感資訊

## 範例 1 ︰ 避免給大型通訊群組的郵件衝擊

若要控制郵件給大型通訊群組，您可能需要仲裁者核准傳送給該群組的郵件。如果不有任何準則的郵件要求核准，最簡單方式為此設定是設定群組需要郵件核准。

在這個範例中，將所有員工\] 群組的所有郵件必須被都核准、 以外的寄件者是否名為 Legal 小組通訊群組的成員。

![通訊群組的訊息核准設定](images/Dd298007.77721509-93f9-4a90-8d77-986db2b0acf4(EXCHG.150).png "通訊群組的訊息核准設定")

若要要求特定通訊群組的郵件會核准、 Exchange 系統管理中心 (EAC) 中移至 \[**收件者**\>**群組**，編輯通訊群組，然後選取 \[**郵件核准**。

## 範例 2： 將郵件轉寄給寄件者經理進行核准

以下是一些常見的其可能會想要需要管理員核准的郵件類型：

  - 從使用者傳送至特定通訊群組或收件者的郵件

  - 郵件傳送給外部使用者或協力廠商

  - 兩個群組之間所寄送的郵件

  - 使用特定的內容，例如特定客戶的名稱傳送的郵件

  - 實習生所傳送的郵件

若需要核准的可傳送的訊息，請先建立規則使用 \[**傳送郵件給仲裁者**的範本，並選取郵件應移至 \[寄件者主管，如下列螢幕擷取畫面所示。

![使用範本來建立新的規則](images/Dd298007.051a5653-1a09-4db4-908f-48b56cc8d13f(EXCHG.150).png "使用範本來建立新的規則")

然後，定義需要核准的郵件。

以下是送出的實習生阮建輝由組織外部收件者的所有郵件都需要的管理員核准的範例。

![將訊息轉寄給使用者管理員的規則](images/Dd298007.7f94c22e-b5ba-45a3-9ccd-31996b6c863a(EXCHG.150).png "將訊息轉寄給使用者管理員的規則")

若要開始，請移至 EAC \>**郵件流程**\>**規則**，並建立新的規則使用 \[**傳送至仲裁者的郵件**\] 範本。


> [!IMPORTANT]  
> 在 [<strong>新增規則</strong>] 頁面上的預設的一些條件和動作，包括轉寄給寄件者的經理處於隱藏狀態。若要查看所有條件和動作，選取 [<strong>其他選項</strong>。




## 範例 3： 設定郵件核准鏈結

您可能需要核准的多個層級的郵件。例如，您可以要求客戶關係經理與法務，由特定客戶的郵件會先核准或您可以要求費用報表由兩個層級的管理員核准。

若要建立這種類型的多層核准，建立一個傳輸規則的每個核准層級。每個規則偵測相同模式中的郵件，如下所示：

  - 第一個規則將郵件轉寄至第一個核准者。當第一個核准者接受郵件時、 郵件自動會移到第二個規則中核准者。

  - 如果鏈結中的所有核准者選取**核准**完成鏈結中的最後一個核准時收到核准要求時，原始郵件會傳送給預定的收件者。

  - 如果核准鏈結中的任何人選取**拒絕**收到核准要求時，寄件者會收到拒絕郵件。

  - 如果有任何核准要求不核准 （2 天的Exchange Online、 Exchange Server 20135 天） 的到期時間內的寄件者會收到到期訊息。

下列範例假設您已經呼叫 Blue Yonder Airlines、 客戶，而且您希望客戶關係管理員及法務核准前往此客戶的所有郵件。您建立兩個規則，另一個適用於每個核准者。第一個規則會移到第一層核准者。第二個規則會移到第二層核准者。

![兩個用於核准層級的規則](images/Dd298007.29686c05-eaa0-42b9-86ad-d577f656392c(EXCHG.150).png "兩個用於核准層級的規則")

第一個規則會識別與公司名稱 Blue Yonder Airlines 主旨或郵件中的所有郵件並將這些訊息傳送到 Blue Yonder Airlines，Garret Vargas 的內部客戶關係管理員。

![第一層級核准者的規則](images/Dd298007.e22d1c04-85c5-4227-88e6-b118d5593350(EXCHG.150).png "第一層級核准者的規則")

第二個規則會將這些訊息傳送給法務 Tony Krijnen。

![第二層級核准規則，具有相同的準則](images/Dd298007.5d888786-8e48-4459-ab86-8a4b9a016d58(EXCHG.150).png "第二層級核准規則，具有相同的準則")

## 範例 4： 將符合其中一個幾項準則的郵件轉寄

傳輸規則中規則內設定的所有條件都必須要比對規則，則為 true。如果您要套用的任一條件的同一個動作，您應建立為每一個個別規則。

若要這樣做，在 EAC 中的 \[**規則**\] 頁面上建立第一個條件的規則。然後選取 \[規則、 選取的**複本**，並將變更中要比對的第二個條件的新規則的條件。

請小心當您建立多個規則"OR"條件與因此您不結束訊息傳送給核准多次。若要避免此問題，新增例外狀況的第二個規則讓它會忽略比對的第一個規則的郵件。

例如，單一規則無法檢查郵件是否要有 「 銷售報價"任一主旨中或附件標題中。若要避免所傳送的郵件多次來核准，如果第一個規則可檢查 「 銷售報價"主旨或內文的郵件中檢查的附件內容中的 「 銷售引號 」 的第二個規則需要包含的第一個規則條件的例外狀況。

![使用第二個規則的例外狀況](images/Dd298007.c39bbdcf-c619-4f84-8922-114ad1da824d(EXCHG.150).png "使用第二個規則的例外狀況")


> [!NOTE]  
> 在 [<strong>新增規則</strong>] 頁面上的預設會隱藏例外狀況。若要查看所有條件和動作，選取 [<strong>其他選項</strong>。




## 範例 5 ︰ 轉寄郵件包含敏感資訊

如果您有 「 [資料遺失防護](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)(DLP) 」 功能，是預先定義的許多的敏感資訊類型。使用 DLP，您會看到郵件包含敏感資訊條件。有 DLP，您可以建立識別是唯一的貴組織的特定的敏感資訊模式的條件。

以下是敏感資訊的郵件要求核准的其中一個範例。在此範例中包含信用卡號郵件需要核准。

![轉寄具有機密資訊之郵件的規則](images/Dd298007.7ec1ca74-5d20-42ea-a9ee-3a8b25beb7df(EXCHG.150).png "轉寄具有機密資訊之郵件的規則")

## 請參閱


[管理郵件核准](manage-message-approval-exchange-2013-help.md)

