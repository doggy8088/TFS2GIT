
主要說明
--------

支援正體中文版的 TFS2GIT.ps1 指令檔。

Instructions on how to use this script can be found at 
http://walkingthestack.blogspot.com/2010/09/importing-tfs-repository-into-git.html

使用範例
--------

套用預設值

	TFS2GIT.ps1 $/repository

或

	TFS2GIT.ps1 -TFSRepository $/repository

指定特定版本範圍

	TFS2GIT.ps1 -TFSRepository $/repository -StartingCommit 1 -EndingCommit 100

指定使用者對應檔

	TFS2GIT.ps1 -TFSRepository $/repository -UserMappingfile filename

完整範例

	Tfs2Git.ps1 -TFSRepository $/DoggyENS -WorkspaceName DoggyENS -GitRepository DoggyENS.git -UserMappingFile .\userMappings.txt


參數說明
--------

-TFSRepository (必要的)
請設定你想要匯入 GIT 的 TFS 儲存庫，例如：$/repository. 

-GitRepository (選項)
請設定你想要建立的 GIT 儲存庫名稱(資料夾名稱)，若未輸入預設為 'ConvertedFromTFS.git'

-Collection (選項)
請設定你目前的集合網址(FQDN)

-WorkSpaceName (選項)
在匯入期間，預設會在本地建立一個工作區，你可以指定工作區名稱，預設為 'TFS2GIT'

-StartingCommit (選項)
You can import a sequential range of commits. Specify the first TFS commit you want to import.
When this parameter is used, EndingCommit must also be used.

-EndingCommit (選項)
You can import a sequential range of commits. Specify the last TFS commit you want to import.
When this parameter is used, StartingCommit must also be used.

-UserMappingFile (選項)
通常你需要指定一個「使用者對應檔」用以轉換 TFS 上人員的身分到 GIT 版控中。
請查看 'userMappings.txt' 範例檔案。

userMappings.txt 注意事項
----------------------------------

* 格式: ```TFS帳號=GIT帳號```
* TFS帳號可能的格式:
	* 本機帳號: will
	* 網域帳號: DC1\will
* GIT帳號的格式:
	* ```姓名``` &lt;```EMAIL```&gt;
	* 注意: **姓名** 與 **&lt;** 之間一定要加上一個空白字元，否則會無法建立版本。

感謝
----

此工具基於 Wilbert van Dolleweerd (wilbert@arentheym.com) 的 [WilbertOnGithub/TFS2GIT](https://github.com/WilbertOnGithub/TFS2GIT) 專案進行延伸開發。